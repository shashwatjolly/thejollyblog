---
title: "The coding period starts! - GSoC 2020 with KDE and EteSync [Part 2]"
date: "2020-06-02"
template: "post"
draft: false
slug: "gsoc-part-2-the-coding-period-starts"
category: "Tech"
tags:
  - "KDE"
  - "GSoC"
  - "Open Source"
description: "The coding period for GSoC 2020 has officially started!"
socialImage: "/media/gsoc-kde-etesync.png"
---

<!-- ![Akonadi Resources in Action](/media/gsoc-kde-etesync.png)
_The 42–Line Bible, printed by Gutenberg._ -->

| ![Akonadi Resources in Action](/media/Akonadi-resources-in-action.png) |
| :--------------------------------------------------------------------: |
|                     _Akonadi Resources in Action_                      |

Hey everyone!
The month-long _Community Bonding_ period of GSoC '20 has ended, and with it begins the exciting phase of beginning work on our projects. My project, [EteSync sync backend for Akonadi](/posts/KDE/gsoc-part-1-lets-get-started), will add support for syncing users' contacts, calendars and tasks to Kontact. Here are the things I've studied about the project, as well as my plans for the upcoming phase.

## Resources in Akonadi

All address books, calendars and tasks that can be added to KAddressbook and KOrganizer (KDE PIM apps) are because of Akonadi Resources. Resources are processes that get data from a server, and serve it to KDE PIM apps through Akonadi. To this end, Akonadi provides an abstract class called [_ResourceBase_](https://api.kde.org/kdepim/akonadi/html/classAkonadi_1_1ResourceBase.html). To create a new resource, one must subclass ResourceBase and implement the relevant functions. This makes the job of a resource developer quite simple, as compared to manually storing data in Akonadi and dealing with a ton of additional things.

All resources have their code in the [KDE PIM Runtime](https://invent.kde.org/pim/kdepim-runtime) repository.

So, to create a new resource:

- Create a new subdirectory for the resource
- Get kdepim-runtime to build, with any external libraries you might need for your resource (restart Akonadi to see any changes)
- Implement the resource

## Plans for the work ahead

I have added the new resource subdirectory to the project, and have the project is building successfully. I am currently working on implementing read-only sync for contacts, which will be then extended to push changes, as well as to calendars and tasks.

Hope to be back with more updates soon!
