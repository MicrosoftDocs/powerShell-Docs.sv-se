---
title: Format parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359318"
---
# <a name="format-parameters"></a><span data-ttu-id="11981-102">Formatparametrar</span><span class="sxs-lookup"><span data-stu-id="11981-102">Format Parameters</span></span>

<span data-ttu-id="11981-103">I följande tabell visas rekommenderade namn och funktioner för parametrar som används för att formatera eller generera data.</span><span class="sxs-lookup"><span data-stu-id="11981-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="11981-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="11981-104">Parameter</span></span>|<span data-ttu-id="11981-105">Funktioner</span><span class="sxs-lookup"><span data-stu-id="11981-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="11981-106">**Som**</span><span class="sxs-lookup"><span data-stu-id="11981-106">**As**</span></span><br><span data-ttu-id="11981-107">Datatyp: nyckelord</span><span class="sxs-lookup"><span data-stu-id="11981-107">Data type: Keyword</span></span>|<span data-ttu-id="11981-108">Implementera den här parametern för att ange formatet för cmdlet-utdata.</span><span class="sxs-lookup"><span data-stu-id="11981-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="11981-109">Möjliga värden kan till exempel vara text eller skript.</span><span class="sxs-lookup"><span data-stu-id="11981-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="11981-110">**Binär**</span><span class="sxs-lookup"><span data-stu-id="11981-110">**Binary**</span></span><br><span data-ttu-id="11981-111">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="11981-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="11981-112">Implementera den här parametern för att ange att cmdleten hanterar binära värden.</span><span class="sxs-lookup"><span data-stu-id="11981-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="11981-113">**Inställning**</span><span class="sxs-lookup"><span data-stu-id="11981-113">**Encoding**</span></span><br><span data-ttu-id="11981-114">Datatyp: nyckelord</span><span class="sxs-lookup"><span data-stu-id="11981-114">Data type: Keyword</span></span>|<span data-ttu-id="11981-115">Implementera den här parametern för att ange vilken typ av kodning som stöds.</span><span class="sxs-lookup"><span data-stu-id="11981-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="11981-116">Möjliga värden kan till exempel vara ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, byte och String.</span><span class="sxs-lookup"><span data-stu-id="11981-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="11981-117">**Ny rad**</span><span class="sxs-lookup"><span data-stu-id="11981-117">**NewLine**</span></span><br><span data-ttu-id="11981-118">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="11981-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="11981-119">Implementera den här parametern så att rad matnings tecken stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="11981-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="11981-120">**Kortnamn**</span><span class="sxs-lookup"><span data-stu-id="11981-120">**ShortName**</span></span><br><span data-ttu-id="11981-121">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="11981-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="11981-122">Implementera den här parametern så att korta namn stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="11981-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="11981-123">**LED**</span><span class="sxs-lookup"><span data-stu-id="11981-123">**Width**</span></span><br><span data-ttu-id="11981-124">Datatyp: Int32</span><span class="sxs-lookup"><span data-stu-id="11981-124">Data type: Int32</span></span>|<span data-ttu-id="11981-125">Implementera den här parametern så att användaren kan ange bredden på utmatnings enheten.</span><span class="sxs-lookup"><span data-stu-id="11981-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="11981-126">**Flytta**</span><span class="sxs-lookup"><span data-stu-id="11981-126">**Wrap**</span></span><br><span data-ttu-id="11981-127">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="11981-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="11981-128">Implementera den här parametern så att figur sättningen stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="11981-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="11981-129">Se även</span><span class="sxs-lookup"><span data-stu-id="11981-129">See Also</span></span>

[<span data-ttu-id="11981-130">Cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="11981-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="11981-131">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="11981-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="11981-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="11981-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
