---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfigurationApply-metoden
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942603"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="230bf-103">SendConfigurationApply-metoden</span><span class="sxs-lookup"><span data-stu-id="230bf-103">SendConfigurationApply method</span></span>

<span data-ttu-id="230bf-104">Skickar konfigurations dokumentet till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="230bf-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="230bf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="230bf-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="230bf-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="230bf-106">Parameters</span></span>

<span data-ttu-id="230bf-107">*ConfigurationData* \[i\] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="230bf-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="230bf-108">*tvinga* \[i\] **Sant** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="230bf-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="230bf-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="230bf-109">Return value</span></span>

<span data-ttu-id="230bf-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="230bf-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="230bf-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="230bf-111">Remarks</span></span>

<span data-ttu-id="230bf-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="230bf-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="230bf-113">Krav</span><span class="sxs-lookup"><span data-stu-id="230bf-113">Requirements</span></span>

<span data-ttu-id="230bf-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="230bf-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="230bf-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="230bf-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="230bf-116">Se även</span><span class="sxs-lookup"><span data-stu-id="230bf-116">See also</span></span>

[<span data-ttu-id="230bf-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="230bf-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
