---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Bilaga 1 Kompatibilitetsalias
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086314"
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
|**typ**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**Nytt objekt**|**ni**|
|**pushd**|**pushd**|**Push-plats**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|