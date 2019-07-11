---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: StopConfiguration-metoden
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726999"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="54dcf-103">StopConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="54dcf-103">StopConfiguration method</span></span>

<span data-ttu-id="54dcf-104">Stoppar konfigurationsändring som håller på att skapas.</span><span class="sxs-lookup"><span data-stu-id="54dcf-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="54dcf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="54dcf-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="54dcf-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="54dcf-106">Parameters</span></span>

<span data-ttu-id="54dcf-107">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="54dcf-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="54dcf-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="54dcf-108">Return value</span></span>

<span data-ttu-id="54dcf-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="54dcf-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="54dcf-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="54dcf-110">Remarks</span></span>

<span data-ttu-id="54dcf-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="54dcf-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="54dcf-112">Krav</span><span class="sxs-lookup"><span data-stu-id="54dcf-112">Requirements</span></span>

<span data-ttu-id="54dcf-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="54dcf-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="54dcf-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="54dcf-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="54dcf-115">Se även</span><span class="sxs-lookup"><span data-stu-id="54dcf-115">See also</span></span>

[<span data-ttu-id="54dcf-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="54dcf-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
