---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISESnippetCollection-objektet
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406013"
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection-objektet

Den **ISESnippetCollection** objekt är en samling **ISESnippet** objekt. Samlingen filer som är associerad med en **PowerShellTab** objektet är medlem i den här klassen. Ett exempel är den **$psISE.CurrentPowerShellTab.Files** samling.

## <a name="methods"></a>Metoder

### <a name="load-filepathname-"></a>Läs in\( FilePathName \)

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Inläsningar en. snippets.ps1xml-fil som innehåller användardefinierade kodfragment. Det enklaste sättet att skapa kodfragment är att använda cmdleten New-IseSnippet, som automatiskt lagrar dem i profilmappen så att de har lästs in varje gång du startar Windows PowerShell ISE.

**FilePathName** - sträng i sökväg och filnamn till en. snippets.ps1xml-filen som innehåller definitioner för kodfragment.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Se även

- [ISESnippetObject](The-ISESnippetObject.md)
- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)