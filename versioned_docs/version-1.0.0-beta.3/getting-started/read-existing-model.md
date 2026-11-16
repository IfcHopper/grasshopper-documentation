---
sidebar_position: 3
title: Read an existing model
sidebar_label: Read an existing model
---

This guide reads an IFC file and explores it. It follows samples **02 Read and explore** and **15 Find and summarise**, which read the file written by sample 01; download them from the [samples](../samples) page.

## 1. Read the file

- **Read IFC Header** takes a **Path** and gives the file header without reading the model: schema, author, organisation, the application that wrote it.
- **Read IFC** takes the same **Path** and outputs the **Model**. IFC2X3, IFC4 and IFC4X3 files are supported.

A relative path is taken from the folder of the saved definition.

Reading is lazy: only the project is read at first, and every object is read the first time a component asks for it. Large files open quickly, and you only wait for what you explore. When the file changes on disk, it is read again.

:::tip[Units]
IfcHopper converts the file units to the Rhino document units. When they differ, Read IFC shows a remark; its context menu offers **Match Rhino units to file**.
:::

## 2. Explore the spatial tree

Deconstruct the model step by step:

- **Deconstruct Model** → the **Project** (plus the header author, organisation and the source file).
- **Deconstruct Project** → **Sites** and **Facilities**, contexts, units, georeference, property sets.
- **Deconstruct Site**, **Deconstruct Facility**, **Deconstruct Storey**, **Deconstruct Facility Part**, **Deconstruct Space** → their children and **Elements**.
- **Deconstruct Object** → class, type, geometry (meshes in world coordinates, with openings cut), colour, parts, openings, material, property sets, classifications, element type and placement.

Element parameters preview their geometry in the viewport and bake it: one mesh per element (or one block instance per element of a type), named after the element, with its IFC class and GlobalId as user text.

## 3. Find and summarise

You don't have to walk the tree by hand:

- **Model Info** gives the schema, the units, the number of objects per class and the spatial tree as text.
- **Find Objects** searches the model, or below any object, by **Classes** (with their subclasses, e.g. `IfcBuiltElement` for all built elements), **Name** patterns with `*` and `?`, **GlobalIds**, and **Properties** filters such as `Pset_WallCommon.IsExternal = true` or `Qto_WallBaseQuantities.Length > 5`. It outputs the objects, their parents and their paths in the tree.

## Next steps

Everything you read can be edited and written back to the same file: [Edit an existing model](edit-existing-model).
