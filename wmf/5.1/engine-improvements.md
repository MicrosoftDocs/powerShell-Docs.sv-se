---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: PowerShell-motorn förbättringar i WMF 5.1
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892900"
---
# <a name="powershell-engine-improvements"></a>Förbättringar av PowerShell-motorn

Följande förbättringar i PowerShell core-motorn har införts i WMF 5.1:

## <a name="performance"></a>Prestanda

Prestanda har förbättrats i vissa viktiga områden:

- Start
- Pipelining i cmdletar som `ForEach-Object` och `Where-Object` är ungefär 50% snabbare

Några exempel förbättringar (dina resultat kan variera beroende på din maskinvara):

| Scenario | 5.0 tid (ms) | 5.1-tid (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Första någonsin PowerShell kör: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Kommandot analysis cache som skapats: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> [!Note]
> En ändring som rör start kan påverka vissa scenarier som inte stöds.
> PowerShell läser inte längre filerna `$pshome\*.ps1xml` – de här filerna har konverterats till C# för att undvika att vissa fil och CPU overhead bearbeta XML-filer.
> Filerna som finns kvar till support V2 sida vid sida, så om du ändrar filens innehåll, men inte har någon effekt till V5, endast V2.
> Observera att ändra innehållet i filerna har aldrig ett scenario som stöds.

En annan synbar förändring är hur PowerShell cachelagrar de exporterade kommandona och annan information för moduler som är installerade på ett system.
Tidigare var det här cacheminnet har lagrats i katalogen `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.
I WMF 5.1 cacheminnet är en enskild fil `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Se [modulen Analysis Cache](scenarios-features.md#module-analysis-cache) för mer information.