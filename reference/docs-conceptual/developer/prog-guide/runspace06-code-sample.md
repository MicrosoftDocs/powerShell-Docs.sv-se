---
title: RunSpace06 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: f0197e6ca3535b72f843ba52e97381c0f2531598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356968"
---
# <a name="runspace06-code-sample"></a>RunSpace06 – kodexempel

Här är käll koden för Runspace06-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av en Windows PowerShell-snapin-modul](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Det här exempel programmet skapar en körnings utrymme baserat på en Windows PowerShell-snapin-modul, som sedan används för att köra en pipeline med ett enda kommando. För att göra detta skapar programmet körnings utrymme konfigurations information, skapar en körnings utrymme, skapar en pipeline med ett enda kommando och kör sedan pipelinen.

> [!NOTE]
> Du kan ladda ned C# käll filen (runspace06.CS) med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .

## <a name="code-sample"></a>Kod exempel

[!code-csharp[Runspace06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)