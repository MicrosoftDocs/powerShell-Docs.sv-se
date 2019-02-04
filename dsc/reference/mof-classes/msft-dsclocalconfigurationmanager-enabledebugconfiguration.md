---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: EnableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684810"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="37674-103">EnableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="37674-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="37674-104">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="37674-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="37674-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="37674-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="37674-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="37674-106">Parameters</span></span>

<span data-ttu-id="37674-107">*BreakAll* \[i\] anger en brytpunkt på varje rad i resurs-skriptet.</span><span class="sxs-lookup"><span data-stu-id="37674-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="37674-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="37674-108">Return value</span></span>

<span data-ttu-id="37674-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="37674-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="37674-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="37674-110">Remarks</span></span>

<span data-ttu-id="37674-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="37674-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="37674-112">Krav</span><span class="sxs-lookup"><span data-stu-id="37674-112">Requirements</span></span>

<span data-ttu-id="37674-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="37674-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="37674-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="37674-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="37674-115">Se även</span><span class="sxs-lookup"><span data-stu-id="37674-115">See also</span></span>

[<span data-ttu-id="37674-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="37674-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)