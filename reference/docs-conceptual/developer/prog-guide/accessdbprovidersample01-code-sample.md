---
title: AccessDbProviderSample01 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 429339a86b44bfa53302329fe1e21f6f91c52b42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352803"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md). Den här implementeringen innehåller metoder för att starta och stoppa providern och även om det inte ger möjlighet att komma åt ett data lager eller hämta eller ange data i data lagret, innehåller den de grundläggande funktioner som krävs av alla leverantörer.

> [!NOTE]
> Du kan ladda ned C# käll filen (AccessDBSampleProvider01.CS) för den här providern med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .
>
> Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Kod exempel

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
