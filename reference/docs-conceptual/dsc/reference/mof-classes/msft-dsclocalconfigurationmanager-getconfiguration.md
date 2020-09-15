---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfiguration-metoden
ms.openlocfilehash: 989aeef4cd9aa5d55741b48c8565c657c4b6512c
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463830"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="4ae23-103">GetConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="4ae23-103">GetConfiguration method</span></span>

<span data-ttu-id="4ae23-104">Skickar konfigurations dokumentet till den hanterade noden och använder **Get** -metoden för konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4ae23-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ae23-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4ae23-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="4ae23-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="4ae23-106">Parameters</span></span>

<span data-ttu-id="4ae23-107">**configurationData** \[ i \] anger de konfigurations data som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="4ae23-107">**configurationData** \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="4ae23-108">**konfigurationer** \[ ut \] vid retur innehåller en inbäddad instans av konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="4ae23-108">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="4ae23-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="4ae23-109">Return value</span></span>

<span data-ttu-id="4ae23-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="4ae23-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ae23-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="4ae23-111">Remarks</span></span>

<span data-ttu-id="4ae23-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="4ae23-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4ae23-113">Krav</span><span class="sxs-lookup"><span data-stu-id="4ae23-113">Requirements</span></span>

<span data-ttu-id="4ae23-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="4ae23-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4ae23-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4ae23-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4ae23-116">Se även</span><span class="sxs-lookup"><span data-stu-id="4ae23-116">See also</span></span>

[<span data-ttu-id="4ae23-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4ae23-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
