---
title: "Call for beta testers! | The final lap  - GSoC 2020 with KDE and EteSync [Part 5]"
date: "2020-08-18T15:00:00+05:30"
template: "post"
draft: false
slug: "gsoc-part-5-call-for-beta-testers"
category: "Tech"
tags:
    - "KDE"
    - "GSoC"
    - "Open Source"
description: "Adding EteSync calendars and tasks to Kontact!"
socialImage: "/media/gsoc-kde-etesync.png"
---

| ![Adding a new EteSync address book](/media/EteSync-resource-visible-logo.png) |
| :----------------------------------------------------------------------------: |
|                        _Native EteSync support in KDE_                         |

Hey everyone!

For the last 3 months, I have been working on native EteSync integration in Kontact. Since my [last status update](https://www.thejollyblog.tech/posts/KDE/gsoc-part-4-adding-etesync-calendars-tasks), I have been working on improving the resource - handling errors, token refreshes, making the configuration dialog better, locally caching journals and a lot more. Now, the resource is finally ready for testing, and we are thankful to everyone who has volunteered to test the resource ([related post](https://blog.etesync.com/gnome-and-kde-integrations-looking-for-beta-testers/))! This post will detail how to test out the new EteSync-KDE integration.

## How to test the new integration?

1. Install [Kontact](https://kde.org/applications/en/office/org.kde.kontact) (or upgrade it if you have it installed already)
2. Install the EteSync library

    - Clone [etesync-rs](https://github.com/etesync/etesync-rs) (`git clone https://github.com/etesync/etesync-rs`)
    - Install [cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html)
    - cd into the cloned folder and run:
        ```shell
        $ make && sudo make install
        ```

3. Compile and build kdepim-runtime from source:
    - Clone [the repo](https://invent.kde.org/sjolly/kdepim-runtime/-/tree/etesyncResource) (`git clone https://invent.kde.org/sjolly/kdepim-runtime/-/tree/etesyncResource`)
    - cd into the cloned folder and run these commands:
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
    - A configuration dialog should show up - enter your EteSync username and password. If you are hosting your own EteSync server, click on "Advanced Settings" and enter the full server URL (https://...).
    - Your calendar events, tasks and contacts should now show up!

**Note**: These are general instructions. If you're facing difficulties in building the project, or in getting the resource working, please head over to the [community chat](https://www.etesync.com/community-chat/).

Do let us know of any issues you face. You can contact us on the [community chat](https://www.etesync.com/community-chat/), or directly email me at [shashwat.jolly@gmail.com](mailto:shashwat.jolly@gmail.com).

**For arch linux users**: We already have the EteSync library and the new resource packaged for you, so you can directly install those. Message us on the [community chat](https://www.etesync.com/community-chat/) for more.

Thanks for the support! :D
