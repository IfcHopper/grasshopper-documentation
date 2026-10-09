---
slug: /
sidebar_position: 1
title: Introduction
sidebar_label: Introduction
---

## openBIM inside Rhino and Grasshopper

**IfcHopper** (formerly IfcHopperShell) is an open-source Grasshopper plugin for Rhino 8 that creates, reads, updates and deletes (CRUD) data directly in native IFC files. There is no conversion to another format: what you build in Grasshopper is written as IFC, and what you read from an IFC file can be edited and written back, keeping everything else in the file as it was.

:::info[1.0 beta]
This is the documentation of the **1.0 beta**. Try it on your models and [tell us](#get-involved) what works and what does not. Component inputs and outputs may still change until 1.0.
:::

## What you can do

- **Read** IFC2X3, IFC4 and IFC4X3 files and explore them: spatial tree, elements, geometry, types, materials, property and quantity sets, classifications, openings. Only what you look at is loaded, so large files open quickly.
- **Create** IFC models: projects, sites, buildings and the IFC 4.3 infrastructure facilities (bridges, roads, railways, marine facilities), storeys, facility parts, spaces and any IFC element class, with geometry, types (linked to Rhino blocks), materials, property sets and classifications.
- **Update** existing files in place: names, types, placements, geometry, colours, properties, materials, classifications. Objects are matched by GlobalId, and what IfcHopper does not touch stays in the file unchanged.
- **Delete** objects with everything under them.
- **Write** IFC4X3_ADD2, IFC4 or IFC2X3, with a warning for everything an older schema cannot hold.
- **Find** objects by class, name, GlobalId or property values, and summarise a model.

## How it is built

IfcHopper is a C# plugin with its own IFC model (IfcHopper Core), [xBIM Essentials](https://github.com/xBimTeam/XbimEssentials) to read and write IFC files, and RhinoCommon for geometry. It needs no Python and no other installation besides the plugin.

## Coming from IfcHopperShell 0.1

IfcHopper 1.0 is the next version of IfcHopperShell, under its new name. It is a **breaking change**: definitions made with 0.1 are not compatible with 1.0 and have to be rebuilt with the 1.0 components. It no longer needs Python or IfcOpenShell. The 0.1 documentation is still available: choose **v0.1** in the version menu.

## Get involved

IfcHopper is open source (LGPL-3.0), developed by Mattia Bressanelli and Luca Florio.

- Report bugs and ask questions in the [issues](https://github.com/IfcHopper/grasshopper-code/issues) of the code repository.
- Read the code, the roadmap and how to contribute in the [code repository](https://github.com/IfcHopper/grasshopper-code).

Start with the [installation](getting-started/installation), then build your [first model](getting-started/create-new-model).
