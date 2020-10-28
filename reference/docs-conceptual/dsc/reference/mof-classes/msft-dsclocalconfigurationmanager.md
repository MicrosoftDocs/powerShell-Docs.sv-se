---
ms.date: 07/14/2020
ms.topic: reference
title: MSFT_DSCLocalConfigurationManager-klass
description: MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 31112c7d15884699171ec732ac20b6960b0858a9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644811"
---
# <a name="msft_dsclocalconfigurationmanager-class"></a><span data-ttu-id="54604-103">MSFT_DSCLocalConfigurationManager-klass</span><span class="sxs-lookup"><span data-stu-id="54604-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="54604-104">Den lokala Configuration Manager (LCM) som styr tillståndet för konfigurationsfiler och använder konfigurations agenten för att tillämpa konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="54604-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="54604-105">Följande syntax är förenklad från Managed Object Format (MOF) kod och innehåller alla ärvda egenskaper.</span><span class="sxs-lookup"><span data-stu-id="54604-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="54604-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="54604-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="54604-107">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="54604-107">Members</span></span>

<span data-ttu-id="54604-108">**MSFT_DSCLocalConfigurationManager** -klassen har följande medlemmar:</span><span class="sxs-lookup"><span data-stu-id="54604-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="54604-109">Indatametod []</span><span class="sxs-lookup"><span data-stu-id="54604-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="54604-110">Metoder</span><span class="sxs-lookup"><span data-stu-id="54604-110">Methods</span></span>

<span data-ttu-id="54604-111">Klassen **MSFT_DSCLocalConfigurationManager** har dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="54604-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="54604-112">Metoder</span><span class="sxs-lookup"><span data-stu-id="54604-112">Methods</span></span> |<span data-ttu-id="54604-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="54604-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="54604-114">ApplyConfiguration (boolesk)</span><span class="sxs-lookup"><span data-stu-id="54604-114">ApplyConfiguration(boolean)</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="54604-115">Använder konfigurations agenten för att tillämpa den konfiguration som väntar.</span><span class="sxs-lookup"><span data-stu-id="54604-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="54604-116">DisableDebugConfiguration ()</span><span class="sxs-lookup"><span data-stu-id="54604-116">DisableDebugConfiguration()</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="54604-117">Inaktiverar fel sökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="54604-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="54604-118">EnableDebugConfiguration (boolesk)</span><span class="sxs-lookup"><span data-stu-id="54604-118">EnableDebugConfiguration(boolean)</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="54604-119">Aktiverar fel sökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="54604-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="54604-120">GetConfiguration ()</span><span class="sxs-lookup"><span data-stu-id="54604-120">GetConfiguration()</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="54604-121">Skickar konfigurations dokumentet till den hanterade noden och använder **Get** -metoden för konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="54604-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="54604-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="54604-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="54604-123">Hämtar konfigurations agentens utdata som är relaterade till ett speciellt jobb.</span><span class="sxs-lookup"><span data-stu-id="54604-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="54604-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="54604-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="54604-125">Hämta konfigurations status historik.</span><span class="sxs-lookup"><span data-stu-id="54604-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="54604-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="54604-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="54604-127">Hämtar de LCM-inställningar som används för att kontrol lera konfigurations agenten.</span><span class="sxs-lookup"><span data-stu-id="54604-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="54604-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="54604-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="54604-129">Startar konsekvens kontrollen.</span><span class="sxs-lookup"><span data-stu-id="54604-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="54604-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="54604-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="54604-131">Tar bort konfigurationsfilerna.</span><span class="sxs-lookup"><span data-stu-id="54604-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="54604-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="54604-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="54604-133">Anropar direkt **Get** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="54604-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="54604-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="54604-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="54604-135">Anropar **set** -metoden för en DSC-resurs direkt.</span><span class="sxs-lookup"><span data-stu-id="54604-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="54604-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="54604-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="54604-137">Anropar direkt **test** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="54604-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="54604-138">Ånger</span><span class="sxs-lookup"><span data-stu-id="54604-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="54604-139">Återställer till en tidigare konfiguration.</span><span class="sxs-lookup"><span data-stu-id="54604-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="54604-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="54604-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="54604-141">Skickar konfigurations dokumentet till den hanterade noden och sparar det som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="54604-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="54604-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="54604-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="54604-143">Skickar konfigurations dokumentet till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="54604-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="54604-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="54604-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="54604-145">Skicka konfigurations dokumentet till den hanterade noden och börja använda konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="54604-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="54604-146">Använd GetConfigurationResultOutput för att hämta resultatet av utdata.</span><span class="sxs-lookup"><span data-stu-id="54604-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="54604-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="54604-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="54604-148">Anger de LCM-inställningar som används för att kontrol lera konfigurations agenten.</span><span class="sxs-lookup"><span data-stu-id="54604-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="54604-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="54604-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="54604-150">Stoppar den konfiguration som pågår.</span><span class="sxs-lookup"><span data-stu-id="54604-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="54604-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="54604-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="54604-152">Skickar konfigurations dokumentet till den hanterade noden och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="54604-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="54604-153">Krav</span><span class="sxs-lookup"><span data-stu-id="54604-153">Requirements</span></span>

<span data-ttu-id="54604-154">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="54604-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="54604-155">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="54604-155">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>
