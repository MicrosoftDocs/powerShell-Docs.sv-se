---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: da71d4ef896befaadd7ed64f9a013dc19508a54c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709043"
---
# PSReadLine-modul

## Beskrivning

Modulen PSReadLine innehåller cmdletar som gör att du kan anpassa redigerings miljön för kommando tolken i PowerShell. De här artiklarna dokumenten PSReadLine v 2.0. Den här versionen levereras i PowerShell V6 och Windows 10 oktober 2018-uppdateringen (build 1809).

> [!NOTE]
> Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats. PSReadLine fungerar för närvarande inte bra med skärm läsare. Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt. Du kan läsa in modulen manuellt om det behövs.

## PSReadLine-cmdletar

### [PSConsoleHostReadLine](PSConsoleHostReadLine.md)
Den huvudsakliga start punkten för PSReadLine.

### [Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)
Hämtar de kopplade nyckel funktionerna för PSReadLine-modulen.

### [Get-PSReadLineOption](Get-PSReadLineOption.md)
Hämtar värden för de alternativ som kan konfigureras.

### [PSConsoleHostReadLine](PSConsoleHostReadLine.md)
Den här funktionen är den viktigaste start punkten för PSReadLine.

### [Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)
Tar bort en nyckel bindning.

### [Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.

### [Set-PSReadLineOption](Set-PSReadLineOption.md)
Anpassar beteendet för kommando rads redigering i **PSReadLine**.

