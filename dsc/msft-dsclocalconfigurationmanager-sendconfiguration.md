---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892451"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e0191-103">SendConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="e0191-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e0191-104">Skickar konfigurationsdokumentet till hanterad nod och sparar den som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="e0191-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0191-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0191-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e0191-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e0191-106">Parameters</span></span>

<span data-ttu-id="e0191-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="e0191-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="e0191-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="e0191-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e0191-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="e0191-109">Return value</span></span>

<span data-ttu-id="e0191-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="e0191-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0191-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e0191-111">Remarks</span></span>

<span data-ttu-id="e0191-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="e0191-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0191-113">Krav</span><span class="sxs-lookup"><span data-stu-id="e0191-113">Requirements</span></span>

<span data-ttu-id="e0191-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e0191-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e0191-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0191-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e0191-116">Se även</span><span class="sxs-lookup"><span data-stu-id="e0191-116">See also</span></span>

[<span data-ttu-id="e0191-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e0191-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)