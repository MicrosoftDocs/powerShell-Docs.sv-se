---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404888"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0ca0b-103">GetConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="0ca0b-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0ca0b-104">Skickar konfigurationsdokumentet till hanterad nod och använder den **hämta** metod för Configuration agenten att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0ca0b-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ca0b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ca0b-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="0ca0b-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="0ca0b-106">Parameters</span></span>

<span data-ttu-id="0ca0b-107">*configurationData* \[i\] anger att skicka konfigurationsdata.</span><span class="sxs-lookup"><span data-stu-id="0ca0b-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="0ca0b-108">*konfigurationer* \[ut\] på return innehåller en inbäddad förekomst av konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="0ca0b-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0ca0b-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="0ca0b-109">Return value</span></span>

<span data-ttu-id="0ca0b-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="0ca0b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ca0b-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0ca0b-111">Remarks</span></span>

<span data-ttu-id="0ca0b-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="0ca0b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ca0b-113">Krav</span><span class="sxs-lookup"><span data-stu-id="0ca0b-113">Requirements</span></span>

<span data-ttu-id="0ca0b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0ca0b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0ca0b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0ca0b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0ca0b-116">Se även</span><span class="sxs-lookup"><span data-stu-id="0ca0b-116">See also</span></span>

[<span data-ttu-id="0ca0b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0ca0b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)