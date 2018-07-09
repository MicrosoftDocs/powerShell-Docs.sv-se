---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: EnableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892407"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d3b71-103">EnableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="d3b71-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d3b71-104">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d3b71-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3b71-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d3b71-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="d3b71-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d3b71-106">Parameters</span></span>

<span data-ttu-id="d3b71-107">*BreakAll* \[i\] anger en brytpunkt på varje rad i resurs-skriptet.</span><span class="sxs-lookup"><span data-stu-id="d3b71-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="d3b71-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="d3b71-108">Return value</span></span>

<span data-ttu-id="d3b71-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="d3b71-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d3b71-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d3b71-110">Remarks</span></span>

<span data-ttu-id="d3b71-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="d3b71-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d3b71-112">Krav</span><span class="sxs-lookup"><span data-stu-id="d3b71-112">Requirements</span></span>

<span data-ttu-id="d3b71-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d3b71-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d3b71-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d3b71-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d3b71-115">Se även</span><span class="sxs-lookup"><span data-stu-id="d3b71-115">See also</span></span>

[<span data-ttu-id="d3b71-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d3b71-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)