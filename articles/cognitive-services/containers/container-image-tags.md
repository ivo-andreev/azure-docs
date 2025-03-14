---
title: Cognitive Services container image tags
titleSuffix: Azure Cognitive Services
description: A comprehensive listing of all the Cognitive Service container image tags.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.topic: reference
ms.date: 03/14/2022
ms.author: aahi
---

# Azure Cognitive Services container image tags and release notes

Azure Cognitive Services offers many container images. The container registries and corresponding repositories vary between container images. Each container image name offers multiple tags. A container image tag is a mechanism of versioning the container image. This article is intended to be used as a comprehensive reference for listing all the Cognitive Services container images and their available tags.

> [!NOTE]
> See [Form Recognizer container image tags and release notes](../../applied-ai-services/form-recognizer/containers/form-recognizer-container-image-tags.md) for **Applied AI Services Form Recognizer** container tag information and updates.

> [!TIP]
> When using [`docker pull`](https://docs.docker.com/engine/reference/commandline/pull/), pay close attention to the casing of the container registry, repository, container image name and corresponding tag - as they are **case sensitive**.

## Anomaly Detector

The [Anomaly Detector][ad-containers] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/decision` repository and is named `anomaly-detector`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/decision/anomaly-detector`.

This container image has the following tags available. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/decision/anomaly-detector/tags/list).

# [Latest version](#tab/current)

| Image Tags                    | Notes |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.013560003-amd64-preview` |      |

# [Previous versions](#tab/previous)

| Image Tags                    | Notes |
|-------------------------------|:------|
| `1.1.012300001-amd64-preview` |       |

---

## Read OCR (Optical Character Recognition)

The [Computer Vision][cv-containers] Read OCR container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services` repository and is named `read`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/vision/read`.

This container image has the following tags available. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/vision/read/tags/list).

# [Latest version](#tab/current)

Release notes for `3.2`:

* Read OCR container is now generally available.

| Image Tags                    | Notes |
|-------------------------------|:------|
| `3.2`                     |       |

# [Previous versions](#tab/previous)


Release notes for `3.2-preview.2`:

* Distroless release
* ReadingOrder parameter to choose between text line order in JSON response
* Enhanced logging
* Hotfixes to CJK model
* 
Release notes for `v2.0.013250001-amd64-preview`:

* Further decrease memory usage for container.
* External cache is required for multi-pods setup. For example, set-up Redis for caching.
* Fixed missing results when Redis cache is set-up and `ResultExpirationPeriod` is set to 0.
* Remove request body size limitation of 26MB. Container can now accept >26MB files.
* Add time stamp and build version to console logging.

Release notes for `1.1.013050001-amd64-preview`

* Added `ReadEngineConfig:ResultExpirationPeriod` container initialization configuration to specify when the system should clean up recognition results. 
    * The setting is in hours, and the default value is 48 hours.
    * The setting can reduce memory usage for result storing, especially when container in-memory storage is used.
    * Example 1. ReadEngineConfig:ResultExpirationPeriod=1, the system will clear the recognition result 1hr after the process.
    * If this configuration is set to 0, the system will clear the recognition result after the result is retrieved.

* Fixed a 500 internal server error when an invalid image format is passed to the system. It will now return a 400 error:

    ```json
    {
        "error": {
        "code": "InvalidImageSize",
        "message": "Image must be between 1024 and 209715200 bytes."
        }
    }
    ```

| Image Tags                    | Notes |
|-------------------------------|:------|
| `3.2.2.014850001-49e0eac6-amd64-preview` |       |
| `2.0.013250001-amd64-preview` |       |
| `1.1.013050001-amd64-preview` |       |
| `1.1.011580001-amd64-preview` |       |
| `1.1.009920003-amd64-preview` |       |
| `1.1.009910003-amd64-preview` |       |

---

## Language Understanding (LUIS)

The [LUIS][lu-containers] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/language` repository and is named `luis`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/language/luis`.

This container image has the following tags available. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/language/luis/tags/list).

# [Latest version](#tab/current)

| Image Tags                    | Notes |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.012280003-amd64-preview` |       |


# [Previous version](#tab/previous)

| Image Tags                    | Notes |
|-------------------------------|:------|
| `1.1.012130003-amd64-preview` |       |

---

## Custom Speech-to-text

The [Custom Speech-to-text][sp-cstt] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/speechservices/` repository and is named `custom-speech-to-text`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/speechservices/custom-speech-to-text`. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/custom-speech-to-text/tags/list).


# [Latest version](#tab/current)

Release note for `3.2.0-amd64`:

**Features**
* Security upgrade.
* HTTP Proxy support.
* Improve custom speech model download output message.
* Speech components upgrade.

Note that due to the phrase lists feature, the size of this container image has increased.

| Image Tags                    | Notes | Digest                                                                   |
|-------------------------------|:------|:-------------------------------------------------------------------------|
| `latest`                      |       | `sha256:90e5d8c1675571de926bfffd0e9844fabe8d763cc881bdbccb5bb4faa0258122`|
| `3.1.0-amd64`                 |       | `sha256:90e5d8c1675571de926bfffd0e9844fabe8d763cc881bdbccb5bb4faa0258122`|


# [Previous version](#tab/previous)

Release note for `3.1.0-amd64`:

**Features**
* Support Full Display Process. The final display outcomes is expected highly improved if this feature is enabled.
* Security Upgrade.

Release note for `3.0.0-amd64`:

**Features**
* Support for using containers in [disconnected environments](disconnected-containers.md).

Release note for `2.18.0-amd64`:

Regular monthly upgrade

Release note for `2.17.0-amd64`:

**Features**
* Upgrade to latest `media`, `text` component.

**Fixes**
* Security patches

Release note for `2.16.0-amd64`:

Regular monthly upgrade

Release note for `2.15.0-amd64`:

**Fixes**

* Fix container start issue that may occur when customers run it in some RHEL environments.
* Fix model download nil error issue in some cases when customers download customized models.


Release note for `2.14.0-amd64`:

Regular monthly release

Release note for `2.13.0-amd64`:

Regular monthly release

Release note for `2.12.1-amd64`:

Regular monthly release

Release note for `2.11.0-amd64`:

**Fixes**
* Keep user's inputs case-sensitive.

Release note for `2.10.0-amd64`:

Regular monthly release

Release note for `2.9.0-amd64`:

**Features**
* More error details for issues when fetching custom models by ID.
* Hypothesis is supported in conversation results by default.

Release note for `2.7.0-amd64`:

**Features**
* Punctuation is set as enabled by default.

Note that due to the included phrase lists, the size of this container image has increased.

Release note for `2.6.0-amd64`:

**Features**
* Support for phraselist v2 
* Phrase lists are supported in the following locales:
    * en-au
    * en-ca
    * en-gb
    * en-in
    * en-us
    * zh-cn
* Support for custom base model download. 
    * Use `BaseModelLocale=<locale>` with the `docker run` command
* Fully migrated to .NET 3.1

**Fixes**
* Fixed an issue where the confidence score was always 1 in Diarization mode
* Migrated to the TextAnalytics 3.0 api

Note that due to the included phrase lists, the size of this container image has increased.

Release note for `2.5.0-amd64`:

**Features**
* Support custom pronunciation on custom models
* Support Azure and Azure US Government Cloud

**Fixes**
* Fix run as non-root user issue on Diarization mode

| Image Tags                    | Notes               |
|-------------------------------|:--------------------|
| `3.1.0-amd64`                 |                     |
| `3.0.0-amd64`                 |                     |
| `2.18.0-amd64`                |                     |
| `2.17.0-amd64`                |                     |
| `2.16.0-amd64`                |                     |
| `2.15.0-amd64`                |                     |
| `2.14.0-amd64`                |                     |
| `2.13.0-amd64`                |                     |
| `2.12.1-amd64`                |                     |
| `2.11.0-amd64`                |                     |
| `2.10.0-amd64`                |                     |
| `2.9.0-amd64`                 |                     |
| `2.7.0-amd64`                 |                     |
| `2.6.0-amd64`                 |                     |
| `2.5.0-amd64`                 |   1st GA version    |

---

## Speech-to-text

The [Speech-to-text][sp-stt] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/speechservices/` repository and is named `speech-to-text`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/speechservices/speech-to-text`. You can find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/speech-to-text/tags/list).

Since Speech-to-text v2.5.0, images are supported in the *US Government Virginia* region. Please use the *US Government Virginia* billing endpoint and API keys when using this region.

# [Latest version](#tab/current)

Release note for `3.2.0-amd64-<locale>`:

**Features**
* Security upgrade.
* Speech components upgrade.
* HTTP Proxy support.

Note that due to the phrase lists feature, the size of this container image has increased. 

| Image Tags                    | Notes                                                                                                |
|-------------------------------|:-----------------------------------------------------------------------------------------------------|
| `latest`                      | Container image with the `en-US` locale.                                                             |
| `3.2.0-amd64-<locale>`        | Replace `<locale>` with one of the available locales, listed below. For example `3.2.0-amd64-en-us`. |

This container has the following locales available.

| Locale for v3.2.0           | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:d63c13880627778742e42e00e25fd61aef1c4ee713e5def90642c68ddebc33c6` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:22e8d931602bb91a86a68caac2c81e323ee9039b0bbd6bb19db35997b7fbd359` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:80e8e9c6cfec8e53f9b04dcf20d1ee555bd89e72f8c0cdef88b1fbfbd83d6c6c` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:4a4810d2c3c0be63787994db412845909f10582d428620c70afb41bbeac1d034` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:acca38a880c5ef6575647d372769acaaa7f14de848b3d07daa05138a27b51d96` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:d63c13880627778742e42e00e25fd61aef1c4ee713e5def90642c68ddebc33c6` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:3522d12e3be5eff50b4b33f41c51a137f0efe86aa9a7070ce3b84c78057804c7` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:2a586ff0be16883091e4853f1a15ce0c412e75936db57ad8e6b1a1d8321e2a46` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:d63c13880627778742e42e00e25fd61aef1c4ee713e5def90642c68ddebc33c6` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:d63c13880627778742e42e00e25fd61aef1c4ee713e5def90642c68ddebc33c6` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:082ae364aaffd636676ed0cea755fcc3d0c2654ccd1a5659dada7dc135d43196` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:e6639b807c3988f39b8a9478d043b847cc6e6223892840323ddd81883a8519c1` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:56570074924735a5952e280aab4e369be4c16b5d8fef14d1f2a6aa7946018e7b` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:bc8661627ce501091f0754d7062686882c5084cfbd9cb76670cd4e83a04f1834` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:2843edc7b98bc189ded859d17ce8f92a650c73caa4e3ebb6752ea06241ce3bdf` |
| `de-at`                     | Container image with the `de-AT` locale. | `sha256:e6b55644ebf9e0e9cf5072725a331a688c65f5b0e3a4257aea11470110c4aa71` |
| `de-ch`                     | Container image with the `de-CH` locale. | `sha256:57fe70566d02e2dee1078fd7b1effdf82ebad01aed9195051b3fc27f81239e09` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:f6d46be11e09e01ccf99de0c643fefb38ed2d705ec693d797bc7543202b34007` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:e5182ee56f28f43dafe9d503a659bc80e569a7fd6fbc57bc47465feea516c4fc` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:1e400d993fe59757fc4cf3de67d6b27654a9f53e21cb274145432ad6b880a7c6` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:49c5bf1b0d5c83ddd85574005fb56b6e13c11fbc0590af7e731d8b5a603adee1` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:d716caaf2e3699ef48e68cc5835b4fbcc8da756076efa30db1ba931cf995bf72` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:5a9973801f79fec0faa591de42bd33e32c5b06b157d70ae7a5131cdcc05ea4e8` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:c370b14c5fc0121201f6a14c7b713970ae02e6fce1d94b6768f9e301d793cb6f` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:a3fb074743369368233e8028f3c36e335fc04facff9b8700d1a092aba1dff3ac` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:71ed81d050168774f89da32854a0be5dbe4d89636109fc604d11afba313517ea` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:0bb215fc8ce0e669add37630f90e42c93d6936e159ccd1a3fb83e9039212c2a5` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:7b827a8f75610bc7f4838857e94231d50e4cb2c3602010ad00b0e970da45d6ef` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:8141da6240e78c7b81955ee91c71eb7dec17f345c9b4dbe577494ee9e159bf5a` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:9fe15bf9e12fe4185f8f3295f7f2a6a8563f894754537c1d8cd403a60763010f` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:a136551dc0d33791deb370ee7af0ce198110467639a56f4e17a926b56808b0a9` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:937cbabebf4f03dc0031e6716d6148479f5bba4d5dd9b7563a4dfa154b6eeace` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:b0b9a7cdf96ddda5b90067c4efe7d4e8fb11ab2e3df05f5727b4e8aa916ff102` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:d639e4db6e3c005f76d36079514e2771e2516ebde86ba6594a9c9691453d0667` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:01e2de748bd3632b1a4e25ae9a53503dcfbfc6d4f90f1a4ca804ca3045b6d1df` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:1c25106375dbc5846a5ff1c5f594f969efeeb81d6fdb520dd41fae52f23dcc27` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:2f403243e5b7e097708532903777cf65ea95ab901067fe406a6aba81fc54819c` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:164a27ae9c122617197ed67f6df3ac8bb1b38347d2f1e6dcd72254ff5c4cc92b` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:a39b95ffb862a82345780210aa5e7a8991fe271d55bf8c36693ce81a7adb0739` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:90c3c225666dc74f6fe74cbbc8bc8c339a469c36c51ee87a9921253366c6ce69` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:fc9e3c9e9dfc0bfda67d11fc9dba3edc62d65187bc9f54de68f473305639d147` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:f2e15fe3dca24366240f4f20fc683c45d3a59c1150481f9286dedeb1113ec4da` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:bdd341e3180888c3e0bd8fe271d1dccb95be82eca4a0b96ccfeba8f849d5c2d7` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:065c343fa668f6ecc580c6e0e0284c76921428a458b50a02f0e7c6a0f65ae155` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:17e801c032d8259cdd969ae4de492b1bd57aee9fe1f7345b276e69e93e91d8df` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:79d846898998a801f3306657b2ef7a03c083684dec4f59700d82a569a293d5bd` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:f8efedcf1e8a2c078ff6e1e9c8a958a8d87e1390b51d2bbfb8be13c472e1b82b` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:e88890fe32e107175f256452301eced892d4db17b29413926540676471b8f870` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:0a7dcd7199629e2c5e3c36dd5adaa1f91ef59d27fca7b3786a62206dea002d77` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:dd79516dbaf642ad42d12be89345914b38130e42f16585dd14c53f1de1303b12` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:6ad036af7238b80953947f6a50d7838e977bde43fdebed58a26fc88167110cd0` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:e9bcb09b2a777e3034509bba624d7fdb9ce3fc2c10195d9373bd53e1ed09646e` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:2c28e8b15ae8f0797c66c0e3289637a325f573dd0c80f3e40053c57fd7b6ed79` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:77ea9f489d3e200be8e701a1c26aa1701569c923af3c64444383f7b7533206be` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:a3772449d4e7f4f720dc83dc4d29416c9e6e5f6b097cc5645cb1c0b3d42454fa` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:e4019ce8cb3707abf7bc6b04371822d6f524e6dc22144ca3dc6017899162c8da` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:dff44a4aed248f5b908d4dde61eab3b31ae0505b30f9a096f99569c5eba57e06` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:2b94843006eb3648a47f41b0164ad5d2b09c3169a0266895a91ef78e374b8ad3` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:4f9932479f7d1bf8b27feae12efa94ad850f7cee277007845629b0a3a81ce1b7` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:73c84a4a1e58e81b064c29c0e1671639b772eecbfb1b0091ce71a4ccde19b0f2` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:e8f5491a4bfed56ca5316d36ad216c8fd1a9947eb74c3062c3a4f2c22545e3f6` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:5ef963124f8c9764d2c7b4abf503a185d781ed200de21071cc7326d8e9360d15` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:07871a0eeab99e99a22c59a5b234f8ff7ade8c52e216d1770c5af4e6d0889304` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:bc5dc364b127bb0ef76547952f73e8efe6c9bde949566575ba180ecc143187a8` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:09bcdf3781771e6826cd50463c1cf16e5b05f68e431ace04dfad97bde1cbae3c` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:e30f8d0d222944699afddbf08e28cdfe59e2d6a291f7ee7adbc7322fca495720` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:69bd4ecc03ceb9beee1e0328ba2f03c0e68d0e5f66bfe0a7147f743dcba41f1b` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:2bce49324c5b50dfaaec6ac62627876130e0819a70c6f97792932eee4a866cd5` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:87c365f3aa880bf7161895b7e14766473557634f0b2b80cb1caac526c548e3fa` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:07710d4061204d09a271685464793474c53b7d641bd96ce2e23bdec9ce30102d` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:c41224ecaa09922773181d2af75efbcec670cce31c02bb72f5b83a6221b2707e` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:017119251b3de7c5bba3f6e94bc6f0ca1c61978816278bd915367776ed063641` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:a47954801c3a012fec68453200e35d3f90c5ddb501b8e2b2f57d4066bb9a801a` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:450c847a023508e0ce113363c90bdd68492fb0ebf3505ba25371682f42615ee0` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:938fc1b1dd4395ddfe3dda5aea74a6e69c1fda42170ac60110429751d93c2afa` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:31e428a55fbc3b09729a2e0ab52dd5e992d370ff16648c26ff4c36deefe9e7ee` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:bdec89e2f318831bc3caf7b2cf27de9f8b339b7482409902b45e363ad0e97d86` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:1b6e6abad2602708c29677c7c51f01f917da74eb46b4a0a0f304b99057b1a5d5` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:8d91b732895c4813fa1f14abcc45a0fbe6761a7012451fdc73101b06af708a52` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:6023049982f58bb4482b64ed68a37aacb09303c5769c8b15a85fb859fe091392` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:b1196fa5e04f0c597a988a34340fc53d8736fd401bfd8c00dcedfa43767a5de4` |
| `uk-ua`                     | Container image with the `uk-UA` locale. | `sha256:8b1b3f06dd8061d336de03cdb8b6853f8299ac15b081675337a40a72c02f6b04` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:be65edec8ca921e4706de1d64d80ea59e7e0500dc7c21423fb7c756bc32b99a3` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:d43398f02b9a607ae4c2352d760e7cba4e6546badc904a06f8a855d27fd730e9` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:ef47403de6bc723682b316c1d97968c11cf28dedda869e689d4e5eecd8d024b2` |


# [Previous version](#tab/previous)

Release note for `3.1.0-amd64-<locale>`:

**Features**
* Support Full Display Process and this feature is enabled by default on all listed locales. The size of images increases 2-5 Gb because of full display models. And for `en-US`, the container takes extra 150 Mb memory usage.
* Security Upgrade.

Release note for `3.0.1-amd64-<locale>`:

**Features**
* Support new locale `uk-UA`.

Release note for `3.0.0-amd64-<locale>`:

**Features**
* Support for using containers in [disconnected environments](disconnected-containers.md).

Release note for `2.18.0-amd64-<locale>`:

Regular monthly release

Release note for `2.17.0-amd64-<locale>`:

**Features**
* Upgrade to latest `media`, `text` components.
* Support `de-AT`, `de-CH` locales.

**Fixes**
* Upgrade security patches.

Release note for `2.16.0-amd64-<locale>`:

Regular monthly upgrade

Release note for `2.15.0-amd64-<locale>`:

**Fixes**
* Fix container start issue that may occur when customer runs it in some RHEL environments.

Release note for `2.14.0-amd64-<locale>`:

Regular monthly release

Release note for `2.13.0-amd64-<locale>`:

Regular monthly release

Release note for `2.12.1-amd64-<locale>`:

**Feature**
* Upgrade to latest models.

Release note for `2.11.0-amd64-<locale>`:

**Feature**
* Upgrade to latest models.

**Fixes**
* Keep user's inputs case-sensitive.

Release note for `2.10.0-amd64-<locale>`:

**Feature**
* Upgrade to latest models.

Release note for `2.9.0-amd64-<locale>`:

**Feature**
* More error details for issues when fetching custom models by ID.
* Hypothesis is supported in conversation results by default.

Release note for `2.7.0-amd64-<locale>`:

**Features**
* Support for the following new locales:
    * ar-bh, ar-iq, ar-jo, ar-lb, ar-om, ar-sy
    * bg-bg
    * el-gr
    * en-hk, en-ie, en-ph, en-sg, en-za
    * es-ar, es-bo, es-cl, es-co, es-cr, es-cu, es-do, es-ec, es-gt, es-pa, es-pe, es-pr, es-py, es-sv, es-us, es-uy, es-ve
    * et-ee
    * ga-ie
    * hr-hr
    * hu-hu
    * lt-lt
    * lv-lv
    * mt-mt
    * ro-ro
    * sk-sk
    * sl-sl
* Punctuation is enabled by default.

Note that due to the included phrase lists, the size of this container image has increased. 

Release note for `2.6.0-amd64-<locale>`:

**Features**
* Upgraded to latest models and fully migrated to .NET 3.1
* Support for phraselist v2
* Phrase lists are supported in the following locales:
    * en-au
    * en-ca
    * en-gb
    * en-in
    * en-us
    * zh-cn
* Support for new locale `cs-CZ` 
    * Capitalization and punctuation are currently not supported.

**Fixes**
* Fixes an issue where confidence scores were always 1 in Diarization mode
* Migrated use the TextAnalytics 3.0 API

Note that due to the included phrase lists, the size of this container image has increased. 

Release note for `2.5.0-amd64-<locale>`:

**Features**
* Support for Azure US Government Cloud

**Fixes**
* Fixes an issue with running as a non-root user in Diarization mode

| Locale for v3.1.0           | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:e01ede581475934ee2873fd28cfabc500aa7334e1a0994bda5f9748f30a85fb5` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:644e871429b75a0168e6a3d893a12de719e58a1a95d99c4a82bfeced634eeefd` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:82a9affeae9379b0503be0fce64f6844e0afffa7b24ad8813c2c8ce8390c452a` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:161278801bce4fdf34eb4d9569d814266ec59f5e951b625d39d493d1208f12d0` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:9d833b3f3d3fc773a25e667b15f41856922c6ae862cc09ae9b64857a4fb23824` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:e01ede581475934ee2873fd28cfabc500aa7334e1a0994bda5f9748f30a85fb5` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:bc8e49cbb6eef0bc268e8f8bfa0f41a1730aa9e38d79d91232226ddcc41a417e` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:2bbe8d69f1042f71d92fa66a768b538d116a2db87e0f024d0a61999325507a9f` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:e01ede581475934ee2873fd28cfabc500aa7334e1a0994bda5f9748f30a85fb5` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:e01ede581475934ee2873fd28cfabc500aa7334e1a0994bda5f9748f30a85fb5` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:cc7d1d5272637104966e0acd290881a19e17d6466599d2dde853cf81c5dd249b` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:9af266e51be11dbcf116e19ded5fd39848aeee800f0366125c4b635535dc2b2b` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:ab8c80b66404d2720d086b32a413b87064b7884240e8fbfbc5ee2f8c9ca9b174` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:c24b56ad144600bf301b3960b4b829afffec2d7d7cc64e707aa1f34de8e48e79` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:52cb5fc8660adb4e92e7b1f886f19c529367733543c8df05c9db5f87e1a8c08f` |
| `de-at`                     | Container image with the `de-AT` locale. | `sha256:cb8a8febd76d831d9505c7f61c841499f097c0a2c09aae1374668f9bc38fb952` |
| `de-ch`                     | Container image with the `de-CH` locale. | `sha256:d9d6624f14dc0f35fe9b20da5fe601b40abfc98b89092b40a934532d3cfe6dc9` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:0c9da57b2c5312de859de1ad53e244bdb68103ce072e0ea42ab3078ff0339132` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:f9c2a3172bd5671c590ae309d4ae49ea45ec696c112f6d9bf3b6007e94f0bdc5` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:6df7313d6900b847ef29a44e967cac4e9a013e7b89493041b7a2e45f1e3fbba8` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:39896bc91b15c5fe6c1f17cc79ff6c391c0b2051135a206ac64ae2a590b37fe9` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:c251b61c54fc9e0b269901e8c9b12447f3a4facc8688aded07eed378b35b2e48` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:767fa5f3668692de9f1913786b1a7e343dc359c4c0c3275f6823b3bb4934e278` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:24dabb8ecf0d06e0a4d67b72dda7e436bd31ee27e28370fc2f9cbed790f716ff` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:662f6a8119eee2ed3093b65d70b0bb2301723dece4bfa270ecb8e007ac102a76` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:3ba5b5d4f6fd68f242ceea8640545ab520f704d315672c9631e7ad151d75f1b7` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:374e48220c590cc8d89805d35a10b6a8e8a46ae16b5199775b75289b8f58c636` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:c084a1ccd2efcabcd260be4c0c22ced90f8666f56f16e31ea039d677b74597d7` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:1aab9d20a7bef256e5140a94c7fb6662a4ada2c8c5cb5ed75836f4e9101f2d13` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:8dc4c73b7100b9f115f1707a2021874866ae4e1024d2ea2db7b1f3734b1121fc` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:8f0735b84d9e8aef4e8fc9eb30d263c871b2de93080744b086bf97de1c0aa21b` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:b6e1d56befb6279c6937b9eb0530426ca2fbb2b94e0b06bf442a72ca7d2db1f8` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:74bc32f5853a70bf26707bea6815f31b593335f73693c940fac66cc00a17b4ea` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:58c12bd3ed9876665a08b221e483f233e2096e9f4364fffd24487412dde3939a` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:12da366cc0d126bd5831994348acb255a9cd05a3929af7affa513458d981352d` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:edb533d5cddb0188b900b70a71b95c759b8f4f2d17da12c4959621644af0a92e` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:cdf27024a777d00c776df3c3175f5fe4778de8fa6da77658d6dc538a6bf64f57` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:20c6c5cf52f75b178c5ff9ef2d5d1990ca8fcce0056ff3939ccbb7a10fbdca1f` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:0de092a826f3e847ff60629837cb06949afde6690cbe8da8805998d114f477c2` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:1e3d2dad7350fcd91c6db64fde8375c83fff2ed34ad2e1758773400d6b42c0b3` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:0bd284e5edbdb93ab2e802d2f05ab44cf484e884b3bca72171ee8f72b19cdb4a` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:aa033f75eb4abf13e9f40b452140780cb8c416881f512a2b9c18ce7d46032bc0` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:6f15f6fd2ef3d029bf8f508268cf26e22b67b4f02fcde4c06414a47c57817f6d` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:4d99d615ea7b0e33acbf69c593c4cfd03a83bb15f30e7d71ee9d9c606870408e` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:9ba5fbb172e32c526a9662190a1c106a635f0637dd44a00bf0b4927b7388c31f` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:7419eed485084b99dc527a5ecc48b130bbf9a13807c9dff0fe9097655fcb6ea7` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:485a0b0c5831973358249e084dee285e0ae9c960e3f550f7d971b89e3d1e3d91` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:56108b647909b60053053369907eb46f23049fbf7296135165f58e10dc218214` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:eb68916713f83c4bc8ae9a621b022d73f7737b9c9479ad79acb76657fd8f6c0f` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:779199a5133d8690d5c983baa8aac8088a30eb746ba80d90d91b7c54eb4396de` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:c3bc655c9bc2d4d44aca7a0c9bfe0be68f2640fd48c3112ccde4667553282a79` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:bd11b40b81920c3796ceb9ba8d6bf61be1aff4f16bffb6100d8ca860d40d8552` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:6df492b55b7934f207b1c6d047e57c2cb13a10147e26c2b4864f4d02f8a4e786` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:75e756cfc34e335eaed8bcf12aaaad54043e3727129fddd0e260818680fbb987` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:2e88bcbc57355244eb8a543f32805252ffee8d20f8724e106a7eeae6d9c41d33` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:e77f9716f2db3ea8dc98dfb8edbb2a6c9cbb11137d0a46d592dc4079b4797c8c` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:1c1ba6d7af9d69e9b5beeb3a1a2502e2747bf7f5350a4dbee14508698806542b` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:29f270a67e87e57643cf6b3e6407547becc94ffd7d7c32f5c466feab9f43df9e` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:6c3b8b8ea8d0f04b486efce72c061569dd993c251ca1c874ee7b75cfe28e078b` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:0db167fa90de896318b56d6a534f7ea5241f6e4414081b0b1f07b60aaeacd211` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:1bcca1c51d282f5f78a5323df0d927cd6161a49fded1e0c0ce83a999a60a0cec` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:4b9ba7b007d9dc0872976768a44604c31e5f671648082cfdb3f395bd8d52e3a8` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:1fd625c589dde9547db32232f7151f073851e84764e439bb48928bf3697dc280` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:a6aaacb60377fd137d52251b6855cbf6f584b6c2407cde7ef4be9f0315293ddf` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:3d9feeb98a4650164704161b9c38aa4eb441505b7ef45b227fe471026224c590` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:03fe81b7a7da4573a012400955e3f9505e2cfee5b40b1e59c32abd7d65a84636` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:0c76e4a8695421a80b87b5ed348c7ba4771486dc7befcb8c13b0f8216018e360` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:c617c263f7b090591d347148b3c9970cbde3b5864e602f7eb54361bcdbad80a8` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:db8c0341e7d7995dda288fe7232f7ce810994317738759bbc7adb0ed93050701` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:5393a0c72d49b50836a8820f2a7fa7c381606cbf1ea03e19b60c48cad320dd29` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:fc888ddc056bba30be9aebbf94fbcdf322ee35f20805d80914ddd1b9fe146510` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:10ac67830ef5fa49c8bbeef1bb6becbbb34875d6fdfcc8bd78abef030b71853b` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:44195bab625e430089a333ae25348ddbb7052e1ce9c223e2bb1c444a4add25ea` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:bb5ead4296e76463b2f54108afa8c4cb5a12f65470012763fa973af466960400` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:d6922755249be4c85a1e119366e5044e62986c0e065abfc4cec8ec5d788b1f28` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:5f3225b01d023eb99711033f1531d32b8627207ebf9cdb560f3429106677eb85` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:9fd69d7b18579e9813d69a53fa008e4e43521e81c3b8db0f91df047f7f85d53f` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:a2c4ced531ebcf41e6653d72eaa689b665748d1fbce428ed1542d2183a0c23c3` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:8e9df83624627f58cebb0b0654035e746b60f4fd30eeb44d9bf30733ace02886` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:060ea9db2f153e5c3296e3280616f6c4c24423a352237e91db8ffc5939db5038` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:fffe495ae24885a69447f553ad0c8a8fec7fc805163f0aae6f27374c9c5f7ae6` |
| `uk-ua`                     | Container image with the `uk-UA` locale. | `sha256:8ee7118a2a4e3aa9d7d9fd21770d274dd4081a6c7290374db8892dbc604ea819` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:fea665892e189ff3778cb2ff35865da9c7aa5c62a2711d359203ae0f288dadc0` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:b46dd6bbcf01ce28d10279bd4c6a749f0f5871b293c059f35db43314b4e7a4a8` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:ff98176465d574d4eede6339605dbd21d1197ca82d33b86b961d86d114283927` |

| Locale for v3.0.1           | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `uk-ua`                     | Container image with the `uk-UA` locale. | `sha256:af8c370a7ed3e231a611ea37053e809fa7e52ea514c70f4c85f133c7b28a4fba` |

| Locale for v3.0.0           | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:3ce4ab5141dd46d2fce732b3659cba8fc70ab83fa5b37bf43f4dfa2efca5aef7` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:86ed164f98f1d1776faa9bda4a7846bc0ad9232dd0613ae506fd5698d4823787` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:43fa641504d6e8b89e31f6eaa033ad680bb586b93fa3853747051a570fbf05ca` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:001c0d3ac2e3fec59993e001a8278696b847b14a1bd1ed5c843d18959b3d3d4e` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:1707f21fa9cbe5bd2275023620718f1a98429e5f5fb7279211951500d30a6e65` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:3ce4ab5141dd46d2fce732b3659cba8fc70ab83fa5b37bf43f4dfa2efca5aef7` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:d237ecf21770b493c5aaf3bbab5ae9260aba121518996192d13924b4c5e999f4` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:d1e4e45ba5df3a9307433e8a631f02142c246e5a2fbf9c25edf97e290008c63a` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:3ce4ab5141dd46d2fce732b3659cba8fc70ab83fa5b37bf43f4dfa2efca5aef7` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:3ce4ab5141dd46d2fce732b3659cba8fc70ab83fa5b37bf43f4dfa2efca5aef7` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:a51c67916deac54a73ea1bb5084b511c34cd649764bd5935aac9f527bf33baf0` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:f0d70b8ab0e324ee42f0ca7fe57fa828c29ac1df11261676f7168b60139a0e3c` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:b876d37460b96cddb76fd74f0dfa64ad97399681eda27969e30f74d703a16b05` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:73bb40181bae4da3d3aaa1f77f5b831156ca496fbd065b4944b6e49f0807d9e9` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:a0b65559390af1100941983d850bf549f1aefe3ce56574de1a8cab63d5c52694` |
| `de-at`                     | Container image with the `de-AT` locale. | `sha256:78030695ef9ff10e5a465340e211f1ca76dce569b9e8bd8c7758d28d2139965e` |
| `de-ch`                     | Container image with the `de-CH` locale. | `sha256:7705a78e3ea3d05bdf1a09876b9cd4c03a8734463f350e0eed81cc989710bcd5` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:d10066583f94bc3db96d2afd28fa42e880bd71e3f6195cc764bda79d039a58c7` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:d8b7d28287e016baacb4df7e3bf2d5cd7f6124ec136446200ad70b9472ee8207` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:493742b671c10b6767b371b8bb687241cbf38f53929a2ecc18979d531be136b4` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:61fa4cb2a671b504f06fa89f4d90ade6ccfbc378d93d1eada0cc47434b45601f` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:3b0f47356aab046c176bf2a5a5187404e3e5a9a50387bd29d35ce2371d49beff` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:bf98a2553b9555254968f6deeeee85e83462cb45a04adcd9c35be62c1cf51924` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:952a611a3911faf893313b51529d392eeac82a4a8abe542c49ca7aa9c89e8a48` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:6ad1168ac4e278ed65d66a8a5de441327522b27619dfdf6ecae52a68ab04b214` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:03174464fab551c34df402102cac3b4f4b4efc0a4250a14c07f35318787ad9e2` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:e38bbe4ae16dc792be3b6e9e2e488588fdd9d12eed08f330cd5dfc5d318b74e0` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:58476a88fb548b0ad18d54a118024c628a555a67d75fa5fdf7e860cc43b25272` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:e1ea7a52fd45ab959d10b597dc7f455f02100973f3edc8a67d25dd8cb373bac3` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:e5eabe477da8f6fb11a8083c67723026f268ba1a35372d1dffde85cc9d09bae9` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:b5c1279f30ee301d7e8d28cb084262da50a5c495feca36f04489a29ecd24f24f` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:d2e70e3fe109c6dcf02d75830efae3ea13955a1e68f590eeaf2c42239cd4a00a` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:70c5975df4b4ae2f301e73e35e21eaef306c50ee62a51526c1c29a0487ef8f0c` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:b81dd737747421ebb71b8f02cd16534a80809f2c792425d04f78388b4e9b10f1` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:2b5a469f630a647626a99a78d5bfe9afec331a18ea895b42bd5aa68bebdca73e` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:5c5c54cfa3da78579e872fec36c49902e402ddb14ffbe4ef4c273e6767219ccf` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:d417cedae4b7eb455700084e3e305552bbd6b2c20d0bba3d03d4a95052002dbc` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:82258abbba72a1238dfa334da0046ffd760480d793f18cbea1441c3fdb596255` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:efad3474a24ba7662e3d10808e31e2641580e206aa381f5d43af79604b367fc0` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:86dc0a12fdd237abc00e14e26714440e311e9945dd07ff662ca24881f23a5b2f` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:52139db949594a13a1c6f98f49b30d880d9426ce2f239bfde6090e3532fd7351` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:0ab8ea9a70f378f6684e4fc7d9d4db0596e8790badf0217b4c415f4857bce38f` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:512853c5af3b374b82848d3c5117d69264473a08d460b85d072829e36e3bd92f` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:c3a871d1f4b6c22e78e92f96ac3af435129ea2cfbe80cfef97d10d88e68ac763` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:bd1ea7e260276d0ea29506270bc790c4eabb76b6d6026776b523628eb7806b08` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:005e23623966802ed801373457ad57bf19aed5031f5fcd197cacb387082c7d95` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:fb0c71003d5dd73d93e10c04b7316d13129152ca293f16ac2b8b91361ecde1ca` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:23d1e068a418845a1783e6f9beb365782dc95baea21304780ea4023444d63352` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:268ef7cec34fd0e2449f15d924a263566dcfb147b66f1596c3b593cdc9080119` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:229e68ab16658646556f76d61e1e675aa39751130b8e87f1aba1d723036230e2` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:764337c9d5145986a1e292dfd6b69fa2a2cc335e0bd9e53c4d4f45b8dff05cc4` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:4ba59e9b68686386055771d240d8b5ca8e5e12723c7017b15e2674f525c46395` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:aa8040e8467194f654cb7c8444e027757053e0322e87940b2f4434e09686cec3` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:b213da609a2f2c8631a71d3e74f6d155e237ddbf1367574a3e6f0fc2144c4b73` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:6b5f98a5c8573dc03557b62ccda6ce9a1426b0ad6f2d432788294c1e41cd9deb` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:b5f5955b4baf9d431fc46c1a8c1afe994e6811ff9ae575106954b1c40821a7d3` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:a1bc229571563ca5769664a2457e42cce82216dfee5820f871b6a870e29f6d26` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:f28b07751cbebcd020e0fba17811fc97ee1f49e53e5584e970d6db30f60e34e9` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:c4bea85be0d7236b86b1a2315de764cb094ab1e567699b90a86e53716ed467f6` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:189bc20605d93b17c739361364b94462d5007ff237ec8b28c0aa0f7aadc495ab` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:572887127159990a3d44f6f5c3e5616d3df5b9f7b4696487407dcda619570d72` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:4b961e96614ce3845d5456db84163ae3a14acca6a8d7adf1ebded8a242f59be8` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:1b2ca4c7ff3361241c6eb5090fd739f9d72c52a6ffcaf05b1d305ae9cac76661` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:4733f6390a776707fc082fd025a73b5e73532c859c6add626640b1705decaa8b` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:84ebb7ab14e9ccd04da97747bc2611bff3f5d7bb2494e16c7ca257f1dacf3742` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:ca3edf97d26ff985cfe10b1bdcec2f65825758884cf706caca6855c6b865f4fd` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:f3f9e5ee72abed81d93dae46a13be28491f833e96e43312d685388deee39af67` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:e0f5df9b49ebcd341fa4de899d4840c7b9e0cb291d5d6b3c8269f5e40420933c` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:895ce0059b0fafe145053e1521fb63188a6d856753467ab85bd24aa8926102c1` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:f74afc0b64860b97db449a8c6892fb1cb484e0ab9a02b15ab4e984a0f3a7c62d` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:963c4cca989f14861d56aafa1a58ad14f489f7b5ba2ac6052a617d8950ee507c` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:468d4511672566d7d3de35a1c6150fdaa70634664a2553ae871c11806b024cb8` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:4de5d11d77c1e7015090da0a82b81b3328973a389d99afeb2c188e70464bc544` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:8a643ce653efcbf7e8042d87d89e456cd44ab6f100970ed4a38a1d6b5491a6c0` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:8b11c142024cee74d395a5bf0d8e6ed980304ac7a127302b08ad248fb66d82ea` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:bd140766406a58c679e4cf7f4c48448d2cd9f9cacd005c1f5bfd4bf4642b4193` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:a47258027fdaf47b776e1e6f58d71a130574f42a0bccf14ba0a1d215d4546add` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:376cb98f99e733c4f6015cb283923bb07f3c126341959b0ba1cb5472619a2836` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:d0ae77a2e5539dbdd809d895eea123320fb4aab24932af38b769d26968a4150c` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:522c14b9cbb6a218839942bf7c36b3fc207f26cf6ce4068bc883e8dd7890237b` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:c5f1ef181cb8287c917b9db2ee68eaa24b4f05e59372a00081bec70797bd54d1` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:110e1e79bbb10254f9bd735b1c9cb70b0bf5a88f73da7a68985d2c861a40f201` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:c1e0830d3cb04c8151c2e9c8c6eb0fb97036a09829fc8539a06bb07ca68a8e5e` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:dd1ef4db3784594ba8c7c211f6196714690fbd360a8f81f5b109e8a023585b3d` |

| Image Tags                  | Notes                                    |
|-----------------------------|:-----------------------------------------|
| `2.18.0-amd64-<locale>`     | Replace `<locale>` with one of the available locales, listed below. For example `2.18.0-amd64-en-us`.|
| `2.17.0-amd64-<locale>`     | Replace `<locale>` with one of the available locales, listed below. For example `2.17.0-amd64-en-us`.|
| `2.16.0-amd64-<locale>`     | Replace `<locale>` with one of the available locales, listed below. For example `2.16.0-amd64-en-us`.|
| `2.15.0-amd64-<locale>`     | Replace `<locale>` with one of the available locales, listed below. For example `2.15.0-amd64-en-us`.|
| `2.14.0-amd64-<locale>`     | Replace `<locale>` with one of the available locales, listed below. For example `2.14.0-amd64-en-us`.|
| `2.13.0-amd64-<locale>`     | Replace `<locale>` with one of the available locales, listed below. For example `2.13.0-amd64-en-us`.|
| `2.12.1-amd64-<locale>`     | Replace `<locale>` with one of the available locales, listed below. For example `2.12.1-amd64-en-us`.|
| `2.11.0-amd64-<locale>`     | Replace `<locale>` with one of the available locales, listed below. For example `2.11.0-amd64-en-us`.|
| `2.10.0-amd64-<locale>`     | Replace `<locale>` with one of the available locales, listed below. For example `2.10.0-amd64-en-us`.|
| `2.9.0-amd64-<locale>`      | Replace `<locale>` with one of the available locales, listed below. For example `2.9.0-amd64-en-us`. |
| `2.7.0-amd64-<locale>`      | Replace `<locale>` with one of the available locales, listed below. For example `2.7.0-amd64-en-us`. |
| `2.6.0-amd64-<locale>`      | Replace `<locale>` with one of the available locales, listed below. For example `2.6.0-amd64-en-us`. |
| `2.5.0-amd64-<locale>`      | Replace `<locale>` with one of the available locales, listed below. For example `2.5.0-amd64-en-us`. |


This container has the following locales available.

| Locale for v2.18.0          | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:5cbc37cc91e0608cf174be5f2a320ca7daf312ade59fd9a3983d5324e68edae2` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:16e6f169cf2ea025fc7d21c805a4a452e12b8d7b9530c8e9fc54ae68ee4f08dd` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:05dd5bc85de5567809259339aa213fc802b38924d025dc1786600e663bfd4996` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:94973685069d212c19d67d9c0c8eb3f0124e08ff82807e976b59578f1bd67e97` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:0dd7f1985b8544136bb1049d1b40d7c5858551f81721181a2e34fd1f9cb68e5b` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:5cbc37cc91e0608cf174be5f2a320ca7daf312ade59fd9a3983d5324e68edae2` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:9879fce4158fb8af2457eb6503607f78b7aade76eb4146c1ee7c142e7f9a21d4` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:0b1cd0c810cabad4217833d44b91479cd416d375e7ea43f2d14645f7bf859aa6` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:5cbc37cc91e0608cf174be5f2a320ca7daf312ade59fd9a3983d5324e68edae2` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:5cbc37cc91e0608cf174be5f2a320ca7daf312ade59fd9a3983d5324e68edae2` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:7b206ca47a9004866857ad8b9c9ea824bd128089a8bdb374e6da565b0ea30f05` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:a560c4e58476dcd9e5044f81da766a350b3b3464faaa6c93741a094c4afb621c` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:405cb4f74d10d5ff50efe9161b5cf21204d51c74b83766ea31ec2b8a878de495` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:87bde59f8fc441165f638a8665c480d259a3107b0edae5f022cb1b8f7e02a837` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:ee6773b88378e9a01a35804f965bec0531b01327630174b927320553f023b7e9` |
| `de-at`                     | Container image with the `de-AT` locale. | `sha256:f66bee7e43c05c1e434e0218d57ad094d47ec7be39e90ede3eb48fc9398fb873` |
| `de-ch`                     | Container image with the `de-CH` locale. | `sha256:adb77da42c2637c072850fb2b5b2b2e508dff79e1ccdc5111b8f635167e35cc1` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:7143c59231017104bab633a108b5605166355f78e9dde2e3a4ebe6ffe71faafb` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:4ce2fdeeaf53edc6811c079365e2aab56be75ea9abe3d94a6a96ca8dc0368573` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:e02827b1dcef490f792b04e7cd39eb7d46df4dbe57d340549b11193753136e76` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:f5411eccf7659b1cc2303e118ef1ef002a700dd1a7363688a224763a6d19b7fe` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:a87007b86fb1ca31b9a0368d01d7bfc4337b4262afb3356a88c752a29480f364` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:a6014d4cbfafd2d49453f3ff12ea82fe8abc1e14bae639a2e9361de85a095f34` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:aa6202c44028d4a8c608f04d6b66f473566d945012372182053d94dfc78eaa93` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:7ec9eaef19a2545e0a1afd70cb9707cf48029031e9f6b50cb6833045cbe66b29` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:48a95d03dc1200bfb56b1e3416dd1f94a0ad0227c0cf6c3c1730d862f2e99c15` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:ab220ea3063af44c0ee7f7b9805289302faea578a50f4da5790b587ea49d31bc` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:0f9cadefbe4d8236ef8e9c57b7473327541c1e37f53a2796f332bb2e190391f4` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:bb13765581c938cbdcdcdec16fbc86f098fcebeecd16f33a50d9e5728a9dedb7` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:096f4652fa8150cd1e2fa9b504cd2cce5bbb55b467ca9ba9f33d6b5c904fc51f` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:acccaa583aaedab78d6614ada897d948d1d36d994d2fcd7f6b7e6435fe0b224f` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:8d6631fefc679fe27366521a124d65dfa21c3e6b2a983f7da953e87d8711fad0` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:0cd131cc39c2fe1231b7442f43f81b5e7c5317b51f5c9d9306bfa38c6abee060` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:ef4dcdcbce5f0dadde35f52c4322084274312e7b4a1e7dd18d76f92471a0688a` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:8ee41457cf10efda1f3b126ae8dc21a1d5d2e966c9e3327a2134c597cfc16d89` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:d00af5e4c41c9a240b64029ea8035e5e0012f54eec970771e84cfc4b59ecc373` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:9905d776b637cc5de8014a36af94ecc67088c1725fc578f805b682e969e04b3f` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:a4e8d08b0a696d879cc20fb55171e90b32590514e999f73f98146b6921443cc3` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:1ecb4b3c86ff34b26b25058fd6c00b738c3c65d98f15c7a42e187f372ebadb60` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:fd575f64f124bcb909d0515666e0a2555c3f1fe31dc8383c7fc953b423eed2e7` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:5f96eebe2cea5a67e054c211cb744205e0ef15c957e8d38d618c746ff2c9f82a` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:f9c8beb68ac7a1090f974b192df158013da5817b84b7e4c478ca646afe777c70` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:150b98205f6802d85c4bb49fd8d334a6dd757ca1bb6cec747f93a5450a94eb85` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:b27591217dc5b6db01570e9afac00949cdd78b26fe3469ed538bda62d6fb9209` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:77dc8b771f638c2086de2ab573a28953865b95145cf82016459361e5cc3c5a47` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:9f429598b0fc09efc6e9ce575fde538d400ceb7fa92807319873daba4b19dcf1` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:5cdaefc98a799ddd3800176efd6ffb896f5356af9b53a215d0600e874d94d893` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:888bee57b4962c05c7a2cf569a22bb7bdc8bf2cf502e7f235ef1a0dafacb352d` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:b021255ff7916f2d4b669114f3e5aad06de0c0b87656a9cc37af1f5f452e910b` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:f69c019aa438f3f701b84805842dad98eeaa9a6998b261ea63e56dd80c1cd42c` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:6cbd6d11bf9a021277c2fd42ef53242f12b7df00b559e572bbbe6baf48a84bac` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:7b3a11a1e6f03ea4b802d97034588fbd461ebfed7ad08dc100c92586feff2208` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:eb765a640aa8ff89e9bc718b100635a7c6adc2342b2da8fc621e66b7ba8696d4` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:90127487c698e5d1a45c1a5813cda6805ba52a41468130f6dd4c28fe87f98fab` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:ffc7c3844873f7e639f2a137b991edc54b750b362756f6f8897fbfaaa32fe1df` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:ab41b4ad9161c342fac69fbd517264ad23579512a2500190b62e97586e5ec963` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:ac4da9f6d62baa41a193c4765e76eb507f51d069f989ae2860bada1c3e5ff968` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:9131208103997e9829239e3a8585c23f5dc2affc4ffbe3840270247d30b42be6` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:4ccb5056e7763b736362b7f7b663f71f2bd20b23fc4516a6c63dd105f2b99e9b` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:05a8d6be2d280cf8aa43fa059f4571417d47866bf603b8c1714ce079c4e66e6d` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:9e35544bc1a488d4b3fefc05860279c7a189505562fe2e4b1267da67154efded` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:a1a3a6a81916a98aa6df68704f8a2d8ad318e3cd54d78ed97a98ee3b6af1e599` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:67af86517f8915f3ebe107f65e62175dd2a7bb995416c963dca1eb398ed1502a` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:aa2248878811831ab58438f40c66be6332505f3194037275b37babfceaed1732` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:1ac940c96d054cf75e93cda1b88942ad5a7f4d3a269bbaf42060b91786394356` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:ca917fa5139516a75a9747f479fbbfb80819899c9d447c893578aadebf2d1c84` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:8f2e0aac8961d8c7d560b83ff02f9fdb50708c1e508f8c0c12662391940354df` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:7eae1acddc5341e653944dbe26fd44669e1868b70e5d49559529f2eeb8f33b02` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:5c3767d6f563b6b201a55338de1149fac43706c026c4ba6a358675d44c44d743` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:22ee4fd3a864576b58276b9a02821fba439f7ea5f5c462e62deca1778a8b91a6` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:660c69103e721206e14436882272e80396592a45801a186d2830993140d4c8e0` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:3579963235d8b05173fac42725e3509475bc42e197a5f0f325828a37ef2cf613` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:23c07debd00bf4a817898784fb77bdf3fd27071b196226a8df81de5bdf4bf9f8` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:b310ce3849e3c066678e4c90843ccf24e5972759a58b32863ba94801a481811b` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:a750a88a2c7677b2507730905819764ae56e560a96394abe3340888d4c986f3f` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:3b92dde403d279395de09c77e3f866fc5d6757fc1c9bbf52639be59aee57b3be` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:70291a568a3093db066fbeff4ae294dac1d3ee41789e293896793b9c76990eb9` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:e1a5d1a748137d549b858635c6c9f470e3049a14dc3f5b300dca46819765de9b` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:0e11a0d8be515c7149f4d1774c1621d6a3b27674a31beaa7a9f62e54f9497858` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:2164d04ab1f9821c4beccc2d34e97bc9cec7ad387b17e8257801cd25a28dc412` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:011ce659926bb4d4a56c8b3616b16ac7b80228c43e23d4b9154c96c67aa5db1b` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:c7357d975838ae827376cc10ef48c6db8ee65751ee4f15db9a31ab5e51a876f2` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:ea1c310631044b22fb61b79da59089db5ecd2e2ea0c3ab75d63e1c1c1d204a48` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:c3a2388d3cb7d22035b3a5e4562185541cbfe885ab6ed96f3b9e3a3aa65aa56c` |

| Locale for v2.17.0          | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:4e7fd7c2412e13e4f5d642b105230e90ae6cc2f0457ceabd2db340e0ae29f316` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:da8805f4f64844f140e7a72b2adf367d45b2435e2dc1cd579a1adb2ec77a8df2` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:d5a8652c680097c54668e6b16b01248be523d756ad859c9449931adee95df9d7` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:19a19894bb9a1c1b28e8bb7234e19757a1f870f4032ad50f44a477fc2b452ada` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:2279655c98bbf09f221212fbe6876bad5662ccdc55be069975a23512f4a3d55c` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:4e7fd7c2412e13e4f5d642b105230e90ae6cc2f0457ceabd2db340e0ae29f316` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:f1b0e5083e71f5c2f56f841b6db399f50f44c154126e3316e8e6e73b6b895c97` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:8af7ce49be6d3839ac0e1ce4f1f45d4361fbbcbffa66081b0e7c6824dfa7c1a0` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:4e7fd7c2412e13e4f5d642b105230e90ae6cc2f0457ceabd2db340e0ae29f316` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:4e7fd7c2412e13e4f5d642b105230e90ae6cc2f0457ceabd2db340e0ae29f316` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:de0521c0728468540699387e4152887c2a0a43ba37e9c144256a5c541a2f1d7e` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:533272cf3c8920b002461e8cdb51fea9a6318aed41c9b77d0cbcfce3bfd7d077` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:10af2a3eb4f8cfe88925a512165c3fb555681b9a89d3db9d67fed02a33809063` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:95cf93202ae922318862ba585b38a989b4fc83e4d335f2c3916be4564df0d215` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:fa66a446e0575fa1c89f52b06e16279fee0fe4f0d61b1e18a0dcebc8a866ddf6` |
| `de-at`                     | Container image with the `de-AT` locale. | `sha256:e0d8a74ebf48981999306e6cc9f99dfb9fa3fa16cc12aa5086e9720639ce9f52` |
| `de-ch`                     | Container image with the `de-CH` locale. | `sha256:ab58cb7bbe5a5a78a7459b690c95f036d1b4703610f563f5854334f7332d5fca` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:abbbf003661da23eb6bc2133d3585ffe58af3a9d3167b7eece656d0007bc65d2` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:01311455b2425e41031368691de73e28c3c08de0486e50f4801ade584af27c2d` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:86c84a560a23b5bfcbadae8dee62805f897520b7d3ac6969d80e3eb88141d7ef` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:0f5912fa924212aca1522f6a27970778b0c22d943a8b2c9e9410df243ad62ff7` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:a5f3efff449bb9e43fafc9feafe0b31f11070c8f2bb9c60e34892b0765fbf0c5` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:57274ea44bd9dd34afc845e4dcdadf61b33681b0e4e5dba1f3c0e13511b40fe8` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:f4406c366940ef5185aedf42bfdacc1246ef636aebb8ad5b5a6bc521589f528c` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:9b6529181e7fe12ca00222c6164342b32ff637e4f394240ff2194489c56408df` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:10978a40cc3b7101517f35215c663ddec69679d5650ba827476060da8b84812d` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:a76b360f883ee746f77a650f285244d0424be9d6b3990a0c8075ec475f6e77d3` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:336f939f5db41312e6bfeda5419570db456df05c09d01fc98d7bc1967e4a8c3f` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:e8cec9044fd1f7958b2188dfe818311932fe0560d0f1d56aab684bec42a05723` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:b80e9e6349e057dae1c60a0b718cc2bb9e6db01681b1910afb5c48525aaf99a2` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:b9b9bc3cd87c5524b9630c29ab790a5e10e725237c4a482ba09673b3e98cb7f6` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:849f9f3a4ad8b1266b07837afcd9cbd5815bef2473bb8b3726b1cfaec75c8a62` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:dc09280f0d7df607e363f137ddc6ad333d0b7628492296eece9d3717d60ea339` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:270de8bfbae05c984f164d0c4e15c096459f41bf8f1aeb5cb18c1b7d20419bf3` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:e6c7e8ded3c75c19ce0f94db2d468b1d48548eb9b9827a67a9995e4820b6ae58` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:56510d176425bc3ba329ac0cf9520ee5a041370777320faf8081288c89c83c14` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:af3c853b766eb01a7ec51660ceb179040ac007c7b85f07c68a32adcdc3b280f1` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:cf05048a4762dabc23dc44bbb5c59d26cef5946658d653da4e2965d5331ea497` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:9575b02e64c47e4b4253a90dbc8cc3ebc393fd1a3a1b5680d3eff6efd76b1f3f` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:86775303621fc1a80761cefba4aae5aa769a998d96cf61e54490d4aa59edae6c` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:a8246e041c1a10338397c8ce9ba1389b0ee517bb8c0ec8e6fd1579c10704529b` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:d709a021dd398fd2bb77f0fa5478646642774b5b91f25699001ee2d7ee7c9e4b` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:e532978cf0d7d696016d3b5353543b6f9f0f4bfbd41669403a5e69e144c67259` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:3f45b4169cb131bfa81820d0c08a80f27ecd54e7a56755a2d9db7da358fb9f27` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:2b9eddd484a3262002dc92e07603cb161e254bc5460ecfdccb6f0db91c48c5a9` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:2b95ff684b8c60e91531bf7c19f4ca71a69ede37d1d06262cf90368cc6b1ff9a` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:b03ac0b66f5af771cf3d4e3bb61efd674df0ef2fd0934f77467d163472308805` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:e5bc6399ef63b07e6e154e438b25a58622beb1a2f90e31e043ae2720dfe1daaa` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:21de294ee17c097d7624ad679c24715ec93aa46e0b982afcbf2d6defd4177ff6` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:d4827464db58661c57f7ba981b03e493302d9b51a89f41cf7ca633a4e7f69f6a` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:b56baf94cedc5d50e2cf3846d995f63f36473c4146008f50b31b9b747c8e4c45` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:b2f45988b0d077f4f7279a58353d3179fac181ad5cdc3848667fa25d7d96e4f0` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:c13210ddfc885f359dfc020f7a1c39773ee62db15617ef472ac10d62f8829904` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:2a6f9e5afcac65f9030dbffbd22da428a6633f7dde8386eff674961dc61fd040` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:11f4ac68104d3853558bf7a7d08871cbec4ab1194281eda80906b256e8b82f18` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:c07dfc10ed61e3a35142d0ea26c7b87adeeecfb95a5a3a16ac44023b3df03e0a` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:76b9c92a1e77513681249e71c7194e94067ff3af97ad35ca2ac0d476dfb2b744` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:f45c3de121f2b922c413468bfa9214a5dedd3e34049fbe2d77f50cba7ef8fcbd` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:b9f01a38f65884b9f690394c5e06f7d4ce02067c18d41dfbe9bcdc7c36b85373` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:f5da4f23d87d41438220822cd26be08376cd2c2920560fcee4e892673227c90c` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:93cda63ee7583bee565fd8a49d2bd331ac9033c5111858185aec916d50af988c` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:d9a3e69997cbbd490e471f09048bf78aea828323eb49702ed51c60d5af98b40e` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:a8978adf5b51b0daeac13e605d1930bc06be5cfb44159ec759d1fa460ebac9cd` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:a69cc1b076321b951d2746e401bf17b18b720e0a7e27004f64e15bfa7ec4f68a` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:27e2d8eb315ff43406332479e20780576efb4319ac153129f695a09b092987d8` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:1e89166b7851bd7ed58804e4bf5cd23ab9bd522ea4ec178ddc46b5c47fd85fda` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:df02ebd3291d24b9f46ae9ef109c4c4713a6494dcf980581c70855f9a08abdbd` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:3aa31830f15fb90165169bac9bd23ffbdc5d3cca2eda6dc80bdefefeb9567fcf` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:532ccc97086b6afd99c83277d9c09ac6f94873f8f7556f407085e0aa2d50bc30` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:fc1d7af8419904e98ec41b789eb17a406f8097ed01b4a95776f2a208ff4636b1` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:37b45b5a8cbd8cdccde0005276a09fe4b3b8e04922499644e67fad1b480507a7` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:b5d9a3d6f343e6b20919f00dbe51b41e55034bf2a29407b344ba2352c7014741` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:0526a3e3bb31e0a929492fdb886f3f5ef6be61bc81dd58c64b773ca13ed27731` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:1db419aa78fdcfd78078361d2c547d962d22677e6aab4d44856334ea90e1dffa` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:baf36c0b1a4e50c586a71d9b266d1e528e194d6fbe7ab630521bda6fa4191974` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:e5a119c4f7fae31d6dfb988d1930bfcea0d0c5d44b0fd8486f777041c6051f97` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:1dce2cac02b6100f87173dbad9128bf2a7c9bd214033b01b9e50fb377a837ea5` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:091876dbf3a8b40d6737f3d6d8717868e9fcd1bafdd2a590598769a53dc25d5a` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:b44f16adb5124ea16cabc640079ffaf26d654a86cc25b5d98663b6e139e9e653` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:e315b48f2f76c11a9fa0f59a6ed5fc346014be7adc23fbf0a2719eea6a9abe9d` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:77a345f63a3c357b072052cdd38604a0f3bfa885e3b3058b77f37e46c80109d9` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:91400eb20a9d4a49cfa587e5d9ac15f3714239d8189bf6ec55f04caa1d0fadd9` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:3f1a782e85ba536d7761a4addc315915464bd949a9298fc7c93ee17ff5b15994` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:f0088423fbaaac0cf20e1f747b1bb17adc58214e45cda4f571985d86a93565ad` |

| Locale for v2.16.0          | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:66d3df9332cac66bcba96c8f62af4f1f66658c35b9dba9b382fe7f4c67587e3e` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:cc0b82b09aad69278903a4e4f1b0aabfbe91fd287d391e89cd05582be0b71ab6` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:cd4a1f6766c11a4204f789d7534e7ad7255896e99158450362f47417dec39a6d` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:4748f3f456e0c79cfeff6250e1b51de87d8298e683d45ae3aaaeae4c11445fb6` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:030c207f1e114bef95418924b2aa7672ba9c17fc127d5dbee7df3a556b4aaabe` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:66d3df9332cac66bcba96c8f62af4f1f66658c35b9dba9b382fe7f4c67587e3e` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:c45c73e524c7880a25acfd99428a57077b041d81e19dc190e7ec396ff980b5a1` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:9fa4fed0e0482aee11f2a341d97a89a5613247e6b3a6450fe932bdc0920c1845` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:66d3df9332cac66bcba96c8f62af4f1f66658c35b9dba9b382fe7f4c67587e3e` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:66d3df9332cac66bcba96c8f62af4f1f66658c35b9dba9b382fe7f4c67587e3e` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:2f8700e87f7ed1d9fd808f7904fd8ef6be799dab29e20f6d67de441021ae5a22` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:01dfeb367631fbcaa987d0962ed9a3662839842f105e65e780abe7157207cbf9` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:7dbe7d245b02ffa810416d70275240ecbb107669d9d1c85f6c2634b79469fe4e` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:c0c9adc8e5216069b56fe96871e3b4fc6469ba42703690de7049456f11626cf4` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:ba46c6d9ffacf97a07afe52fec6a3684666fa90e88f39c99759a27dc282e12ab` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:2cbce47529c9060e4fee468542217fb2e22012f2026928f8fc837c2d628e4fa3` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:e024a3c28389ad1217e3230bb34b7930c3de1d9a21df302acb0dd6e05097f74f` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:a0077aca7aadd2a00a0fc382fc5fd0db57bb85bd6b5f016f5dcba1902c005445` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:a3462eaefa5011fbb22674d51af97c7dcff63616cb6e56609acc0972b673e0dd` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:8abf2b179447cc42c7c4e914dcdf08fa75f851b326955aacc5d925fffafadaf6` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:8dc38299134eb2943550ba1a6e091195fe1c052838d91d385cb9a531bea7cd5c` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:a10ddf6a9e87110bbbf051d40d7bfbae288d095c97d2e0c4f3c518943a8f5377` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:5092271c4531804bacc51a7f2b4a66009e1e10946687f140f5bad8292a58fb32` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:b53ed09c9fd78ca5b5d6591f8be03b97202b9a46f6bd8a6f7cd7d04165fe42de` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:ab4c876990917f8e3ad46bc350a2502607866a0346d7108ba5c04f0913a10371` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:29971af1bf73faf4b50577fe0f35544a3402001473aad96696acdfbce425c6de` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:b043cedbfa9560d79cf0aaed2de87bca81f53e70f6333638e62bd9ce4d9ace4f` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:0e1a6700ed451f8139d5fb492689832b742f04fe716ae887ec77ed97e0b16fd1` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:1292e383b854250956eacfd01b299386fab7a08c6e3a84ddcdd33e759fb6b236` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:45d66460c80e195cfb8d424642cfa05a4810b5789083dcdfbd02c293665225a6` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:bd5b4d9dd3080dde2cb9c4f37c303fe05d13d2d10a71885f79a1116b3ac65a6f` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:362e9ef6df7aa12c686108f9e63dd3c8526c3bbf13d403e4e278f0d3164423bd` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:22ec5f103ed02120475d5a653add1755ad4e918a0c42dae8f642d6b159dead43` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:e8355cc6c58efa0b71ed9d72e6fbccecb0a72e91c5d1ae40e06deb401d13b06f` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:e583318dc7297be07478fc8ffb9af0e92bae8f3bd19710fbef5a807a5db18e92` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:ba009383d68c72e3959c867003e1084ae6dfc1b3265b779f9f22d955bb83e909` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:ba3e327c0bc2f7e3834118c33717096aa4b46c093914c281d6ac997ad9fb297a` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:eb1933adefdfb398fd63686608be746fd82b0fcd8d624ad5a7deca91859875e6` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:6b4f7053eafdab649d2eab19ff4733dc4378520ad76af100b3b3f157b25f5bd3` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:5b755aac00c0a935df9977c39f7983142f29496ffa48944ae8945ca443fd7021` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:3f69e2b827a64a3f90cf3c091e41e8812439fec9c74d0870b40583c89132b8fb` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:514cd92fb0e86086c3b2a823d182d430f6d7adcccef2630b0c1b6fcf5d1992b1` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:f6514a41f0bf0f64cf1c2bb2fd376e310821987e89f2cdc2db1a4ea44096c9db` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:386911dbe6aaf56d712de34347f6bf22112f0528c283064e203a9ba203437843` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:ec6ffa67b0c8cc86bb346f61a53530001dfe480a6310da3312bf640057566289` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:866de9a427f2452b059bd9dcdd789700f2548a0fe0155ccb3772e8917c5ef092` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:ce83da1e99858de3ca061ec88b63ee7432d65cdcb552ad318f52b5b056b7729b` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:4c1f6dde6223822c86cf360999b80c71dc16d7c9b9aca5def9ade2410e1350a4` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:c8aee541e08c5a56b6f52b2104803b410ded52bbc098dfe187a24f25650e2ade` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:8f1359a00cb26f0d4a125b7679a3c3a1a224094ca3d10cf6cf95d2e652a23f13` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:aae716f342587b0ba3b5edbee54b795ecd795304784e0bebebc25d3613be8003` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:8382eb984b7da565c0cc89e3f43bb78cf743882ef179d252cc0845ee29d56925` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:91bbf6cd73a8de92affc392fd59daf2a8a11648fdc603330ada61a86b847a975` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:2cbd71e233b67982005a9bfdc8efb08c8e5791e30fd3ff9fd13e4630142071bd` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:2fb3a645cc4c2211570ad1a53072bcbb275238b7c3fce0ad337cf14056bd437e` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:9298c25cfa026f20653975eaee6048159fe5d2e59ae987291ec910c32e3195b1` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:66494df736b5835a3365628ad4fb3921d8919622defd9caaa0eb0d1fe09e3288` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:50e50586ae54f4466251338fa4c2606191c56dfb0bcf63679834d204566af19a` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:110d50d508663be0407f88d72f29e5adf16ad494ae3e8a0f65b3ec5ce3a2ab54` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:11df3967ce61d3d0c9cf3328cd9db476017e5bfdc2d3b80e9a0dd192b56754f9` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:ba08b3543058835df7e93ef494fd63fcbcd5225239c0fdad9ec44bf48ff4a92d` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:cf2e575a7c4cc2661edcb120f88a5286bff14f5acbbfb4d0cba779ccc045262f` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:1375408c410da92ed438c820619c3ad91acaa1200a999a8faaa64c569cb55609` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:4c288e63a087469b5199cbacb45b18da2c0b6827919eea205da93162ca31dc5c` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:c07f593487761ec1032e69d95a42f70a20f6f250edbff296df6098a0adb5cdba` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:46f565fff50b5f552755ba2077381cda59c3e1805aedc495c626df908c1ddf64` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:4d98c54134af5f5ad3accd3ef3b3d1ca82e3992ba8a471cd7dab204e78184386` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:43a343b10d45286a11a147cdd6d77ad5cfaa8511f16791ebacfafc160796d6ad` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:d39dab9c34af576e669cd32fd40870c71aa10574da9514d9d95872db2824cdb6` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:c7ca70edde199824ecb5c5d436c631053a08f084ffdb4bd005c06af4c2bf103b` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:75295fcf02d37c28af2767be68f2afaa437cfd3ab8b9aa9342f8218f9cd9e324` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:733912731512fa49a07a7feda04d96ef9b9394fc79f9c185b7abe4b965d5d453` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:3993117518568f0b8afdb96173eb899395c530b83bd8aec7ba2657e460b289ba` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:00540ff9eaba51ddf053320bb218d4baaf0bdae17485d08bfe6cfc7915ae390f` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:b34263c3679564aa34013ec05f918adc25ef34c56f50ba18617782ac2e7899ef` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:4da568d5ff21f4d3bd48bb3c9717eb8d0e81039e6ac15d3a1060db2ef587744c` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:a659e570550fc20afea6da7aabe3febe362238f55a207eee4d256154f7b7e938` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:3b61bde38fe5e7ce7b1c67d8706fae7efdb2a2095f2a1d9a6ba1bec916fe37b6` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:2fc93929ecaeaab70bb8551984390275a2fb56b37f6a3ee986595e5f3bbdfb6d` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:85b29efca239efa9bad2a74d6028aebec1cd8af817b6eb3276846c1923789389` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:2e225f369f20784837f5cf55d1d00e2045a9317c79592ed0b224bc24143b21c0` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:b3a476b5b653271d5758de33ae1ffbe59e5098a5b033399cdb1fb542f3ce8c4e` |

| Locale for v2.15.0          | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:d2c650631f10bb3d13b90ac13cc8f9780a791b6b6eae4d3663703d61d4fcfa0b` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:7dddd89b8b4bf37ab90d1940344ffea2058234328bca2b549cd37e4343f553f3` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:b7efc1801d4d3f04349495ac7d22bf33a497fd1a84bfffeb410acb159c533aef` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:4979c5c0081efa70c6fc8dcd332a832eee97a4b04b0cbfc384764fe0d86567e1` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:770b2986c9563d980b4558502799d3b8250a7d7219b57c57ed9d7184f9022b90` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:d2c650631f10bb3d13b90ac13cc8f9780a791b6b6eae4d3663703d61d4fcfa0b` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:51f5cd8e34df11675da0c4f7fd4e13c00cecbbede60437fefc038e3a21137558` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:c34b2659629285e82f1bed7e50c6f6ee80f6c9ddb1ed6962af4875303fe0b11f` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:d2c650631f10bb3d13b90ac13cc8f9780a791b6b6eae4d3663703d61d4fcfa0b` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:d2c650631f10bb3d13b90ac13cc8f9780a791b6b6eae4d3663703d61d4fcfa0b` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:b3d3da168b41f08156b9df8e9dd5030e73edb49be71d05f8e7af0e6e8ed9f706` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:1dd1a311b7e4b7e10dc91836b0d211f1545e6437e6a7814624684c5d71491cc1` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:e0f7df4badc9ccd4b6cdd08eec7c88258a7e09e0647abbb900bd4df114599473` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:5dab3f7de27f841c2f7ca8a6829eb6ad8f28ab3af62b60fa7e306132b87c7621` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:bd35ad26cba823f99d917a726ce5d915fb9dfa6c50d522c23904b7e4236ac4d8` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:2ce791d2e99c9a7b2ea74978d97f3d433bf6069a2f3f664f98154afef211182e` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:5be44216c88ad990592205d01249f5cec661e96409ea56099126c5d7c94ced21` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:2a038ff2195b76e461ad06de8b402e24394a1f00147853aab148517614c21d5e` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:9cc83d8d00d6ab436f2bf8a8094b6e12d8770ea7383db034a46a32e16ce1fbd2` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:561e476e9a65446adf7faa5a4966ee9533ce0d24c4543a21347f7f3b3fb25198` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:f13e37cb642c93734839136779357aed562d738f1029e0f724950a79e241b954` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:375d0abe0627959e11f496b889f227b13b021d7509573e5e0d5c7854be684000` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:45c88bbe82902d192ed5acff707a26e9d2e126a3f75b982a9871a56c5d6a88b3` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:43e8e036d51ce9cd717d12fecff0e8cbe6d3380484132def9150dc28d28a2367` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:b90ce831b16ae8c19b2cabbb100ef934e5123ae55ff655b5d05ae56d47cc6ca9` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:2a4559e4fe9b69642e84cf9a349d2183bba5704c095a8ab8f418774d6cdc6dd9` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:bcad8e08c3309e8386d2cdabbbaa940dc438f15ef981fd2f458bd75167f3ab54` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:7b083e13cc36621d80b8909a5497cd245693be7ea08bf6504b570f0842db5be2` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:4334226f55e2545705c6d7ba0ce844a06c2c92added3997e611a72dec1a4f2c3` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:0975691a18470ff69c12e1ef8a644447dad11da057c19e554f5f7b4db72ca5fc` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:c44bdff4174fc83959511e64dd8ed2bdb6806d12a3ff5d5c70b94c3fee7ee2f8` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:15e046b7ae1b47b32258bd80c5d609c148a5c1d2d01ba319c49df834e1e8f193` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:8706ca92a56c6a32cec7d7c0d490d3ce16d52888518df93bae9ed0ad6981632c` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:99f6fec4002825e9e4e6dafafe1347e3ffd75f313c4db35d6b3bac3616bf4e30` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:44cf6984f82f0eb286fec16dcd142c21d3f86b36ba9fc364e305c9ce15b723b4` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:079808b43605b7386a4af22b18e295cbb377dce83c3a81dbae7aba980a022c3e` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:f678a5dd24dd4ffbea1872ec545de0e1ec2cd4326b9383ba6b1c041a375693ff` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:b541dd582365e727f0deccbf50ed7ae1ad11f525b02a5e9d97c8fe796f5f4054` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:859cff274dac5370c00c279b003b4cbcd194e982e3e5d26c65fda7fb71cbdc8d` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:01dc0b5cb4effba99d071292d7fbc709ed4a64f89eadc809f86ea97501f6e411` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:7f4572b7dd89ac1b5376050f6b35226fb9aec52eea9405969cc684175487e699` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:da29fe62e9e32de8d954d2bd9ee739dd8d24b31cd4943df79dda5f10f5814b08` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:cefd94d4b3fbdfd2b66994e970024922dcba2edf8b8b9da6f66affe540b24ee6` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:1622652a17e67d9cf28a407bc37067c0d06b496fef4bfc121566a054b5529613` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:18b729556bafdcd42e6c71e52b2dde4f50a358cbbafb8774b565f157744bbd50` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:6192e1752fe67d6fad7ee977899847616e20612d13fe62d869591e0bbaa9b98c` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:05268165b9192848af5c20b66d0dd36ab6f32eb4d8f14be05cbb99e82c02bef6` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:cacc39fa400e40d92530d90e4ce266fb33251f771b9809c48814c30b98bc0631` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:2607efa555ab788fc6e8065e70c853a4aafcfd544d3b83964604f4de4a1a698d` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:ed9c87c68be413dbd37f166906a81ca195ac13a176b77ee05a6fcc74a5d7c4aa` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:d68902cf6ae127401d3b76deff8977e2570a7c93ed1ea412991b5a24258a4ecc` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:73af6f6cc0c199509f7f36c4ce3745f9f098f215e76d3bc6186c0afad169e590` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:2f6627d46f11f78fb60681edd80646f274a90950735e29b75cf0bacf2ff1977e` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:51baee622521baabf97df36ee0855158a57795b0af25081656afec59edbc9586` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:41d74cef7c62996b51c179ff523a6a81fdb9dfecbc818386d703633176802a7b` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:6bd7ecadd5031c66f798c0307eb85bdf98b912c5d3ffd81dd93a7325e164dbba` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:bab0220a4968a23bea4616421b81199cf5eb195e041c1ba78b23c7fee12473c7` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:5aaaaf0a65790dcf57adf8bc6647b8bfb86d0d287d0a9d7a04efb8ec793fe750` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:aa4c24a470b246bb77d00c11aed16042e8e7516fd1fe9df294e7c1337e4ecaaf` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:ff2ede2432a62a40237f6a72a6e60884f14b70bfbf22fc5c304e5491e57a163d` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:5208472ce238b2a71390564535c077bafd9ca8333bb05e89d23e95462d6930f9` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:27ccc4ed68df0ac08c5cca4b365904292f2dc0294dd35f507aba7228ed6184ac` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:238141d56fcd9ed45462dfd6189f252c2ef82f9d2c78b2d31ec1d35d4006b2b1` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:80015aea35aee6bdf9fd0dfcc07ed944b971e2910cb5f87f659df5a699d4ea4a` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:e92f28a42dc7f78042cf232662a0f6841c6eee7eba1c2df7a98b11b68bffb146` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:9263f969b4305f11954c38b1fce443f7c4f0b258fdd376d2446a0d0146decc69` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:2ad8e5d741723d5457f5698c5f6c2bdbbca9d8e405582aa68ea86bad60e88ff7` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:d872ae9cbfbc7baf76c21144fdda28ef908922d14cd2b76c527eb0af24a72bf6` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:881a2b767b0cbc0fe5f5960a83f6126bff0f3adff8d9aefe85dbba00a0f0b586` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:df48b6c13b55f483dff794110e47f9735accfa84ec025028f5334954dbb6f947` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:058482ae932fde66ecfb990c23d5c49d2cffb4c47c99f4a1551b582aa0a26af4` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:27b9215c6034cae40be0b3b7b19a366cd134b0ec51ade33d90245cdf32205fc4` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:544686ad0e4a7ab4e33735dba769b5ce11057bf81e6714d124f0230389c473c0` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:bf6e5d3e2536de160a79957b063935627d98f15359f673f89b4a55934ca06209` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:7cf5498bab1a5b28131d12c72a0ea107f2d00e562c51f37cbb87032dbcf50f17` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:0ea488d1dec874d527938e622ec61406ac3d79e99cb7d905042b55bbc6d675c9` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:8030a1ee3d71b857f1138be2357c4b82113813899e35a0a01a7f465b4f17dd2f` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:fabe5868e4cb793e6ff0b7dd24bfe1aa2a5f8f833e44b0b414cf2a11531a37bc` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:eef963f3fc2ea78f806f233c2eb3500dd74e9f82e54a37a7a21ab294ea8adb83` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:e9f280bf51858e332cdb6a0cc0609ff89c4092e21053249125700efa85d543de` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:73a5f5553c64af018ba7e3202668ca7964143b0fc25d60e33b0c76a60687add8` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:8254191226a38235eedaacf603958b66b24e560d3fb56e1e40b5b0c8bae5b520` |

| Locale for v2.14.0          | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:1f9fc0564b2ba2bdbeb5a3160e7afe6d867f3ad48cc90825054359f0f129b730` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:7af3ad10e6095078ee67d0426863117e2c7c861299b3f9323b6f71a87bd7fc1a` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:ebe36bd9689e12ed888a327de459b3ae26b261ff3371a696924b540ddd8375b9` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:dd46d062ba1b7ad03b59c9dd04816a139f976db04739788316431d223e0b5ea8` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:10284e45719cc5ad1f0783807e5a3b731bb8728fc09e56206788fbb80f0943ee` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:1f9fc0564b2ba2bdbeb5a3160e7afe6d867f3ad48cc90825054359f0f129b730` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:1bf6456a34e1ae5f6797741039848020b1c4b7fb68f1816533091abf92be56c1` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:f1389c71a85ea2bc16c9f990bfcd74b0c8d92e576f0dfd5e68bdc9d1e860ba71` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:1f9fc0564b2ba2bdbeb5a3160e7afe6d867f3ad48cc90825054359f0f129b730` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:1f9fc0564b2ba2bdbeb5a3160e7afe6d867f3ad48cc90825054359f0f129b730` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:58ffbf778fa71cacfdddcb6421d9e2514356b75797a3f0f689056c4e7267e527` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:37baff85bfe5d78b3858c8f7bf921af4c8d73b02fa40b731a0843df908107eba` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:43abb6d9c2a85fb3f7daf757acccbc67058cd5d49d268ef043cf67851fe8d3b7` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:db9192414bc542b77670f4a281f0f2b818d23a95cba2751fa43bf60203942b81` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:88c502880609a9cd2f35faa7d6d4a527e4e4bc80477deb21977086615677a700` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:3567cf9cfbc72a0280cc79b561e832c1a3a26d63ddcf41fa2d08e3a80e09b765` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:484935e2a676d561c94a2e2a335f5328688e0b71a9683351ef1439a386e92651` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:b1d18f984bbb86f3cbcc9401608a31c85b9af1c0c6a6cc0f7366bda18e79d5f9` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:c04c67628e49557136860cbb64ea350aee8f09ab0664ed00fa09cdeb3fb19726` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:dad0620af6f3c4880914b9ca25266c6436d372127a41531f639bf682972197fe` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:43dc4ea303c9509f562d50f470b3590beb755aab295b40d9de6a5d2f4ca62c04` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:c8370e1398b7ec2b4ca88b4d2e6d62df9e4495c25644231abe59a2baa89287fe` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:cdf5a3f4dc32113b9fd7e667bddc36820ac359c65b860cc8b94faa6a6c5009b0` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:5d4d5811f02295831b90133aa47ca370a3243ea854ae52971c3439d156eb72c3` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:051497eadedd0d9de7a36ce111ea2b82b37e2c98b3e8b06b408d32b791c4b76b` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:d2b89396713a1188eef7873f479f8deca9ba2a80c43e19a7d227a6f73509010a` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:5f66867b47fd9fd8d1bc67c05da8ae775f937ab208c192f4199d2de7b30e5aa6` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:e08d7cc82725de9ff7aa392a08dc484407f60c950b85525f337c42ff274aff11` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:126d73f1cb82c3e2b8995afab07a9d6470ca7b236681ef7aff5194827df52008` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:7cfe66dc2bcc9c7b975841954735061e0b287664083f35bb75d226015cd32805` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:27c45610f38099a50934e214b75bbb578d3ed61fb982e49427985ac76f7be9d1` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:b06e4a35f6ad8b195870dfa9816fb81016a9cbdd8adb3c31f30dc09e370f17d4` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:8c50b7e3847f095de6bd7599c7a953b82fca9f849411cc7407b20b805c5132a7` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:73434492751b1ff9e2a3f141f0c5857d5cf2c5891f1084ce981181cdcb115e69` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:769db62fab433e1337a8a47db155127e887de4826d035e05345ccd86c9668c72` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:e765c40a9b09fc4d9f42a9ef4bd138181c4f4826e63af1787453c10b10cc1554` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:b589b794035513de33740d5b5b6ecdda04fd059e9efcb1110525d4b076168cf6` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:b30b4a330b7e74777e5d2575b1c2bd4dbb7a920d7165dad40b00765a0b04c564` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:8d29f96322db11e99200cf14390e225d8c332b3a6848eb6d23d099bfe552dd99` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:bf6edf5bd61b57095181546579df3033e26aca7261e822b932137eca6078a947` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:a02537bbfd3a4231938a321dbf9a575178018122aa4c387ebc9bbae070f35152` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:82f14c7711bcc02b82b75e3be1620b528991e4c5f1859155926bbb58c4941858` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:500fa361a26d3da4e1d9c2523b232ab0d6c00ab4a15141bed6086e39022b79d4` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:e364eec54c48e2bb5c14d53356ac3942f8bfdd65d7e139c86ce79fa9f85d4634` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:165bab6f0a5a12c58c8ec04e1b5168228f97031b80ca368529576d507152ccc0` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:42855d56f39956d456c5337b022c71352bd54bfd2d7a6a9a9ffeda1b821c938d` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:622193b64874a3169c21862762017c4b9a46590057e388330fba80ab775e7909` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:a33ca1aeb6181f6b034ce831aaf3ca1da0df8260b08c87749eceafce6346afd7` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:6cf2522c507c77ccf7fa61ef4b54e8dc4a3f3b47b7602aa8306ae867bc53c8c2` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:e6672fc9da94245f7d75d91b7d09e4b929d60ef0157d28885e057eef20e347d8` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:3731f5a8baeebf02300f3d40a3ea3e3fdf343b817122eba47a0188b5568e1666` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:1567e85ffe2e2660585a40b43e61fa936abf4ccdd8eb89a37294c2bad83f70b3` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:bea4884eee3382741e1d02d99a530b608d30e48a446ba52a73749bba7ad34fa7` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:f40151a6519e0678969adb2d492f240e355ac7ac9b4f57f75e0eff878741d33c` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:ab196670c90b23d8a40448431f703483da9605f92e71f6ebc75a72cfc38e1598` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:ec26ed76cde3ae36eae3a5f0b6567ac60ea341e2f95838a84524819829967f4f` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:054f188fd9be04f57858053a0a6c1146c13c2781eecd732c137807ee94009d22` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:ea6bf9b3b4bfa1c4a25f1890c90a18fc309ef17afd6044cb66ed0fc31083c957` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:6869362837c0124964ed75ab8901fcfede3894902018b41b400a55a0b5f20cf0` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:7f8557bc112fd4ffef29df308bd10c0803cce1f1f6e79e69f88be53d636aeaf6` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:746602c288d80c0599af276acd50f1434a331f288c95a3cf9ba269386a9a3929` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:b6f432bc80770f13ca537a2b49a4e89e8f979a8167f2cdaaa8f1242bb3edc97b` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:f2126bc8886218374550f2f9a941500cf48675abdb70332990e90e456c332f5d` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:82c75a0c741543c2195d271dd82bfd4400901204584d9f7b83d154d418b3eea5` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:e95f2edc5bc2090e0359c63047c4c5c879522080f8bf7cbc9484d1854b606a12` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:49c5d9b0d9de260d88deda5eeaa09979f44972610b26ddfad7969c91278f055b` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:3c5789fbb82c62eaa68451d391ec736ae78c298248f3afba027172c477609489` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:79a2bb077362c29495fdbee7fc6c8fd0990f080718390fb469ae1f01051d597d` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:ef80359958fdf6b07461c3742c3f860c22652ccf9d123693a9947d11626531db` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:000345b6a1a28cb5970c471e47963f10209acee74cd46afa7d41310a397c9b61` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:c4a996b483f91f278f42f1696ed1d89d2e4ee8c0ed409e9d21d471303f78bb71` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:396bab6bcfe341b53b0992fc2aaf4809767d47b8637f6fd21448dee899e5480f` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:73624839708f88c93645a6a35278d0c2ce9a944c5992e237a4096be9142b74a0` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:86fbdc4e994507b020ff27735b741407d9f7d1e01fce2b17e610dfc9c16d3af9` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:c3ee782b60499ef16127b5829c36fd98c1933890752fdc4af6cc34b7a90747d9` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:d10ced4e32336d4b411e65066dd5486733d19b8d1f4756d60602117bce6557b7` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:ebcbaec4e3a494099c7edf15b22acbd7b29347fe7cb4825d13504474e72a5900` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:bb239e9081d9cf4fffeee666346cc3c67ce83b9bda1d2e81a09fdbdf705a7c46` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:68d554ae90b0a2202be5f09fb03a7d277f7d0cb0336cb0510bb09ecd7f42eb12` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:2ec742699abb843b91f9516cb863d66ecf5f38d5350c3c23c693dcb2f5804c66` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:34f21fed7129dbeaef6476b286e5d6741b635f034ea038b8fe467512ee0092e2` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:f2e2dc638ac2e58177302947df30bea7448563a012deb3e4f48f345c09902bb0` |

| Locale for v2.13.0          | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:9114c6885513cc3ae8d3c9393d3f4f334bb68ff9e444734951f469f8d56fb41c` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:924dc807076633f4e04f1f604c3db63d908a484c69459bf593d72b58d901cd43` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:13387db275daf6375e12ce1da5b858493ab71b249a3759e438345ac32119c6b2` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:2e8bea90f7a106a94e36d9c90e767c58cd8004a61880af53bd4ffb4292a655fe` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:23c8529ee0e91fee549523021711a755da4c249f21493a1864a64941b36e2986` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:9114c6885513cc3ae8d3c9393d3f4f334bb68ff9e444734951f469f8d56fb41c` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:70bbb43641f22e96e70d3b5723b2599dd83533f33d979ff9dfb04a627799f4d1` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:f6fc1c1bcb7d20f2daa30506a039d16ad0537a60c01e41b399159704a001fe42` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:9114c6885513cc3ae8d3c9393d3f4f334bb68ff9e444734951f469f8d56fb41c` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:9114c6885513cc3ae8d3c9393d3f4f334bb68ff9e444734951f469f8d56fb41c` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:218c1f57623b81770c22c7f871bce58a3227ef5fcbe7581e18a69f77107b5c96` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:9537460403216802831fa02a6eb3bf7a3f6e1e6669953ab4ae9c98ea6283799a` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:94f68e496546eb3c33cf07b7f88807fa23c3f9d5022c2e630b589e29951f0538` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:10de908ebf603c6b3a2a937edc870d5fe1c4dc6bc9bb7e1f0eca9b9ed2b19a88` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:cf03effc2a616b8fea8eacf7d45728cd00b9948f4f3e55d692db0125c51881da` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:9c9a51d595253c54811ba8d7502799b638f6332c0524fca2543f20efb76c7337` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:6bb17c45a291f6293970a4de7bfdc9e31fdffedf80e76f66bca3cab118f76252` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:1e58c2e2416208b658d18fc4bf6374d6032710ff29c09f125c6d19a4d6609e92` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:f0c4da3aa11f9eb72adbc7eab0c18047eec5016ec8c2fec2f1132ddceb3b6f3a` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:4d0917974effee44ebf1721e9c0d9a3a2ab957613ce3862fe99062add5d5d08a` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:b72a01b0cfaa97ea6102b48acb0a546501bb63618ee4ec9b892bdbdc6fd7ce8c` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:d26f56f1f4c41b1c035eb47950cb5bc6bd86cbe07ef08c2276275a46ac4c4ad4` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:0ad933b9b3626d21d8ac0320f7fb4c72bcf6767258e39ac57698ce0269ed7750` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:d6f9344f7cf0b827b63fb91c31e490546732e8a6c93080e925cd922458ae3695` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:dbd1fe80e1801b5fa7e468365f469c1b5770b0f27f2e5afb90c25a74702a0a21` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:f234725e54af7bda1c6baa7e9f907b703a85118d65249ca0c050c52109397cc6` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:88dd53d975829707f6ef91ad91aec9ed5fd12df8f4ef33e8c3bdf4701eaaca84` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:502693715b8b666a9c10084c733848f95201e9882f9bfae7df770bd9dc8bb983` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:6aa4f300639f7ee958adced5e7e5867e7f4d4093f2ca953f3ee5da9128bf08f6` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:60f01882b393e00743c61c783e98c1cdcf73097c555999f10e5612b06b5afa90` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:7b58b3a823c0fff1b92e46dd848610f2c9dcae5be0463845292e810d3efa1b1b` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:c51291acc65e1a839477f9bdbd042e4c81d2e638f48a00b6ca423023c9fd6c2c` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:085b3bf2869fcedb56745e6adc98f2a332d57d0b1ac66cc219cec436a884d7d5` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:43e5425cab3f708ed8632152514f4152f45a19953758fb7b5ebe9f4a767bcfdb` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:249f3165e0347b223ff06e34c309a753965a3df55bda2a78e04d86c946205d06` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:624eeed264f25bab59a7723c6e6c3ae760bc63c46ebe3bcd3db171220682c14d` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:6d2d41e3b78ebba9d5d46fc8bddb90d0d69680a904774f5da1fa01eb4efd68e1` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:ce4b4b761d1a2ca2b657b877c46a341a83f0b1a46447007262c051f6785b7312` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:d4ecebce65a18763ac1126bf83706e49ebed80b79255e3820a68e97037d2a501` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:c3088a60818b85cd0f04445837ea0ddcb6e7ac4f77269471717002166195d6d2` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:1d88e66f6fd86ddf6e47596d2e2b9b3fe64ea7e72f6c4c965d3f1c5b98592e1b` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:bb07eb832bcd23f302f0a7b6c4e87bf33186a47ed154ac8b42a1f6dea0f35432` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:b726f92daf85c8aa6b169767efdb2af1691ddb7b21b8af3e9afcb984f41d8539` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:660a5f9e13d62a963c9c92219f8268ad7f7af5ed08890534679e143cff184004` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:cb708bc008a59ac35e292094eba912af741c49eb7e67c2df3c1023ab41a6d454` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:acd788410f8f6f8c269c85e6c70365e751a92976d61b34b7435766c0ae2fd11a` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:f7ef486a64a413f7d69510f25a39ddce9653265852da1b3cc438000f1bbfa368` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:7f6975423cbcf201e318bea9865e93a8e4a6a241b472845d90a877400470338b` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:e2f498c4a19f88779dfae350e0cefb4f0aa1c518c18f43139d4bec6a4f655f45` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:66ec075ea26141d73e07a223f72f10ea8237d0d9675e67d569f026ca6125cd95` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:34b4ee60880d310aa08f1584c2f8d1a9a0236ac0067b9d8ad8bf5057749f2d9b` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:709bc27ebd387cc18d3d16136280234f64c4ba28f05383a52e0bbe066574105a` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:cfd3140a3c7a5234c0273e34b9b124897cff6c2d11403217096616dd34c14e38` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:f03b3407772d4a5be1642ff0f78c64283c2e8fd9b473f8bab90864a59d4f8a4a` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:c67190092fcf7af406406e5906d9de79a8fb37565e84b2dc0786caee0b5b27e2` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:eea6f9608d9802ac43e755de39d87e95e708d5c642f58de09863363051112540` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:3943c40ef4696c44887d08a1cb911f535af451b811737b0101a4fa0ef4284d68` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:52eb41ca6694497356cb23bd02daf4bb2408ffad418696aeb1bdf1f03c2e2845` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:70aa2b907f114278d839a958dea29c74b64cd1f7a5a0406194d2aa3583c12048` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:14e222688387847f51fd858c5575e554046796090e41f072d6200d89f5608e4a` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:8f3ed7b3896b205b5690e5515a5511581715e698cd6fe0704c153d35a4c9af80` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:806572a1ae31575806062301d22233b753c415388184496ee67589ddbc264d49` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:780444acc9be4514072926146c36b7ccce003f27577b339cf431fec2ca6d79f5` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:75460753cba8d45babaf859f94dfd1a1c75b312a841eacded099680dc77c2f89` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:8d92a5f26100d309a11f05ce13e5e5a0f2bbc072df917af158cc251dc75a4d4f` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:d9c75c885591ced0e10cca5594ae5cf92cb1dde73306f8454737b7927aada89a` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:15cc274d238cae2a1d9cabc3e5a71e4ba90ae6318fea63937c8830bd55da0fc2` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:a45730afdc6d15060eff8526e1be08f679b25a2be26156d39266a40e6cd82bc9` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:8f578440ae5c9cd81eee18f68c677bb56ced7c6a6a217d98da60dc856fd2e002` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:99fedeb4acc49fd3185d34532b1a7321931b17f2eda16ab8643312dbf8afcf38` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:7677c49b2426fb26eff59a97a012d5890aa7fdbc09684ef0fb29fdbe63fac333` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:452d269e8e12ae1379d4568bc1b15fefdd3679903365adb3a68bc6669c738615` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:e6fd994a344b5452b4a5b90a499fed0681dd6ef2fab3db161d407cf4f45ff5dd` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:4df5fdc9732c07d479275561522ce34a38c3864098a56e12ec8329e40f4e6f2a` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:49180ac0eccee59a22800f4c1ae870e3a71543e46d2986fc82ec9b77c7de1ea0` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:a0c64efbf2d9d0a111efc79cc7b70e06ac01745de57d9c768f99c54ac5642cee` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:8811c30c10980a3ddf441f1d4e21240bfb8663af6200c2d666fdeb83f48a79c5` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:99860f484f52d9665f33d95659daa8aec5071fa5a97534d40ee4941690ce3e96` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:170b56107ccb22335422c1838e368c0f5cb4518c3309e6259b754ede9e46ff51` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:d8721f303ca0b24705c42e8c0f5d20dcafb3d00b278b7c363d1a4c129f5e2cbd` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:12af9f057acec8231dcdeb1e4037ac53a95957796b5e8dbf48f55db6970a4431` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:b2c1d333b7718c9cc2708287e388c45abcd28a3e8d7fc3c758cc4b73d2697662` |

| Locale for v2.12.1          | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:070b6f390dbe7b81b72845c1c9c83087979e1e330d84d417f39a371298a4d270` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:2b67e2a2a3ba79e52c5de4b2af7f3d3db565466d9a55d5f9d7501f349f42b49d` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:71cccd4dc4938397ea5b065fb32ab7347350c834edb036805362ca28e7cfec94` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:a9000def8d9c634af244384442c2723ad887c79e7f80a767bf7fcf3638a9deac` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:b8be9222b3e1bc40ba86c41e707f239d9ae23bc87d90b800615c314a443d947f` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:070b6f390dbe7b81b72845c1c9c83087979e1e330d84d417f39a371298a4d270` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:d41dbc9e93ae524abb95d2adde53924a32956ab1ec14a115916e5e531b3f3624` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:3071d896f82d062e126331e3162d5408eb399aeda3041be2336f81bed0634e5e` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:070b6f390dbe7b81b72845c1c9c83087979e1e330d84d417f39a371298a4d270` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:070b6f390dbe7b81b72845c1c9c83087979e1e330d84d417f39a371298a4d270` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:d7207eb391d0455ae112b61bc2c22280618131ad9591324bcde7e5057777fc26` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:c5c9639b9e09e07f6d8733017d30beed3aad54fa91c69c72526d34aa27ead884` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:dc6b7697099cd966aa4c8ba0b192ccb286b4241a76b12dbf494a9de319191334` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:ded8e56b863567e73b92cba4b7abeaf3f8c9ae335280a9645961d683ebfe8f9f` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:d3fc39e0d0454609bde5f6df67d7ade199f5361559ce11f097e97fca312d78b7` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:bbd8ede305ec5b551cdfac857507a1d05c3ca95119e431f0f43fe073d830f8fd` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:e4f39db7de5fb8106237f73adb2fbb229a7b8cb21291e593a346f928af87503f` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:186731d8479923a9dce053aee78f1347cd512471ead33802faef19bfa4e94883` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:04ede5a65eaf6f1d7a36d97056468b024b1577e3cf3a2cdafcd511d1de64f9d8` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:ef48d6889daec88405e7a86b3851df449066da8f0f62404260eabe68081e9b32` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:7d66fb960d55822c648919557d8e921c570dbbe36b165621f2bd5081df3c51c1` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:4285ff1d4b2231bc112a50c22072dabb303240ce18aeeab7183da3a572298a6a` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:b32b94f8a2bf56e0fa2cf63f885e9456b430411038ce2ebef6abd45159787ef6` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:c2162d7524bafd554fea81f2b3d95f3848ff0bf4ec0c4bd9d9bc4f2eae75ca27` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:e55f7d21d3b9d230bba78b41eb2418abacb7e6d832a0ec350ab86f98420260ce` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:d0d3d6d266f05cdedcaf75949ece66492e2e37b15684a80d08de3494381a5d10` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:b708d553eeb22958563c24fef18edc67f89d1b4ea0ff31a66ea34c624fcec878` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:5a5ad9afb9f0935ec9ffd5a1034bed186c46d2f9ea82ab485f949695ca4c2b61` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:c0f4dde13c319b4fd75b6b8615fc68aacd22ac04cf8b605d8d62486a08851d2d` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:af5f1435cd3e58ee9e98d8623a071dd72f30bf9ddbd90e1a61f06677ff34c0d3` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:ba42ed9a8c102b1af53873fc0d9ccd288723be3f5a409bf1480363381f8127fa` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:08292bac0b6d97c5ba3cb2b277c53289235216c124c72ce74c0a2d734860c777` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:e245443a75fdcdd8c10463a45a80d716d36cf336dfb23948f17d50939f65e919` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:d5d853b26104f2b9b7bf48a89dfe8a19f72c5d689eb474d68c8234c8b297dbf0` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:9a503a29fdf52a973c0e9339ac8b4f52442e7130c340ca7e12c8a38df004c8a1` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:661726852daeb5d1d839c05e95c0a683e9722564356089bd4023edfbf83076ae` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:3c55158c8e030fbad2f090b587cbd6501303128af77ff0bddc8819e6a9a88e62` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:31ea64c3cf1d442b5182d664a16afd81ac402ab8a0c2434e642317f20c920be4` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:1ed31bb1cd484fc23b177c355ef65c12dc2b937c113b2b175f8b383e9390ca86` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:0c979930fa983fd76f6d3610b2d9c1018eaefe456b8b5d07f5ff90d605bebc9e` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:7bb685a97e64130caaea382d1b33b57ffb4dbeb16881f421ed212f81f0d46de2` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:4da6a791737e136e494753666c7a40518e147c7bd225461165714510c19a44c6` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:62b41c8003fcc17f5aef9729cfcbbdf81990e1ba2bc4ddefcd947ce3374f5794` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:eb396527bd28bfbd4a5d70ea29775b8352f3490d159b3ceeb32b442058817e12` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:a70f0196b552934d35b165059b28f192f97f83d451ae08ec0d267ab8a3c6adf5` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:361588561ed3ade02926e9db88ae1a9455fd76e6370ad794638d794129aa0036` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:120b28f629f4825e7b7f52f28f535f6c1bf2f8139c8288867a4bf491fc155a4e` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:ebc2b82704cb4d1be4d3dcfad933978ceb3daa8077cf6cadf560d8c33d6f4334` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:33931d7b35f8e7a05822aa7052fb89e8de3124311e70ff567a7f9ca158223f27` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:cd0a9c661b4645763d73a947e933b9d4e817485f4b9d6d0ac173195693a29f33` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:06e90396c307396ef395c23efc3157f75c207f230fb048d73ece407edd24c7b4` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:d9be6bca9c3abf839796d8f89bf43d2646080150057f6eb343c66042bc98ccfc` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:1c3ffb5730c401124edbb7b347569ca3bebd33412a24b32802f4d41401e911dc` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:218d319b2835da7b09ab4536e5d8301ede2bcd3bc023606d05d7294c534982cf` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:dea03196c1ad06cb1bf9914b5c5d1a631aafbaa5bd74a4d53d08dec982f545fe` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:5f33b06d0f77fd3c5d351284b2aff41681927cfa7fbda00ead338f7bd54f6575` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:2b7e558abb94a74e6b5a7f467289ba5cb32970967cd7409db2c150290ed9844d` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:05619049274edcd572d1ac6fabf11e0bdd2e95a9145e99065f46d2f26a2dc960` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:75253c7bb0ef67b50767593e36129dc98c8d9de60a31b2a7069d07a0cb6b6400` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:46bce0ab6a09f0837a4f884e29a69d38591e513e157d334fd39a2c6f1f08bb06` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:747bfeb07d354b848f7ffbd292c16befc00586d62b958fbb42f8b497a0dec87c` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:eab3cf2323ec4d86b923693595e16724dd6090d60a1a93a9d65f73c55b684448` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:1c5085250bcdbde6b619594b2f920c307b3d97672f01f03608618bd52a4374a7` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:b35274995b93587b8957101e8139598011d760df1f4c36f966114a4352b865cf` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:59b5088fef6b8ba41eed98dd738159e914c292ce790a3b8a934aa0ac6c161cca` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:a0074f10622c8ccc7d288cfa131786a02fe2c98e2cbe22caa0d07690c436f8b3` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:a6fc1ad6ea87c5f6282f3d10f724358e30f0f05c91084d52fd665e356bd6119b` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:9fc1363f4466d4e0bba3f2fb74efc54ff24fe43a55fe7703aa75da2b42e563c3` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:e3ec228d0eb76f91cd1fe723607eb0b96b9e1dc8874c40d1307f2b3585ab1912` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:9e6bdf31a80cb8a97b495ce39144d4957d9608e541aae9be6c5c35456476d4af` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:240baf152c419caeee33c7f18285d930af15d14ce784967305accf6541722a22` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:53eff9f8eb08bba90efb30d8fdb2c9760bb0d8ae60cda967b72f0433ae18f524` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:39ff9f4f25ed4953cd5db2d0083339d712ab1ff2adfdcf3e8cd461da94cb1c97` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:a4747493c498b85448de88e4a2b9f967a33886e256c5b7b257c0cebe41963245` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:f49c20ffe5a816f929d0231f7bbd8ddfec37b74b0de992012401b6ff1f0d7b92` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:d56c941c25964d6eca44fa033f12e4bfdc1e34df24bcad03ea35ba687fd91a4a` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:18cec69b7f443140755c55cdc3593a4be7decbf774420e7aeeb38eff92b7b880` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:60f1de16c63c4b1d1450c1b58f06b9ae6f33547d133b07e6f9e57035188a82f6` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:b314044779cd4296cca629d1e5cd01c0c1caebccfb32603b32c07e0374b2832c` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:5819f0f4fb50e4fb8f0485dfdd134ebac74b2376371a0b8f6c915a3e15873d6d` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:c2346a98f8d17ee50da4ced6d4cccf7d36a4e9589c571237b3f4850a411d66e0` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:3accfe8f947359764e92831bdfb5d33ac8add29e8c43ef0af3dfe1c3ff004783` |

| Locale for v2.11.0          | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:32c26ed8370d1f30098811fda382e68aceccabc671570365f15ead37c3d84304` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:a6af48cdaf9f7562bfaced449016106dbde5c678fdd4c69985d166959a38b146` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:43cec166dcde9dc7cd535228440d11d396518fcfb14d9fa617e6e26f5156dc84` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:b55095b27e8eef60dfe9657735a425b9ca1fe3c29ce4ff1f3d67bf7b2ac77bb1` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:7cc4ad997a76844414a982982251653525f27dc396db44f23b7f012d20f53677` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:32c26ed8370d1f30098811fda382e68aceccabc671570365f15ead37c3d84304` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:5d3b402f41f616ee792a5e7e3f41b4ec5638dc8ad60a3c133ec588e07b09d581` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:c4f88fdaec73ebe241d6c94695b20eb2c792a9fd77dbb51f24fc7807dfd0dc61` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:32c26ed8370d1f30098811fda382e68aceccabc671570365f15ead37c3d84304` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:32c26ed8370d1f30098811fda382e68aceccabc671570365f15ead37c3d84304` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:a42b6f63a16313f280088bd47978e177bc2f1bf2d392a070cf5c6a06d9f7a62c` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:21425557e62d71326e9eb614c535878f981a914bf66d9dd883221656ca891858` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:682e8a8ad5f2582f25a18b0518f9fba9b3849b72eb5dab5454586724272c52de` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:1d0661ae5920f82e607c72ae7d6eee917c190d80c3d13403d770947c67a4294e` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:8d5257d6c326e4d96ba395faa0c717f48c4d437866f8dc1e1252c5e983b3008f` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:086a4e33f746868fc1865322f1d7dfb5c1c3af64bdbd369804155f18710ad96e` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:0e2c7d5337f953d45fc7594317e6eab5eecec44a1c15fba51a128fc510519c3f` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:dcfe3fc95b895d0205a7b72368595e98dfdcb4b6398522e7daa2fbbe2b087ef6` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:f04cedb6b50560f0584cb3634cbfee5e9c147d60fc044cbd0df10fc28f04ed98` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:9692c45c6b5b8716f99852a2ddf4b7fd1e2c00ea29f9a20da68e899cf3064fa1` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:97106aa991b4ef5b0f1859ae7a7df3c6e22dd009123281a7458d336a78ebd854` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:da2bc14cd86f200a439b3ce708c6643d507d482daabae87c351bee4c10efa60b` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:f8fc43e5d20afe8108b6f35c3e09d403557f150413672d45322421be1fddff20` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:abb8ca669c806a71af88d3643694252e1833ca99aacbd739a3962ec00c3cdb61` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:13bc7717dd73f4323956a3f7441b24dd2f86c13d41adc709e3f6f26266cacd91` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:b7f44d7cf4bbe4d89729207a38e91726c321ea03a66c5e5624b27ae9913fdafa` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:d81ee15821646607aec9fa46223c9197f74675a89070912ca892ad5adfcab6f9` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:2e2f9102c9f6fba0736fb01d745d35b677bf92750eed5cad245ee089998f66f2` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:dd962ec3f32b8fdeb15f7ab18ea9d19e7c93baf4c801fac59d44f5cf845e9935` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:f89c0e513f43800e1d19177384b815c1a04f5b07ccba8fd9c80aa5ebf5c71648` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:3ebc64dceb1b7fbef716de3736a020b23e8fb4e9aceb183524863681e0b278fe` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:ba05465c312acf6b9a1a1866c81c795027470e8bda8389dd0fcb641c9f1af592` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:51d49d90f600ae971019974a6a38c71b3bf01a84301ee6e8604c3f424bc6773f` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:a19f0ab805d0268c06a0e83aad2dcab458638e8c2f7869f5b2315695ae2ea4d8` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:a9539f091ec3feef34511ce9d337436151980eda69c7f8c8f2493e8d1be81e66` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:a0f5c19a683b92566747db79e30ac7ad09cde07bcb15451166b5257d036a86bc` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:2aa5e82c726a8771c706a2de38bed09ca9c8298bb166c49fa227b8966011efa4` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:60361c1a305d0fef3deb0e4886c4044aebcf41878a748bc0615b94fcf9489cf9` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:d628b894966988880bb11f1ec1380702077bd45c2a83b912ae3e7451d8fd90cb` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:2bd901c320237e041ecca1ea34c359cf847cf8dacecfcb0e1ed8fd1794463fe5` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:099d21e5e5816d5d7e0965cda5878bfe78f5447e4994957dcc45ae40223b14b1` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:af6c258b7e984ee17d32b9dfc49969cfc1d7ee33aa2485017fab191d8d574e92` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:7d0e03c7f44f61b4632b730c2cf8e3d7c584a869bb5d53b9e5021549d1d500a8` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:ad580c1ac73d919434387869803d9fabec24e19afd6b4cc5aa7e809fb93dc908` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:2e85df2af0003c0a41752c6e989ed8b724a22958e7ed3cbf67e54ca621bb5975` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:bae49ae543878096c1dd0c77a8f83a30ba1416605efa58dad59ca3577f7006ea` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:fd9deebe4e5a4466af439a8e40a1a39261a7b0228a4ed979b8086e1c65c60e26` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:0e69fc4689dafad97e00bed7c4eb7ca44b94e3a3d9357d6d36bed8135963e9e4` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:37ebac38fac4306668858140736d83e008ae0756f8e1fe5ed6386780bc9796ba` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:223d494cf64cdceaabe6e9bae82d378d7ea53eb8c01d58bdbd2e1ed360aaa34b` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:378e5735198e38d6bed8c87a59ed69f8c3bd57ac8a462332d74dd8495cb07ed2` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:d92f672c2a61a67db43d9884bc2692c304b3c2c5446bed2d315892876270366b` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:11dc172c7ae91b6cba7fb4ab1a61e48b27b193bf434a68827eb197c0ba05d6fb` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:3057eaaf8e0403690c0223c0db3a392b05f2ec45e53511327b8447912e32b8b4` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:37062edf6805dce30309e4615c2947dded730b5b5be7e3bcd85bb93e38b08f31` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:9f1bf1901a6b0e2caf4c9ff30e0b6bb3f1f4f814ad86fc62a471d4fe1fe4c101` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:095b40ad1afeebd932c299410a4732fd64da2251230aa044ca2c43b4d0bb6791` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:60e9257735cee7dc6cde1b5725588b1c1ea84f852220f1f4f3e873177a24fc5c` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:71c5e3a9196155678a6ad9cd62b812386579521ac410b40e3526dee153d749e1` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:fce7d215575d2a94cdb4818bb1525f6448f5f881fc3e7f04274c64978bd6aaa7` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:d71d8e1e3692bb0781e98b984dea79950a8009a6fa03e729325c338ca5c09a98` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:dc2e35e158c09fd793b180050a0100df4a3716da4d0a7a528dc3ea65b6ecf21b` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:e6ab373eb9477d90d44175fffb646298d403405633e0a61ccf20f9e7381243b8` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:0ce15c2d14bba49639adea30c91df1ac47e7b2a7796be551276bad8ec8312ed4` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:bbe958ff9c7c51efc6521866173b26ac2cfe682d114ce3ed6b1f6b8e9b3a7327` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:4e4d890605e09717ef88982f586611c605342465a8ef81f2280f665ad1378522` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:60bd2d1f817019e6626876b15f5697be07c3b2b368e4cc7e3c3871c3e9181052` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:c8520e7155ef176fb9fea48c541acae995a6a80ba6913ac4289786ee55062ce6` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:c8440308a5cb77791f33ae458c49abc084a1be8c418df9feeda9a4aa917a59bc` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:a66739b36a410c181ccd2205c59fee2726b3905d1c5ba4531909be96cf85a55c` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:c4ba7ff5c11d4243a3e128aca1f8110e62df82d956706c97c237016a94cb485f` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:c3fc4117598c0dcea0fd5e6f19adf7763e42732e32e3ac93ff74795fdc167e67` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:78bcfa610f645c113134cc24c8af8dd3c630065c1b009fb5e36dfab4999c16fb` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:134eb68c900787bae3a98a2bdf192f2a5460fb96b92590d65765d982245a7ccf` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:d194aaefe82a5f91df9e01beec271ad9565c4d36cb0539421e947b5c8e67228d` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:cf272b112b10587c034f00f7df2bfcdefbf542859fa089c15581040db99ed383` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:7364a1068f9940e9bb6ea5476b0a007a37d42b899dc4ba56be833e4d2b8d359d` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:21ce33714fa37bfede60560a7a24c17c88566c767b76c58c877a48c51811c9ac` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:b97035a4f0334f890ff3630a2de249b72a879de3c7d4fcc849c3d76aa97f4d2e` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:ae4a89a26768c978d91ed797e9ecb8035fdb61f12c1b1124c86939c79ddcb38e` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:41bc980abe79cd69034a8ade2be203478b531a00f5e74b1f7b8f9c5267700261` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:51a50a7fcd5a9db6422235a2df0e8fba360efcd3cefee9abe44ab2cdce62088f` |

| Locale for v2.10.0          | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:f81f6c53e8ca9c3ae10c335ad45054cea571eca2f4ab32e44e13445936ce3f17` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:da276dc1b481c002a9b3d2944e190af799175b5a2eabafab87153e22529bdab1` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:c2ae166526cb0c5d481b537daa3accd379c4b1bf51fce6d85ac20591e7e0b4c0` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:7d4a6cb1d9d66f6bd62f90b82000ef811f8a3dd58b03641b6c51ad6f0f4fd4dc` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:7489a0ed06fdf1da1d25e3211f5a66abe420babee148961a2ffe8cdbd82564a7` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:f81f6c53e8ca9c3ae10c335ad45054cea571eca2f4ab32e44e13445936ce3f17` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:478e4575073660e9153811f58e74815f62395ee2ebd868d448fbc3a5e16442be` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:025dcbd6a7d1912812b2556ffd7a16ad2158be6c3746e2822f2b97f460aa685b` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:f81f6c53e8ca9c3ae10c335ad45054cea571eca2f4ab32e44e13445936ce3f17` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:f81f6c53e8ca9c3ae10c335ad45054cea571eca2f4ab32e44e13445936ce3f17` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:5af93722e70e445b3a4102bf621e6d5bb5854bcc99f60d4590e23fc24e50297e` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:a9402f03b02150288d51e03ec97b8efb98ad6c444df3ab50a3b4ce1129d02d86` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:122df16df46a84a14b28e4ff406a047947fdc10a65b40482438beee55579f687` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:7b7d7ef798a0210b8c33a3a201ba149e1264cc7ac6ddaf986721d86e91e5e444` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:ba8dd6564939eda7b81b1a4c13ad31672927528dd146698fce10c12d21f647a9` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:d0fa9bc409238ebdab0a15174b3169c99cbad42323087ea589bb7812a0550149` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:4c4a115ae8daf53e344c1c4f838ebc68c3de2dae4d1f1aceb021425807d96ac0` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:f18c31f2bc9e655b93f71049b40dae2213c7417169f7a4e42f603d5891857b2a` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:67f02cdb2285c2891aff8ff8d35ee20bad11f2d1cc1d67c461185466edefa5d6` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:ed606155b5f9b6c6dd68c0c1f5e48a0735bc4a5ded872655c0ef7de2bf084312` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:2fb6a64aaea5efdb2cac8bda2c7d437638fca93aa24268a45f2a395285e022df` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:9ddb64e481cec6449dfc48091092247fa401fcd48ab1d955c5186565f903bd34` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:060a87ae817a82486966a4f10d1e872d30370ea58e297ca4c2018d0e034bfbe5` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:ece4299bd7f02fe4403b53320cf55bb2e3ab65da3d94bfea09124c14955a3de3` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:6b47286a882122de8114942d426cbb8b4f1aded318032317b03a6b68237372e0` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:41fa2caec6a732736f75b682e0410b89ba5e12307cd6e2652986a2676a5dd560` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:80ae57602d8e66c6ed0366327a87c0ed5717b44c596b981a2b5be09c7f5a4c8a` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:705c125e5105b6eed37d745e2092d55ca8b6ccff22f4eeac9c2df958f36c72e9` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:67f794f16fdac457f0e0a84192e588611adb43777635b14706754c19fd90b130` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:94f755e70043dbe011424a0f756970f1d01ec51cb95a469531e3a6b0aa84aed1` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:c42eb56cbb48e0957f73793f83435c705ed0f857579acb020394025abdd760e2` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:7cfacb01fdb80bd1b5e68d16f9e2741237ae4ec1a41a9121aed1be2622fc9f3f` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:7dbe5becdf4f3264764eb596d61781a2b2ee54bf9552bbb8f4db5e7fcf75d8f8` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:a1064b4498b7c5972a8a79ea84b78c2e1e7698c039eab49fd08963d11798ac61` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:03cd0f0bae11df645dff52b15746e31493522db5399a18878df765b6aace0a80` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:3dc8d3f0842089edde4703abe8df3a219fb177afd5ac370c5b04c85abae4ca15` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:7b0927c3b60bf38e995c57a27843680d9062d88611c49378dda8f71a4602f7a4` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:72e51683124c76255ec9280cd0641d6e44633199bda769ddb31336362f6e641d` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:a948970cd11e2597ba150291b2dcc72f2d59ad4f693933ef1f72c210f19fb663` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:b773cd7bbb5eba548bc468c2f6d50732e2553c5f8ba4b955404140def4c3f3fd` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:db73492bd83597c1fa47e7c4ab5eedbc1afa7662088fb03df2aaa5b737b5f837` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:d3a86e840438eb2278d0bbfdf1fc98a48fd744fb8c92118f6d3d6298c45a2b96` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:b60dae65bf1fe20e698ce32811373473d811bc363d4db093b643238f71461d4c` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:2a81a9d1b32c546ec03caeeaeddb1b26e5e00747c691f5be62f9d23c5ba84377` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:c4b91cd5e017060a82a34f83d3f62a16b856313c02fea048d300abf149aadf67` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:2a5bddc5355d6eb0b101423c733d6cf067bafd0e152b63bf6c4dcd943ff561f3` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:f60037ad8dd2b40f588608a5eace8b0b9f3171d05d39a02c2dd1afe98ea7e18d` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:e302da84ee0264221f0e663470f579348664ddef37050bc0fe57c620264bae06` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:b6a79de315c73ec3301aa0cfa7ed920abbf8b6f80fd3d42637b785ee97a85584` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:2de931f1e6f38cdc2f54a08bc1e64a13876326d57784f0ad1c50384381790b05` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:47c1b3cceb8a6f0b2ea16160ba8c503d39ac77f44c254dc880b5e17d2aba4a4c` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:bf40fbfce8241e14656df47178d7b57f19022cc6b2598de5b337c6710eba99b6` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:93e0d58ed07d637c3e394ce80ee93524697063cb693da2aed9013660b2543702` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:1d239549ecf7f6bef5f9d258f5fd34f81fb0e5fff89c66dfec769e912b1cbf7b` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:596f42a366a61d1cf05dedb81a4f373cfae2dc04e8bec3479bfec121417dd4fb` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:fcdad9382db8fc7ff0a7ad59fa9fd4cd319ca258edff869b66d76031bcfee640` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:533a6420a4a98d4a2c947d26511e90651fc341c96b90a02615b38ce2a799f058` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:ec6b95c03d9d5030457c4a9e1fd8e07fbae24ec50b0bb3b2a95eadcd81a1d136` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:67cc80b8159122c530913505fed0f7bc4edfd3d77b25bc34b6c6157d57178728` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:2b1f3b4220f8a7a44c8339e4c6a4b9a55f7583b5540f045997c9cab8364facb2` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:4703fd5e1c5020d5c58b1adde30e5209b1e6f21d0636bac11013dcf8da9340d3` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:58c2bb9cf2ead05fc77b3962ee7cef0e0eec33e32697757f65ae8925d55f87b8` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:dcdeed91559fb7e1b7d2ea70215ec373a59afa6b67468d13316af109314ca384` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:06745d241654571428c219c38cd43b56e92b97eeb5aa6656ac726da79460afc1` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:3c85f1057b5942c5d2094055e7b9ecc6ef995905bbdabfad48bfefb805f436cf` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:313f2fb20b8c2a18bd6ce5e7877899310575d390a2c3c54cd2519d0538393201` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:7c897fdb38661eb60f576c0a1a9d69bab9e44e7a70e8136fa3d12531cde0e4d7` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:9bf17aa5d4c577a440c770b6a63b66037a201cbea0202af4856257fde0548f0e` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:08f0bb7f1454c5d6c740d218013f47c54bed17701e05c239364f5b2eba07692e` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:0643e1c342cf6d526620a46b3435c130702b9320a6075ede1351810956ed6ae9` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:139f83900395a0d1af99dc90e661238ca2fa0bc06c74cbac28631ba0399345bf` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:1c38423ccd1b8042d43eabe013f5b6989556610ada803b4367848b58c4832a76` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:2b33e5d5ae0cc46bd9a4ae860fe22f088903d4978b287df4eff6ae63b91566f3` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:40a667412882bfe8073abf376fe94378d7c364e7b22aee410d7b6e99d65e55be` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:d55464b46585fcfd86c420a30d11b10f3b5c9c0d70390b75f40fe9dbbeeefa99` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:06f3f986ff92f16e963771da485695ec9e1da482b10f35babb2d54e260da23e7` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:0566062d116cb06c3eb365dce6e86d9c46ce37293b11ef71c4e219c3a11ca559` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:0fa6da985d839919fedb503625383dcda04de6bd39558f2f72b64410675b8f85` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:88418775c8a8df79aa52de03091b938b7a4efc708907556dfbe3e1d686050e81` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:9087a08cc455772515f5775a788cdde35d7f5bbe3aa3ba34ae99573fd87b29a1` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:372e1c256520e9ee84c4c400eae935c1d6b1d59adb2be4c4dbc56439db069ba0` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:8406a3be34530c7d654d1dfa1c593dd51b8946b480fe80a100e599e86385dc2b` |

| Locale for v2.9.0           | Notes                                    | Digest                                                                    |
|-----------------------------|:-----------------------------------------|:--------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:08885bedb2993daf0c918ecdc6ec775f7982ffa5ca561e80ab9b8a103cde8194` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:41e7942e4026beaad93e50f199a6a2d855f77c74e60bc9636bf2bf2c7d3bd482` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:d27f383435770aa01bb4117ba2d50a05ec172a1da35c4920ab43cd0fb74f44c2` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:ca2734a6bfc562c4c07981358051d281fb5e089815b9eac14c66a0e6f92e9858` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:57429ee8e95a76ec953f1b1f94b39a20507626cd7fe5431df826912e5b959e41` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:08885bedb2993daf0c918ecdc6ec775f7982ffa5ca561e80ab9b8a103cde8194` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:4c5fb6fdc08343e8640222583373effae3d03907cf1262a4fad3303df9385797` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:5ffd280908e3ee65fcb7bea0b532844f9d8510044ab4c2c612dc3c235938ad0a` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:08885bedb2993daf0c918ecdc6ec775f7982ffa5ca561e80ab9b8a103cde8194` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:08885bedb2993daf0c918ecdc6ec775f7982ffa5ca561e80ab9b8a103cde8194` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:00f3d1fd6ccb857ccef8a72322336e7a097d04027411f0dcc5499b44229fb470` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:aa6ae12f786dcaa028e5867abba198effed875b6bc4cbafd4be37349e95dceef` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:515a940ccd76ef1926bab3ad259e1cc7ac2bd90bb3860d28f83d0f6324b3f0fe` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:03f6242d73de64c3eb3347400ea6e7408a8816bd96f3d6368ea2a8193accd457` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:ed6714e804ff2d1bbd41512c78906ad9b8827dfdfed0076a271817e075c2ec40` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:386f2bb4c4b6ba797919ddcb5bbc9942bf8a03e774f9b01438f9bae0928414ef` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:28696d10c78404fec033794e6e6ae0bfd92b0dab5cf7eb1d24cc2cdfbfcb646d` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:dd9ce70f83767a5bdc52fd62b96e09ce6f79ecc1903ed8e116753099b06b03cd` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:70095cf952565256f3a0927358d0fd802d28fe1c3b89b26ead31ba1127cd0b06` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:836bc38328636799ec9c8717618d51ab8b50ea2f0dc9663f342c4454938c9b23` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:eda3702d95d4ae3b64ceb93bda42e8522776e141a18b2a3dde3bc3fcf0e9a2b8` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:bfc2126fffb947bf10ac379efb70db3d2c7ee2c16dd541a5b86e03e73d7d477c` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:5660d02eabf4e1e9f58e7993ed7e5917b1990b41ed35a484a715d7265400cd0b` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:891c1805fd8011865de7371ffd4bde85d879341f2100e8053bbbc722d7c792bc` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:21d6d46398f940a769241fdfffec5658356e54b4127b44efe5e061724f7a7681` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:6f473b8ba56bad098c21a0c0496cb312dafcfb83dc1a2e1aff21011f6b39321d` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:20aa22d24e35f7d92ceac96d2cbab8ce46ee0ed7bb601f18fa867f1bd0bcf5ab` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:5e5ad2b016a1ceac500813e0a68ff4108ddf5a4ca98cb0aed4930b6d1e8920dd` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:b372d9e32e7b518bb9949d8db459bd4e300304e53aed1342aba65a054d4a4c25` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:d3538f3834c554ebebbdfe75e261a06f104dfa27143353601c3a6a3d41025129` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:0bb100ef5313b182a59c08949e4baf1086bde2c1a6bca3324c4e052f465f7632` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:cdab27080ef3ded55dcf89cf85bc2ae16de1372f84a42d836ff5f20612b68a61` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:e4ea51ffa38f347adc7c0642d50237cfa045683f52b5e3e726e4c28688231d35` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:f81c0b7f774d64e673a1311d00604f5e4837fdba4d8fb4a2ab0c8bb8b7fde87d` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:78035c54e649e34cd8276a402f9c9845e13bc40503da6c2f631698a16a049c67` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:e4e4d9c123e452f8ae89bf6cc1292a406f7b482668e36b48ef2fbb29f14c4360` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:10a4ddd279633cc8696b00be77f6e9309494a560244a325982522aaa805806e7` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:a603a8f9c1778808df5d14e3fa1c7e993ef9cca3e0b515a4d4586c2c3a1d14b6` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:4f539f8019c489623868bf02f3c61ed4b66d3a85e89250a9b484717a91e9489e` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:20fc3806f08ad4e6fd5fb1f71318f1f5b591e2085ee4cbba2f25ea06135e5f6a` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:d65520a4f628f6a416171ac58341579fdffba97ddd2941a910bda385d31c735d` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:d38ea88613f5db6d6d9f879ef92a204c524bb27766848b825d1e6ce2a9b13cf7` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:02205d1ecc29feed3ac8442dbdc1855c419749d9dcbd98028a5d1619166f0328` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:c9c3e1ac800120a14f472c8be62730a489e00f29df29fe770a56429ea1c09ef5` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:859c24c40e65bc19a866218466eb7678f71205bedfcb6ee3180b6cb721194b9a` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:036f13d34005f5d6634387c9d13c3535724795b0d6cad832fc46363609fc2f11` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:b8eb300d0a11dc397d0bab02e1f6b26de6091595fd052ebb607f196c28d16f1c` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:0ffba124ecd79777ca08055689a1d853916ccd8c8f2806d0001edf5eb4aa42fa` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:4d7caf48264eaf18bb2d07b0258d6f64b7c26815fdbdf812718dd8e88f1a6d1e` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:310abdc1a8490990a99ce061f04c9d49cafb7a452fbfdc2790de6f60e1505c6c` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:8f209d30b2d148224b296c2d2c204b5970fbe7aaf5eb3289cf8b6644bfd78373` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:11b718d4b86d606b198e47deaa25f6ce164cfc53267048e3d2dbe1bc8500cc5a` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:7a4264a0e9560e6aa3fdee80c3e3f55a0e26cddce8ebbeb7a9c87693ab451a25` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:bbc764ac08b2ef10ac58a8f9534d4d375109fdf16ab75c8cdbf2d57aa692d3e2` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:2d0a83b7bcf1cfc50cf013c95442519e5236a146b7968e75e129b3a5c33ad3a1` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:f0ee8f259035ac5dd9ef38807495d0f8d989ddbb8eacf83893f1fea22265e6b4` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:6101ecac9f5f35c1ea1b8cd8e52fdbbc1be2582e4f3e385c16509fd95a002217` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:9e94c4d6fff73058ce4eef609b8404430a429c6961648655c915cb2fac10656f` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:44986ad44bb53eaf350e0865e62ea5ba7f37d1f5b52e388f61f56fd7afe8ff32` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:6b7aaa828d1b2d2fce1831e540e08ba60307088b90ca32e96fd002a67aff926b` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:1abeda544a7579daac7f8b8f8d34a2cc63b4bd3631e474315d424973ae024ab0` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:455da50a7db591df7be69d7cd361a77734b9249101d8cf86b807f0350b5167ef` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:676e17b6223e35d1897b46536e6f523e1d18b78f834b62ec00bb126ad3a2e71a` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:dbfb97e52dc4b4c71dec1a9e622714f004b1e59d7900260e09a85bf15912fccd` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:19f7f644ae3a0639fdcc53acc065d0e534b74c07f8c095418d4d4d444c566bf1` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:d3a13ab6fa2eb5d5ca0e3281b1092452650e9ede8749f6edcab990e3bbb8d198` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:7ad5e61f9a72c600bdc79e4c04ac63c239951ac4c0d44e02fe0607a6aff356cc` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:fe6a4812534d704b145b84fd8857fb3d9052f67fcbbd5d490c5902082e295195` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:adcd34941d4ace7db01bd476d61c9bbafe071419932b4cfae5231cf202af3a14` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:0534a7e4b391f1ee666b248a274879c081496ed4939b0ad33154d8a96fd67f94` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:091ea4a31652ff9dbc6259636f6c12b0ceb79a269e2cf3cdec677a1914b6a64e` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:5eef3ae8afb445e60bb913edd6eed1415abb0bfbc439978f69f4cba7b61c8e6e` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:98709e9349d889b57933317005af42770e47ce8178a7d9c737d9fbdd81148478` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:3a9139334c4780dc6f6a9b0f15fba5292e16ecf1f5d45fe49a9c8ef3b0e110b3` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:b29b2a65d83c20d65ba4e4fbca66f9fc07e536e161f90448c2bb360eb8de1e55` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:4302e1d979b24a23595ee2b1fd074a57ee36166ce9ac400a3deb397341ae52b2` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:69be11a63199d9a6f63ac346e689051ba9cd5214894b110da2879aaa0f4a8e88` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:2e4167dacdcb2c9d91930356ebae311b6b33ceb3e85f908422e880edbd42da64` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:d46289ee9ba71c9c1dbbefa5da439e71310af74633c9d6d6d448d2ebee60da02` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:49eeee500e07ffd3056ba8aab314d6c8458399a8c0d6d44ce1d9aebf50ddca06` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:5a3251ad6df9565d44dd422de4fa0d83a9b50c8a80ec15213403482940d2b2fc` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:2c45dd90b0c19d7f12b1be44d3e85fe2603cea2389c2877b79d6de351839cf6a` |

| Locale for v2.7.0           | Notes                                    | Digest                                                                   |
|-----------------------------|:-----------------------------------------|:-------------------------------------------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. | `sha256:c8e99e71e6740cf671f3bf79de8b7dd890122cb674eedd2440e71e7cbc4c66b` |
| `ar-bh`                     | Container image with the `ar-BH` locale. | `sha256:5a2c140661f50d0c95587121ec1ab8895289f4dda5b3ad14074413e869e6bd4` |
| `ar-eg`                     | Container image with the `ar-EG` locale. | `sha256:783bb8321fcfb7890b0c99935099f7e84c85a698c2fe0031c661e265358d79c` |
| `ar-iq`                     | Container image with the `ar-IQ` locale. | `sha256:abd0101f73c1cf71f30da7b11b93d2a7ac8877dbfcfc2d34553d20705aca7a2` |
| `ar-jo`                     | Container image with the `ar-JO` locale. | `sha256:d4c7fd2a1637e163aa106c23b6a759e8c78366c60ece83b3aabfe93ebabae07` |
| `ar-kw`                     | Container image with the `ar-KW` locale. | `sha256:c8e99e71e6740cf671f3bf79de8b7dd890122cb674eedd2440e71e7cbc4c66b` |
| `ar-lb`                     | Container image with the `ar-LB` locale. | `sha256:20e5c9105e86625c72de54290a6eb07630d35c3760f729c4b855e3661583dfe` |
| `ar-om`                     | Container image with the `ar-OM` locale. | `sha256:97f1b44f2cbb837a2ef86441a0a52a07f706240edb6ef6618ee4db8cbbe1c19` |
| `ar-qa`                     | Container image with the `ar-QA` locale. | `sha256:c8e99e71e6740cf671f3bf79de8b7dd890122cb674eedd2440e71e7cbc4c66b` |
| `ar-sa`                     | Container image with the `ar-SA` locale. | `sha256:c8e99e71e6740cf671f3bf79de8b7dd890122cb674eedd2440e71e7cbc4c66b` |
| `ar-sy`                     | Container image with the `ar-SY` locale. | `sha256:51980a2e2c3dd3548deedcedaf5fc688db602a5eced1a4b7df7d10750393623` |
| `bg-bg`                     | Container image with the `bg-BG` locale. | `sha256:1c1acf0fbb353ebb04692f37eb4d4cdf0b4e309720dd7e709001dada0d1ea81` |
| `ca-es`                     | Container image with the `ca-ES` locale. | `sha256:c60baa0007f61c7652b97b49645215de63411125d627c974c09222e316df204` |
| `cs-cz`                     | Container image with the `cs-CZ` locale. | `sha256:3fa09fc3a6bde6b77df2444aae8fc78b5f25fb9010171d1682db116ea5801f5` |
| `da-dk`                     | Container image with the `da-DK` locale. | `sha256:4b26dbba50c2771943880b68e0e4ea0713d0e3bb8bad884454849bccc9e94a3` |
| `de-de`                     | Container image with the `de-DE` locale. | `sha256:5109ed80b1fecf4db0328adcd50528d0aa9e726b5fc84587c40aaea4e91256d` |
| `el-gr`                     | Container image with the `el-GR` locale. | `sha256:fc8b466c588bf097efac2b79454d5ac0df5c6990398f07ede9be7e1d536e4bd` |
| `en-au`                     | Container image with the `en-AU` locale. | `sha256:3461892a27fc3eb3f9610b2def00bc15f380c6b9797c90ceca19e6abb55f6a6` |
| `en-ca`                     | Container image with the `en-CA` locale. | `sha256:a0509be39785f1e869bd96ab10e7c07d3f4e61c9aa17ff5900076e7bd64ba11` |
| `en-gb`                     | Container image with the `en-GB` locale. | `sha256:1b976fc7ac109e61dcf74af3652c12535e3db92931d2d0bb2ea59bd46f9efed` |
| `en-hk`                     | Container image with the `en-HK` locale. | `sha256:0b1e1df101f978869c98f6e50632712016b8311fc89b334e7f44e968d64bf2f` |
| `en-ie`                     | Container image with the `en-IE` locale. | `sha256:c5ba0d3c7219ce39f0b918a51a7cae8a65c277f564279cad920e068725aa39f` |
| `en-in`                     | Container image with the `en-IN` locale. | `sha256:e907f07be498f024103f6fe6abffa23e242bf3585724741b29a2f3f41d0899c` |
| `en-nz`                     | Container image with the `en-NZ` locale. | `sha256:66845f6ce20ae71d609867c6eb4772366ce042499e4bcdce4c1b579daf7fad7` |
| `en-ph`                     | Container image with the `en-PH` locale. | `sha256:e7874653bf66b1a1ab344b3391eb8767be34260b7f11b62fd057cbe17b805b2` |
| `en-sg`                     | Container image with the `en-SG` locale. | `sha256:827cdb158280e6f4037f4815410c7aa78abf9c6467876c1504aecfef787bdd7` |
| `en-us`                     | Container image with the `en-US` locale. | `sha256:248d17340055e3e137219ddc234c605e6a53ceead136ea55c9697c352da6a8d` |
| `en-za`                     | Container image with the `en-ZA` locale. | `sha256:a8abc99f498db7088bb25acec47da81e90b6a5eaa1c6f78e0f9a314d839d0ae` |
| `es-ar`                     | Container image with the `es-AR` locale. | `sha256:edf78429630851b6eb01f54f8a8a1aeeda9971c6a834403a204662eda22b3b9` |
| `es-bo`                     | Container image with the `es-BO` locale. | `sha256:5832b44f1da2f6b9a097c99babfbc370d8d0eabe1ff8daabec2c3f482dc9d63` |
| `es-cl`                     | Container image with the `es-CL` locale. | `sha256:409a712b96235e154472134f96ff9272265f1e5b555e00ad03c2260b0781009` |
| `es-co`                     | Container image with the `es-CO` locale. | `sha256:99792bc083dc16e0edf15491e6a840d786c9140b747551563a8d98f66f0b415` |
| `es-cr`                     | Container image with the `es-CR` locale. | `sha256:21fe14a538e5b8b2d288b00b8f5a02d87469e285f32e725155042079f336ac9` |
| `es-cu`                     | Container image with the `es-CU` locale. | `sha256:05d40eae01cec4c42c4febd379cd61373eb43d0aacfd47b988bb95e6a6ad216` |
| `es-do`                     | Container image with the `es-DO` locale. | `sha256:73dd0e0d4f39a259563ee7cc18c2e72c9ab20c52905fe343e0413ca7c4b3f0d` |
| `es-ec`                     | Container image with the `es-EC` locale. | `sha256:c3e69139ef365fe9332b5b68b43458242c7dad9d9f2b557431272306e81cb9e` |
| `es-es`                     | Container image with the `es-ES` locale. | `sha256:bd83fcfc116ba645a0e12a7a93b6ada74a8f701172f826a91c5f223a1dbaa61` |
| `es-gt`                     | Container image with the `es-GT` locale. | `sha256:5bb9b18b91b74e123e3720893d88bfcb0a87dac31a1f7171d23c7cb1fa09fee` |
| `es-hn`                     | Container image with the `es-HN` locale. | `sha256:941d108a4b76eb554e8f13cf5090665a702de3ebf35b75e4350f0916dfccd72` |
| `es-mx`                     | Container image with the `es-MX` locale. | `sha256:cebea03732781b4425500d162ae6580bbd7ce9b5f4ede988c4570fe311d8567` |
| `es-ni`                     | Container image with the `es-NI` locale. | `sha256:8ba165f94ad840936ebd0af17a0a63aa08a6292e7ad9029f5b93eef41165eb9` |
| `es-pa`                     | Container image with the `es-PA` locale. | `sha256:c61b7f1b6801a03c3eab0dd1aede87017a86bc7368ded2f8bad8d9e5f60d0d3` |
| `es-pe`                     | Container image with the `es-PE` locale. | `sha256:447a3ab3f302aba24d201d9f5b2877ffcd64dfd5e9d6b88d9924847160b2de2` |
| `es-pr`                     | Container image with the `es-PR` locale. | `sha256:a53b3295c986e91ee8cf93ebe1057b997c76ef7f99913508b859311a194fdd4` |
| `es-py`                     | Container image with the `es-PY` locale. | `sha256:85b3f75e75e63e29521daf772ee68a59ac2428579512501aa81dc51a2315652` |
| `es-sv`                     | Container image with the `es-SV` locale. | `sha256:db5ece7ba536e38d5de59cd37807630ab76589dcf1c97e253f98d7f44d9424e` |
| `es-us`                     | Container image with the `es-US` locale. | `sha256:99f2743725bb71e25543484f49bcfde14584ccbbaaa912678938d69d965075a` |
| `es-uy`                     | Container image with the `es-UY` locale. | `sha256:a3e11c16a97a1ae76408d812b2fee1e4b3ba07160bbcb62a22814523568ee5d` |
| `es-ve`                     | Container image with the `es-VE` locale. | `sha256:8cb431aafd84263ead8de946377c1d3f2ddfa7e172b8a4c5aa7ba477c5b41f0` |
| `et-ee`                     | Container image with the `et-EE` locale. | `sha256:943e7cf894e9d75341a58993104824c1c8cd8da1322cc5a732e9d53882c6523` |
| `fi-fi`                     | Container image with the `fi-FI` locale. | `sha256:35658e9dce796cb96a1371f250398e86351ea1b5ada080da7ce8471b30c7cae` |
| `fr-ca`                     | Container image with the `fr-CA` locale. | `sha256:62256cad671e8baa03fdd4c5f4eca7d5c5effedd64cafd9020ba72c9c4210e0` |
| `fr-fr`                     | Container image with the `fr-FR` locale. | `sha256:b385993232d9daa327d1a7b067268927b17f36eed3e8d423748794544c62746` |
| `ga-ie`                     | Container image with the `ga-IE` locale. | `sha256:ab9abdb993b0f7487edda8200f1393ac44ba4888c0f444a02afb6c85ca3e393` |
| `gu-in`                     | Container image with the `gu-IN` locale. | `sha256:328e69488f2948722d7ccc97e266071f61a8c9f65cd671688490955806526de` |
| `hi-in`                     | Container image with the `hi-IN` locale. | `sha256:b9b0bfec80aa53d06ea2cbd9097f753ec5caaf00ac2f00321ae7ad916fd7fa6` |
| `hr-hr`                     | Container image with the `hr-HR` locale. | `sha256:ab849cd2eeea682f8958bba8986fe90f0f7bb3b447512a10cf464e8e1ce4ea5` |
| `hu-hu`                     | Container image with the `hu-HU` locale. | `sha256:30f239b155d91523442cf74a1f2732304fa2b50ae7b786833bb6a020b982621` |
| `it-it`                     | Container image with the `it-IT` locale. | `sha256:288f95413870eb9d33bf1dabfa6fbd6b55b0faa52e4d5face3171d1dd4ddbdd` |
| `ja-jp`                     | Container image with the `ja-JP` locale. | `sha256:e3ab37a80c215dec565eca212f57eb81887fc2894452868dff92e3bd42c4bb9` |
| `ko-kr`                     | Container image with the `ko-KR` locale. | `sha256:c1208b8459333b606af516cd7806e9d4d5e002247bb1225e1f246563b356890` |
| `lt-lt`                     | Container image with the `lt-LT` locale. | `sha256:8dec331161d3c29fc65ba6651fcc6cfe69fa314519f408b5f9f8eb27da09830` |
| `lv-lv`                     | Container image with the `lv-LV` locale. | `sha256:7cf31282910b339666bb2b0a555caa7fc6ae414eea4423a41f35c3527f83235` |
| `mr-in`                     | Container image with the `mr-IN` locale. | `sha256:9cb012bd58ef7723d4905d6fa3c1fde96e33c354b3d96d4e3ff69cf6e1bfe3a` |
| `mt-mt`                     | Container image with the `mt-MT` locale. | `sha256:a0094c032ea555b168ec5751ab3257337d902d526e9ae335671fb751a352378` |
| `nb-no`                     | Container image with the `nb-NO` locale. | `sha256:6bbc326e20a6a785b1ca33143b42a060858efb67b863a267d6efb7aebb48f87` |
| `nl-nl`                     | Container image with the `nl-NL` locale. | `sha256:94b4ddf4cc80fa666e422f8416aea3f98ebe4842dfe9b1f4bfea7c47eb61127` |
| `pl-pl`                     | Container image with the `pl-PL` locale. | `sha256:58e5f78bf772c3c8cbd5f0c5d6e67f5348e04e3f893d84738a2a3e964bab256` |
| `pt-br`                     | Container image with the `pt-BR` locale. | `sha256:f500ef956bd28807f40df1f9f0520e437c5084f61a3be6d1379e746887d5b7c` |
| `pt-pt`                     | Container image with the `pt-PT` locale. | `sha256:c841d2dbe5f40adf6039242c106985febb1a44212feb55d9769fe31134ec116` |
| `ro-ro`                     | Container image with the `ro-RO` locale. | `sha256:93271c39c0a134e987a069c2a65289acff9869ae0d90fdcb39928c9ef0fd86b` |
| `ru-ru`                     | Container image with the `ru-RU` locale. | `sha256:8d6b3c600e56cc96813b8c14b7916c5539a20ba561dc1c6d5bbef6285d6eef6` |
| `sk-sk`                     | Container image with the `sk-SK` locale. | `sha256:6d604092cc6c964663a1c97d91c8f1c8cf4b46d07427d03f7041c0cc55eb521` |
| `sl-si`                     | Container image with the `sl-SI` locale. | `sha256:f237ed58fedefcc749e74be1258cc70e5a690ee6c5a6b6388bd24075faa61da` |
| `sv-se`                     | Container image with the `sv-SE` locale. | `sha256:da4233e6658b00eefdadb9d4acd889c6550a5e2a4a7af7a9f915c878abd4c9c` |
| `ta-in`                     | Container image with the `ta-IN` locale. | `sha256:22b77606d25e9c2f52bf3cad6218782b4719f6a9dcfadc770468d266758a56c` |
| `te-in`                     | Container image with the `te-IN` locale. | `sha256:7f4d11372862ca1d65fc9b868e2d775701b8e6eabd786c90c4e9ab82ba86e88` |
| `th-th`                     | Container image with the `th-TH` locale. | `sha256:69033bcd7c0f59d31bafec6c2b7a9ff343928cdd58c16105415c291d555d37b` |
| `tr-tr`                     | Container image with the `tr-TR` locale. | `sha256:4b7d339846a0d371dfe25aa2e626f131003c01329c9a1da468eb3703ef176ea` |
| `zh-cn`                     | Container image with the `zh-CN` locale. | `sha256:a428459830fb766083212f71c5638a65ce30d8dd84f6c624ae22768e8a76976` |
| `zh-hk`                     | Container image with the `zh-HK` locale. | `sha256:7a2903462b67336a6ce4c8e2faac42052f0a4392d1d5eb3839758cc8d0429f1` |
| `zh-tw`                     | Container image with the `zh-TW` locale. | `sha256:30fd2b3660e047d24a46fbba14ba282f15bc0339ec93f49afd0d02ff4069146` |

| Locale for v2.6.0           | Notes                                    |
|-----------------------------|:-----------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. |
| `ar-eg`                     | Container image with the `ar-EG` locale. |
| `ar-kw`                     | Container image with the `ar-KW` locale. |
| `ar-qa`                     | Container image with the `ar-QA` locale. |
| `ar-sa`                     | Container image with the `ar-SA` locale. |
| `ca-es`                     | Container image with the `ca-ES` locale. |
| `cs-cz`                     | Container image with the `cs-CZ` locale. |
| `da-dk`                     | Container image with the `da-DK` locale. |
| `de-de`                     | Container image with the `de-DE` locale. |
| `en-au`                     | Container image with the `en-AU` locale. |
| `en-ca`                     | Container image with the `en-CA` locale. |
| `en-gb`                     | Container image with the `en-GB` locale. |
| `en-in`                     | Container image with the `en-IN` locale. |
| `en-nz`                     | Container image with the `en-NZ` locale. |
| `en-us`                     | Container image with the `en-US` locale. |
| `es-es`                     | Container image with the `es-ES` locale. |
| `es-mx`                     | Container image with the `es-MX` locale. |
| `fi-fi`                     | Container image with the `fi-FI` locale. |
| `fr-ca`                     | Container image with the `fr-CA` locale. |
| `fr-fr`                     | Container image with the `fr-FR` locale. |
| `gu-in`                     | Container image with the `gu-IN` locale. |
| `hi-in`                     | Container image with the `hi-IN` locale. |
| `it-it`                     | Container image with the `it-IT` locale. |
| `ja-jp`                     | Container image with the `ja-JP` locale. |
| `ko-kr`                     | Container image with the `ko-KR` locale. |
| `mr-in`                     | Container image with the `mr-IN` locale. |
| `nb-no`                     | Container image with the `nb-NO` locale. |
| `nl-nl`                     | Container image with the `nl-NL` locale. |
| `pl-pl`                     | Container image with the `pl-PL` locale. |
| `pt-br`                     | Container image with the `pt-BR` locale. |
| `pt-pt`                     | Container image with the `pt-PT` locale. |
| `ru-ru`                     | Container image with the `ru-RU` locale. |
| `sv-se`                     | Container image with the `sv-SE` locale. |
| `ta-in`                     | Container image with the `ta-IN` locale. |
| `te-in`                     | Container image with the `te-IN` locale. |
| `th-th`                     | Container image with the `th-TH` locale. |
| `tr-tr`                     | Container image with the `tr-TR` locale. |
| `zh-cn`                     | Container image with the `zh-CN` locale. |
| `zh-hk`                     | Container image with the `zh-HK` locale. |
| `zh-tw`                     | Container image with the `zh-TW` locale. |

| Locale for v2.5.0           | Notes                                    |
|-----------------------------|:-----------------------------------------|
| `ar-ae`                     | Container image with the `ar-AE` locale. |
| `ar-eg`                     | Container image with the `ar-EG` locale. |
| `ar-kw`                     | Container image with the `ar-KW` locale. |
| `ar-qa`                     | Container image with the `ar-QA` locale. |
| `ar-sa`                     | Container image with the `ar-SA` locale. |
| `ca-es`                     | Container image with the `ca-ES` locale. |
| `da-dk`                     | Container image with the `da-DK` locale. |
| `de-de`                     | Container image with the `de-DE` locale. |
| `en-au`                     | Container image with the `en-AU` locale. |
| `en-ca`                     | Container image with the `en-CA` locale. |
| `en-gb`                     | Container image with the `en-GB` locale. |
| `en-in`                     | Container image with the `en-IN` locale. |
| `en-nz`                     | Container image with the `en-NZ` locale. |
| `en-us`                     | Container image with the `en-US` locale. |
| `es-es`                     | Container image with the `es-ES` locale. |
| `es-mx`                     | Container image with the `es-MX` locale. |
| `fi-fi`                     | Container image with the `fi-FI` locale. |
| `fr-ca`                     | Container image with the `fr-CA` locale. |
| `fr-fr`                     | Container image with the `fr-FR` locale. |
| `gu-in`                     | Container image with the `gu-IN` locale. |
| `hi-in`                     | Container image with the `hi-IN` locale. |
| `it-it`                     | Container image with the `it-IT` locale. |
| `ja-jp`                     | Container image with the `ja-JP` locale. |
| `ko-kr`                     | Container image with the `ko-KR` locale. |
| `mr-in`                     | Container image with the `mr-IN` locale. |
| `nb-no`                     | Container image with the `nb-NO` locale. |
| `nl-nl`                     | Container image with the `nl-NL` locale. |
| `pl-pl`                     | Container image with the `pl-PL` locale. |
| `pt-br`                     | Container image with the `pt-BR` locale. |
| `pt-pt`                     | Container image with the `pt-PT` locale. |
| `ru-ru`                     | Container image with the `ru-RU` locale. |
| `sv-se`                     | Container image with the `sv-SE` locale. |
| `ta-in`                     | Container image with the `ta-IN` locale. |
| `te-in`                     | Container image with the `te-IN` locale. |
| `th-th`                     | Container image with the `th-TH` locale. |
| `tr-tr`                     | Container image with the `tr-TR` locale. |
| `zh-cn`                     | Container image with the `zh-CN` locale. |
| `zh-hk`                     | Container image with the `zh-HK` locale. |
| `zh-tw`                     | Container image with the `zh-TW` locale. |

---

## Neural Text-to-speech

The [Neural Text-to-speech][sp-ntts] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/speechservices/` repository and is named `neural-text-to-speech`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/speechservices/neural-text-to-speech`.

This container image has the following tags available. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/neural-text-to-speech/tags/list).


# [Latest version](#tab/current)

Release notes for `v2.1.0`:

**Features**
* Security upgrade.

| Image Tags                                  | Notes                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `latest`                                    | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `2.1.0-amd64-<locale-and-voice>`            | Replace `<locale>` with one of the available locales, listed below. For example `2.1.0-amd64-en-us-arianeural`. |

| v2.1.0 Locales and voices           | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `am-et-amehaneural`                 | Container image with the `am-ET` locale and `am-ET-Amehaneural` voice.     |
| `am-et-mekdesneural`                | Container image with the `am-ET` locale and `am-ET-Mekdesneural` voice.    |
| `ar-bh-lailaneural`                 | Container image with the `ar-BH` locale and `ar-BH-Lailaneural` voice.     |
| `ar-eg-salmaneura`                  | Container image with the `ar-EG` locale and `ar-eg-Salmaneura` voice.      |
| `ar-eg-shakirneural`                | Container image with the `ar-EG` locale and `ar-eg-shakirneural` voice.    |
| `ar-sa-hamedneural`                 | Container image with the `ar-SA` locale and `ar-sa-Hamedneural` voice.     |
| `ar-sa-zariyahneural`               | Container image with the `ar-SA` locale and `ar-sa-Zariyahneural` voice.   |
| `cs-cz-antoninneural`               | Container image with the `cs-CZ` locale and `cs-CZ-Antoninneural` voice.   |
| `cs-cz-vlastaneural`                | Container image with the `cs-CZ` locale and `cs-CZ-Vlastaneural` voice.    |
| `de-ch-janneural`                   | Container image with the `de-CH` locale and `de-CH-Janneural` voice.       |
| `de-ch-lenineural`                  | Container image with the `de-CH` locale and `de-CH-Lenineural` voice.      |
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-gb-sonianeural`                 | Container image with the `en-GB` locale and `en-GB-SoniaNeural` voice.     |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `so-so-muuseneural`                 | Container image with the `so-SO` locale and `so-SO-Muuseneural` voice.     |
| `so-so-ubaxneural`                  | Container image with the `so-SO` locale and `so-SO-Ubaxneural` voice.      |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |
| `zh-cn-xiaochenneural-preview`      | Container image with the `zh-CN` locale and `zh-CN-XiaoChenNeural` voice.  |
| `zh-cn-xiaohanneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoHanNeural` voice.   |
| `zh-cn-xiaomoneural`                | Container image with the `zh-CN` locale and `zh-CN-XiaoMoNeural` voice.    |
| `zh-cn-xiaoqiuneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoQiuNeural` voice.   |
| `zh-cn-xiaoruineural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoRuiNeural` voice.   |
| `zh-cn-xiaoshuangneural-preview`    | Container image with the `zh-CN` locale and `zh-CN-XiaoShuangNeural` voice.|
| `zh-cn-xiaoxuanneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoXuanNeural` voice.  |
| `zh-cn-xiaoyanneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoYanNeural` voice.   |
| `zh-cn-yunxineural`                 | Container image with the `zh-CN` locale and `zh-CN-YunXiNeural` voice.     |


# [Previous version](#tab/previous)

Release notes for `v2.0.0`:

**Features**
* Support for using containers in [disconnected environments](disconnected-containers.md).
* Support `ar-bh-lailaneural` and `ar-eg-salmaneural` and `ar-eg-shakirneural` and `ar-sa-hamedneural` and `ar-sa-zariyahneural`.
* `es-MX-Dalia` model upgrade.

Release notes for `v1.12.0`:

**Features**
* Support `am-et-amehaneural` and `am-et-mekdesneural` and `so-so-muuseneural` and `so-so-ubaxneural`.

Release notes for `v1.11.0`:

**Features**
* Support `de-ch-janneural` and `de-ch-lenineural`.

**Fixes**
* Upgrade security patches.

Release notes for `v1.10.0`:
Regular monthly upgrade

Release notes for `v1.9.0`:
* Add 1 new `en-GB` and 9 (4 are preview) new `zh-CN` voices.

Release notes for `v1.8.0`:
Regular monthly release

Release notes for `v1.7.0`:
* Upgrade to latest models with quality improvements and bug fixes

Release notes for `v1.6.0`:
* Upgrade to latest models with quality improvements and bug fixes

Release notes for `v1.5.0`:
* Upgrade to latest models with quality improvements and bug fixes
* Support up to 38 neural voices

Release notes for `v1.4.0`:
* Upgrade to latest models. 
* The CPU cost and latency was reduced.
* Better support of prosody tuning with SSML tag (e.g. pitch contour).

Release notes for `v1.3.0`:
* The Neural Text-to-speech container is now generally available. 

| v2.0.0 Locales and voices           | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `am-et-amehaneural`                 | Container image with the `am-ET` locale and `am-ET-Amehaneural` voice.     |
| `am-et-mekdesneural`                | Container image with the `am-ET` locale and `am-ET-Mekdesneural` voice.    |
| `ar-bh-lailaneural`                 | Container image with the `ar-BH` locale and `ar-BH-Lailaneural` voice.     |
| `ar-eg-salmaneura`                  | Container image with the `ar-EG` locale and `ar-eg-Salmaneura` voice.      |
| `ar-eg-shakirneural`                | Container image with the `ar-EG` locale and `ar-eg-shakirneural` voice.    |
| `ar-sa-hamedneural`                 | Container image with the `ar-SA` locale and `ar-sa-Hamedneural` voice.     |
| `ar-sa-zariyahneural`               | Container image with the `ar-SA` locale and `ar-sa-Zariyahneural` voice.   |
| `cs-cz-antoninneural`               | Container image with the `cs-CZ` locale and `cs-CZ-Antoninneural` voice.   |
| `cs-cz-vlastaneural`                | Container image with the `cs-CZ` locale and `cs-CZ-Vlastaneural` voice.    |
| `de-ch-janneural`                   | Container image with the `de-CH` locale and `de-CH-Janneural` voice.       |
| `de-ch-lenineural`                  | Container image with the `de-CH` locale and `de-CH-Lenineural` voice.      |
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-gb-sonianeural`                 | Container image with the `en-GB` locale and `en-GB-SoniaNeural` voice.     |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `so-so-muuseneural`                 | Container image with the `so-SO` locale and `so-SO-Muuseneural` voice.     |
| `so-so-ubaxneural`                  | Container image with the `so-SO` locale and `so-SO-Ubaxneural` voice.      |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |
| `zh-cn-xiaochenneural-preview`      | Container image with the `zh-CN` locale and `zh-CN-XiaoChenNeural` voice.  |
| `zh-cn-xiaohanneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoHanNeural` voice.   |
| `zh-cn-xiaomoneural`                | Container image with the `zh-CN` locale and `zh-CN-XiaoMoNeural` voice.    |
| `zh-cn-xiaoqiuneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoQiuNeural` voice.   |
| `zh-cn-xiaoruineural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoRuiNeural` voice.   |
| `zh-cn-xiaoshuangneural-preview`    | Container image with the `zh-CN` locale and `zh-CN-XiaoShuangNeural` voice.|
| `zh-cn-xiaoxuanneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoXuanNeural` voice.  |
| `zh-cn-xiaoyanneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoYanNeural` voice.   |
| `zh-cn-yunxineural`                 | Container image with the `zh-CN` locale and `zh-CN-YunXiNeural` voice.     |

| v1.12.0 Locales and voices          | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `am-et-amehaneural`                 | Container image with the `am-ET` locale and `am-ET-Amehaneural` voice.     |
| `am-et-mekdesneural`                | Container image with the `am-ET` locale and `am-ET-Mekdesneural` voice.    |
| `cs-cz-antoninneural`               | Container image with the `cs-CZ` locale and `cs-CZ-Antoninneural` voice.   |
| `cs-cz-vlastaneural`                | Container image with the `cs-CZ` locale and `cs-CZ-Vlastaneural` voice.    |
| `de-ch-janneural`                   | Container image with the `de-CH` locale and `de-CH-Janneural` voice.       |
| `de-ch-lenineural`                  | Container image with the `de-CH` locale and `de-CH-Lenineural` voice.      |
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-gb-sonianeural`                 | Container image with the `en-GB` locale and `en-GB-SoniaNeural` voice.     |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `so-so-muuseneural`                 | Container image with the `so-SO` locale and `so-SO-Muuseneural` voice.     |
| `so-so-ubaxneural`                  | Container image with the `so-SO` locale and `so-SO-Ubaxneural` voice.      |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |
| `zh-cn-xiaochenneural-preview`      | Container image with the `zh-CN` locale and `zh-CN-XiaoChenNeural` voice.  |
| `zh-cn-xiaohanneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoHanNeural` voice.   |
| `zh-cn-xiaomoneural`                | Container image with the `zh-CN` locale and `zh-CN-XiaoMoNeural` voice.    |
| `zh-cn-xiaoqiuneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoQiuNeural` voice.   |
| `zh-cn-xiaoruineural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoRuiNeural` voice.   |
| `zh-cn-xiaoshuangneural-preview`    | Container image with the `zh-CN` locale and `zh-CN-XiaoShuangNeural` voice.|
| `zh-cn-xiaoxuanneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoXuanNeural` voice.  |
| `zh-cn-xiaoyanneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoYanNeural` voice.   |
| `zh-cn-yunxineural`                 | Container image with the `zh-CN` locale and `zh-CN-YunXiNeural` voice.     |

| Image Tags                                  | Notes                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `1.11.0-amd64-<locale-and-voice>`           | Replace `<locale>` with one of the available locales, listed below. For example `1.11.0-amd64-en-us-arianeural`. |
| `1.10.0-amd64-<locale-and-voice>`           | Replace `<locale>` with one of the available locales, listed below. For example `1.10.0-amd64-en-us-arianeural`. |
| `1.9.0-amd64-<locale-and-voice>`            | Replace `<locale>` with one of the available locales, listed below. For example `1.9.0-amd64-en-us-arianeural`. |
| `1.8.0-amd64-<locale-and-voice>`            | Replace `<locale>` with one of the available locales, listed below. For example `1.8.0-amd64-en-us-arianeural`. |
| `1.7.0-amd64-<locale-and-voice>`            | Replace `<locale>` with one of the available locales, listed below. For example `1.7.0-amd64-en-us-arianeural`. |
| `1.6.0-amd64-<locale-and-voice>`            | Replace `<locale>` with one of the available locales, listed below. For example `1.6.0-amd64-en-us-arianeural`. |
| `1.5.0-amd64-<locale-and-voice>`            | Replace `<locale>` with one of the available locales, listed below. For example `1.5.0-amd64-en-us-arianeural`. |
| `1.4.0-amd64-<locale-and-voice>`            | Replace `<locale>` with one of the available locales, listed below. For example `1.4.0-amd64-en-us-arianeural`. |
| `1.3.0-amd64-<locale-and-voice>-preview`    | Replace `<locale>` with one of the available locales, listed below. For example `1.3.0-amd64-en-us-arianeural-preview`. |
| `1.2.0-amd64-<locale-and-voice>-preview`    | Replace `<locale>` with one of the available locales, listed below. For example `1.2.0-amd64-en-us-arianeural-preview`. |

| v1.11.0 Locales and voices          | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `cs-cz-antoninneural`               | Container image with the `cs-CZ` locale and `cs-CZ-Antoninneural` voice.   |
| `cs-cz-vlastaneural`                | Container image with the `cs-CZ` locale and `cs-CZ-Vlastaneural` voice.    |
| `de-ch-janneural`                   | Container image with the `de-CH` locale and `de-CH-Janneural` voice.       |
| `de-ch-lenineural`                  | Container image with the `de-CH` locale and `de-CH-Lenineural` voice.      |
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-gb-sonianeural`                 | Container image with the `en-GB` locale and `en-GB-SoniaNeural` voice.     |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |
| `zh-cn-xiaochenneural-preview`      | Container image with the `zh-CN` locale and `zh-CN-XiaoChenNeural` voice.  |
| `zh-cn-xiaohanneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoHanNeural` voice.   |
| `zh-cn-xiaomoneural`                | Container image with the `zh-CN` locale and `zh-CN-XiaoMoNeural` voice.    |
| `zh-cn-xiaoqiuneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoQiuNeural` voice.   |
| `zh-cn-xiaoruineural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoRuiNeural` voice.   |
| `zh-cn-xiaoshuangneural-preview`    | Container image with the `zh-CN` locale and `zh-CN-XiaoShuangNeural` voice.|
| `zh-cn-xiaoxuanneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoXuanNeural` voice.  |
| `zh-cn-xiaoyanneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoYanNeural` voice.   |
| `zh-cn-yunxineural`                 | Container image with the `zh-CN` locale and `zh-CN-YunXiNeural` voice.     |

| v1.10.0 Locales and voices          | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `cs-cz-antoninneural`               | Container image with the `cs-CZ` locale and `cs-CZ-Antoninneural` voice.   |
| `cs-cz-vlastaneural`                | Container image with the `cs-CZ` locale and `cs-CZ-Vlastaneural` voice.    |
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-gb-sonianeural`                 | Container image with the `en-GB` locale and `en-GB-SoniaNeural` voice.     |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |
| `zh-cn-xiaochenneural-preview`      | Container image with the `zh-CN` locale and `zh-CN-XiaoChenNeural` voice.  |
| `zh-cn-xiaohanneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoHanNeural` voice.   |
| `zh-cn-xiaomoneural`                | Container image with the `zh-CN` locale and `zh-CN-XiaoMoNeural` voice.    |
| `zh-cn-xiaoqiuneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoQiuNeural` voice.   |
| `zh-cn-xiaoruineural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoRuiNeural` voice.   |
| `zh-cn-xiaoshuangneural-preview`    | Container image with the `zh-CN` locale and `zh-CN-XiaoShuangNeural` voice.|
| `zh-cn-xiaoxuanneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoXuanNeural` voice.  |
| `zh-cn-xiaoyanneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoYanNeural` voice.   |
| `zh-cn-yunxineural`                 | Container image with the `zh-CN` locale and `zh-CN-YunXiNeural` voice.     |

| v1.9.0 Locales and voices           | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `cs-cz-antoninneural`               | Container image with the `cs-CZ` locale and `cs-CZ-Antoninneural` voice.   |
| `cs-cz-vlastaneural`                | Container image with the `cs-CZ` locale and `cs-CZ-Vlastaneural` voice.    |
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-gb-sonianeural`                 | Container image with the `en-GB` locale and `en-GB-SoniaNeural` voice.     |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |
| `zh-cn-xiaochenneural-preview`      | Container image with the `zh-CN` locale and `zh-CN-XiaoChenNeural` voice.  |
| `zh-cn-xiaohanneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoHanNeural` voice.   |
| `zh-cn-xiaomoneural`                | Container image with the `zh-CN` locale and `zh-CN-XiaoMoNeural` voice.    |
| `zh-cn-xiaoqiuneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoQiuNeural` voice.   |
| `zh-cn-xiaoruineural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoRuiNeural` voice.   |
| `zh-cn-xiaoshuangneural-preview`    | Container image with the `zh-CN` locale and `zh-CN-XiaoShuangNeural` voice.|
| `zh-cn-xiaoxuanneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoXuanNeural` voice.  |
| `zh-cn-xiaoyanneural-preview`       | Container image with the `zh-CN` locale and `zh-CN-XiaoYanNeural` voice.   |
| `zh-cn-yunxineural`                 | Container image with the `zh-CN` locale and `zh-CN-YunXiNeural` voice.     |

| v1.8.0 Locales and voices           | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `cs-cz-antoninneural`               | Container image with the `cs-CZ` locale and `cs-CZ-Antoninneural` voice.   |
| `cs-cz-vlastaneural`                | Container image with the `cs-CZ` locale and `cs-CZ-Vlastaneural` voice.    |
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |

| v1.7.0 Locales and voices           | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `cs-cz-antoninneural`               | Container image with the `cs-CZ` locale and `cs-CZ-Antoninneural` voice.   |
| `cs-cz-vlastaneural`                | Container image with the `cs-CZ` locale and `cs-CZ-Vlastaneural` voice.    |
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-mianeural`                   | Container image with the `en-GB` locale and `en-GB-MiaNeural` voice.       |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |

| v1.6.0 Locales and voices           | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-mianeural`                   | Container image with the `en-GB` locale and `en-GB-MiaNeural` voice.       |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |

| v1.5.0 Locales and voices           | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `de-de-conradneural`                | Container image with the `de-DE` locale and `de-DE-ConradNeural` voice.    |
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-au-williamneural`               | Container image with the `en-AU` locale and `en-AU-WilliamNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-ca-liamneural`                  | Container image with the `en-CA` locale and `en-CA-LiamNeural` voice.      |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-mianeural`                   | Container image with the `en-GB` locale and `en-GB-MiaNeural` voice.       |
| `en-gb-ryanneural`                  | Container image with the `en-GB` locale and `en-GB-RyanNeural` voice.      |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-alvaroneural`                | Container image with the `es-ES` locale and `es-ES-AlvaroNeural` voice.    |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `es-mx-jorgeneural`                 | Container image with the `es-MX` locale and `es-MX-JorgeNeural` voice.     |
| `fr-ca-antoineneural`               | Container image with the `fr-CA` locale and `fr-CA-AntoineNeural` voice.   |
| `fr-ca-jeanneural`                  | Container image with the `fr-CA` locale and `fr-CA-JeanNeural` voice.      |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `fr-fr-henrineural`                 | Container image with the `fr-FR` locale and `fr-FR-HenriNeural` voice.     |
| `hi-in-madhurneural`                | Container image with the `hi-IN` locale and `hi-IN-MadhurNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-diegoneural`                 | Container image with the `it-IT` locale and `it-IT-DiegoNeural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `it-it-isabellaneural`              | Container image with the `it-IT` locale and `it-IT-IsabellaNeural` voice.  |
| `ja-jp-keitaneural`                 | Container image with the `ja-JP` locale and `ja-JP-KeitaNeural` voice.     |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-injoonneural`                | Container image with the `ko-KR` locale and `ko-KR-InJoonNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-antonioneural`               | Container image with the `pt-BR` locale and `pt-BR-AntonioNeural` voice.   |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `tr-tr-ahmetneural`                 | Container image with the `tr-TR` locale and `tr-TR-AhmetNeural` voice.     |
| `tr-tr-emelneural`                  | Container image with the `tr-TR` locale and `tr-TR-EmelNeural` voice.      |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |

| v1.4.0 Locales and voices           | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-mianeural`                   | Container image with the `en-GB` locale and `en-GB-MiaNeural` voice.       |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |
| `zh-cn-xiaoyouneural`               | Container image with the `zh-CN` locale and `zh-CN-XiaoYouNeural` voice.   |
| `zh-cn-yunyangneural`               | Container image with the `zh-CN` locale and `zh-CN-YunYangNeural` voice.   |
| `zh-cn-yunyeneural`                 | Container image with the `zh-CN` locale and `zh-CN-YunYeNeural` voice.     |

| v1.3.0 Locales and voices           | Notes                                                                      |
|-------------------------------------|:---------------------------------------------------------------------------|
| `de-de-katjaneural`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-ca-claraneural`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-gb-libbyneural`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-mianeural`                   | Container image with the `en-GB` locale and `en-GB-MiaNeural` voice.       |
| `en-us-arianeural`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `en-us-jennyneural`                 | Container image with the `en-US` locale and `en-US-JennyNeural` voice.     |
| `es-es-elviraneural`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `fr-ca-sylvieneural`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `hi-in-swaraneural`                 | Container image with the `hi-IN` locale and `hi-IN-Swaraneural` voice.     |
| `it-it-elsaneural`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `ja-jp-nanamineural`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-sunhineural`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-franciscaneural`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `zh-cn-xiaoxiaoneural`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |

| v1.2.0 Preview Locales and voices           | Notes                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `latest`                                    | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `de-de-katjaneural-preview`                 | Container image with the `de-DE` locale and `de-DE-KatjaNeural` voice.     |
| `en-au-natashaneural-preview`               | Container image with the `en-AU` locale and `en-AU-NatashaNeural` voice.   |
| `en-ca-claraneural-preview`                 | Container image with the `en-CA` locale and `en-CA-ClaraNeural` voice.     |
| `en-gb-libbyneural-preview`                 | Container image with the `en-GB` locale and `en-GB-LibbyNeural` voice.     |
| `en-gb-mianeural-preview`                   | Container image with the `en-GB` locale and `en-GB-MiaNeural` voice.       |
| `en-us-arianeural-preview`                  | Container image with the `en-US` locale and `en-US-AriaNeural` voice.      |
| `en-us-guyneural-preview`                   | Container image with the `en-US` locale and `en-US-GuyNeural` voice.       |
| `es-es-elviraneural-preview`                | Container image with the `es-ES` locale and `es-ES-ElviraNeural` voice.    |
| `es-mx-dalianeural-preview`                 | Container image with the `es-MX` locale and `es-MX-DaliaNeural` voice.     |
| `fr-ca-sylvieneural-preview`                | Container image with the `fr-CA` locale and `fr-CA-SylvieNeural` voice.    |
| `fr-fr-deniseneural-preview`                | Container image with the `fr-FR` locale and `fr-FR-DeniseNeural` voice.    |
| `it-it-elsaneural-preview`                  | Container image with the `it-IT` locale and `it-IT-ElsaNeural` voice.      |
| `ja-jp-nanamineural-preview`                | Container image with the `ja-JP` locale and `ja-JP-NanamiNeural` voice.    |
| `ko-kr-sunhineural-preview`                 | Container image with the `ko-KR` locale and `ko-KR-SunHiNeural` voice.     |
| `pt-br-franciscaneural-preview`             | Container image with the `pt-BR` locale and `pt-BR-FranciscaNeural` voice. |
| `zh-cn-xiaoxiaoneural-preview`              | Container image with the `zh-CN` locale and `zh-CN-XiaoxiaoNeural` voice.  |

---

## Speech language detection

The [Speech language detection][sp-lid] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/speechservices/` repository and is named `language-detection`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/speechservices/language-detection`.

This container image has the following tags available. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/speechservices/language-detection/tags/list).

# [Latest version](#tab/current)

* Release notes for version `1.7.0`:
    * Update dependencies


| Image Tags                                  | Notes                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `latest`                       |      |
| `1.7.0-amd64-preview`                       |      |

# [Previous versions](#tab/previous)

| Image Tags                                  | Notes                                                                      |
|---------------------------------------------|:---------------------------------------------------------------------------|
| `1.6.1-amd64-preview`                       |      |
| `1.5.0-amd64-preview`                       |      |
| `1.3.0-amd64-preview`                       |      |
| `1.2.0-amd64-preview`                       |      |
| `1.1.0-amd64-preview`                       |      |

---

## Key Phrase Extraction

container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/textanalytics/` repository and is named `keyphrase`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/textanalytics/keyphrase`.

This container image has the following tags available. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/textanalytics/keyphrase/tags/list).

# [Latest version](#tab/current)


| Image Tags                    | Notes |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.013570001-amd64` |       |

# [Previous versions](#tab/previous)

| Image Tags                    | Notes |
|-------------------------------|:------|
| `1.1.012840001-amd64` |       |
| `1.1.012830001-amd64`    |       |

---

## Text language detection

The [Language Detection][ta-la] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/textanalytics/` repository and is named `language`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/textanalytics/language`


This container image has the following tags available. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/textanalytics/language/tags/list).

# [Latest versions](#tab/current)

| Image Tags                    | Notes |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.013570001-amd64` | |
   

# [Previous versions](#tab/previous)


| Image Tags                    | Notes |
|-------------------------------|:------|
| `latest`                      |       |
| `1.1.012840001-amd64` |   |
| `1.1.012830001-amd64` |   |

---

## Sentiment analysis

The [Sentiment Analysis][ta-se] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/textanalytics/` repository and is named `sentiment`. The fully qualified container image name is, `mcr.microsoft.com/azure-cognitive-services/textanalytics/sentiment`

This container image has the following tags available. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/textanalytics/sentiment/tags/list).

| Image Tags | Notes                                         |
|------------|:----------------------------------------------|
| `latest`   |                                               |
| `3.0-en`   | Sentiment Analysis v3 (English)               |
| `3.0-es`   | Sentiment Analysis v3 (Spanish)               |
| `3.0-fr`   | Sentiment Analysis v3 (French)                |
| `3.0-it`   | Sentiment Analysis v3 (Italian)               |
| `3.0-de`   | Sentiment Analysis v3 (German)                |
| `3.0-zh`   | Sentiment Analysis v3 (Chinese - simplified)  |
| `3.0-zht`  | Sentiment Analysis v3 (Chinese - traditional) |
| `3.0-ja`   | Sentiment Analysis v3 (Japanese)              |
| `3.0-pt`   | Sentiment Analysis v3 (Portuguese)            |
| `3.0-nl`   | Sentiment Analysis v3 (Dutch)                 |
| `2.1`      | Sentiment Analysis v2                         |


## Text Analytics for health

The [Text Analytics for health][ta-he] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/textanalytics/` repository and is named `healthcare`. The fully qualified container image name is `mcr.microsoft.com/azure-cognitive-services/textanalytics/healthcare`

This container image has the following tags available. You can also find a full list of [tags on the MCR](https://mcr.microsoft.com/v2/azure-cognitive-services/textanalytics/healthcare/tags/list).


# [Latest version](#tab/current)

Release notes for `3.0.017010001-onprem-amd64`:

* You can now use the [Text Analytics for health container with the client library](../text-analytics/how-tos/text-analytics-how-to-install-containers.md?tabs=healthcare#run-the-container-with-client-library-support) 

| Image Tags                    | Notes |
|-------------------------------|:------|
| `latest`                      |       |
| `3.0.017010001-onprem-amd64` |       |

# [Previous versions](#tab/previous)

Release notes for `3.0.015490002-onprem-amd64`:

* new model-version `2021-03-01`
* Container released to MCR.

| Image Tags | Notes                                         |
|------------|:----------------------------------------------|
| `latest`   |                                               |
| `3.0.015490002-onprem-amd64`   |                           |

---

## Translator

The [Translator][tr-containers] container image can be found on the `mcr.microsoft.com` container registry syndicate. It resides within the `azure-cognitive-services/translator` repository and is named `text-translation`. The fully qualified container image name is `mcr.microsoft.com/azure-cognitive-services/translator/text-translation:1.0.019410001-amd64-preview`.

This container image has the following tags available.

| Image Tags                    | Notes |
|-------------------------------|:------|
| `1.0.019410001-amd64-preview`                      |       |


[ad-containers]: ../anomaly-Detector/anomaly-detector-container-howto.md
[cv-containers]: ../computer-vision/computer-vision-how-to-install-containers.md
[fa-containers]: ../face/overview.md
[fr-containers]: ../../applied-ai-services/form-recognizer/containers/form-recognizer-container-install-run.md
[lu-containers]: ../luis/luis-container-howto.md
[sp-stt]: ../speech-service/speech-container-howto.md?tabs=stt
[sp-cstt]: ../speech-service/speech-container-howto.md?tabs=cstt
[sp-tts]: ../speech-service/speech-container-howto.md?tabs=tts
[sp-ctts]: ../speech-service/speech-container-howto.md?tabs=ctts
[sp-ntts]: ../speech-service/speech-container-howto.md?tabs=ntts
[sp-lid]: ../speech-service/speech-container-howto.md?tabs=lid
[ta-kp]: ../text-analytics/how-tos/text-analytics-how-to-install-containers.md?tabs=keyphrase
[ta-la]: ../text-analytics/how-tos/text-analytics-how-to-install-containers.md?tabs=language
[ta-se]: ../text-analytics/how-tos/text-analytics-how-to-install-containers.md?tabs=sentiment
[ta-he]: ../text-analytics/how-tos/text-analytics-how-to-install-containers.md?tabs=healthcare
[tr-containers]: ../translator/containers/translator-how-to-install-container.md
