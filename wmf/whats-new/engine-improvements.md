---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: PowerShell-motorn förbättringar i WMF 5.1
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856184"
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

> [!NOTE]
> En ändring som rör start kan påverka vissa scenarier som inte stöds. PowerShell läser inte längre filerna `$pshome\*.ps1xml` – de här filerna har konverterats till C# att undvika att vissa fil- och CPU-belastning som bearbeta XML-filerna. Filerna som finns kvar till support V2 sida vid sida, så om du ändrar filens innehåll, men inte har någon effekt till V5, endast V2. Observera att ändra innehållet i filerna har aldrig ett scenario som stöds.

En annan synbar förändring är hur PowerShell cachelagrar de exporterade kommandona och annan information för moduler som är installerade på ett system. Tidigare var det här cacheminnet har lagrats i katalogen `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. I WMF 5.1 cacheminnet är en enskild fil `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Se [modulen Analysis Cache](release-notes.md#module-analysis-cache) för mer information.