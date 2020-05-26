---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Förbättringar i PowerShell-motorn i WMF 5.1
ms.openlocfilehash: cccfcf8872ac60e0902669bcc797d0ed250317ba
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810381"
---
# <a name="powershell-engine-improvements"></a>Förbättringar i PowerShell-motorn

Följande förbättringar av Core PowerShell-motorn har implementerats i WMF 5,1:

## <a name="performance"></a>Prestanda

Prestanda har förbättrats i vissa viktiga områden:

- Start
- Pipelining till-cmdletar som `ForEach-Object` och `Where-Object` är cirka 50% snabbare

Några exempel på förbättringar (resultatet kan variera beroende på maskin vara):

| Scenario | 5,0 tid (MS) | 5,1 tid (MS) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Första gången PowerShell kördes:`powershell -command "Unknown-Command"` | 30000 | 13000 |
| Kommando analys-cache har skapats:`powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> [!NOTE]
> En ändring som är relaterad till Start kan påverka vissa scenarier som inte stöds. PowerShell läser inte längre filerna `$pshome\*.ps1xml` – de här filerna har konverterats till C# för att undvika vissa fil-och processor kostnader för bearbetning av XML-filerna. Filerna finns kvar för att stödja v2 sida vid sida, så om du ändrar fil innehållet har den ingen effekt på V5, bara v2. Observera att ändringar av innehållet i dessa filer aldrig har ett scenario som stöds.

En annan synlig ändring är hur PowerShell cachelagrar de exporterade kommandona och annan information för moduler som är installerade på ett system. Tidigare lagrades cacheminnet i katalogen `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` . I WMF 5,1 är cachen en enda fil `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache` . Mer information finns i [modul Analysis cache](release-notes.md#module-analysis-cache) .
