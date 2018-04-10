---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 598bd7490043975d9d965c12a7337fb3475b3ded
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d010a-103">MSFT_DSCLocalConfigurationManager-klass</span><span class="sxs-lookup"><span data-stu-id="d010a-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d010a-104">Den lokala Configuration Manager (MGM) som styr tillstånd konfigurationsfiler och använder Configuration Agent för att tillämpa konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="d010a-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="d010a-105">Följande syntax är förenklad från kod Managed Object Format (MOF) och innehåller alla ärvda egenskaper.</span><span class="sxs-lookup"><span data-stu-id="d010a-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="d010a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d010a-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="d010a-107">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="d010a-107">Members</span></span>
-------

<span data-ttu-id="d010a-108">Den **MSFT_DSCLocalConfigurationManager** klassen har följande medlemmar:</span><span class="sxs-lookup"><span data-stu-id="d010a-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="d010a-109">[Metoder] []</span><span class="sxs-lookup"><span data-stu-id="d010a-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="d010a-110">Metoder</span><span class="sxs-lookup"><span data-stu-id="d010a-110">Methods</span></span>

<span data-ttu-id="d010a-111">Den **MSFT_DSCLocalConfigurationManager** klassen har dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="d010a-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="d010a-112">Metod</span><span class="sxs-lookup"><span data-stu-id="d010a-112">Method</span></span> |<span data-ttu-id="d010a-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d010a-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="d010a-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="d010a-115">Använder Configuration Agent för att använda den konfiguration som är i vänteläge.</span><span class="sxs-lookup"><span data-stu-id="d010a-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="d010a-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="d010a-117">Inaktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d010a-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="d010a-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="d010a-119">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d010a-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="d010a-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="d010a-121">Skickar konfiguration dokumentet till hanterade noder och använder den **hämta** metod för att tillämpa konfigurationen Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="d010a-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="d010a-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="d010a-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="d010a-123">Hämtar Configuration Agent utdata som är relaterade till ett visst jobb.</span><span class="sxs-lookup"><span data-stu-id="d010a-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="d010a-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d010a-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="d010a-125">Hämta statushistorik konfiguration.</span><span class="sxs-lookup"><span data-stu-id="d010a-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="d010a-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="d010a-127">Hämtar MGM inställningarna som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="d010a-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="d010a-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="d010a-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="d010a-129">Startar en konsekvenskontroll.</span><span class="sxs-lookup"><span data-stu-id="d010a-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="d010a-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="d010a-131">Tar bort konfigurationsfilerna.</span><span class="sxs-lookup"><span data-stu-id="d010a-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="d010a-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="d010a-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="d010a-133">Direkt anropar den **hämta** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d010a-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="d010a-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="d010a-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="d010a-135">Direkt anropar den **ange** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d010a-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="d010a-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="d010a-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="d010a-137">Direkt anropar den **Test** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d010a-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="d010a-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="d010a-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="d010a-139">Samlar tillbaka till en tidigare konfiguration.</span><span class="sxs-lookup"><span data-stu-id="d010a-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="d010a-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="d010a-141">Skickar konfiguration dokumentet till noden hanterade och sparar den som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="d010a-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="d010a-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="d010a-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="d010a-143">Skickar konfiguration dokumentet till noden hanterade används Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d010a-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="d010a-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="d010a-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="d010a-145">Skicka konfiguration dokumentet till hanterade noder och börja använda Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d010a-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="d010a-146">Använd GetConfigurationResultOutput för att hämta resultatet utdata.</span><span class="sxs-lookup"><span data-stu-id="d010a-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="d010a-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="d010a-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="d010a-148">Anger MGM inställningarna som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="d010a-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="d010a-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="d010a-150">Stoppar den konfiguration som pågår.</span><span class="sxs-lookup"><span data-stu-id="d010a-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="d010a-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="d010a-152">Skickar konfiguration dokumentet till hanterade noder och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="d010a-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|





## <a name="requirements"></a><span data-ttu-id="d010a-153">Krav</span><span class="sxs-lookup"><span data-stu-id="d010a-153">Requirements</span></span>
------------
><span data-ttu-id="d010a-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d010a-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d010a-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d010a-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>