---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetMetaConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: ebf2b65f152c622ccf42e12545b0048a0b96d963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="84e36-103">GetMetaConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="84e36-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="84e36-104">Hämtar den lokala Configuration Manager-inställningar som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="84e36-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="84e36-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="84e36-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="84e36-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="84e36-106">Parameters</span></span>
----------

<span data-ttu-id="84e36-107">*Metakonfigurationen* \[ut\] på RETUR, innehåller en inbäddad instans av den **MSFT_DSCMetaConfiguration** klass som definierar inställningar.</span><span class="sxs-lookup"><span data-stu-id="84e36-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="84e36-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="84e36-108">Return value</span></span>
------------

<span data-ttu-id="84e36-109">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="84e36-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="84e36-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="84e36-110">Remarks</span></span>

<span data-ttu-id="84e36-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="84e36-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="84e36-112">Krav</span><span class="sxs-lookup"><span data-stu-id="84e36-112">Requirements</span></span>
------------
><span data-ttu-id="84e36-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="84e36-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="84e36-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="84e36-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="84e36-115">Se även</span><span class="sxs-lookup"><span data-stu-id="84e36-115">See also</span></span>


[<span data-ttu-id="84e36-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="84e36-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)