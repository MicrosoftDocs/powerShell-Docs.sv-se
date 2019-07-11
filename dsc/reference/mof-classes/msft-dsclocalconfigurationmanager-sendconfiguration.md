---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfiguration-metoden
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734324"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="d1c38-103">SendConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="d1c38-103">SendConfiguration method</span></span>

<span data-ttu-id="d1c38-104">Skickar konfigurationsdokumentet till hanterad nod och sparar den som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="d1c38-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1c38-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1c38-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d1c38-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d1c38-106">Parameters</span></span>

<span data-ttu-id="d1c38-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d1c38-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d1c38-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="d1c38-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d1c38-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="d1c38-109">Return value</span></span>

<span data-ttu-id="d1c38-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="d1c38-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1c38-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d1c38-111">Remarks</span></span>

<span data-ttu-id="d1c38-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="d1c38-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1c38-113">Krav</span><span class="sxs-lookup"><span data-stu-id="d1c38-113">Requirements</span></span>

<span data-ttu-id="d1c38-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d1c38-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d1c38-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1c38-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d1c38-116">Se även</span><span class="sxs-lookup"><span data-stu-id="d1c38-116">See also</span></span>

[<span data-ttu-id="d1c38-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d1c38-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
