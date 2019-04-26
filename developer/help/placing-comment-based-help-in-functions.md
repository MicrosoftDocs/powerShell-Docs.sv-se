---
title: Placera Kommentarbaserad hjälp i Functions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083203"
---
# <a name="placing-comment-based-help-in-functions"></a>Lägga till kommentarsbaserad hjälp i funktioner

Det här avsnittet förklarar var du ska placera kommentarbaserad hjälp för en funktion så att den `Get-Help` cmdlet associerar hjälpavsnitt kommentarbaserad med rätt funktion.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Var man ska placera Kommentarbaserad hjälp för en funktion

- I början av funktionen brödtext.

- I slutet av funktionen brödtext.

- Innan den `Function` nyckelord. När funktionen är i ett skript eller en skriptmodul, det får inte finnas mer än en tom rad mellan den sista raden i kommentarbaserad hjälp och `Function` nyckelord. I annat fall `Get-Help` associerar hjälp med skriptet, inte funktionen.

## <a name="examples-of-help-placement-in-a-function"></a>Exempel på Hjälp placering i en funktion

 I följande exempel visas var och en av de tre placeringsalternativ för kommentarbaserad hjälp för en funktion.

### <a name="help-at-the-beginning-of-a-function-body"></a>Hjälp i början av brödtexten för en funktion

 I följande exempel visas kommentarbaserad i början av brödtexten för en funktion.

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

### <a name="help-at-the-end-of-a-function-body"></a>Hjälp i slutet av brödtexten för en funktion

 I följande exempel visas kommentarbaserad i slutet av brödtexten för en funktion.

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

### <a name="help-before-the-function-keyword"></a>Hjälpa innan nyckelordet Function

 I följande exempel visar kommentarbaserad på rad innan nyckelordet function.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```