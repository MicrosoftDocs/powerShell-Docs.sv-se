---
title: Placera kommenterad hjälp i skript | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353251"
---
# <a name="placing-comment-based-help-in-scripts"></a>Lägga till kommentarsbaserat hjälp i skript

I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för ett skript så att `Get-Help` cmdlet associerar det kommenterade hjälp avsnittet med skript och inte med funktioner som kan finnas i skriptet.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Var du vill placera kommenterad hjälp för ett skript

- I början av skript filen. Skript hjälpen kan bara föregås av kommentarer och tomma rader.

- I slutet av skript filen.

  Om det första objektet i skript texten (efter hjälpen) är en funktions deklaration måste det finnas minst två tomma rader mellan slutet av skript hjälpen och funktions deklarationen. Annars tolkas hjälpen som hjälp för funktionen, inte för att hjälpa till med skriptet.

## <a name="examples-of-help-placement-in-a-script"></a>Exempel på hur hjälp placeras i ett skript

 I följande exempel visas var och en av placerings alternativen för den kommenterade hjälpen för ett skript.

### <a name="help-at-the-beginning-of-a-script"></a>Hjälp i början av ett skript

 I följande exempel visas en kommentar baserad i början av ett skript.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Hjälp i slutet av ett skript

 I följande exempel visas en kommentar baserad i slutet av ett skript.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```