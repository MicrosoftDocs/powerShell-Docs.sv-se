---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace05 – kodexempel
description: RunSpace05 – kodexempel
ms.openlocfilehash: f128e09522bdb05cba2c160bce4944c829a5c108
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654209"
---
# <a name="runspace05-code-sample"></a>RunSpace05 – kodexempel

Här är käll koden för Runspace05-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).
Det här exemplet visar hur du skapar konfigurations informationen för körnings utrymme, skapar en körnings utrymme, skapar en pipeline med ett enda kommando och sedan kör pipelinen. Kommandot som körs är `Get-Process` cmdleten.

> [!NOTE]
> Du kan ladda ned C#-käll filen (runspace05.cs) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
