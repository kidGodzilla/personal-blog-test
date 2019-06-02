---
title: "The Simple Way to add Account Delegates (Exchange Delegates) to Office 365 Resource Mailboxes"
description: "For some services, such as ours, it can be useful to create a Service Account that can access all of the resource mailboxes in your company, so that you can easily control third-party access to your…"
date: "2018-08-23T18:45:14.665Z"
categories: 
  - Microsoft
  - Office 365
  - Information Technology
  - Startup
  - Business

published: true
canonicalLink: https://medium.com/meeting-room-365/adding-account-delegates-exchange-delegates-to-an-office-365-resource-mailbox-a90b93678da2
---

For some services, such as ours, it can be useful to create a **Service Account** that can access all of the resource mailboxes in your company, so that you can easily control third-party access to your tenant via a single set of credentials. Not to mention, this also simplifies the setup and provisioning process.

This has always been an option for Office 365 and Exchange users via EMC and PowerShell. But recently, the Office 365 Admin portal has quietly added the feature as well. Meaning, you can enable delegated access and create a service account in just a few clicks.

### 1\. Log into the Office 365 Admin Portal & Select Rooms and Equipment from the Left Menu

First, you’ll want to log into the Office 365 Admin Portal, located at [**https://portal.office.com/**](https://portal.office.com/) (select Admin). You will need to be an Office 365 Administrator to complete this step.

![](./asset-1.jpeg)

### 2\. Select your Resource Mailbox

This is the mailbox which will be accessed via your service account.

![](./asset-2.jpeg)

### 3\. Select Edit to edit your list of Delegates

![](./asset-3.jpeg)

### 4\. Click ‘Add Delegate’, and add your service account as a delegate

Then click ‘Save’ to confirm.

![](./asset-4.jpeg)![](./asset-5.jpeg)![](./asset-6.jpeg)

Once you confirm your list of delegates, which should include your service account, you can close this pane.

![](./asset-7.jpeg)![](./asset-8.jpeg)

### 5\. Confirm your service account as a delegate

![](./asset-9.jpeg)

### That’s it!

You’ll need to repeat this process for each Office 365 Resource Mailbox you want to access via a Service User.