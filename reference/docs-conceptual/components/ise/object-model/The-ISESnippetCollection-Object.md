---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISESnippetCollection-objektet
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736053"
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection-objektet

**ISESnippetCollection** -objektet är en samling av **ISESnippet** -objekt. Den fil samling som är associerad med ett **PowerShellTab** -objekt är medlem i den här klassen. Ett exempel är den `$psISE.CurrentPowerShellTab.Files` samlingen.

## <a name="methods"></a>Metoder

### <a name="load-filepathname-"></a>Läs in\( FilePathName \)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Läser in en `.snippets.ps1xml`-fil som innehåller användardefinierade kod avsnitt. Det enklaste sättet att skapa kodfragment är att använda `New-IseSnippet`-cmdleten, som automatiskt lagrar dem i din profilmappar så att de läses in varje gång som du startar Windows PowerShell ISE.

**FilePathName** -sträng med sökvägen och fil namnet till en. ps1xml-fil som innehåller kod avsnitts definitioner.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Se även

- [ISESnippetObject](The-ISESnippetObject.md)
- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
