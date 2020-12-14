---
external help file: PSReadLine-help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: e02f06137395e187cfe86eb1aeb4b30dbb3f09f1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709049"
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

### Inga

## UTDATA

### Inga

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_PSReadLine](./About/about_PSReadLine.md)

