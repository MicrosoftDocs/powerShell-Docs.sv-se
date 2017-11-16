---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a>Objektet ISESnippetCollection
  Den **ISESnippetCollection** objekt är en samling **ISESnippet** objekt. Samlingen filer som är associerad med en **PowerShellTab** objektet är medlem i den här klassen. Ett exempel är den **$psISE.CurrentPowerShellTab.Files** samling.

## <a name="methods"></a>Metoder

### <a name="load-filepathname-"></a>Läs in\( FilePathName\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Belastningar en. snippets.ps1xml-fil som innehåller användardefinierade kodavsnitt. Det enklaste sättet att skapa kodavsnitt är att använda cmdlet New-IseSnippet, som lagrar dem automatiskt i profilmappen så att de har lästs in varje gång du startar Windows PowerShell ISE.

 **FilePathName** - sträng sökväg och filnamn till en. snippets.ps1xml-filen som innehåller kodavsnitt definitioner.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a>Se även
- [ISESnippetObject](The-ISESnippetObject.md) 
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)

  
