---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfiguration-metoden
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942715"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="0d2a8-103">GetConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="0d2a8-103">GetConfiguration method</span></span>

<span data-ttu-id="0d2a8-104">Skickar konfigurations dokumentet till den hanterade noden och använder **Get** -metoden för konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0d2a8-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d2a8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d2a8-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="0d2a8-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="0d2a8-106">Parameters</span></span>

<span data-ttu-id="0d2a8-107">*configurationData* \[i\] anger de konfigurations data som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="0d2a8-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="0d2a8-108">*konfigurationer* \[ut\] vid retur innehåller en inbäddad instans av konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="0d2a8-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d2a8-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="0d2a8-109">Return value</span></span>

<span data-ttu-id="0d2a8-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="0d2a8-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d2a8-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0d2a8-111">Remarks</span></span>

<span data-ttu-id="0d2a8-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="0d2a8-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d2a8-113">Krav</span><span class="sxs-lookup"><span data-stu-id="0d2a8-113">Requirements</span></span>

<span data-ttu-id="0d2a8-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="0d2a8-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0d2a8-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d2a8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0d2a8-116">Se även</span><span class="sxs-lookup"><span data-stu-id="0d2a8-116">See also</span></span>

[<span data-ttu-id="0d2a8-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0d2a8-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
