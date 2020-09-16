---
title: Deklaration av OutputType-attribut | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a4cc874031bba092cfef6041bef0e19e6af3f09c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786551"
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
