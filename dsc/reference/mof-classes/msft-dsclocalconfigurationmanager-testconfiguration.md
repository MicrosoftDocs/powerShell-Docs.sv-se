---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: TestConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078086"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="dfd27-103">TestConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="dfd27-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="dfd27-104">Skickar konfigurationsdokumentet till hanterad nod och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="dfd27-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="dfd27-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dfd27-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="dfd27-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="dfd27-106">Parameters</span></span>

<span data-ttu-id="dfd27-107">*configurationData* \[i\] miljödata för confuguration.</span><span class="sxs-lookup"><span data-stu-id="dfd27-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="dfd27-108">*InDesiredState* \[ut\] på RETUR, anger du om hanterad nod är i tillståndet anges i konfigurationsdokumentet.</span><span class="sxs-lookup"><span data-stu-id="dfd27-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="dfd27-109">*ResourcesInDesiredState* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_ResourceInDesiredState** klass som anger resurser som finns i önskat läge.</span><span class="sxs-lookup"><span data-stu-id="dfd27-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="dfd27-110">*ResourcesNotInDesiredState* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_ResourceNotInDesiredState** klass som anger resurser som inte ingår i önskat läge.</span><span class="sxs-lookup"><span data-stu-id="dfd27-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="dfd27-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="dfd27-111">Return value</span></span>

<span data-ttu-id="dfd27-112">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="dfd27-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dfd27-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="dfd27-113">Remarks</span></span>

<span data-ttu-id="dfd27-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="dfd27-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dfd27-115">Krav</span><span class="sxs-lookup"><span data-stu-id="dfd27-115">Requirements</span></span>

<span data-ttu-id="dfd27-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="dfd27-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="dfd27-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dfd27-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="dfd27-118">Se även</span><span class="sxs-lookup"><span data-stu-id="dfd27-118">See also</span></span>

[<span data-ttu-id="dfd27-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dfd27-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)