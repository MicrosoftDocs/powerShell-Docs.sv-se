---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113630
Help Version: 7.0.1.0
keywords: powershell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: fc059318507b7a875eedf47692c1b6e3572efbbc
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195550"
---
# PSReadLine-modul

## Beskrivning

Modulen PSReadLine innehåller cmdletar som gör att du kan anpassa redigerings miljön för kommando tolken i PowerShell. Dessa artiklar dokument PSReadLine v 2.0. Den här versionen levereras i PowerShell V6 och Windows 10 oktober 2018-uppdateringen (build 1809).

> [!NOTE]
> Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats. PSReadLine fungerar för närvarande inte bra med skärm läsare. Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt. Du kan läsa in modulen manuellt om det behövs.

## PSReadLine-cmdletar

### [PSConsoleHostReadLine](PSConsoleHostReadLine.md)
Den huvudsakliga start punkten för PSReadLine.

### [Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)
Hämtar nyckel bindningarna för PSReadLine-modulen.

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

