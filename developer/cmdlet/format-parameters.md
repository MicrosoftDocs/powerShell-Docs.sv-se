---
title: Formatera parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068121"
---
# <a name="format-parameters"></a><span data-ttu-id="d8f64-102">Formatparametrar</span><span class="sxs-lookup"><span data-stu-id="d8f64-102">Format Parameters</span></span>

<span data-ttu-id="d8f64-103">I följande tabell visas rekommenderade namn och funktioner för parametrar som används för att formatera eller för att generera data.</span><span class="sxs-lookup"><span data-stu-id="d8f64-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="d8f64-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="d8f64-104">Parameter</span></span>|<span data-ttu-id="d8f64-105">Funktioner</span><span class="sxs-lookup"><span data-stu-id="d8f64-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="d8f64-106">**Som**</span><span class="sxs-lookup"><span data-stu-id="d8f64-106">**As**</span></span><br><span data-ttu-id="d8f64-107">Datatyp: Nyckelord</span><span class="sxs-lookup"><span data-stu-id="d8f64-107">Data type: Keyword</span></span>|<span data-ttu-id="d8f64-108">Implementera den här parametern om du vill ange formatet för cmdlet-utdata.</span><span class="sxs-lookup"><span data-stu-id="d8f64-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="d8f64-109">Möjliga värden kan exempelvis vara Text eller skript.</span><span class="sxs-lookup"><span data-stu-id="d8f64-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="d8f64-110">**Binary**</span><span class="sxs-lookup"><span data-stu-id="d8f64-110">**Binary**</span></span><br><span data-ttu-id="d8f64-111">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="d8f64-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="d8f64-112">Implementera den här parametern om du vill ange att cmdleten hanterar binära värden.</span><span class="sxs-lookup"><span data-stu-id="d8f64-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="d8f64-113">**Kodning**</span><span class="sxs-lookup"><span data-stu-id="d8f64-113">**Encoding**</span></span><br><span data-ttu-id="d8f64-114">Datatyp: Nyckelord</span><span class="sxs-lookup"><span data-stu-id="d8f64-114">Data type: Keyword</span></span>|<span data-ttu-id="d8f64-115">Implementera den här parametern om du vill ange vilken typ av kodning som stöds.</span><span class="sxs-lookup"><span data-stu-id="d8f64-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="d8f64-116">Möjliga värden kan exempelvis vara ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte och sträng.</span><span class="sxs-lookup"><span data-stu-id="d8f64-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="d8f64-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="d8f64-117">**NewLine**</span></span><br><span data-ttu-id="d8f64-118">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="d8f64-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="d8f64-119">Implementera den här parametern så att radmatningstecken stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="d8f64-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="d8f64-120">**Kortnamn**</span><span class="sxs-lookup"><span data-stu-id="d8f64-120">**ShortName**</span></span><br><span data-ttu-id="d8f64-121">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="d8f64-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="d8f64-122">Implementera den här parametern så att kortnamn stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="d8f64-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="d8f64-123">**Bredd**</span><span class="sxs-lookup"><span data-stu-id="d8f64-123">**Width**</span></span><br><span data-ttu-id="d8f64-124">Datatyp: Int32</span><span class="sxs-lookup"><span data-stu-id="d8f64-124">Data type: Int32</span></span>|<span data-ttu-id="d8f64-125">Implementera den här parametern så att användaren kan ange bredden på enheten.</span><span class="sxs-lookup"><span data-stu-id="d8f64-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="d8f64-126">**Omsluta**</span><span class="sxs-lookup"><span data-stu-id="d8f64-126">**Wrap**</span></span><br><span data-ttu-id="d8f64-127">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="d8f64-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="d8f64-128">Implementera den här parametern så att radbrytning stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="d8f64-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="d8f64-129">Se även</span><span class="sxs-lookup"><span data-stu-id="d8f64-129">See Also</span></span>

[<span data-ttu-id="d8f64-130">Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="d8f64-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="d8f64-131">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d8f64-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="d8f64-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d8f64-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
