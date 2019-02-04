---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685454"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

En **ISESnippet** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISESnippet. Medlemmarna i den **$psISE.CurrentPowerShellTab.Snippets** samling är alla exempel på **ISESnippet** objekt. Det enklaste sättet att skapa ett fragment är att använda den [New-IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

## <a name="properties"></a>Egenskaper

### <a name="author"></a>Författare

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som hämtar namnet på författaren kodfragmentet.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som hämtar kodfragment som ska infogas i redigeraren.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Genväg

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Skrivskyddad egenskap som hämtar Windows kortkommando för menyalternativets.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Se även

- [ISESnippetCollection-objektet](The-ISESnippetCollection-Object.md)
- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)