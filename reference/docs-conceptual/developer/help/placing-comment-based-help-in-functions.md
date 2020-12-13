---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till kommentarsbaserad hjälp i funktioner
description: Lägga till kommentarsbaserad hjälp i funktioner
ms.openlocfilehash: 3bd72f0c71d8f6ad54c43c99f044423c072fdeeb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658213"
---
# <a name="placing-comment-based-help-in-functions"></a>Lägga till kommentarsbaserad hjälp i funktioner

I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för en funktion så att `Get-Help` cmdleten associerar det kommenterade hjälp avsnittet med rätt funktion.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Var du ska placera Comment-Based hjälp för en funktion

- I början av funktions texten.

- I slutet av funktions texten.

- Före `Function` nyckelordet. När funktionen finns i en skript-eller skriptbaserad modul får det inte finnas mer än en tom rad mellan den sista raden i den kommenterade hjälpen och `Function` nyckelordet. Annars `Get-Help` associeras hjälpen med skriptet, inte med funktionen.

## <a name="examples-of-help-placement-in-a-function"></a>Exempel på hur hjälp placeras i en funktion

I följande exempel visas var och en av de tre placerings alternativen för en kommenterings-baserad hjälp för en funktion.

### <a name="help-at-the-beginning-of-a-function-body"></a>Hjälp i början av en funktions text

I följande exempel visas en kommentar baserad i början av en funktions text.

```powershell
function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}
```

### <a name="help-at-the-end-of-a-function-body"></a>Hjälp i slutet av en funktions text

 I följande exempel visas en kommentar baserad i slutet av en funktions text.

```powershell
function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}
```

### <a name="help-before-the-function-keyword"></a>Hjälp innan nyckelordet Function

 I följande exempel visas en kommentar baserad på raden före nyckelordet function.

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```
