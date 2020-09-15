---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfiguration-metoden
ms.openlocfilehash: afd6e8d7acc969df16fad1d0ba15c9fe0b1a26fd
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463949"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="3ba54-103">SendConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="3ba54-103">SendConfiguration method</span></span>

<span data-ttu-id="3ba54-104">Skickar konfigurations dokumentet till den hanterade noden och sparar det som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="3ba54-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ba54-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ba54-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="3ba54-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3ba54-106">Parameters</span></span>

<span data-ttu-id="3ba54-107">**ConfigurationData** \[ i \] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3ba54-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="3ba54-108">**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="3ba54-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ba54-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="3ba54-109">Return value</span></span>

<span data-ttu-id="3ba54-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="3ba54-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ba54-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="3ba54-111">Remarks</span></span>

<span data-ttu-id="3ba54-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="3ba54-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ba54-113">Krav</span><span class="sxs-lookup"><span data-stu-id="3ba54-113">Requirements</span></span>

<span data-ttu-id="3ba54-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="3ba54-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3ba54-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ba54-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3ba54-116">Se även</span><span class="sxs-lookup"><span data-stu-id="3ba54-116">See also</span></span>

[<span data-ttu-id="3ba54-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3ba54-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
