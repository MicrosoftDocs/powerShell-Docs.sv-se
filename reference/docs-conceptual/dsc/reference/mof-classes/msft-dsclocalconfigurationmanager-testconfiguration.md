---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: TestConfiguration-metoden
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942589"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="dba97-103">TestConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="dba97-103">TestConfiguration method</span></span>

<span data-ttu-id="dba97-104">Skickar konfigurations dokumentet till den hanterade noden och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="dba97-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="dba97-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dba97-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="dba97-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="dba97-106">Parameters</span></span>

<span data-ttu-id="dba97-107">*configurationData* \[i\] miljö data för confuguration.</span><span class="sxs-lookup"><span data-stu-id="dba97-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="dba97-108">*InDesiredState* \[ut\] vid retur anger om den hanterade noden är i det tillstånd som anges av konfigurations dokumentet.</span><span class="sxs-lookup"><span data-stu-id="dba97-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="dba97-109">*ResourcesInDesiredState* \[ut\] vid retur innehåller en inbäddad instans av **MSFT_ResourceInDesiredState** -klassen som anger resurser som är i önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="dba97-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="dba97-110">*ResourcesNotInDesiredState* \[ut\] vid retur innehåller en inbäddad instans av **MSFT_ResourceNotInDesiredState** -klassen som anger resurser som inte är i önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="dba97-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="dba97-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="dba97-111">Return value</span></span>

<span data-ttu-id="dba97-112">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="dba97-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dba97-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="dba97-113">Remarks</span></span>

<span data-ttu-id="dba97-114">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="dba97-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dba97-115">Krav</span><span class="sxs-lookup"><span data-stu-id="dba97-115">Requirements</span></span>

<span data-ttu-id="dba97-116">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="dba97-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="dba97-117">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dba97-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="dba97-118">Se även</span><span class="sxs-lookup"><span data-stu-id="dba97-118">See also</span></span>

[<span data-ttu-id="dba97-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dba97-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
