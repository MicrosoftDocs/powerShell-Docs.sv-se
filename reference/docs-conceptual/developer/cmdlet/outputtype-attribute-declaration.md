---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet OutputType
description: Deklaration av attributet OutputType
ms.openlocfilehash: b5e33346e9ac29c13323781d62daffab892573a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646454"
---
# <a name="outputtype-attribute-declaration"></a>Deklaration av attributet OutputType

`OutputType`Attributet identifierar de .NET Framework typer som returneras av en cmdlet, funktion eller skript.

## <a name="syntax"></a>Syntax

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parametrar

Typ ( `string[]` eller `Type[]` ) krävs. Anger de typer som returneras av cmdlet-funktionen eller skriptet.

ParameterSetName (String []) är valfritt. Anger parameter uppsättningar som returnerar de typer som anges i `type` parametern.

providerCmdlet valfritt. Anger Provider-cmdleten som returnerar de typer som anges i `type` parametern.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
