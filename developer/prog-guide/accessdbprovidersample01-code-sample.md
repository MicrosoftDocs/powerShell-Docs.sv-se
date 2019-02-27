---
title: AccessDbProviderSample01 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849380"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapar en grundläggande Windows PowerShell-providern](./creating-a-basic-windows-powershell-provider.md). Den här implementeringen ger metoder för att starta och stoppa providern, och även om det inte ger ett sätt att få åtkomst till ett datalager eller för att hämta eller ange data i datalagret kan det tillhandahåller grundläggande funktioner som krävs av alla leverantörer.

> [!NOTE]
> Du kan ladda ned den C# källfilen (AccessDBSampleProvider01.cs) för den här providern med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.
>
> Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Kodexempel

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)