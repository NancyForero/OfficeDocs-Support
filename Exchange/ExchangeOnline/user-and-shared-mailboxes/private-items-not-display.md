---
title: Private items aren't displayed in a shared mailbox in Outlook
description: Provides workarounds to an issue in which Private items aren't displayed in a shared mailbox in Outlook.
author: TobyTu
ms.author: shmcdani
manager: dcscontentpm
audience: ITPro
ms.topic: troubleshooting
ms.prod: office-perpetual-itpro
localization_priority: Normal
ms.custom: 
  - CSSTroubleshoot
  - CI 123194
ms.reviewer: shmcdani
appliesto:
- Outlook for Microsoft 365
- Outlook 2019
- Outlook 2016
- Outlook 2013
- Exchange Online
search.appverid: MET150
---

# Private items aren't displayed in a shared mailbox in Outlook

In Outlook, Items such as emails or meeting requests that were [marked as Private](https://support.microsoft.com/office/mark-your-email-as-normal-personal-private-or-confidential-4a76d05b-6c29-4a0d-9096-71784a6b12c1) in a shared mailbox aren't displayed in **Inbox**.

This is an expected behavior as Outlook client was designed not to display private items in shared mailboxes.

> [!NOTE]
> Only the sender can set the the items' sensitivity level. This option will be grayed out in the recipient's **Inbox**.

## Workarounds

Here are three ways to work around this issue:

- Use Outlook on the Web (OWA).
- Add the user as a delegate to the shared mailbox with access to private items.

    In PowerShell:

    ```powershell
    Add-MailboxFolderPermission -Identity ayla@contoso.com:\Calendar -User laura@contoso.com -AccessRights Editor -SharingPermissionFlags Delegate,CanViewPrivateItems
    ```

    In Outlook:

    1. Select **File** > **Account Settings** > **Delegate Access**
    2. Double-click the username of the delegate or select **Add** to add a new delegate.
    3. In the **Delegate Permissions** dialog, check **Delegate can see my private items**.
    4. Select **OK**.
- In Outlook, add the shared mailbox as an [additional account](https://support.microsoft.com/office/add-an-email-account-to-outlook-6e27792a-9267-4aa4-8bb6-c84ef146101b) by using the email address and password of the user that has rights over that mailbox.

    Make sure automapping was removed and the mailbox was not added as an additional mailbox. To learn how to remove automapping for a shared mailbox, read [this article](https://docs.microsoft.com/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).