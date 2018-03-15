---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f1b023291826d5568eb8bdf5a898a00228825276
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="the-isesnippetobject"></a>ISESnippetObject
  En **ISESnippet** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISESnippet. Medlemmarna i den **$psISE.CurrentPowerShellTab.Snippets** samling är alla exempel på **ISESnippet** objekt. Det enklaste sättet att skapa en fragment är att använda den [ny IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

## <a name="properties"></a>Egenskaper

### <a name="author"></a>författare
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Den skrivskyddade egenskapen som hämtar namnet på författare för kodavsnittet.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a>CodeFragment
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Den skrivskyddade egenskapen som hämtar koden som ska infogas i redigeraren.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a>Genväg
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Skrivskyddad egenskap som hämtar Windows kortkommando för menyalternativet.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Se även
- [Objektet ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Syftet med Windows PowerShell ISE Scripting Object Model](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
