---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendMetaConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404781"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9b0dd-103">SendMetaConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="9b0dd-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9b0dd-104">Anger de Local Configuration Manager-inställningar som används för att styra agenten Configuration.</span><span class="sxs-lookup"><span data-stu-id="9b0dd-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b0dd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b0dd-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9b0dd-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9b0dd-106">Parameters</span></span>

<span data-ttu-id="9b0dd-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="9b0dd-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9b0dd-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="9b0dd-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9b0dd-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="9b0dd-109">Return value</span></span>

<span data-ttu-id="9b0dd-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="9b0dd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b0dd-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="9b0dd-111">Remarks</span></span>

<span data-ttu-id="9b0dd-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="9b0dd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b0dd-113">Krav</span><span class="sxs-lookup"><span data-stu-id="9b0dd-113">Requirements</span></span>

<span data-ttu-id="9b0dd-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9b0dd-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9b0dd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9b0dd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9b0dd-116">Se även</span><span class="sxs-lookup"><span data-stu-id="9b0dd-116">See also</span></span>

[<span data-ttu-id="9b0dd-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9b0dd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)