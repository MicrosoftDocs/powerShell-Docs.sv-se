---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendMetaConfigurationApply-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1fdf3-103">SendMetaConfigurationApply-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1fdf3-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1fdf3-104">Anger Local Configuration Manager-inställningar som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="1fdf3-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="1fdf3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1fdf3-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="1fdf3-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="1fdf3-106">Parameters</span></span>
----------

<span data-ttu-id="1fdf3-107">*ConfigurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="1fdf3-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="1fdf3-108">Miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="1fdf3-108">The environment data for the configuration.</span></span>

<span data-ttu-id="1fdf3-109">*Tvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="1fdf3-109">*force* \[in\]</span></span>  
<span data-ttu-id="1fdf3-110">**SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="1fdf3-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="1fdf3-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="1fdf3-111">Return value</span></span>
------------

<span data-ttu-id="1fdf3-112">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="1fdf3-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fdf3-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="1fdf3-113">Remarks</span></span>

<span data-ttu-id="1fdf3-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="1fdf3-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1fdf3-115">Krav</span><span class="sxs-lookup"><span data-stu-id="1fdf3-115">Requirements</span></span>
------------
><span data-ttu-id="1fdf3-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1fdf3-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1fdf3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1fdf3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1fdf3-118">Se även</span><span class="sxs-lookup"><span data-stu-id="1fdf3-118">See also</span></span>


[<span data-ttu-id="1fdf3-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1fdf3-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



