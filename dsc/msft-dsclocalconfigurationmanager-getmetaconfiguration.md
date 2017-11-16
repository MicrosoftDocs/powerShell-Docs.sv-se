---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetMetaConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="885cc-103">GetMetaConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="885cc-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="885cc-104">Hämtar den lokala Configuration Manager-inställningar som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="885cc-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="885cc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="885cc-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="885cc-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="885cc-106">Parameters</span></span>
----------

<span data-ttu-id="885cc-107">*Metakonfigurationen* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="885cc-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="885cc-108">På RETUR, innehåller en inbäddad instans av den **MSFT_DSCMetaConfiguration** klass som definierar inställningar.</span><span class="sxs-lookup"><span data-stu-id="885cc-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="885cc-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="885cc-109">Return value</span></span>
------------

<span data-ttu-id="885cc-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="885cc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="885cc-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="885cc-111">Remarks</span></span>

<span data-ttu-id="885cc-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="885cc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="885cc-113">Krav</span><span class="sxs-lookup"><span data-stu-id="885cc-113">Requirements</span></span>
------------
><span data-ttu-id="885cc-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="885cc-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="885cc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="885cc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="885cc-116">Se även</span><span class="sxs-lookup"><span data-stu-id="885cc-116">See also</span></span>


[<span data-ttu-id="885cc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="885cc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



