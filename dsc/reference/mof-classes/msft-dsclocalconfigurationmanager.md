---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 09b30edd48384c0e8412e0e6ee926a719249c5b8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726884"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6fc88-103">MSFT_DSCLocalConfigurationManager-klass</span><span class="sxs-lookup"><span data-stu-id="6fc88-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6fc88-104">Den lokala Configuration Manager (LCM) som styr tillstånd för konfigurationsfiler och använder konfigurationen agenten för att tillämpa konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="6fc88-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="6fc88-105">Följande syntax är förenklad från kod Managed Object Format (MOF) och innehåller alla ärvda egenskaper.</span><span class="sxs-lookup"><span data-stu-id="6fc88-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fc88-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6fc88-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="6fc88-107">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="6fc88-107">Members</span></span>

<span data-ttu-id="6fc88-108">Den **MSFT_DSCLocalConfigurationManager** klassen har följande medlemmar:</span><span class="sxs-lookup"><span data-stu-id="6fc88-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="6fc88-109">[Methods][]</span><span class="sxs-lookup"><span data-stu-id="6fc88-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="6fc88-110">Metoder</span><span class="sxs-lookup"><span data-stu-id="6fc88-110">Methods</span></span>

<span data-ttu-id="6fc88-111">Den **MSFT_DSCLocalConfigurationManager** klassen har dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="6fc88-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="6fc88-112">Metod</span><span class="sxs-lookup"><span data-stu-id="6fc88-112">Method</span></span> |<span data-ttu-id="6fc88-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6fc88-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="6fc88-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="6fc88-115">Använder Configuration-agenten för att tillämpa konfigurationen som väntar.</span><span class="sxs-lookup"><span data-stu-id="6fc88-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="6fc88-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="6fc88-117">Inaktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="6fc88-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="6fc88-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="6fc88-119">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="6fc88-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="6fc88-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="6fc88-121">Skickar konfigurationsdokumentet till hanterad nod och använder den **hämta** metod för Configuration agenten att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6fc88-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="6fc88-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="6fc88-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="6fc88-123">Hämtar Configuration-agenten utdata som är relaterade till ett specifikt jobb.</span><span class="sxs-lookup"><span data-stu-id="6fc88-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="6fc88-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="6fc88-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="6fc88-125">Hämta statushistorik konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6fc88-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="6fc88-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="6fc88-127">Hämtar LCM-inställningar som används för att kontrollera konfigurationen Agent.</span><span class="sxs-lookup"><span data-stu-id="6fc88-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="6fc88-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="6fc88-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="6fc88-129">Startar en konsekvenskontroll.</span><span class="sxs-lookup"><span data-stu-id="6fc88-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="6fc88-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="6fc88-131">Tar bort filerna.</span><span class="sxs-lookup"><span data-stu-id="6fc88-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="6fc88-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="6fc88-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="6fc88-133">Direkt anropar den **hämta** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="6fc88-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="6fc88-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="6fc88-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="6fc88-135">Direkt anropar den **ange** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="6fc88-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="6fc88-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="6fc88-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="6fc88-137">Direkt anropar den **Test** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="6fc88-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="6fc88-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="6fc88-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="6fc88-139">Samlar in tillbaka till en tidigare konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6fc88-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="6fc88-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="6fc88-141">Skickar konfigurationsdokumentet till hanterad nod och sparar den som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="6fc88-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="6fc88-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="6fc88-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="6fc88-143">Skickar konfigurationsdokumentet till hanterad nod och använder konfigurationen agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6fc88-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="6fc88-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="6fc88-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="6fc88-145">Skicka konfigurationsdokumentet till hanterad nod och börja använda Configuration agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6fc88-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="6fc88-146">Använd GetConfigurationResultOutput för att hämta resultatet utdata.</span><span class="sxs-lookup"><span data-stu-id="6fc88-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="6fc88-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="6fc88-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="6fc88-148">Anger LCM-inställningar som används för att styra agenten konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6fc88-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="6fc88-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="6fc88-150">Stoppar konfigurationen som håller på att skapas.</span><span class="sxs-lookup"><span data-stu-id="6fc88-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="6fc88-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="6fc88-152">Skickar konfigurationsdokumentet till hanterad nod och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="6fc88-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="6fc88-153">Krav</span><span class="sxs-lookup"><span data-stu-id="6fc88-153">Requirements</span></span>

<span data-ttu-id="6fc88-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6fc88-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6fc88-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fc88-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>
