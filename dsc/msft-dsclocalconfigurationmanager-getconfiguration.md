---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 46eec896df643996bea5f2c371a9294034caae6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2eeaf-103">GetConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="2eeaf-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2eeaf-104">Skickar konfiguration dokumentet till hanterade noder och använder den **hämta** metod för att tillämpa konfigurationen Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="2eeaf-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="2eeaf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2eeaf-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="2eeaf-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="2eeaf-106">Parameters</span></span>
----------

<span data-ttu-id="2eeaf-107">*configurationData* \[i\] anger konfigurationsdata för att skicka.</span><span class="sxs-lookup"><span data-stu-id="2eeaf-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="2eeaf-108">*konfigurationer* \[ut\] på RETUR, innehåller en inbäddad instans av konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="2eeaf-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="2eeaf-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="2eeaf-109">Return value</span></span>
------------

<span data-ttu-id="2eeaf-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="2eeaf-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2eeaf-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2eeaf-111">Remarks</span></span>

<span data-ttu-id="2eeaf-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="2eeaf-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2eeaf-113">Krav</span><span class="sxs-lookup"><span data-stu-id="2eeaf-113">Requirements</span></span>
------------
><span data-ttu-id="2eeaf-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2eeaf-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2eeaf-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2eeaf-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2eeaf-116">Se även</span><span class="sxs-lookup"><span data-stu-id="2eeaf-116">See also</span></span>


[<span data-ttu-id="2eeaf-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2eeaf-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)