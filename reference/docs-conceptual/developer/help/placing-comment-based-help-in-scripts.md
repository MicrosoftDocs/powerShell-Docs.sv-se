---
title: Lägga till kommentarsbaserat hjälp i skript
ms.date: 09/12/2016
ms.openlocfilehash: a3ade6c3138826b924939056b9d1ffb233006d44
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893194"
---
# <a name="placing-comment-based-help-in-scripts"></a>Lägga till kommentarsbaserat hjälp i skript

I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för ett skript så att `Get-Help` cmdleten associerar det kommenterade hjälp avsnittet med skript och inte med funktioner som kan finnas i skriptet.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Var du vill placera kommenterad hjälp för ett skript

- I början av skript filen.

  Skript hjälpen kan bara föregås av kommentarer och tomma rader.

- I slutet av skript filen.

  Om det första objektet i skript texten (efter hjälpen) är en funktions deklaration måste det finnas minst två tomma rader mellan slutet av skript hjälpen och funktions deklarationen. Annars tolkas hjälpen som hjälp för funktionen, inte för att hjälpa till med skriptet.

## <a name="examples-of-help-placement-in-a-script"></a>Exempel på hur hjälp placeras i ett skript

I följande exempel visas var och en av placerings alternativen för den kommenterade hjälpen för ett skript.

### <a name="help-at-the-beginning-of-a-script"></a>Hjälp i början av ett skript

I följande exempel visas en kommentar baserad i början av ett skript.

```powershell
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
