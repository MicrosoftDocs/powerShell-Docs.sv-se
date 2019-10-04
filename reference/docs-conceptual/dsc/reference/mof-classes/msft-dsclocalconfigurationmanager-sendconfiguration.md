---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfiguration-metoden
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941553"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="a74b9-103">SendConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="a74b9-103">SendConfiguration method</span></span>

<span data-ttu-id="a74b9-104">Skickar konfigurations dokumentet till den hanterade noden och sparar det som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="a74b9-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="a74b9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a74b9-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="a74b9-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a74b9-106">Parameters</span></span>

<span data-ttu-id="a74b9-107">*ConfigurationData* \[in @ no__t-2 miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a74b9-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="a74b9-108">*tvinga* \[in @ no__t-2 **True** så att konfigurationen stoppas.</span><span class="sxs-lookup"><span data-stu-id="a74b9-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="a74b9-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a74b9-109">Return value</span></span>

<span data-ttu-id="a74b9-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="a74b9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a74b9-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a74b9-111">Remarks</span></span>

<span data-ttu-id="a74b9-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a74b9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a74b9-113">Krav</span><span class="sxs-lookup"><span data-stu-id="a74b9-113">Requirements</span></span>

<span data-ttu-id="a74b9-114">**-** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="a74b9-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a74b9-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a74b9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a74b9-116">Se även</span><span class="sxs-lookup"><span data-stu-id="a74b9-116">See also</span></span>

[<span data-ttu-id="a74b9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a74b9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
