---
title: "Adding EteSync calendars and tasks to Kontact - GSoC 2020 with KDE and EteSync [Part 4]"
date: "2020-07-08T21:00:00+05:30"
template: "post"
draft: false
slug: "gsoc-part-4-adding-etesync-calendars-tasks"
category: "Tech"
tags:
    - "KDE"
    - "GSoC"
    - "Open Source"
description: "Adding EteSync calendars and tasks to Kontact!"
socialImage: "/media/gsoc-kde-etesync.png"
---

Hey!

Last month, I wrote about [adding EteSync address books to Kontact](https://www.thejollyblog.tech/posts/KDE/gsoc-part-3-adding-etesync-addressbooks). Since then, I have been working on extending this functionality to calendars and tasks as well. I am happy to report that fetching and modifying EteSync contacts, calendars and tasks is now possible in Kontact. If you want to test it out, skip to "[Testing the resource](#testing-the-resource)" section below. You can read on for updates on the project:

## The configuration dialog

When a new EteSync address book or calendar is added to Kontact, a configuration dialog pops up, asking you to enter your EteSync server URL, username, password and existing password. Entering the relevant credentials will fetch your contacts and calendars/tasks in KAddressBook and KOrganizer.

| ![Fetching EteSync contacts, calendar and tasks](/media/EteSync-fetch-everything.gif) |
| :-----------------------------------------------------------------------------------: |
|                    _Fetching EteSync contacts, calendar and tasks_                    |

## Adding/Modifying collections and items

Kontact now implements a two-way client for EteSync. Not only does it support fetching data, but we can also use it to create, modify and delete contacts, events and tasks. We can even create new EteSync address books, calendars and task lists right from within Kontact.

Here, all changes made using KOrganiser are reflected in the EteSync web client too.

| ![Creating an event](/media/EteSync-create-event.gif) |
| :---------------------------------------------------: |
|                  _Creating an event_                  |

<br />

| ![Deleting an event](/media/EteSync-delete-event.gif) |
| :---------------------------------------------------: |
|                  _Deleting an event_                  |

## Testing the resource

Testing the resource is as simple as cloning and building `KDE PIM Runtime` from [this repo](https://invent.kde.org/sjolly/kdepim-runtime/-/tree/etesyncResource).

-   Clone the repo
-   Build the project using `make` or `kdesrc-build`
-   Restart Akonadi (`akonadictl restart`)
-   Open Kontact and add a new EteSync address book or calendar

## About the implementation

-   The configuration dialogue is implemented by subclassing the `Akonadi::AgentConfigurationBase` class.
-   There are basically three handler classes for the three different types - `ContactHandler`, `CalendarHandler` and `TaskHandler`. Classes CalendarHandler and TaskHandler are derived from the abstract class `CalendarTaskBaseHandler`, which contains a lot of code common for handling calendars and tasks.

## What next?

-   The configuration dialog is currently a single dialog that takes as input the username, password, server url and encryption password. It should ideally be a two-step process, where the user enters the server url, username, password and then, on successful login, the encryption password should be entered. This is needed to initialise new accounts which do not have encryption passwords set up.
-   A lot of stuff needs to be looked up and implemented - like setting up the collection refresh rates, the Akonadi cache policies and Akonadi resource status signals.
