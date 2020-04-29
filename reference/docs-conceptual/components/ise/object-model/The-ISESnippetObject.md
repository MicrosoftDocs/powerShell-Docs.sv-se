---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISESnippetObject
ms.openlocfilehash: f810e6b26f0ded04be15bdc37f336d7890e29dad
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500927"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

Ett **ISESnippet** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISESnippet. Medlemmarna i `$psISE.CurrentPowerShellTab.Snippets` samlingen är alla exempel på **ISESnippet** -objekt. Det enklaste sättet att skapa ett kodfragment är att använda cmdleten [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) .

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
- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
