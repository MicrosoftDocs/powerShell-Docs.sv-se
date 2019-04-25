---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: EnableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078778"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="96809-103">EnableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="96809-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="96809-104">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="96809-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="96809-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="96809-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="96809-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="96809-106">Parameters</span></span>

<span data-ttu-id="96809-107">*BreakAll* \[i\] anger en brytpunkt på varje rad i resurs-skriptet.</span><span class="sxs-lookup"><span data-stu-id="96809-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="96809-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="96809-108">Return value</span></span>

<span data-ttu-id="96809-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="96809-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="96809-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="96809-110">Remarks</span></span>

<span data-ttu-id="96809-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="96809-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="96809-112">Krav</span><span class="sxs-lookup"><span data-stu-id="96809-112">Requirements</span></span>

<span data-ttu-id="96809-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="96809-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="96809-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="96809-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="96809-115">Se även</span><span class="sxs-lookup"><span data-stu-id="96809-115">See also</span></span>

[<span data-ttu-id="96809-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="96809-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)