---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfiguration-metoden
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941553"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="fcf27-103">SendConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="fcf27-103">SendConfiguration method</span></span>

<span data-ttu-id="fcf27-104">Skickar konfigurations dokumentet till den hanterade noden och sparar det som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="fcf27-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="fcf27-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fcf27-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="fcf27-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="fcf27-106">Parameters</span></span>

<span data-ttu-id="fcf27-107">*ConfigurationData* \[i\] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fcf27-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="fcf27-108">*tvinga* \[i\] **uppfyllelse** att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="fcf27-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="fcf27-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="fcf27-109">Return value</span></span>

<span data-ttu-id="fcf27-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="fcf27-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcf27-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="fcf27-111">Remarks</span></span>

<span data-ttu-id="fcf27-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="fcf27-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fcf27-113">Krav</span><span class="sxs-lookup"><span data-stu-id="fcf27-113">Requirements</span></span>

<span data-ttu-id="fcf27-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="fcf27-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fcf27-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fcf27-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fcf27-116">Se även</span><span class="sxs-lookup"><span data-stu-id="fcf27-116">See also</span></span>

[<span data-ttu-id="fcf27-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fcf27-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
