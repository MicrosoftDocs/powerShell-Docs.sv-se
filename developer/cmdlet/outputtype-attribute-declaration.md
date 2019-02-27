---
title: OutputType-attributet deklarationen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845215"
---
# <a name="outputtype-attribute-declaration"></a>Deklaration av attributet OutputType

Den `OutputType` attributet anger .NET Framework-typer som returneras av en cmdlet, en funktion eller ett skript.

## <a name="syntax"></a>Syntax

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parametrar

Typ (`string[]` eller `Type[]`) krävs. Anger vilka typer som returneras av cmdlet: en funktion eller skript.

ParameterSetName (string[]) valfritt. Anger parameteruppsättningar som returnerar de angivna typerna i den `type` parametern.

providerCmdlet valfritt. Anger den provider-cmdlet som returnerar de angivna typerna i den `type` parametern.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
