---
title: "Using EteSync with Kontact - GSoC 2020 with KDE and EteSync [Part 6]"
date: "2020-08-31T20:00:00+05:30"
template: "post"
draft: false
slug: "gsoc-part-6-user-guide"
category: "Tech"
tags:
    - "KDE"
    - "GSoC"
    - "Open Source"
    - "EteSync"
description: "A guide on using your EteSync account in Kontact."
socialImage: "/media/gsoc-kde-etesync.png"
---

Hey everyone!

Over the past few months, I have been working on enabling EteSync users to sync their calendars, contacts and tasks to Kontact. Recently, the resource has been beta-tested, and it is becoming better with every feedback we're getting. This is a guide on how to add your EteSync account to Kontact and use it to manage your EteSync contacts, calendars and tasks.

## Installing the resource

The resource is currently not released with KDE software - we are aiming to have it in the next release. So, it needs to be compiled separately. Follow this guide to install the resource, and head over to the [community chat](https://www.etesync.com/community-chat/) in case of any problems, or even for general help.

## Adding your EteSync account to Kontact

**Note**: The below steps assume that you already have an EteSync account. If not, head over to the [EteSync website](https://www.etesync.com) to create one, and you're good to go!

1. Open the calendar app in Kontact (called Korganizer).
2. On the left, you'll see a list of all your calendars. Right click and select "Add Calendar".
3. A dialog box will pop up, asking you to select the service you want. Select "EteSync Groupware Resource".
4. A configuration dialog will appear:

    If you've already setup an EteSync encryption password:     
    - Enter your EteSync username/email and password and click "Next". 
    - Enter your EteSync encryption password and click "Finish".

    <video autoplay loop muted playsinline src="/media/Adding an existing EteSync account to Kontact.mp4"></video>

    If you have a new EteSync account: 
    - Enter your EteSync username/email and password and click "Next".
    - In the page that opens, you have to set your EteSync encryption password. This is used to encrypt/decrypt all your data, so make sure you double check it, as it cannot be changed if wrong.
    - Enter your EteSync encryption password and click "Finish".
    - Your account will be initialized with three default journals - "My Calendar", "My Contacts" and "My Tasks". Feel free to add more journals as you wish!

    <video autoplay loop muted playsinline src="/media/Setting up a new EteSync account in Kontact.mp4"></video>

<details>
    <summary>
        <b>Advanced: If you have a self-hosted EteSync server</b>
    </summary>

EteSync is completely open-source and so, you can host your own EteSync server if you prefer to do so. Thanks to the way EteSync is designed, there is very little benefit in running your own instance, however, if you still wish to do so, please [follow the instructions](https://github.com/etesync/server).

After you have sucessfully set up your own instance, and verified it works by connecting to it from the browser, click on the "Advanced Settings" checkbox in the configuration dialog while setting up the resource. Enter the server URL of your self-hosted instance in the text-box that appears. Click on "Next" and follow the remaining steps as mentioned above.

<video autoplay loop muted playsinline src="/media/Using local EteSync server in Kontact.mp4"></video>

</details>

## Using EteSync with Kontact

You can now use the Kontact calendar and address book applications (KOrganizer and KAddressBook) to manage your EteSync calendars, tasks and contacts as you normally would. 

Using these applications should be quite straight-forward, but KDE has a handbook on [KOrganizer](https://docs.kde.org/trunk5/en/pim/korganizer/korganizer.pdf) and [KAddressBook](https://docs.kde.org/trunk5/en/pim/kaddressbook/kaddressbook.pdf) if you wish to have a look. 

Example usage:

<video autoplay loop muted playsinline src="/media/Example EteSync use in Kontact.mp4"></video>

That's it! If you have any more questions, or any changes to propose to this guide, do head over to the [community chat](https://www.etesync.com/community-chat/) and let us know. :)