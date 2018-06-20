---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219886"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a06cc-103">RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="a06cc-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a06cc-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="a06cc-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="a06cc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a06cc-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="a06cc-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a06cc-106">Parameters</span></span>
----------

<span data-ttu-id="a06cc-107">*configurationNumber* \[i\] anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a06cc-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a06cc-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a06cc-108">Return value</span></span>
------------

<span data-ttu-id="a06cc-109">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="a06cc-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a06cc-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a06cc-110">Remarks</span></span>

<span data-ttu-id="a06cc-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a06cc-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a06cc-112">Krav</span><span class="sxs-lookup"><span data-stu-id="a06cc-112">Requirements</span></span>
------------
><span data-ttu-id="a06cc-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a06cc-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a06cc-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a06cc-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a06cc-115">Se även</span><span class="sxs-lookup"><span data-stu-id="a06cc-115">See also</span></span>


[<span data-ttu-id="a06cc-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a06cc-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)