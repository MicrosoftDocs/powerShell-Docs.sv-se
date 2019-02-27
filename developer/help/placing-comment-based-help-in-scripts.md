---
title: Placera Kommentarbaserad hjälp i skript | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850150"
---
# <a name="placing-comment-based-help-in-scripts"></a>Lägga till kommentarsbaserat hjälp i skript

Det här avsnittet förklarar var du ska placera kommentarbaserad hjälp för ett skript så att den `Get-Help` cmdlet associerar hjälpavsnitt kommentarbaserad med skript och inte med alla funktioner som kan vara i skriptet.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Var man ska placera Kommentarbaserad hjälp för ett skript

- I början av skriptfilen. Hjälp för skript kan föregås i skriptet bara av kommentarer och tomma rader.

- I slutet av skriptfilen.

  Om det första objektet i skripttext (efter hjälp) är en funktionsdeklarationen, måste det finnas minst två tomma rader mellan slutet av skriptet hjälp och funktionsdeklarationen. I annat fall tolkas hjälp som hjälp för funktionen inte hjälp för skriptet.

## <a name="examples-of-help-placement-in-a-script"></a>Exempel på Hjälp placering i ett skript

 I följande exempel visas var och en av placeringsalternativ för kommentarbaserad hjälp för ett skript.

### <a name="help-at-the-beginning-of-a-script"></a>Hjälp i början av ett skript

 I följande exempel visas kommentarbaserad i början av ett skript.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Hjälp i slutet av ett skript

 I följande exempel visas kommentarbaserad i slutet av ett skript.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```