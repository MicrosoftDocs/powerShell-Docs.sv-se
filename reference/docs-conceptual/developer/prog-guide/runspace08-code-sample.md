---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace08 – kodexempel
description: RunSpace08 – kodexempel
ms.openlocfilehash: f8d08e5b6bbd98d0901abe5b05c8b9ee682b8e04
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654227"
---
# <a name="runspace08-code-sample"></a>RunSpace08 – kodexempel

Här är käll koden för Runspace08-exemplet som beskrivs i [skapa ett konsol program som lägger till parametrar till ett kommando](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).
Det här exempel programmet skapar en körnings utrymme, skapar en pipeline, lägger till två kommandon i pipelinen, lägger till två parametrar till det andra kommandot och kör sedan pipelinen. De kommandon som läggs till i pipelinen är `Get-Process` `Sort-Object` cmdletarna och.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
