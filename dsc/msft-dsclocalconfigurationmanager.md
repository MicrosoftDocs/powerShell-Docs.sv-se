---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: MSFT_DSCLocalConfigurationManager class
ms.openlocfilehash: b2d2ce000988f2c10ab04c4ba5a4650bd3c75ec7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="79507-103">MSFT_DSCLocalConfigurationManager class</span><span class="sxs-lookup"><span data-stu-id="79507-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="79507-104">Den lokala Configuration Manager (MGM) som styr tillstånd konfigurationsfiler och använder Configuration Agent för att tillämpa konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="79507-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="79507-105">Följande syntax är förenklad från kod Managed Object Format (MOF) och innehåller alla ärvda egenskaper.</span><span class="sxs-lookup"><span data-stu-id="79507-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="79507-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="79507-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="79507-107">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="79507-107">Members</span></span>
-------

<span data-ttu-id="79507-108">Den **MSFT_DSCLocalConfigurationManager** klassen har följande medlemmar:</span><span class="sxs-lookup"><span data-stu-id="79507-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="79507-109">[Metoder] []</span><span class="sxs-lookup"><span data-stu-id="79507-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="79507-110">Metoder</span><span class="sxs-lookup"><span data-stu-id="79507-110">Methods</span></span>

<span data-ttu-id="79507-111">Den **MSFT_DSCLocalConfigurationManager** klassen har dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="79507-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="79507-112">Metod</span><span class="sxs-lookup"><span data-stu-id="79507-112">Method</span></span> |<span data-ttu-id="79507-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="79507-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="79507-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="79507-115">Använder Configuration Agent för att använda den konfiguration som är i vänteläge.</span><span class="sxs-lookup"><span data-stu-id="79507-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>| 
| [<span data-ttu-id="79507-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="79507-117">Inaktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="79507-117">Disables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="79507-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="79507-119">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="79507-119">Enables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="79507-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="79507-121">Skickar konfiguration dokumentet till hanterade noder och använder den **hämta** metod för att tillämpa konfigurationen Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="79507-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="79507-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="79507-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="79507-123">Hämtar Configuration Agent utdata som är relaterade till ett visst jobb.</span><span class="sxs-lookup"><span data-stu-id="79507-123">Gets the Configuration Agent output relating to a specific job.</span></span>| 
| [<span data-ttu-id="79507-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="79507-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="79507-125">Hämta statushistorik konfiguration.</span><span class="sxs-lookup"><span data-stu-id="79507-125">Get the configuration status history.</span></span>| 
| [<span data-ttu-id="79507-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="79507-127">Hämtar MGM inställningarna som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="79507-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>| 
| [<span data-ttu-id="79507-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="79507-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="79507-129">Startar en konsekvenskontroll.</span><span class="sxs-lookup"><span data-stu-id="79507-129">Starts the consistency check.</span></span>| 
| [<span data-ttu-id="79507-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="79507-131">Tar bort konfigurationsfilerna.</span><span class="sxs-lookup"><span data-stu-id="79507-131">Removes the configuration files.</span></span>| 
| [<span data-ttu-id="79507-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="79507-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="79507-133">Direkt anropar den **hämta** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="79507-133">Directly calls the **Get** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="79507-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="79507-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="79507-135">Direkt anropar den **ange** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="79507-135">Directly calls the **Set** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="79507-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="79507-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="79507-137">Direkt anropar den **Test** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="79507-137">Directly calls the **Test** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="79507-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="79507-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="79507-139">Samlar tillbaka till en tidigare konfiguration.</span><span class="sxs-lookup"><span data-stu-id="79507-139">Rolls back to a previous configuration.</span></span>| 
| [<span data-ttu-id="79507-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="79507-141">Skickar konfiguration dokumentet till noden hanterade och sparar den som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="79507-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>| 
| [<span data-ttu-id="79507-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="79507-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="79507-143">Skickar konfiguration dokumentet till noden hanterade används Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="79507-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="79507-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="79507-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="79507-145">Skicka konfiguration dokumentet till hanterade noder och börja använda Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="79507-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="79507-146">Använd GetConfigurationResultOutput för att hämta resultatet utdata.</span><span class="sxs-lookup"><span data-stu-id="79507-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>| 
| [<span data-ttu-id="79507-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="79507-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="79507-148">Anger MGM inställningarna som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="79507-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>| 
| [<span data-ttu-id="79507-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="79507-150">Stoppar den konfiguration som pågår.</span><span class="sxs-lookup"><span data-stu-id="79507-150">Stops the configuration that is in progress.</span></span>| 
| [<span data-ttu-id="79507-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="79507-152">Skickar konfiguration dokumentet till hanterade noder och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="79507-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>| 



 

## <a name="requirements"></a><span data-ttu-id="79507-153">Krav</span><span class="sxs-lookup"><span data-stu-id="79507-153">Requirements</span></span>
------------
><span data-ttu-id="79507-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="79507-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="79507-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="79507-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>



 

 



