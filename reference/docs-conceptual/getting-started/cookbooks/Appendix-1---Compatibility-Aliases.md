---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Bilaga 1 kompatibilitet alias
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: d789139ef80d4208b56e0b2930f04f824a00537d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
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
|**dir**|**ls**|**Get-ChildItem**|**CGI**|
|**CLS**|**Rensa**|**Rensa värden** (funktion)|**CLS**|
|**del, radera, rmdir**|**RM**|**Ta bort objekt**|**RI**|
|**Kopiera**|**CP**|**Kopiera objekt**|**CI**|
|**Flytta**|**MV**|**Flytta objekt**|**MI**|
|**Byt namn**|**MV**|**Byt namn på objekt**|**rni**|
|**typ**|**cat**|**Get-innehåll**|**global katalog**|
|**CD**|**CD**|**Ange plats**|**Sl**|
|**MD**|**mkdir**|**Nytt objekt**|**ni**|
|**pushd**|**pushd**|**Push-plats**|**pushd**|
|**popd**|**popd**|**POP-plats**|**popd**|

