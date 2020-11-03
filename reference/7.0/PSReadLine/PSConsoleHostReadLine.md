---
external help file: PSReadLine-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: 47d97fd50294a0dda1064bad123dc17931f8a470
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273326"
---
# PSConsoleHostReadLine

## SAMMANFATTNING
Den här funktionen är den viktigaste start punkten för PSReadLine.

## SYNTAX

```
PSConsoleHostReadLine
```

## BESKRIVNING

`PSConsoleHostReadLine` är huvud start punkten för PSReadLine-modulen. PowerShell-konsolens värd laddar automatiskt PSReadLine-modulen och anropar den här funktionen. Under normala drifts förhållanden är den här funktionen inte avsedd att användas från kommando raden.

Tilläggs punkten `PSConsoleHostReadLine` är speciell för konsol värden. Värden anropar ett alias, en funktion eller ett skript med det här namnet. PSReadLine definierar den här funktionen så att den anropas från konsol värden.

## EXEMPEL

### Exempel 1

Den här funktionen är inte avsedd att användas från kommando raden.

## PARAMETRAR

## INDATA

### Inget

## UTDATA

### Inget

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_PSReadLine](./About/about_PSReadLine.md)
