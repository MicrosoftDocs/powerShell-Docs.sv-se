---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Spara skriptet
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="save-script"></a>Spara skriptet

Spara skriptet cmdlet kan du granska skriptfilen genom att spara den på en angiven plats.

## <a name="description"></a>Beskrivning

Spara skriptet cmdlet sparar det angivna skriptet.

## <a name="cmdlet-syntax"></a>Cmdlet-syntax

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet-referens för onlinehjälp

[Spara skriptet](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Exempel på kommandon

### <a name="example-1-save-a-script-from-a-repository"></a>Exempel 1: Spara ett skript från en databas
Detta kommando sparar den senaste versionen av skriptet Fabrikam-ClientScript från GalleryINT databasen till den lokala mappen C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Exempel 2: Spara en version av ett skript genom att rörnät från cmdleten Sök-skript

Det första kommandot hittar version 1.5 för Fabrikam-ClientScript från databasen GalleryINT och sparar den i mappen C:\ScriptSharingDemo

Det andra kommandot verifierar sparat skriptmetadata.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```
