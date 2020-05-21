---
title: Placera kommenterings-baserad hjälp i functions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: 898225a582c7ed25f746dec7f84012db1ae60b98
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557080"
---
# <a name="placing-comment-based-help-in-functions"></a>Lägga till kommentarsbaserad hjälp i funktioner

I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för en funktion så att `Get-Help` cmdleten associerar det kommenterade hjälp avsnittet med rätt funktion.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Var du vill placera kommenterings hjälpen för en funktion

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
