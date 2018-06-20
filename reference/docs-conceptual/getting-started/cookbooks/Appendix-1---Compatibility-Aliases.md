---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Bilaga 1 Kompatibilitetsalias
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954644"
---
# <a name="appendix-1---compatibility-aliases"></a>Bilaga 1 - kompatibilitet alias

Windows PowerShell har flera övergången alias som tillåter att UNIX- och Cmd användarna ska använda gamla kommandonamn i Windows PowerShell. De vanligaste alias visas i tabellen nedan, tillsammans med Windows PowerShell-kommandot bakom alias och standard Windows PowerShell-alias om sådan finns.

Du kan hitta Windows PowerShell-kommandot som något alias pekar från i Windows PowerShell med hjälp av cmdleten Get-Alias. Skriv till exempel **get-alias cls**.

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
|**Flytta**|**mv**|**Flytta objekt**|**mi**|
|**Byt namn**|**mv**|**Byt namn på objekt**|**rni**|
|**Typ**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Ange plats**|**sl**|
|**md**|**mkdir**|**Nytt objekt**|**ni**|
|**pushd**|**pushd**|**Push-plats**|**pushd**|
|**popd**|**popd**|**POP-plats**|**popd**|