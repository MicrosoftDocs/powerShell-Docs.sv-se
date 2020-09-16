---
title: RunSpace06 kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8767ac8dc3a3d9253c2a53a4754d9bd54304abb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784732"
---
# <a name="runspace06-code-sample"></a>RunSpace06 – kodexempel

Här är käll koden för Runspace06-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av en Windows PowerShell-snapin-modul](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).
Det här exempel programmet skapar en körnings utrymme baserat på en Windows PowerShell-snapin-modul, som sedan används för att köra en pipeline med ett enda kommando. För att göra detta skapar programmet körnings utrymme konfigurations information, skapar en körnings utrymme, skapar en pipeline med ett enda kommando och kör sedan pipelinen.

> [!NOTE]
> Du kan ladda ned C#-käll filen (runspace06.cs) med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
