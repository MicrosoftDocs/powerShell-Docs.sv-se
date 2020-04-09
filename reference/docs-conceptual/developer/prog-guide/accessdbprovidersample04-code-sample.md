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
ms.openlocfilehash: 60f0ed4e3d39ee93ab63023161d09a6c7b914798
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978584"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="80317-102">AccessDbProviderSample04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="80317-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="80317-103">Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="80317-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="80317-104">Den här providern fungerar på data lager i flera lager.</span><span class="sxs-lookup"><span data-stu-id="80317-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="80317-105">För den här typen av data lager innehåller lagrings platsen på den högsta nivån rot objekten och varje efterföljande nivå kallas nod för underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="80317-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="80317-106">Genom att tillåta att användaren arbetar på dessa underordnade noder kan en användare interagera hierarkiskt via data lagret.</span><span class="sxs-lookup"><span data-stu-id="80317-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="80317-107">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="80317-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="80317-108">Se även</span><span class="sxs-lookup"><span data-stu-id="80317-108">See Also</span></span>

[<span data-ttu-id="80317-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="80317-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
