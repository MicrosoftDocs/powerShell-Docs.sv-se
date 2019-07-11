---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: Registrera JEA-konfigurationer
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726624"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="1837f-103">Registrera JEA-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="1837f-103">Registering JEA Configurations</span></span>

<span data-ttu-id="1837f-104">När du har din [rollfunktioner](role-capabilities.md) och [session konfigurationsfilen](session-configurations.md) skapas, det sista steget är att registrera JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="1837f-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="1837f-105">Registrera JEA-slutpunkt med systemet gör slutpunkten som är tillgängliga för användning av användare och automation-motorer.</span><span class="sxs-lookup"><span data-stu-id="1837f-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="1837f-106">Konfiguration av enkel dator</span><span class="sxs-lookup"><span data-stu-id="1837f-106">Single machine configuration</span></span>

<span data-ttu-id="1837f-107">För små miljöer kan du distribuera JEA genom att registrera session configuration filen med den [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1837f-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="1837f-108">Innan du börjar måste du kontrollera att följande krav är uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="1837f-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="1837f-109">En eller flera roller har skapats och placeras i den **RoleCapabilities** mapp på en PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="1837f-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="1837f-110">En konfigurationsfil för sessionen har skapats och testats.</span><span class="sxs-lookup"><span data-stu-id="1837f-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="1837f-111">Den användare som registrerar JEA-konfigurationen har administratörsbehörighet på systemet.</span><span class="sxs-lookup"><span data-stu-id="1837f-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="1837f-112">Du har valt ett namn för din JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="1837f-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="1837f-113">Namnet på JEA-slutpunkt krävs när användarna ansluter till systemet med JEA.</span><span class="sxs-lookup"><span data-stu-id="1837f-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="1837f-114">Den [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet visar en lista över slutpunkter på ett system.</span><span class="sxs-lookup"><span data-stu-id="1837f-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="1837f-115">Slutpunkter som börjar med `microsoft` vanligtvis medföljer Windows.</span><span class="sxs-lookup"><span data-stu-id="1837f-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="1837f-116">Den `microsoft.powershell` slutpunkten är standardslutpunkten användas vid anslutning till en PowerShell-fjärrslutpunkten.</span><span class="sxs-lookup"><span data-stu-id="1837f-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="1837f-117">Kör följande kommando för att registrera slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="1837f-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1837f-118">Föregående kommando startar om WinRM-tjänsten i systemet.</span><span class="sxs-lookup"><span data-stu-id="1837f-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="1837f-119">Detta avslutar alla PowerShell-fjärrkommunikation sessioner och alla pågående DSC-konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="1837f-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="1837f-120">Vi rekommenderar att du vidta produktion datorerna offline innan du kör kommandot för att undvika störningar verksamheten.</span><span class="sxs-lookup"><span data-stu-id="1837f-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="1837f-121">Efter registreringen är du redo att [använda JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="1837f-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="1837f-122">Du kan ta bort konfigurationsfilen sessionen när som helst.</span><span class="sxs-lookup"><span data-stu-id="1837f-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="1837f-123">Konfigurationsfilen används inte efter registreringen av slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="1837f-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="1837f-124">Konfiguration för flera datorer med DSC</span><span class="sxs-lookup"><span data-stu-id="1837f-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="1837f-125">När du distribuerar du JEA på flera datorer, den enklaste distributionsmodellen använder JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resursen för att snabbt och enhetligt distribuera JEA på varje dator.</span><span class="sxs-lookup"><span data-stu-id="1837f-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="1837f-126">Om du vill distribuera JEA med DSC, kontrollerar du att följande förutsättningar uppfylls:</span><span class="sxs-lookup"><span data-stu-id="1837f-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="1837f-127">En eller flera rollfunktioner har skapats och lagts till i en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="1837f-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="1837f-128">PowerShell-modulen som innehåller rollerna som lagras på en (skrivskyddad)-filresursen som är tillgängliga med varje dator.</span><span class="sxs-lookup"><span data-stu-id="1837f-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="1837f-129">Inställningar för sessionskonfigurationen har visats.</span><span class="sxs-lookup"><span data-stu-id="1837f-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="1837f-130">Du behöver inte skapa en konfigurationsfil för sessionen när du använder JEA DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="1837f-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="1837f-131">Du har autentiseringsuppgifter som tillåter administrativa åtgärder på varje dator eller åtkomst till DSC-hämtningsserver som används för att hantera datorerna.</span><span class="sxs-lookup"><span data-stu-id="1837f-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="1837f-132">Du har hämtat den [JEA DSC-resurs](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="1837f-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="1837f-133">Skapa en DSC-konfiguration för JEA-slutpunkt på en målserver för dator- eller pull.</span><span class="sxs-lookup"><span data-stu-id="1837f-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="1837f-134">I den här konfigurationen, den **JustEnoughAdministration** DSC-resursen definierar konfigurationsfilen sessionen och **filen** resursen kopierar rollfunktioner från filresursen.</span><span class="sxs-lookup"><span data-stu-id="1837f-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="1837f-135">Följande egenskaper kan konfigureras med hjälp av DSC-resurs:</span><span class="sxs-lookup"><span data-stu-id="1837f-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="1837f-136">Rolldefinitioner</span><span class="sxs-lookup"><span data-stu-id="1837f-136">Role Definitions</span></span>
- <span data-ttu-id="1837f-137">Virtuellt kontogrupper</span><span class="sxs-lookup"><span data-stu-id="1837f-137">Virtual account groups</span></span>
- <span data-ttu-id="1837f-138">Grupp-hanterade tjänstkontonamn</span><span class="sxs-lookup"><span data-stu-id="1837f-138">Group-managed service account name</span></span>
- <span data-ttu-id="1837f-139">Avskriften directory</span><span class="sxs-lookup"><span data-stu-id="1837f-139">Transcript directory</span></span>
- <span data-ttu-id="1837f-140">Enheten</span><span class="sxs-lookup"><span data-stu-id="1837f-140">User drive</span></span>
- <span data-ttu-id="1837f-141">Regler för villkorlig åtkomst</span><span class="sxs-lookup"><span data-stu-id="1837f-141">Conditional access rules</span></span>
- <span data-ttu-id="1837f-142">Startskript för JEA-sessionen</span><span class="sxs-lookup"><span data-stu-id="1837f-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="1837f-143">Syntaxen för var och en av de här egenskaperna i en DSC-konfiguration är konsekvent med PowerShell-session konfigurationsfil.</span><span class="sxs-lookup"><span data-stu-id="1837f-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="1837f-144">Nedan visas en exempelkonfiguration DSC för en modul för underhåll av allmänna.</span><span class="sxs-lookup"><span data-stu-id="1837f-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="1837f-145">Det förutsätts att en giltig PowerShell-modul som innehåller rollfunktioner finns på den `\\myfileshare\JEA` filresurs.</span><span class="sxs-lookup"><span data-stu-id="1837f-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="1837f-146">Sedan konfigurationen används på ett system genom att aktivera direkt i [lokal konfigurationshanterare](/powershell/dsc/managing-nodes/metaConfig) eller uppdatera den [pull-serverkonfiguration](/powershell/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="1837f-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="1837f-147">DSC-resurs kan du ersätta standard **Microsoft.PowerShell** slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="1837f-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="1837f-148">När den ersätts, registrerar resursen automatiskt en säkerhetskopiering slutpunkt med namnet **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="1837f-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="1837f-149">Säkerhetskopiering slutpunkten har standard WinRM ACL som tillåter Fjärrhanteringsanvändare och lokala administratörer gruppmedlemmar att komma åt den.</span><span class="sxs-lookup"><span data-stu-id="1837f-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="1837f-150">Avregistrerar JEA-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="1837f-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="1837f-151">Den [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet tar bort en JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="1837f-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="1837f-152">Avregistrera en JEA-slutpunkt förhindrar att nya användare skapa nya JEA-sessioner på systemet.</span><span class="sxs-lookup"><span data-stu-id="1837f-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="1837f-153">Du kan också uppdatera en JEA-konfiguration genom att registrera en konfigurationsfil för uppdaterade session med samma slutpunktnamn.</span><span class="sxs-lookup"><span data-stu-id="1837f-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1837f-154">Avregistrera en JEA gör endpoint att WinRM-tjänsten startas om.</span><span class="sxs-lookup"><span data-stu-id="1837f-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="1837f-155">Detta avbryter yttersta hanteringsåtgärder pågår, inklusive andra PowerShell-sessioner, WMI-anrop och vissa hanteringsverktyg.</span><span class="sxs-lookup"><span data-stu-id="1837f-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="1837f-156">Avregistrera endast PowerShell slutpunkter under planerat underhållsfönster.</span><span class="sxs-lookup"><span data-stu-id="1837f-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1837f-157">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="1837f-157">Next steps</span></span>

[<span data-ttu-id="1837f-158">Testa JEA-slutpunkt</span><span class="sxs-lookup"><span data-stu-id="1837f-158">Test the JEA endpoint</span></span>](using-jea.md)
