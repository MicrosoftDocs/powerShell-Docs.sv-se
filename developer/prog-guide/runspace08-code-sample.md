---
title: RunSpace08 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081282"
---
# <a name="runspace08-code-sample"></a>RunSpace08 – kodexempel

Här är källkoden för Runspace08-exemplet som beskrivs i [skapar ett program som lägger till Konsolparametrar till ett kommando](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Det här exempelprogrammet skapar ett körningsutrymme, skapas en pipeline, lägger till två kommandon i pipelinen, lägger till två parametrar i det andra kommandot och sedan körs pipelinen. De kommandon som läggs till i pipeline är den `Get-Process` och `Sort-Object` cmdletar.

## <a name="code-sample"></a>Kodexempel

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)