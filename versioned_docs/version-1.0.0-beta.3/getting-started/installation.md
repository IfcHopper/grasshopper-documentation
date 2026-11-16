---
sidebar_position: 1
title: Installation
sidebar_label: Installation
---

## Requirements

- Grasshopper 1 in Rhino 8.20+ using .NET 8, or Rhino 9 using .NET 10, on Windows or Mac.

IfcHopper needs nothing else: no Python and no IfcOpenShell.

Beta.3 includes separate `net8.0` and `net10.0` payloads and targets Rhino 8.20+ (`rh8_20-any`). Recorded host checks used Windows x64, Rhino 8.37 / .NET 8 and Rhino 9.0 / .NET 10. Minimum Rhino 8.20, macOS, clean ZIP/Yak installation, automatic framework selection, update and uninstall remain unverified. See the [release notes](https://github.com/IfcHopper/grasshopper-code/blob/main/docs/RELEASE_NOTES.md) for validation details and limits.

## Install

1. Download the latest zip from the [releases](https://github.com/IfcHopper/grasshopper-code/releases) of the code repository. Beta versions are marked as pre-release.
2. On Windows, unblock the zip before unzipping it: right-click it, choose **Properties** and tick **Unblock**. Otherwise Windows may stop Grasshopper from loading the plugin.
3. Open Grasshopper and choose **File > Special Folders > Components Folder**. Unzip the zip into that folder Keep the `IfcHopper/net8.0` and `IfcHopper/net10.0` folders and their dependencies together; Rhino selects the matching framework.
4. Restart Rhino and open Grasshopper. The components are in the **IfcHopper** tab.

## Update or uninstall

To update, close Rhino and replace the folder with the one of the new version. To uninstall, delete it.

:::warning[Breaking change]
IfcHopper 1.0 is not compatible with IfcHopperShell 0.1. Definitions made with 0.1 do not work with 1.0 and have to be rebuilt with the 1.0 components.
:::

## Migrating from beta.2

Find Objects Name now uses regular expressions: replace `*wall*` with `wall` and `South*` with `^South`. Escape literal regex punctuation. Classes supports exclusions such as `!IfcWall`.

IFC colours now require native Custom Preview: connect object geometry and an IFC material, a Colour output or Class Colours. Default preview uses standard Grasshopper shading. See samples 08 and 17.

Compact inputs and Deconstruct outputs have overall arrows and individual plus/minus controls. Connected parameters and configured inputs stay visible; saved choices survive reopening.
