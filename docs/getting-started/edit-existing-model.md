---
sidebar_position: 4
title: Edit an existing model
sidebar_label: Edit an existing model
---

This guide edits an IFC file in place: it renames and recolours a wall, gives it a property set, renames the storey and writes the file. Everything else in the file stays as it was. It follows sample **13 Edit in place**; download it from the [samples](../samples) page.

## 1. Read and find

- **Read IFC** reads the file (sample 13 reads `ifc/01 First building.ifc`, written by sample 01).
- **Find Objects** with **Classes** `IfcWall` and **Name** `South*` finds the south wall.
- A second **Find Objects** with **Classes** `IfcBuildingStorey` finds the storey.

## 2. Edit

**Modify** components never change their input: they output an edited copy that keeps the GlobalId and the link to the file. Inputs you leave unconnected keep their value.

- **Modify Object**: connect the wall to **Object**, set a new **Name** (`South wall (renovated)`) and a **Colour**, and connect a **Pset** (`Pset_WallCommon` with `IsExternal` = true and `FireRating` = `REI 120`) to **Property Sets**.
- **Modify Storey**: connect the storey and set a new **Name**.

## 3. Apply the edits and write

- **Apply Edits**: connect the read **Model** and the edited objects to **Edits**. It puts them back into the model by GlobalId.
- **Write IFC**: connect the result and write it to the same file (or to a new one).

The file is written by applying only the differences to it: the changed names, colour and property set. Everything IfcHopper did not touch, including entities it does not model (e.g. alignments or tasks), stays in the file unchanged.

## What else you can edit

- Names, descriptions, predefined types, placements and storey elevations.
- Geometry (replaced) and colours; moving an object moves its geometry and openings.
- Property and quantity sets: a set with the same name replaces the existing one, a set without properties deletes it.
- Materials, types and classifications; editing a type or material changes it for everything that uses it.
- Children: connecting a list of children replaces them; children left out are **deleted** with everything under them.

Some changes are not supported in place and give a clear error: changing the units or contexts, changing an object's class or moving an object to another parent.

## Writing another schema

**Write IFC** writes a read model in its own schema. If you choose another **Schema**, the model is rebuilt as a new file from what IfcHopper reads, with a warning that data IfcHopper does not model is not carried over.
