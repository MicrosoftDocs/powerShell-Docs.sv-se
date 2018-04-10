---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: c0a801c4037921e700e447d1434e246df0a63a4f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ba156-103">RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="ba156-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ba156-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="ba156-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="ba156-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ba156-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="ba156-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ba156-106">Parameters</span></span>
----------

<span data-ttu-id="ba156-107">*configurationNumber* \[i\] anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ba156-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="ba156-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ba156-108">Return value</span></span>
------------

<span data-ttu-id="ba156-109">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="ba156-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba156-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ba156-110">Remarks</span></span>

<span data-ttu-id="ba156-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ba156-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba156-112">Krav</span><span class="sxs-lookup"><span data-stu-id="ba156-112">Requirements</span></span>
------------
><span data-ttu-id="ba156-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ba156-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ba156-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba156-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ba156-115">Se även</span><span class="sxs-lookup"><span data-stu-id="ba156-115">See also</span></span>


[<span data-ttu-id="ba156-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ba156-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)