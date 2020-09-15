---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfigurationApply-metoden
ms.openlocfilehash: 9b684790e5a7d6c7bdf074caca6040e13807f1ca
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464323"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="ebd59-103">SendConfigurationApply-metoden</span><span class="sxs-lookup"><span data-stu-id="ebd59-103">SendConfigurationApply method</span></span>

<span data-ttu-id="ebd59-104">Skickar konfigurations dokumentet till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ebd59-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebd59-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ebd59-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="ebd59-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ebd59-106">Parameters</span></span>

<span data-ttu-id="ebd59-107">**ConfigurationData** \[ i \] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ebd59-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ebd59-108">**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="ebd59-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ebd59-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ebd59-109">Return value</span></span>

<span data-ttu-id="ebd59-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="ebd59-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ebd59-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ebd59-111">Remarks</span></span>

<span data-ttu-id="ebd59-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ebd59-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ebd59-113">Krav</span><span class="sxs-lookup"><span data-stu-id="ebd59-113">Requirements</span></span>

<span data-ttu-id="ebd59-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="ebd59-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ebd59-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ebd59-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ebd59-116">Se även</span><span class="sxs-lookup"><span data-stu-id="ebd59-116">See also</span></span>

[<span data-ttu-id="ebd59-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ebd59-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
