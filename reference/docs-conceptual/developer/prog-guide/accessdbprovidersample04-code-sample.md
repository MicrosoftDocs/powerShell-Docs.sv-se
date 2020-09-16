---
title: AccessDbProviderSample04 kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 05509c5b36475bcd3f91c9ab7413974994d668d6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787282"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).
Den här providern fungerar på data lager i flera lager. För den här typen av data lager innehåller lagrings platsen på den högsta nivån rot objekten och varje efterföljande nivå kallas nod för underordnade objekt. Genom att tillåta att användaren arbetar på dessa underordnade noder kan en användare interagera hierarkiskt via data lagret.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
