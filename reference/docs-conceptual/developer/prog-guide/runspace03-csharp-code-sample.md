---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace03 (C#) – kodexempel
description: RunSpace03 (C#) – kodexempel
ms.openlocfilehash: cdb08811de13f8bbf5cd91fcbef552c78594b788
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653839"
---
# <a name="runspace03-c-code-sample"></a>RunSpace03 (C#) – kodexempel

Här är C#-käll koden för konsol programmet som beskrivs i avsnittet "skapa ett konsol program som kör ett angivet skript". I det här exemplet används klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra ett skript som hämtar process information med hjälp av listan över process namn som skickas till skriptet. Den visar hur du skickar indata-objekt till ett skript och hur du hämtar fel objekt samt utgående objekt.

> [!NOTE]
> Du kan ladda ned C#-käll filen (runspace03.cs) för det här exemplet med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs" range="11-88":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
