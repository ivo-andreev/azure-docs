---
title: Document details - Custom Translator
titleSuffix: Azure Cognitive Services
description: The document list page shows the first 10 document in your workspace. For each of the documents, it displays the name, pairing, type, language, upload time stamp, and the email address of the user who uploaded the document.  
author: laujan
manager: nitinme
ms.service: cognitive-services
ms.subservice: translator-text
ms.date: 12/06/2021
ms.author: lajanuar
ms.topic: how-to
#Customer intent: As a Custom Translator user, I want to understand how to view  document details, so that I can to review list of extracted sentences in a document.
---

# View document details

The document list page shows the first 10 document in your workspace. For each
of the documents, it displays the name, pairing, type, language, upload time
stamp, and the email address of the user who uploaded the document.

Select an individual document to view the document details page. The document details page displays the list of extracted sentences from the document.

- By default the "Side-by-side" source and target languages display is selected in the dropdown field, but you can toggle to view sentences in the source or target language.
- 20 sentences are displayed per page by default. You can use the pagination control to browse between pages.

![document details](media/how-to/how-to-view-document-details.png)

## Delete a document

User must be a workspace owner to delete document to delete a document. Additionally, if a document is in use by a model, that is in any part of the training process or any part of the deployment process, the document can't be deleted.

1. Go to document page
2. Hover on any document record and select the **trash bin** icon.

    ![Delete document](media/how-to/how-to-delete-document-1.png)

3. Confirm Delete.

    ![Delete confirm](media/how-to/how-to-delete-document-confirm.png)

## Next steps

- Learn [how to train a model](how-to-train-model.md).
