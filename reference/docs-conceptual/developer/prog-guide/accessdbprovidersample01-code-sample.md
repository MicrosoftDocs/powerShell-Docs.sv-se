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
ms.openlocfilehash: 22cfbc63bd369ebcb2fd8a0d0e8d1995941bbb0f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417999"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md). Den här implementeringen innehåller metoder för att starta och stoppa providern och även om det inte ger möjlighet att komma åt ett data lager eller hämta eller ange data i data lagret, innehåller den de grundläggande funktioner som krävs av alla leverantörer.

> [!NOTE]
> Du kan ladda ned C# käll filen (AccessDBSampleProvider01.CS) för den här providern med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .
>
> Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Kod exempel

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
