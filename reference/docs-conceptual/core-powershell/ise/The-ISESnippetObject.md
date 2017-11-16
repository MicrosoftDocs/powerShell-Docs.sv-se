---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a>ISESnippetObject
  En **ISESnippet** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISESnippet. Medlemmarna i den **$psISE.CurrentPowerShellTab.Snippets** samling är alla exempel på **ISESnippet** objekt. Det enklaste sättet att skapa en fragment är att använda den [ny IseSnippet & #91. PSITPro5_ISE & #93. ](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

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
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)

  
