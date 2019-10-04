---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfiguration-metoden
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942715"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="b29a3-103">GetConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="b29a3-103">GetConfiguration method</span></span>

<span data-ttu-id="b29a3-104">Skickar konfigurations dokumentet till den hanterade noden och använder **Get** -metoden för konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b29a3-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="b29a3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b29a3-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="b29a3-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b29a3-106">Parameters</span></span>

<span data-ttu-id="b29a3-107">*configurationData* \[in @ no__t-2 anger de konfigurations data som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="b29a3-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="b29a3-108">*konfigurationer* \[out @ no__t-2 vid retur, innehåller en inbäddad instans av konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="b29a3-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="b29a3-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b29a3-109">Return value</span></span>

<span data-ttu-id="b29a3-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="b29a3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b29a3-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b29a3-111">Remarks</span></span>

<span data-ttu-id="b29a3-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b29a3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b29a3-113">Krav</span><span class="sxs-lookup"><span data-stu-id="b29a3-113">Requirements</span></span>

<span data-ttu-id="b29a3-114">**-** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="b29a3-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b29a3-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b29a3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b29a3-116">Se även</span><span class="sxs-lookup"><span data-stu-id="b29a3-116">See also</span></span>

[<span data-ttu-id="b29a3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b29a3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
