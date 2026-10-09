---
sidebar_position: 1
title: Installation
sidebar_label: Installation
---

## Requirements

- Rhino 8.20 or later, on Windows or Mac (Grasshopper comes with Rhino).

IfcHopper needs nothing else: no Python and no IfcOpenShell.

## Install

1. Download the latest zip from the [releases](https://github.com/IfcHopper/grasshopper-code/releases) of the code repository. Beta versions are marked as pre-release.
2. On Windows, unblock the zip before unzipping it: right-click it, choose **Properties** and tick **Unblock**. Otherwise Windows may stop Grasshopper from loading the plugin.
3. Open Grasshopper and choose **File > Special Folders > Components Folder**. Unzip the zip into that folder (it holds `IfcHopper.gha` and the DLLs next to it; keep them together).
4. Restart Rhino and open Grasshopper. The components are in the **IfcHopper** tab.

## Update or uninstall

To update, close Rhino and replace the folder with the one of the new version. To uninstall, delete it.

:::warning[Breaking change]
IfcHopper 1.0 is not compatible with IfcHopperShell 0.1. Definitions made with 0.1 do not work with 1.0 and have to be rebuilt with the 1.0 components.
:::
