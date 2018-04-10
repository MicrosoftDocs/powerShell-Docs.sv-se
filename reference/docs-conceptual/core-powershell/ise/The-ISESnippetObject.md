---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

En **ISESnippet** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISESnippet. Medlemmarna i den **$psISE.CurrentPowerShellTab.Snippets** samling är alla exempel på **ISESnippet** objekt. Det enklaste sättet att skapa en fragment är att använda den [ny IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

## <a name="properties"></a>Egenskaper

### <a name="author"></a>författare

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som hämtar namnet på författare för kodavsnittet.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som hämtar koden som ska infogas i redigeraren.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Genväg

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Skrivskyddad egenskap som hämtar Windows kortkommando för menyalternativet.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Se även

- [Objektet ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Syftet med Windows PowerShell ISE Scripting Object Model](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)