---
title: AccessDbProviderSample04 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357304"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md). Den här providern fungerar på data lager i flera lager. För den här typen av data lager innehåller lagrings platsen på den högsta nivån rot objekten och varje efterföljande nivå kallas nod för underordnade objekt. Genom att tillåta att användaren arbetar på dessa underordnade noder kan en användare interagera hierarkiskt via data lagret.

## <a name="code-sample"></a>Kod exempel

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
