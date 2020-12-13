---
ms.date: 09/13/2016
ms.topic: reference
title: Formatparametrar
description: Formatparametrar
ms.openlocfilehash: 5f970683fedc71b208ff6becad761d94611a91a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652819"
---
# <a name="format-parameters"></a><span data-ttu-id="3685c-103">Formatparametrar</span><span class="sxs-lookup"><span data-stu-id="3685c-103">Format Parameters</span></span>

<span data-ttu-id="3685c-104">I följande tabell visas rekommenderade namn och funktioner för parametrar som används för att formatera eller generera data.</span><span class="sxs-lookup"><span data-stu-id="3685c-104">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="3685c-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="3685c-105">Parameter</span></span>|<span data-ttu-id="3685c-106">Funktioner</span><span class="sxs-lookup"><span data-stu-id="3685c-106">Functionality</span></span>|
|---|---|
|<span data-ttu-id="3685c-107">**Som**</span><span class="sxs-lookup"><span data-stu-id="3685c-107">**As**</span></span><br><span data-ttu-id="3685c-108">Datatyp: nyckelord</span><span class="sxs-lookup"><span data-stu-id="3685c-108">Data type: Keyword</span></span>|<span data-ttu-id="3685c-109">Implementera den här parametern för att ange formatet för cmdlet-utdata.</span><span class="sxs-lookup"><span data-stu-id="3685c-109">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="3685c-110">Möjliga värden kan till exempel vara text eller skript.</span><span class="sxs-lookup"><span data-stu-id="3685c-110">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="3685c-111">**Binär**</span><span class="sxs-lookup"><span data-stu-id="3685c-111">**Binary**</span></span><br><span data-ttu-id="3685c-112">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="3685c-112">Data type: SwitchParameter</span></span>|<span data-ttu-id="3685c-113">Implementera den här parametern för att ange att cmdleten hanterar binära värden.</span><span class="sxs-lookup"><span data-stu-id="3685c-113">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="3685c-114">**Kodning**</span><span class="sxs-lookup"><span data-stu-id="3685c-114">**Encoding**</span></span><br><span data-ttu-id="3685c-115">Datatyp: nyckelord</span><span class="sxs-lookup"><span data-stu-id="3685c-115">Data type: Keyword</span></span>|<span data-ttu-id="3685c-116">Implementera den här parametern för att ange vilken typ av kodning som stöds.</span><span class="sxs-lookup"><span data-stu-id="3685c-116">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="3685c-117">Möjliga värden kan till exempel vara ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, byte och String.</span><span class="sxs-lookup"><span data-stu-id="3685c-117">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="3685c-118">**Ny rad**</span><span class="sxs-lookup"><span data-stu-id="3685c-118">**NewLine**</span></span><br><span data-ttu-id="3685c-119">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="3685c-119">Data type: SwitchParameter</span></span>|<span data-ttu-id="3685c-120">Implementera den här parametern så att rad matnings tecken stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="3685c-120">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="3685c-121">**Kortnamn**</span><span class="sxs-lookup"><span data-stu-id="3685c-121">**ShortName**</span></span><br><span data-ttu-id="3685c-122">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="3685c-122">Data type: SwitchParameter</span></span>|<span data-ttu-id="3685c-123">Implementera den här parametern så att korta namn stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="3685c-123">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="3685c-124">**Bredd**</span><span class="sxs-lookup"><span data-stu-id="3685c-124">**Width**</span></span><br><span data-ttu-id="3685c-125">Datatyp: Int32</span><span class="sxs-lookup"><span data-stu-id="3685c-125">Data type: Int32</span></span>|<span data-ttu-id="3685c-126">Implementera den här parametern så att användaren kan ange bredden på utmatnings enheten.</span><span class="sxs-lookup"><span data-stu-id="3685c-126">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="3685c-127">**Flytta**</span><span class="sxs-lookup"><span data-stu-id="3685c-127">**Wrap**</span></span><br><span data-ttu-id="3685c-128">Datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="3685c-128">Data type: SwitchParameter</span></span>|<span data-ttu-id="3685c-129">Implementera den här parametern så att figur sättningen stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="3685c-129">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="3685c-130">Se även</span><span class="sxs-lookup"><span data-stu-id="3685c-130">See Also</span></span>

[<span data-ttu-id="3685c-131">Cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="3685c-131">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="3685c-132">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="3685c-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="3685c-133">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3685c-133">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
