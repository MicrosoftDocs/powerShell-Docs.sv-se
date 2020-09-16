---
title: AccessDbProviderSample01 kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2e9f81b3011ea1b27bafd9e02ea7e0faf7903a62
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784834"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).
Den här implementeringen innehåller metoder för att starta och stoppa providern och även om det inte ger möjlighet att komma åt ett data lager eller hämta eller ange data i data lagret, innehåller den de grundläggande funktioner som krävs av alla leverantörer.

> [!NOTE]
> Du kan hämta C#-källfilen (AccessDBSampleProvider01.cs) för den här providern med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen. Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
