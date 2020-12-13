---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample04 – kodexempel
description: AccessDbProviderSample04 – kodexempel
ms.openlocfilehash: bb70ce9f1b1c94349c354a8771fedf7fcb1bb320
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647563"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).
Den här providern fungerar på data lager i flera lager. För den här typen av data lager innehåller lagrings platsen på den högsta nivån rot objekten och varje efterföljande nivå kallas nod för underordnade objekt. Genom att tillåta att användaren arbetar på dessa underordnade noder kan en användare interagera hierarkiskt via data lagret.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
