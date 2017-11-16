---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ApplyConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b7e32-103">ApplyConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b7e32-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b7e32-104">Använder Configuration Agent för att använda den konfiguration som är i vänteläge.</span><span class="sxs-lookup"><span data-stu-id="b7e32-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="b7e32-105">Om det finns ingen konfiguration väntande, återställer den här metoden den aktuella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b7e32-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="b7e32-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b7e32-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="b7e32-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b7e32-107">Parameters</span></span>
----------

<span data-ttu-id="b7e32-108">*Tvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="b7e32-108">*force* \[in\]</span></span>  
<span data-ttu-id="b7e32-109">Om det här är **SANT**, den aktuella konfigurationen används igen, även om det finns en konfiguration väntande.</span><span class="sxs-lookup"><span data-stu-id="b7e32-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="b7e32-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b7e32-110">Return value</span></span>
------------

<span data-ttu-id="b7e32-111">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="b7e32-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7e32-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b7e32-112">Remarks</span></span>

<span data-ttu-id="b7e32-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b7e32-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7e32-114">Krav</span><span class="sxs-lookup"><span data-stu-id="b7e32-114">Requirements</span></span>
------------
><span data-ttu-id="b7e32-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b7e32-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b7e32-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b7e32-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b7e32-117">Se även</span><span class="sxs-lookup"><span data-stu-id="b7e32-117">See also</span></span>


[<span data-ttu-id="b7e32-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b7e32-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



