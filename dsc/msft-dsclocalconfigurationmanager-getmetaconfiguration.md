---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetMetaConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b7690-103">GetMetaConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b7690-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b7690-104">Hämtar den lokala Configuration Manager-inställningar som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="b7690-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="b7690-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b7690-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="b7690-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7690-106">Parameters</span></span>
----------

<span data-ttu-id="b7690-107">*Metakonfigurationen* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="b7690-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="b7690-108">På RETUR, innehåller en inbäddad instans av den **MSFT_DSCMetaConfiguration** klass som definierar inställningar.</span><span class="sxs-lookup"><span data-stu-id="b7690-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="b7690-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7690-109">Return value</span></span>
------------

<span data-ttu-id="b7690-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="b7690-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7690-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b7690-111">Remarks</span></span>

<span data-ttu-id="b7690-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b7690-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7690-113">Krav</span><span class="sxs-lookup"><span data-stu-id="b7690-113">Requirements</span></span>
------------
><span data-ttu-id="b7690-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b7690-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b7690-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b7690-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b7690-116">Se även</span><span class="sxs-lookup"><span data-stu-id="b7690-116">See also</span></span>


[<span data-ttu-id="b7690-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b7690-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



