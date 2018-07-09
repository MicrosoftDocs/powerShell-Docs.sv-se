---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: TestConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893934"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="07d61-103">TestConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="07d61-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="07d61-104">Skickar konfigurationsdokumentet till hanterad nod och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="07d61-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="07d61-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="07d61-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="07d61-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="07d61-106">Parameters</span></span>

<span data-ttu-id="07d61-107">*configurationData* \[i\] miljödata för confuguration.</span><span class="sxs-lookup"><span data-stu-id="07d61-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="07d61-108">*InDesiredState* \[ut\] på RETUR, anger du om hanterad nod är i tillståndet anges i konfigurationsdokumentet.</span><span class="sxs-lookup"><span data-stu-id="07d61-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="07d61-109">*ResourcesInDesiredState* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_ResourceInDesiredState** klass som anger resurser som finns i önskat läge.</span><span class="sxs-lookup"><span data-stu-id="07d61-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="07d61-110">*ResourcesNotInDesiredState* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_ResourceNotInDesiredState** klass som anger resurser som inte ingår i önskat läge.</span><span class="sxs-lookup"><span data-stu-id="07d61-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="07d61-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="07d61-111">Return value</span></span>

<span data-ttu-id="07d61-112">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="07d61-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="07d61-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="07d61-113">Remarks</span></span>

<span data-ttu-id="07d61-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="07d61-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="07d61-115">Krav</span><span class="sxs-lookup"><span data-stu-id="07d61-115">Requirements</span></span>

<span data-ttu-id="07d61-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="07d61-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="07d61-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="07d61-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="07d61-118">Se även</span><span class="sxs-lookup"><span data-stu-id="07d61-118">See also</span></span>

[<span data-ttu-id="07d61-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="07d61-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)