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
# <a name="sendconfiguration-method"></a><span data-ttu-id="9a3be-103">SendConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="9a3be-103">SendConfiguration method</span></span>

<span data-ttu-id="9a3be-104">Skickar konfigurations dokumentet till den hanterade noden och sparar det som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="9a3be-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a3be-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9a3be-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9a3be-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9a3be-106">Parameters</span></span>

<span data-ttu-id="9a3be-107">*ConfigurationData* \[i\] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="9a3be-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9a3be-108">*tvinga* \[i\] **Sant** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="9a3be-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9a3be-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="9a3be-109">Return value</span></span>

<span data-ttu-id="9a3be-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="9a3be-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a3be-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="9a3be-111">Remarks</span></span>

<span data-ttu-id="9a3be-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="9a3be-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9a3be-113">Krav</span><span class="sxs-lookup"><span data-stu-id="9a3be-113">Requirements</span></span>

<span data-ttu-id="9a3be-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="9a3be-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9a3be-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9a3be-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9a3be-116">Se också</span><span class="sxs-lookup"><span data-stu-id="9a3be-116">See also</span></span>

[<span data-ttu-id="9a3be-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9a3be-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
