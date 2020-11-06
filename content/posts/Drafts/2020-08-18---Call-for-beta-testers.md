---
title: "EteSync 2.0 with Kontact is now available for beta testing!"
date: "2020-11-06T16:45:00+05:30"
template: "post"
draft: false
slug: "etesync-v2-kontact"
category: "Tech"
tags:
    - "KDE"
    - "GSoC"
    - "Open Source"
    - "EteSync"
description: "The new EteSync 2.0 integration in KDE is ready!"
socialImage: "/media/gsoc-kde-etesync.png"
---

| ![Adding a new EteSync address book](/media/EteSync-resource-visible-logo.png) |
| :----------------------------------------------------------------------------: |
|                        _Native EteSync support in KDE_                         |

Hey everyone!

EteSync recently announced the release of [EteSync 2.0](https://blog.etesync.com/etesync-2-0-is-now-released/), which has great improvements over EteSync 1.0 and a completely revamped underlying SDK. I have been working on upgrading the EteSync module for Kontact to the new version, and I am glad to announce that it is now ready for testing! If you use EteSync and KDE, and want to help test the new integration, please read on! 

## How to test the new integration?

If you're running Arch linux, we already have an AUR package for you. Just install [Kontact](https://kde.org/applications/en/office/org.kde.kontact), [libetebase](https://aur.archlinux.org/packages/etebase) and then [follow this link](https://aur.archlinux.org/packages/kdepim-runtime-etesync-git/) to get the package and install it on your system.

Otherwise, follow along to install it on your system:

1. Install [Kontact](https://kde.org/applications/en/office/org.kde.kontact) (or upgrade it if you have it installed already)
2. Install the EteSync library

    - Clone [libetebase](https://github.com/etesync/libetebase) (`git clone https://github.com/etesync/libetebase.git`)
    - cd into the cloned folder
    - Install [cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html)
    - Run the following command(s):
        ```shell
        $ make && sudo make install
        ```

3. Compile and build kdepim-runtime from source:
    - Clone [the repo](https://invent.kde.org/pim/kdepim-runtime) (`git clone https://invent.kde.org/pim/kdepim-runtime.git`)
    - cd into the cloned folder
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

## Bugs/Feedback?

Do let us know of any issues you face. You can contact us on the [community chat](https://www.etesync.com/community-chat/), or email me directly at [shashwat.jolly@gmail.com](mailto:shashwat.jolly@gmail.com).

Thanks for the support! :D
