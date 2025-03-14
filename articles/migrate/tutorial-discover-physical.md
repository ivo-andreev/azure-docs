---
title: Discover physical servers with Azure Migrate Discovery and assessment
description: Learn how to discover on-premises physical servers with Azure Migrate Discovery and assessment.
author: Vikram1988
ms.author: vibansa
ms.manager: abhemraj
ms.topic: tutorial
ms.date: 04/27/2022
ms.custom: mvc, subject-rbac-steps
#Customer intent: As a server admin I want to discover my on-premises server inventory.
---

# Tutorial: Discover physical servers with Azure Migrate: Discovery and assessment

As part of your migration journey to Azure, you discover your servers for assessment and migration.

This tutorial shows you how to discover on-premises physical servers with the Azure Migrate: Discovery and assessment tool, using a lightweight Azure Migrate appliance. You deploy the appliance as a physical server, to continuously discover servers and performance metadata.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Set up an Azure account.
> * Prepare physical servers for discovery.
> * Create a project.
> * Set up the Azure Migrate appliance.
> * Start continuous discovery.

> [!NOTE]
> Tutorials show the quickest path for trying out a scenario, and use default options.  

If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/free-trial/) before you begin.

## Prerequisites

Before you start this tutorial, ensure you have these prerequisites in place.

**Requirement** | **Details**
--- | ---
**Appliance** | You need a server to run the Azure Migrate appliance. The server should have:<br/><br/> - Windows Server 2016 installed.<br/> _(Currently the deployment of appliance is only supported on Windows Server 2016.)_<br/><br/> - 16-GB RAM, 8 vCPUs, around 80 GB of disk storage<br/><br/> - A static or dynamic IP address, with internet access, either directly or through a proxy.<br/><br/> - Outbound internet connectivity to the required [URLs](migrate-appliance.md#url-access) from the appliance.
**Windows servers** | Allow inbound connections on WinRM port 5985 (HTTP) for discovery of Windows servers.
**Linux servers** | Allow inbound connections on port 22 (TCP) for discovery of Linux servers.

> [!NOTE]
> It is unsupported to install the Azure Migrate Appliance on a server that has the [replication appliance](migrate-replication-appliance.md) or mobility service agent installed.  Ensure that the appliance server has not been previously used to set up the replication appliance or has the mobility service agent installed on the server.

## Prepare an Azure user account

To create a project and register the Azure Migrate appliance, you need an account with:
- Contributor or Owner permissions on an Azure subscription.
- Permissions to register Azure Active Directory apps.

If you just created a free Azure account, you're the owner of your subscription. If you're not the subscription owner, work with the owner to assign the permissions as follows:

1. In the Azure portal, search for "subscriptions", and under **Services**, select **Subscriptions**.

    ![Screenshot of search box to search for the Azure subscription.](./media/tutorial-discover-physical/search-subscription.png)

1. Select **Access control (IAM)**.

1. Select **Add** > **Add role assignment** to open the **Add role assignment** page.

1. Assign the following role. For detailed steps, see [Assign Azure roles using the Azure portal](../role-based-access-control/role-assignments-portal.md).

    | Setting | Value |
    | --- | --- |
    | Role | Contributor or Owner |
    | Assign access to | User |
    | Members | azmigrateuser |

    ![Add role assignment page in Azure portal.](../../includes/role-based-access-control/media/add-role-assignment-page.png)

1. To register the appliance, your Azure account needs **permissions to register Azure Active Directory apps.**

1. In Azure portal, navigate to **Azure Active Directory** > **Users** > **User Settings**.

1. In **User settings**, verify that Azure AD users can register applications (set to **Yes** by default).

    ![Verify in User Settings that users can register Active Directory apps.](./media/tutorial-discover-physical/register-apps.png)

1. In case the 'App registrations' settings is set to 'No', request the tenant/global admin to assign the required permission. Alternately, the tenant/global admin can assign the **Application Developer** role to an account to allow the registration of Azure Active Directory App. [Learn more](../active-directory/fundamentals/active-directory-users-assign-role-azure-portal.md).

## Prepare physical servers

Set up an account that the appliance can use to access the physical servers.

**Windows servers**

For Windows servers, use a domain account for domain-joined servers, and a local account for servers that are not domain-joined. The user account can be created in one of the two ways:

### Option 1

- Create an account that has administrator privileges on the servers. This account can be used to pull configuration and performance data through CIM connection and perform software inventory (discovery of installed applications) and enable agentless dependency analysis using PowerShell remoting.

> [!Note]
> If you want to perform software inventory (discovery of installed applications) and enable agentless dependency analysis on Windows servers, it recommended to use Option 1.

### Option 2
- The user account should be added to these groups: Remote Management Users, Performance Monitor Users, and Performance Log Users.
- If Remote management Users group isn't present, then add the user account to the group: **WinRMRemoteWMIUsers_**.
- The account needs these permissions for the appliance to create a CIM connection with the server and pull the required configuration and performance metadata from the WMI classes listed here.
- In some cases, adding the account to these groups may not return the required data from WMI classes as the account might be filtered by [UAC](/windows/win32/wmisdk/user-account-control-and-wmi). To overcome the UAC filtering, user account needs to have necessary permissions on CIMV2 Namespace and sub-namespaces on the target server. You can follow the steps [here](troubleshoot-appliance.md) to enable the required permissions.

    > [!Note]
    > For Windows Server 2008 and 2008 R2, ensure that WMF 3.0 is installed on the servers.

**Linux servers**

For Linux servers, you can create a user account in one of three ways:

### Option 1
- You need a root account on the servers that you want to discover. This account can be used to pull configuration and performance metadata and perform software inventory (discovery of installed applications) and enable agentless dependency analysis using SSH connectivity.

> [!Note]
> If you want to perform software inventory (discovery of installed applications) and enable agentless dependency analysis on Windows servers, it recommended to use Option 1.

### Option 2
- To discover the configuration and performance metadata from Linux servers, you can provide a user account with sudo permissions.
- The support to add a user account with sudo access is provided by default with the new appliance installer script downloaded from portal after July 20,2021.
- For older appliances, you can enable the capability by following these steps:
    1. On the server running the appliance, open the Registry Editor.
    1. Navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AzureAppliance.
    1. Create a registry key ‘isSudo’ with DWORD value of 1.

    :::image type="content" source="./media/tutorial-discover-physical/issudo-reg-key.png" alt-text="Screenshot that shows how to enable sudo support.":::

- You need to enable sudo access for the commands listed [here](discovered-metadata.md#linux-server-metadata). Make sure that you have enabled 'NOPASSWD' for the account to run the required commands without prompting for a password every time sudo command is invoked.
- The following Linux OS distributions are supported for discovery by Azure Migrate using an account with sudo access:

    Operating system | Versions 
    --- | ---
    Red Hat Enterprise Linux | 6,7,8
    Cent OS | 6.6, 8.2
    Ubuntu | 14.04,16.04,18.04
    SUSE Linux | 11.4, 12.4
    Debian | 7, 10
    Amazon Linux | 2.0.2021
    CoreOS Container | 2345.3.0

### Option 3
- If you cannot provide root account or user account with sudo access, then you can set 'isSudo' registry key to value '0' in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AzureAppliance registry and provide a non-root account with the required capabilities using the following commands:

**Command** | **Purpose**
--- | --- |
setcap CAP_DAC_READ_SEARCH+eip /usr/sbin/fdisk <br></br> setcap CAP_DAC_READ_SEARCH+eip /sbin/fdisk _(if /usr/sbin/fdisk is not present)_ | To collect disk configuration data
setcap "cap_dac_override,cap_dac_read_search,cap_fowner,cap_fsetid,cap_setuid,<br> cap_setpcap,cap_net_bind_service,cap_net_admin,cap_sys_chroot,cap_sys_admin,<br> cap_sys_resource,cap_audit_control,cap_setfcap=+eip" /sbin/lvm | To collect disk performance data
setcap CAP_DAC_READ_SEARCH+eip /usr/sbin/dmidecode | To collect BIOS serial number
chmod a+r /sys/class/dmi/id/product_uuid | To collect BIOS GUID

## Set up a project

Set up a new project.

1. In the Azure portal > **All services**, search for **Azure Migrate**.
2. Under **Services**, select **Azure Migrate**.
3. In **Overview**, select **Create project**.
5. In **Create project**, select your Azure subscription and resource group. Create a resource group if you don't have one.
6. In **Project Details**, specify the project name and the geography in which you want to create the project. Review supported geographies for [public](migrate-support-matrix.md#public-cloud) and [government clouds](migrate-support-matrix.md#azure-government).

   ![Screenshot of project name and region.](./media/tutorial-discover-physical/new-project.png)

7. Select **Create**.
8. Wait a few minutes for the project to deploy. The **Azure Migrate: Discovery and assessment** tool is added by default to the new project.

    ![Page showing Server Assessment tool added by default.](./media/tutorial-discover-physical/added-tool.png)

> [!NOTE]
> If you have already created a project, you can use the same project to register additional appliances to discover and assess more no of servers. [Learn more](create-manage-projects.md#find-a-project).

## Set up the appliance

Azure Migrate appliance performs server discovery and sends server configuration and performance metadata to Azure Migrate. The appliance can be set up by executing a PowerShell script that can be downloaded from the project.

To set up the appliance, you:

1. Provide an appliance name and generate a project key in the portal.
2. Download a zipped file with the Azure Migrate installer script from the Azure portal.
3. Extract the contents from the zipped file. Launch the PowerShell console with administrative privileges.
4. Execute the PowerShell script to launch the appliance configuration manager.
5. Configure the appliance for the first time, and register it with the project using the project key.

### 1. Generate the project key

1. In **Migration goals** > **Servers, databases and web apps** > **Azure Migrate: Discovery and assessment**, select **Discover**.
2. In **Discover servers** > **Are your servers virtualized?**, select **Physical or other (AWS, GCP, Xen, etc.)**.
3. In **1:Generate project key**, provide a name for the Azure Migrate appliance that you will set up for discovery of physical or virtual servers. The name should be alphanumeric with 14 characters or fewer.
1. Click on **Generate key** to start the creation of the required Azure resources. Do not close the Discover servers page during the creation of resources.
1. After the successful creation of the Azure resources, a **project key** is generated.
1. Copy the key as you will need it to complete the registration of the appliance during its configuration.

    [ ![Selections for Generate Key.](./media/tutorial-assess-physical/generate-key-physical-inline-1.png)](./media/tutorial-assess-physical/generate-key-physical-expanded-1.png#lightbox)

### 2. Download the installer script

In **2: Download Azure Migrate appliance**, click **Download**.

### Verify security

Check that the zipped file is secure, before you deploy it.

1. On the server to which you downloaded the file, open an administrator command window.
2. Run the following command to generate the hash for the zipped file:
    - ```C:\>CertUtil -HashFile <file_location> [Hashing Algorithm]```
    - Example usage: ```C:\>CertUtil -HashFile C:\Users\administrator\Desktop\AzureMigrateInstaller.zip SHA256 ```
3.  Verify the latest appliance version and hash value:

    **Download** | **Hash value**
    --- | ---
    [Latest version](https://go.microsoft.com/fwlink/?linkid=2140334) | 7745817a5320628022719f24203ec0fbf56a0e0f02b4e7713386cbc003f0053c

> [!NOTE]
> The same script can be used to set up Physical appliance for either Azure public or Azure Government cloud with public or private endpoint connectivity.


### 3. Run the Azure Migrate installer script

1. Extract the zipped file to a folder on the server that will host the appliance.  Make sure you don't run the script on a server with an existing Azure Migrate appliance.

2. Launch PowerShell on the above server with administrative (elevated) privilege.

3. Change the PowerShell directory to the folder where the contents have been extracted from the downloaded zipped file.

4. Run the script named `AzureMigrateInstaller.ps1` by running the following command:

   `PS C:\Users\administrator\Desktop\AzureMigrateInstaller> .\AzureMigrateInstaller.ps1`

5. Select from the scenario, cloud, and connectivity options to deploy an appliance with the desired configuration. For instance, the selection shown below sets up an appliance to discover and assess **physical servers** _(or servers running on other clouds like AWS, GCP, Xen etc.)_ to an Azure Migrate project with **default _(public endpoint)_ connectivity** on **Azure public cloud**.

   :::image type="content" source="./media/tutorial-discover-physical/script-physical-default-inline.png" alt-text="Screenshot that shows how to set up appliance with desired configuration." lightbox="./media/tutorial-discover-physical/script-physical-default-expanded.png":::

6. The installer script does the following:

   - Installs agents and a web application.
   - Installs Windows roles, including Windows Activation Service, IIS, and PowerShell ISE.
   - Downloads and installs an IIS rewritable module.
   - Updates a registry key (HKLM) with persistent setting details for Azure Migrate.
   - Creates the following files under the path:
     - **Config Files:** `%ProgramData%\Microsoft Azure\Config`
     - **Log Files:** `%ProgramData%\Microsoft Azure\Logs`

After the script has executed successfully, the appliance configuration manager will be launched automatically.

> [!NOTE]
> If you come across any issues, you can access the script logs at C:\ProgramData\Microsoft Azure\Logs\AzureMigrateScenarioInstaller_<em>Timestamp</em>.log for troubleshooting.

### Verify appliance access to Azure

Make sure that the appliance can connect to Azure URLs for [public](migrate-appliance.md#public-cloud-urls) and [government](migrate-appliance.md#government-cloud-urls) clouds.

### 4. Configure the appliance

Set up the appliance for the first time.

1. Open a browser on any server that can connect to the appliance, and open the URL of the appliance web app: **https://*appliance name or IP address*: 44368**.

   Alternately, you can open the app from the desktop by clicking the app shortcut.
1. Accept the **license terms**, and read the third-party information.

#### Set up prerequisites and register the appliance

In the configuration manager, select **Set up prerequisites**, and then complete these steps:
1. **Connectivity**: The appliance checks that the server has internet access. If the server uses a proxy:
    - Select **Setup proxy** to specify the proxy address (in the form `http://ProxyIPAddress` or `http://ProxyFQDN`, where *FQDN* refers to a *fully qualified domain name*) and listening port.
    - Enter credentials if the proxy needs authentication.
    - If you have added proxy details or disabled the proxy or authentication, select **Save** to trigger connectivity and check connectivity again.
    
        Only HTTP proxy is supported.
1. **Time sync**: Check that the time on the appliance is in sync with internet time for discovery to work properly.
1. **Install updates and register appliance**: To run auto-update and register the appliance, follow these steps:

    :::image type="content" source="./media/tutorial-discover-vmware/prerequisites.png" alt-text="Screenshot that shows setting up the prerequisites in the appliance configuration manager.":::

    > [!NOTE]
    > This is a new user experience in Azure Migrate appliance which is available only if you have set up an appliance using the latest OVA/Installer script downloaded from the portal. The appliances which have already been registered will continue seeing the older version of the user experience and will continue to work without any issues.

    1. For the appliance to run auto-update, paste the project key that you copied from the portal. If you don't have the key, go to **Azure Migrate: Discovery and assessment** > **Overview** > **Manage existing appliances**. Select the appliance name you provided when you generated the project key, and then copy the key that's shown.
	2. The appliance will verify the key and start the auto-update service, which updates all the services on the appliance to their latest versions. When the auto-update has run, you can select **View appliance services** to see the status and versions of the services running on the appliance server.
    3. To register the appliance, you need to select **Login**. In **Continue with Azure Login**, select **Copy code & Login** to copy the device code (you must have a device code to authenticate with Azure) and open an Azure Login prompt in a new browser tab. Make sure you've disabled the pop-up blocker in the browser to see the prompt.
    
        :::image type="content" source="./media/tutorial-discover-vmware/device-code.png" alt-text="Screenshot that shows where to copy the device code and log in.":::
    4. In a new tab in your browser, paste the device code and sign in by using your Azure username and password. Signing in with a PIN isn't supported.
	    > [!NOTE]
        > If you close the login tab accidentally without logging in, refresh the browser tab of the appliance configuration manager to display the device code and Copy code & Login button.
	5. After you successfully log in, return to the browser tab that displays the appliance configuration manager. If the Azure user account that you used to log in has the required permissions for the Azure resources that were created during key generation, appliance registration starts.

        After the appliance is successfully registered, to see the registration details, select **View details**.

You can *rerun prerequisites* at any time during appliance configuration to check whether the appliance meets all the prerequisites.

## Start continuous discovery

Now, connect from the appliance to the physical servers to be discovered, and start the discovery.

1. In **Step 1: Provide credentials for discovery of Windows and Linux physical or virtual servers​**, click on **Add credentials**.
1. For Windows server, select the source type as **Windows Server**, specify a friendly name for credentials, add the username and password. Click on **Save**.
1. If you are using password-based authentication for Linux server, select the source type as **Linux Server (Password-based)**, specify a friendly name for credentials, add the username and password. Click on **Save**.
1. If you are using SSH key-based authentication for Linux server, you can select source type as **Linux Server (SSH key-based)**, specify a friendly name for credentials, add the username, browse and select the SSH private key file. Click on **Save**.

    - Azure Migrate supports the SSH private key generated by ssh-keygen command using RSA, DSA, ECDSA, and ed25519 algorithms.
    - Currently Azure Migrate does not support passphrase-based SSH key. Use an SSH key without a passphrase.
    - Currently Azure Migrate does not support SSH private key file generated by PuTTY.
    - The SSH key file supports CRLF to mark a line break in the text file that you upload. SSH keys created on Linux systems most commonly have LF as their newline character so you can convert them to CRLF by opening the file in vim, typing `:set textmode` and saving the file.
    - Azure Migrate supports OpenSSH format of the SSH private key file as shown below:
    
    ![Screenshot of SSH private key supported format.](./media/tutorial-discover-physical/key-format.png)

1. If you want to add multiple credentials at once, click on **Add more** to save and add more credentials. Multiple credentials are supported for physical servers discovery.
1. In **Step 2:Provide physical or virtual server details​**, click on **Add discovery source** to specify the server **IP address/FQDN** and the friendly name for credentials to connect to the server.
1. You can either **Add single item** at a time or **Add multiple items** in one go. There is also an option to provide server details through **Import CSV**.


    - If you choose **Add single item**, you can choose the OS type, specify friendly name for credentials, add server **IP address/FQDN** and click on **Save**.
    - If you choose **Add multiple items**, you can add multiple records at once by specifying server **IP address/FQDN** with the friendly name for credentials in the text box. **Verify** the added records and click on **Save**.
    - If you choose **Import CSV** _(selected by default)_, you can download a CSV template file, populate the file with the server **IP address/FQDN** and friendly name for credentials. You then import the file into the appliance, **verify** the records in the file and click on **Save**.

1. On clicking Save, the appliance will try validating the connection to the servers added and show the **Validation status** in the table against each server.
    - If validation fails for a server, review the error by clicking on **Validation failed** in the Status column of the table. Fix the issue, and validate again.
    - To remove a server, click on **Delete**.
1. You can **revalidate** the connectivity to servers anytime before starting the discovery.
1. Before initiating discovery, you can choose to disable the slider to not perform software inventory and agentless dependency analysis on the added servers. You can change this option at any time.

    :::image type="content" source="./media/tutorial-discover-physical/disable-slider.png" alt-text="Screenshot that shows where to disable the slider.":::

### Start discovery

Click on **Start discovery**, to kick off discovery of the successfully validated servers. After the discovery has been successfully initiated, you can check the discovery status against each server in the table.

## How discovery works

* It takes approximately 2 minutes to complete discovery of 100 servers and their metadata to appear in the Azure portal.
* [Software inventory](how-to-discover-applications.md) (discovery of installed applications) is automatically initiated when the discovery of servers is finished.
* The time taken for discovery of installed applications depends on the number of discovered servers. For 500 servers, it takes approximately one hour for the discovered inventory to appear in the Azure Migrate project in the portal.
* During software inventory, the added server credentials are iterated against servers and validated for agentless dependency analysis. When the discovery of servers is finished, in the portal, you can enable agentless dependency analysis on the servers. Only the servers on which validation succeeds can be selected to enable [agentless dependency analysis](how-to-create-group-machine-dependencies-agentless.md).

## Verify servers in the portal

After discovery finishes, you can verify that the servers appear in the portal.

1. Open the Azure Migrate dashboard.
2. In **Azure Migrate - Servers** > **Azure Migrate: Discovery and assessment** page, click the icon that displays the count for **Discovered servers**.

## Delete servers
After the discovery has been initiated, you can delete any of the added servers from the appliance configuration manager by searching for the server name in the **Add discovery source** table and by clicking **Delete**.

>[!NOTE]
> If you choose to delete a server where discovery has been initiated, it will stop the ongoing discovery and assessment which may impact the confidence rating of the assessment that includes this server. [Learn more](./common-questions-discovery-assessment.md#why-is-the-confidence-rating-of-my-assessment-low)

## Next steps

- [Assess physical servers](tutorial-assess-physical.md) for migration to Azure VMs.
- [Review the data](discovered-metadata.md#collected-data-for-physical-servers) that the appliance collects during discovery.