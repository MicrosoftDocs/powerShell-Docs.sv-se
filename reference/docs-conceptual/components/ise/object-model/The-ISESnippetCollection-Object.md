---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISESnippetCollection-objektet
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030509"
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection-objektet

**ISESnippetCollection** -objektet är en samling av **ISESnippet** -objekt. Den fil samling som är associerad med ett **PowerShellTab** -objekt är medlem i den här klassen. Ett exempel är samlingen **$psISE. CurrentPowerShellTab. files** .

## <a name="methods"></a>Metoder

### <a name="load-filepathname-"></a>Läs in\( FilePathName \)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Läser in en. Fragments. ps1xml-fil som innehåller användardefinierade kod avsnitt. Det enklaste sättet att skapa kodfragment är att använda cmdleten New-IseSnippet, som automatiskt lagrar dem i din profilmappar så att de läses in varje gång som du startar Windows PowerShell ISE.

**FilePathName** -sträng med sökvägen och fil namnet till en. ps1xml-fil som innehåller kod avsnitts definitioner.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Se även

- [ISESnippetObject](The-ISESnippetObject.md)
- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
