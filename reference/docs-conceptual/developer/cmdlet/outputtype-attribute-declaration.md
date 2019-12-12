---
title: Deklaration av OutputType-attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356163"
---
# <a name="outputtype-attribute-declaration"></a>Deklaration av attributet OutputType

Attributet `OutputType` identifierar de .NET Frameworks typer som returneras av en cmdlet, funktion eller skript.

## <a name="syntax"></a>Syntax

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parametrar

Typ (`string[]` eller `Type[]`) krävs. Anger de typer som returneras av cmdlet-funktionen eller skriptet.

ParameterSetName (String []) är valfritt. Anger parameter uppsättningar som returnerar de typer som anges i parametern `type`.

providerCmdlet valfritt. Anger Provider-cmdleten som returnerar de typer som anges i parametern `type`.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
