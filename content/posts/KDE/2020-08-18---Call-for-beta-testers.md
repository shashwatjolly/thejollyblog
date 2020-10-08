---
title: "Call for beta testers! | The final lap  - GSoC 2020 with KDE and EteSync [Part 5]"
date: "2020-08-18T16:45:00+05:30"
template: "post"
draft: false
slug: "gsoc-part-5-call-for-beta-testers"
category: "Tech"
tags:
    - "KDE"
    - "GSoC"
    - "Open Source"
    - "EteSync"
description: "The new EteSync integration in KDE is now ready for beta testing!"
socialImage: "/media/gsoc-kde-etesync.png"
---

| ![Adding a new EteSync address book](/media/EteSync-resource-visible-logo.png) |
| :----------------------------------------------------------------------------: |
|                        _Native EteSync support in KDE_                         |

Hey everyone!

For the last 3 months, I have been working on native EteSync integration in Kontact. Since my [last status update](https://www.thejollyblog.tech/posts/KDE/gsoc-part-4-adding-etesync-calendars-tasks), I have been working on improving the resource - handling errors, token refreshes, making the configuration dialog better, locally caching journals and a lot more. Now, the resource is finally ready for testing, and we are thankful to everyone who has volunteered to test the resource ([related post](https://blog.etesync.com/gnome-and-kde-integrations-looking-for-beta-testers/))! This post will detail how to test out the new EteSync-KDE integration.

## How to test the new integration?

If you're running Arch linux, we already have an AUR package for you. Just install [Kontact](https://kde.org/applications/en/office/org.kde.kontact) and then [follow this link](https://aur.archlinux.org/packages/kdepim-runtime-etesync-git/) to get the package and install it on your system.

Otherwise, follow along to install it on your system:

1. Install [Kontact](https://kde.org/applications/en/office/org.kde.kontact) (or upgrade it if you have it installed already)
2. Install the EteSync library

    - Clone [etesync-rs](https://github.com/etesync/etesync-rs) (`git clone https://github.com/etesync/etesync-rs`)
    - cd into the cloned folder and checkout the `legacy` branch (`git checkout legacy`)
    - Install [cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html)
    - Run the following command(s):
        ```shell
        $ make && sudo make install
        ```

3. Compile and build kdepim-runtime from source:
    - Clone [the repo](https://invent.kde.org/sjolly/kdepim-runtime.git) (`git clone https://invent.kde.org/sjolly/kdepim-runtime.git`)
    - cd into the cloned folder and checkout the `etesyncResource` branch
        ```shell
        $ git fetch origin
        $ git checkout etesyncResource
        ```
    - Run the following commands (make sure you have `git` and `cmake` installed):
        ```shell
        $ mkdir build
        $ cd build
        $ cmake ..
        $ make && sudo make install
        ```
4. Restart Akonadi (if it is running)

    ```shell
    $ akonadictl restart
    ```

5. That's mostly it! Now you can add your EteSync account to Kontact:
    - Open Kontact
    - Open the calendar application (KOrganizer) from the left menu (you can also open KOrganizer directly)
    - Right click on the calendar list and choose "Add Calendar"
    - The EteSync option should show up - select it and click "OK"
    - A configuration dialog should show up - enter your EteSync username and password.
      <br>**For self hosters:** Click on "Advanced Settings" and enter the full URL of your hosted server (https://...).
    - Your calendar events, tasks and contacts should now show up!

**Note**: These are general instructions. If you're facing difficulties in building the project, or in getting the resource working, please head over to the [community chat](https://www.etesync.com/community-chat/).

## Known issues

There are currently some known issues, and we're working on fixing them:

-   Creating a new address book from Kontact/KAddressBook is currently not possible. You will probably get an error dialog saying _"Could not create address book folder..."_.
-   Adding todos to calendars and calendar events to task lists is currently possible in Kontact/KOrganizer. You _will_ see an option for adding todos to calendars and vice versa, which shouldn't be the case.
    -   If you do go ahead and add a todo to calendar or an even to a task list, nothing should fail, but the created todo/event will remain visible in KOrganizer.
-   Adding a new EteSync account might take some time for the initial sync. We are looking into optimising it. :)

## Bugs/Feedback?

Do let us know of any issues you face. You can contact us on the [community chat](https://www.etesync.com/community-chat/), or email me directly at [shashwat.jolly@gmail.com](mailto:shashwat.jolly@gmail.com).

Thanks for the support! :D
