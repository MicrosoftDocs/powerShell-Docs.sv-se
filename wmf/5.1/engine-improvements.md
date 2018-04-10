---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
title: PowerShell-motorn förbättringar i WMF 5.1
ms.openlocfilehash: 3c69c4e13f64683f743eb78b0c9e177ff5b3a771
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
#<a name="powershell-engine-improvements"></a>Förbättringar av PowerShell-motorn

Följande förbättringar i PowerShell kärnmotor har implementerats i WMF 5.1:


## <a name="performance"></a>Prestanda ##

Prestanda har förbättrats i vissa viktiga områden:

- Start
- Pipelining till cmdletar som ForEach-Object och Where-Object är ungefär 50% snabbare

Vissa exempel förbättringar (resultat kan variera beroende på din maskinvara):

| Scenario | 5.0 tid (ms) | 5.1-tid (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Första någonsin PowerShell kör: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Kommandot analysis cache har skapats: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> Obs en ändring som rör start kan påverka vissa som inte stöds av scenarier.
> PowerShell läser inte längre filerna `$pshome\*.ps1xml` --filerna har konverterats till C# för att undvika vissa fil- och CPU omkostnader för bearbetning av XML-filer.
Filerna som finns kvar V2-stöd sida vid sida, så om du ändrar filens innehåll kan den inte har någon effekt till V5 endast V2.
Observera att ändra innehållet i filerna har aldrig ett scenario som stöds.

En annan synbar förändring är hur PowerShell cachelagrar exporterade kommandon och annan information för moduler som är installerade på en dator.
Det här cacheminnet har tidigare lagras i katalogen `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.
I WMF 5.1 cacheminnet är en enskild fil `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Se [modulen analys Cache](scenarios-features.md#module-analysis-cache) för mer information.