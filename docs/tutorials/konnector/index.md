---
title: How to write a connector
summary: And import data from a service to your Cozy
table_of_contents:
  page: false
items:
  - installation.md
  - getting-started.md
  - scrape-data.md
  - save-data.md
  - packaging.md
  - how-does-it-works.md
  - going-further.md
---

## Introduction

A connector (also known as _konnector_) is a script that imports data from another web service and put those data into your cozy.
Each connector is an independent application, managed by the [Cozy Collect] application.

To protect your data, each connector runs inside a container in order to sandbox all their interactions with your data.

> ⚠️ For historical reasons, in the Cozy codebase, a cozy connector is named konnector, please follow this convention if modifying an existing application.

In this tutorial you will learn how to:

- [Create the basic structure for your connector](./getting-started.md)
- [Scrape data from the service](./implement.md)
- [Save data to your Cozy](./link-cozy.md)
- [Package your connector and send it to the store](./packaging.md)

If you want to go further: 

- [Learn how konnectors are run by the Cozy stack](./how-it-works.md)
- [Learn how konnectors are run by the Cozy stack](./how-it-works.md)
