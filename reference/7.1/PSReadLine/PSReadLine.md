---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: a404461e2b92f269d581b18c3ebe7643aa86c3a4
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2020
ms.locfileid: "93269817"
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

