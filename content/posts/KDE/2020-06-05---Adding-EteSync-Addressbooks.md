---
title: "Adding EteSync address books to Kontact - GSoC 2020 with KDE and EteSync [Part 3]"
date: "2020-06-05T23:40:00+05:30"
template: "post"
draft: false
slug: "gsoc-part-3-adding-etesync-addressbooks"
category: "Tech"
tags:
  - "KDE"
  - "GSoC"
  - "Open Source"
  - "EteSync"
description: "Adding EteSync contacts to Kontact!"
socialImage: "/media/gsoc-kde-etesync.png"
---

Hey everyone!

Last week, I wrote a [post](https://thejollyblog.netlify.app/posts/KDE/gsoc-part-2-the-coding-period-starts) about adding EteSync address books to Kontact. I'm happy to report that you can now fetch your EteSync address books and contacts in Kontact. If you want to test it out, skip to "[Testing the resource](#testing-the-resource)" section below. You can read on for updates on the project:

## Adding a new EteSync account to KAddressBook

| ![Adding a new EteSync address book](/media/EteSync-resource-visible-logo.png) |
| :----------------------------------------------------------------------------: |
|                      _Adding a new EteSync address book_                       |

I have created a new EteSync resource subdirectory, and added it to the project build system. I've also added the logo for the resource, which shows up while adding a new address book to Kontact.

## Fetching your EteSync contacts

Once the new resource is added, the app should ideally open a configuration dialog for you to provide your username, password, EteSync server url and encryption password. Unfortunately, I haven't implemented that yet. I plan to implement it soon so that users can easily test out the resource.

Currently, the credentials are hardcoded, and will be used to fetch all your address books and contacts. These will then show up in KAddressBook.

| ![EteSync address books and contacts visible](/media/EteSync-addressbook-and-contacts-visible.png) |
| :------------------------------------------------------------------------------------------------: |
|                    _EteSync address books and contacts visible in KAddressBook_                    |

## Testing the resource

As the resource configuration dialog hasn't been implemented yet, you would need to put in your EteSync credentials in the `configure()` function in `etesync/etesyncresource.cpp` to test it out.

All the code for this project is at [this repo](https://invent.kde.org/sjolly/kdepim-runtime/-/tree/etesyncResource). To test the resource, you can:

- Clone the repo
- Enter your EteSync credentials in `etesync/etesyncresource.cpp`
- Build the project using `make` or `kdesrc-build`
- Restart Akonadi (`akonadictl restart`)
- Open KAddressBook and add a new EteSync address book

## To-do

I plan to implement the configuration dialog ASAP. Also, the fetching itself needs more work as it should be done asynchronously using jobs.

Feedback is always welcome!

Hope to have more updates for you soon :)
