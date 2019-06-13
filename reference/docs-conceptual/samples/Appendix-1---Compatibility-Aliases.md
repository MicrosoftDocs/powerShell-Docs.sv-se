---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Bilaga 1 Kompatibilitetsalias
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030342"
---
# <a name="appendix-1---compatibility-aliases"></a>Bilaga 1 - Kompatibilitetsalias

Windows PowerShell har flera övergången alias som tillåter att UNIX- och Cmd användarna att använda bekanta kommandonamn i Windows PowerShell. De vanligaste alias visas i tabellen nedan, tillsammans med Windows PowerShell-kommando bakom aliaset och aliaset som standard Windows PowerShell om en sådan finns.

Du hittar du Windows PowerShell-kommando som något alias pekar från Windows PowerShell med hjälp av cmdleten Get-Alias. Skriv exempelvis **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Kommandot CMD|UNIX-kommando|PS-Kommando|PS Alias|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**CLS**|**clear**|**Rensa värden** (funktion)|**CLS**|
|**del, radera, rmdir**|**rm**|**Ta bort objekt**|**ri**|
|**Kopiera**|**cp**|**Kopiera objekt**|**ci**|
|**Flytta**|**mv**|**Move-Item**|**mi**|
|**Byt namn på**|**mv**|**Byt namn på objekt**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**Nytt objekt**|**ni**|
|**pushd**|**pushd**|**Push-plats**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|
