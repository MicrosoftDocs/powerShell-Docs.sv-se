---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISESnippetObject
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028881"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

Ett **ISESnippet** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISESnippet. Medlemmarna i samlingen **$psISE. CurrentPowerShellTab. Fragments** är alla exempel på **ISESnippet** -objekt. Det enklaste sättet att skapa ett kodfragment är att använda cmdleten [New-&#91;IseSnippet&#93; PSITPro5_ISE](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) .

## <a name="properties"></a>Egenskaper

### <a name="author"></a>Författare

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som hämtar namnet på författaren till kodfragmentet.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>Defragmentera

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som hämtar kodfragmentet som ska infogas i redigeraren.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Genvägar

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som hämtar Windows-kortkommandon för meny alternativet.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Se även

- [ISESnippetCollection-objektet](The-ISESnippetCollection-Object.md)
- [Syftet med Windows PowerShell ISE-skriptets objekt modell](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
