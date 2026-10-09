---
sidebar_position: 4
title: How it works
sidebar_label: How it works
---

The rules IfcHopper follows, for when you want to know why a model came out the way it did. The full technical description is in the [code repository](https://github.com/IfcHopper/grasshopper-code#data-flow).

## The model

IfcHopper has its own model of an IFC file: a project with a tree of sites, facilities (building, bridge, road, railway, marine facility, generic facility), storeys, facility parts, spaces and elements. Components build or edit this model; the file is only written by **Write IFC**.

The tree follows the IFC rules on what may contain what (e.g. a project holds sites or facilities, a building holds storeys, a road holds road parts or generic facility parts). A child its parent does not accept gives an error. Spatial children are written with `IfcRelAggregates`, elements in a spatial object with `IfcRelContainedInSpatialStructure`, and an element's parts with `IfcRelAggregates`.

## Units

- Inputs and outputs are in the **Rhino document units**.
- Files are written in the project **Units** (Units component); by default the Rhino length unit with m², m³ and radians.
- Files in other units are converted when read. Read IFC shows a remark when the file units differ from Rhino's and can match the Rhino units to the file.
- Property and quantity values that are lengths, areas or volumes follow the document units; other measures are in SI units (e.g. weights in kg).

## Placements

Sites, facilities, parts, spaces, objects and openings take an optional world **Placement** plane; empty means the placement of the parent. IfcHopper writes IFC local placements relative to the parent and gives world planes back when reading. Storeys are placed at their **Elevation**.

## GlobalIds

Every object has a GlobalId. Create components take one, or derive a stable one from the component and the data, so writing again keeps the same ids. Objects read from a file keep theirs; edits are matched to the file by GlobalId. A GlobalId used twice in a model is an error.

## Reading

Files are read lazily: the project first, then every object the first time a component asks for it. Entities IfcHopper does not model are kept in the file when it is written back.

## Editing in place

Modify components output edited copies (same GlobalId); **Apply Edits** puts them back into a read model. Writing a read model applies only the differences to a fresh copy of the source file:

- changed names, descriptions, types, placements, elevations, geometry, colours, property sets, materials, types and classifications are updated;
- new children are created;
- children left out of a connected list are deleted, with everything under them;
- lists that were never read stay as they are.

Not supported in place: changing units or contexts, changing an object's class, moving an object to another parent.

## Schemas

**Write IFC** writes IFC4X3_ADD2 (default), IFC4 or IFC2X3. What a schema cannot hold is downgraded and listed as a warning on the component, for example:

- IFC 4.3 facilities and facility parts become `IfcBuilding` and `IfcBuildingStorey` in IFC4 and IFC2X3, with the original class in ObjectType;
- element classes the schema lacks become `IfcBuildingElementProxy`;
- IFC2X3 gets faceted Breps for meshes, the georeference as property sets, and no material descriptions or categories.

## Geometry

- **Written** as meshes (`IfcPolygonalFaceSet` in the Body representation); Breps, extrusions, surfaces and SubDs are faceted.
- **Read** from face sets, faceted Breps, surface models, extrusions of most profiles, half space clippings, mapped items and sectioned solids along alignments. Other kinds are reported as skipped.
- Each mesh can have a **colour** (with transparency); meshes without one show the colour of the element's material.
- Openings are subtracted from their host for preview, bake and Deconstruct Object; the file keeps the body uncut, as IFC does.

## Types and blocks

An **Element Type** holds geometry, a material and property sets shared by its objects, like a Rhino block definition. An object without its own geometry is an instance of its type; a Rhino block instance used as geometry makes the object an instance of the block's type. Instances bake back as block instances. Editing a type in place changes it for every object of that type.

## Property sets, materials and classifications

- **Property and quantity sets** are on every object; an object shows the sets of its type unless it has its own with the same name. The **Pset** and **Qto** components take value types from the standard IFC 4.3 sets and warn about properties the standard set does not have.
- **Materials** are single materials, layer sets or constituent sets, with colours and property sets; an object without its own material shows its type's.
- **Classifications** are references (system, edition, code, name) on objects and types.

## What is not supported yet

The list of IFC 4.3 concepts IfcHopper does not cover yet (e.g. alignments as objects, groups and systems, parametric geometry when writing) and the plan for them are in the [code repository](https://github.com/IfcHopper/grasshopper-code#ifc-43-coverage).
