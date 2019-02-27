---
title: AccessDbProviderSample04 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845138"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapar en Windows PowerShell-providern för behållaren](./creating-a-windows-powershell-container-provider.md). Den här providern fungerar på flera lager datalager. Den översta nivån i arkivet innehåller rot-objekt för den här typen av datalager och varje efterföljande nivå kallas för en nod i underordnade objekt. Genom att tillåta användare att arbeta på dessa underordnade noder, kan en användare interagera hierarkiskt via datalagret.

## <a name="code-sample"></a>Kodexempel

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)