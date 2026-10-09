---
sidebar_position: 5
title: Samples
sidebar_label: Samples
---

Grasshopper definitions, one per workflow, with the IFC files they write.

**[Download the samples (zip)](pathname:///files/ifchopper-samples-1.0-beta.zip)**

Unzip them anywhere and open the definitions in Rhino 8 with IfcHopper installed. Each one explains its steps in groups on the canvas. Geometry is built in Grasshopper and sizes are in metres: the Rhino document units are respected, but the samples are easiest to follow in a metre document.

| Sample | Shows |
| --- | --- |
| 01 First building | The minimum model: objects in a storey, a building, a site and a project, written to an IFC file. |
| 02 Read and explore | Read IFC Header, Read IFC, then the Deconstruct components down to the objects; preview and bake. |
| 03 Units, contexts and georeference | A millimetre file with subcontexts, true north and a map conversion, read back. |
| 04 Infrastructure | Road, bridge, railway and marine facility with typed facility parts (nested) and their elements. |
| 05 Spaces | Spaces in a storey and on the site, a partial space, furniture in a space, Pset_SpaceCommon. |
| 06 Geometry and colour | Brep, mesh and extrusion geometry, colours with transparency, an element assembly. |
| 07 Types and blocks | Element types from Grasshopper geometry and from a Rhino block, placed by objects. Open `07 Types and blocks.3dm` first. |
| 08 Materials | Materials with a property set, a layer set and a constituent set; an object showing its type's material. |
| 09 Property and quantity sets | Standard and custom property sets, a quantity set, deconstructing them, replacing and deleting sets on Modify Object. |
| 10 Classification | Classification references on an object and its type, inheritance, and replacing or removing them by system. |
| 11 Openings | A wall with a door opening, a window opening and a recess, filled by a door and a window; the wall shows cut. |
| 12 Tags and attributes | Tags and class attributes of doors, windows and a window type. |
| 13 Edit in place | Read sample 01's file, find a wall and the storey, modify them, apply the edits and write: only the edits change. |
| 14 Schema export | One model written as IFC4X3_ADD2, IFC4 and IFC2X3, with the downgrade warnings. |
| 15 Find and summarise | Model Info (classes, counts, tree) and Find Objects by class, name, openings and property filters. |

Samples that write a file write it to the `ifc` folder next to the definition. The **Write** toggle is saved off: set it to true to write. The `ifc` folder already holds the files the samples write, so samples 02, 13 and 15 have a file to read.
