---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: RollBack-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="21f4c-103">RollBack-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="21f4c-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="21f4c-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="21f4c-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="21f4c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="21f4c-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="21f4c-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="21f4c-106">Parameters</span></span>
----------

<span data-ttu-id="21f4c-107">*configurationNumber* \[i\]</span><span class="sxs-lookup"><span data-stu-id="21f4c-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="21f4c-108">Anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="21f4c-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="21f4c-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="21f4c-109">Return value</span></span>
------------

<span data-ttu-id="21f4c-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="21f4c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="21f4c-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="21f4c-111">Remarks</span></span>

<span data-ttu-id="21f4c-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="21f4c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="21f4c-113">Krav</span><span class="sxs-lookup"><span data-stu-id="21f4c-113">Requirements</span></span>
------------
><span data-ttu-id="21f4c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="21f4c-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="21f4c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="21f4c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="21f4c-116">Se även</span><span class="sxs-lookup"><span data-stu-id="21f4c-116">See also</span></span>


[<span data-ttu-id="21f4c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="21f4c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



