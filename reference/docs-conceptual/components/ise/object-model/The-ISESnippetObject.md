---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISESnippetObject
ms.openlocfilehash: 60456ec90f56753fa96f141b8b8299ef3f7e41c9
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736972"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

Ett **ISESnippet** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISESnippet. Medlemmarna i den `$psISE.CurrentPowerShellTab.Snippets` samlingen är alla exempel på **ISESnippet** -objekt. Det enklaste sättet att skapa ett kodfragment är att använda cmdleten [New-IseSnippet](/reference/5.1/ISE/New-IseSnippet.md) .

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
