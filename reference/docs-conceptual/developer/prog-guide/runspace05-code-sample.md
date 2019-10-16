---
title: RunSpace05 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: a99d0cc0dd35ae4c1a52e3624a9dd5af2a26c97a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352516"
---
# <a name="runspace05-code-sample"></a>RunSpace05 – kodexempel

Här är käll koden för Runspace05-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). Det här exemplet visar hur du skapar konfigurations informationen för körnings utrymme, skapar en körnings utrymme, skapar en pipeline med ett enda kommando och sedan kör pipelinen. Kommandot som körs är cmdleten `Get-Process`.

> [!NOTE]
> Du kan ladda ned C# käll filen (runspace05.CS) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .

## <a name="code-sample"></a>Kod exempel

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
