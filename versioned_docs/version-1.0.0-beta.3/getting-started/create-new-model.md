---
sidebar_position: 2
title: Create a new model
sidebar_label: Create a new model
---

This guide builds the smallest useful IFC model: a slab and two walls in a storey, in a building, on a site, in a project. It follows sample **01 First building**; download it from the [samples](../samples) page to see the finished definition.

If IFC is new to you, the [IFC 4.3 documentation](https://ifc43-docs.standards.buildingsmart.org/) by buildingSMART explains the concepts used here.

## How a model is built

In IfcHopper you build the model from the bottom up, like the IFC spatial structure:

**objects** → **storey** → **building** → **site** → **project** → **model** → **file**

Each component outputs an IfcHopper object that you connect to the component above it. Nothing is written until you write the model; until then the components only hold data, so you can change anything and see the result at once.

## 1. Objects

Make some geometry, e.g. three **Center Box** components (the floor slab and two walls), and connect each one to the **Geometry** input of an **Object** component. On each Object set:

- **Class**: the IFC class, e.g. `IfcSlab` or `IfcWall`. Any instantiable IFC element class works; an error lists what is wrong when it does not exist.
- **Name**: e.g. `Floor slab`, `South wall`.
- **Type**: the predefined type, e.g. `FLOOR` for the slab and `SOLIDWALL` for the walls. Other values are written as `USERDEFINED` with your value as object type.

Geometry is written as meshes: Breps, extrusions, surfaces and SubDs are faceted. Element parameters preview their geometry in the viewport.

## 2. Spatial structure

- **Storey**: connect the three objects to **Elements** and name it, e.g. `Ground floor`.
- **Building**: connect the storey to **Storeys**.
- **Site**: connect the building to **Facilities**.
- **Project**: connect the site to **Sites** and name it, e.g. `First building`.

Inputs you leave empty take defaults: names (`Hopper Building`, `Hopper Site`…), placements (the parent's), units (the Rhino document's) and GlobalIds. GlobalIds are derived from the component and the data, so writing again keeps the same ids.

A child its parent does not accept in IFC (e.g. a storey directly in a site) gives an error on the component.

## 3. Write

- **Model**: connect the project to **Project**. You can also give an author and an organisation for the file header.
- **Write IFC**: connect the model to **Model**, set the file **Name** (e.g. `01 First building.ifc`) and the **Directory** (empty: an `IfcHopper` folder in your user folder; a relative path is taken from the folder of the saved definition), then set **Write** to true with a Boolean Toggle.

The **Path** output gives the full path of the file. **Schema** chooses IFC4X3_ADD2 (the default), IFC4 or IFC2X3.

## The result

Open the file in any IFC viewer, or in a text editor. These are the lines IfcHopper wrote for the spatial structure and the objects:

```
FILE_SCHEMA (('IFC4X3_ADD2'));
#1=IFCPROJECT('2E5OFGAYvMBxjV_FRIL$Z_',$,'First building',$,$,$,$,(#7),#2);
#10=IFCSITE('1Kh9$mx$TT1Qvy7f4HIz$X',$,'Hopper Site',$,$,#11,$,$,.ELEMENT.,$,$,$,$,$);
#14=IFCBUILDING('0Vg46MsbfQb9l7Ktp2EWgT',$,'Hopper Building',$,$,#15,$,$,.ELEMENT.,$,$,$);
#18=IFCBUILDINGSTOREY('0UChqgxhTPExoTQm2pUrQR',$,'Ground floor',$,$,#19,$,$,.ELEMENT.,0.);
#22=IFCSLAB('0J1lEAucXTD9Xp4xbG6FBV',$,'Floor slab',$,$,#23,#128,$,.FLOOR.);
#129=IFCWALL('2eTALLc3vO9fb2zFqsYDwu',$,'South wall',$,$,#130,#210,$,.SOLIDWALL.);
#211=IFCWALL('2S4anjrHzHaPPs8Sg$UIVT',$,'North wall',$,$,#212,#306,$,.SOLIDWALL.);
#307=IFCRELCONTAINEDINSPATIALSTRUCTURE('0ziXlZJp9HjeiWsVCnb7X7',$,$,$,(#22,#129,#211),#18);
#308=IFCRELAGGREGATES('3HfPT63u5NX8km4XCRlB9X',$,$,$,#14,(#18));
#309=IFCRELAGGREGATES('1fILDxl41HVud8rVAGaY4s',$,$,$,#10,(#14));
#310=IFCRELAGGREGATES('0cwdWRw$nMAf3GoLeKIg1q',$,$,$,#1,(#10));
```

The objects are contained in the storey (`IfcRelContainedInSpatialStructure`) and the storey, building and site are aggregated (`IfcRelAggregates`), as IFC requires.

## Next steps

- Add property sets with **Pset**, materials with **Material**, classifications with **Classification**: see samples 08 to 10.
- Use types and Rhino blocks for repeated objects: sample 07.
- Build infrastructure with **Road**, **Bridge**, **Railway** and their parts: sample 04.
- [Read an existing model](read-existing-model).
