---
title: Antal parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359252"
---
# <a name="quantity-parameters"></a><span data-ttu-id="512db-102">Kvantitetsparametrar</span><span class="sxs-lookup"><span data-stu-id="512db-102">Quantity Parameters</span></span>

<span data-ttu-id="512db-103">I följande tabell visas rekommenderade namn och funktioner för mängd parametrar.</span><span class="sxs-lookup"><span data-stu-id="512db-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="512db-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="512db-104">Parameter</span></span>|<span data-ttu-id="512db-105">Funktioner</span><span class="sxs-lookup"><span data-stu-id="512db-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="512db-106">**Alla**</span><span class="sxs-lookup"><span data-stu-id="512db-106">**All**</span></span><br><span data-ttu-id="512db-107">Datatyp: boolesk</span><span class="sxs-lookup"><span data-stu-id="512db-107">Data type: Boolean</span></span>|<span data-ttu-id="512db-108">Implementera den här parametern så att `true` anger att alla resurser ska åtgärdas på i stället för en standard del av resurserna.</span><span class="sxs-lookup"><span data-stu-id="512db-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="512db-109">Implementera den här parametern så att `false` anger en delmängd av resurserna.</span><span class="sxs-lookup"><span data-stu-id="512db-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="512db-110">**Storlek**</span><span class="sxs-lookup"><span data-stu-id="512db-110">**Allocation**</span></span><br><span data-ttu-id="512db-111">Datatyp: Int32</span><span class="sxs-lookup"><span data-stu-id="512db-111">Data type: Int32</span></span>|<span data-ttu-id="512db-112">Implementera den här parametern så att användaren kan ange antalet objekt som ska allokeras.</span><span class="sxs-lookup"><span data-stu-id="512db-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="512db-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="512db-113">**BlockCount**</span></span><br><span data-ttu-id="512db-114">Datatyp: Int64</span><span class="sxs-lookup"><span data-stu-id="512db-114">Data type: Int64</span></span>|<span data-ttu-id="512db-115">Implementera den här parametern så att användaren kan ange block antalet.</span><span class="sxs-lookup"><span data-stu-id="512db-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="512db-116">**Reparationer**</span><span class="sxs-lookup"><span data-stu-id="512db-116">**Count**</span></span><br><span data-ttu-id="512db-117">Datatyp: Int64</span><span class="sxs-lookup"><span data-stu-id="512db-117">Data type: Int64</span></span>|<span data-ttu-id="512db-118">Implementera den här parametern så att användaren kan ange antalet.</span><span class="sxs-lookup"><span data-stu-id="512db-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="512db-119">**Omfång**</span><span class="sxs-lookup"><span data-stu-id="512db-119">**Scope**</span></span><br><span data-ttu-id="512db-120">Datatyp: nyckelord</span><span class="sxs-lookup"><span data-stu-id="512db-120">Data type: Keyword</span></span>|<span data-ttu-id="512db-121">Implementera den här parametern så att användaren kan ange det omfång som ska användas.</span><span class="sxs-lookup"><span data-stu-id="512db-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="512db-122">Se även</span><span class="sxs-lookup"><span data-stu-id="512db-122">See Also</span></span>

[<span data-ttu-id="512db-123">Cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="512db-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="512db-124">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="512db-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="512db-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="512db-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
