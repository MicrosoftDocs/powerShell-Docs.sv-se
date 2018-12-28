---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Bilaga 1 Kompatibilitetsalias
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406006"
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
|**dir**|**Ls**|**Get-ChildItem**|**CGI**|
|**CLS**|**Rensa**|**Rensa värden** (funktion)|**CLS**|
|**del, radera, rmdir**|**RM**|**Ta bort objekt**|**RI**|
|**Kopiera**|**CP**|**Kopiera objekt**|**CI**|
|**Flytta**|**MV**|**Flytta objekt**|**MI**|
|**Byt namn på**|**MV**|**Byt namn på objekt**|**rni**|
|**Typ**|**cat**|**Get-innehåll**|**global katalog**|
|**CD**|**CD**|**Ange plats**|**Sl**|
|**MD**|**mkdir**|**Nytt objekt**|**ni**|
|**pushd**|**pushd**|**Push-plats**|**pushd**|
|**popd**|**popd**|**POP-plats**|**popd**|