---
ms.date: 12/31/2019
title: ISESnippetCollection-objektet
description: ISESnippetCollection-objektet är en samling av ISESnippet-objekt. Den fil samling som är associerad med ett PowerShellTab-objekt är medlem i den här klassen.
ms.openlocfilehash: e6170ddf72d5ead840aa3015d4de1dcb21dbfeff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655974"
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection-objektet

**ISESnippetCollection** -objektet är en samling av **ISESnippet** -objekt. Den fil samling som är associerad med ett **PowerShellTab** -objekt är medlem i den här klassen. Ett exempel är `$psISE.CurrentPowerShellTab.Files` samlingen.

## <a name="methods"></a>Metoder

### <a name="load-filepathname-"></a>Läs in \( FilePathName \)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Läser in en `.snippets.ps1xml` fil som innehåller användardefinierade kod avsnitt. Det enklaste sättet att skapa kodfragment är att använda `New-IseSnippet` cmdleten, som automatiskt lagrar dem i din profilmappar så att de läses in varje gång som du startar Windows PowerShell ISE.

**FilePathName** – sträng sökvägen och fil namnet till en .snippets.ps1XML-fil som innehåller definitions definitioner för kodfragment.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Se även

- [ISESnippetObject](The-ISESnippetObject.md)
- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
