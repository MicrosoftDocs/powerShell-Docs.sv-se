---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: Registrerar JEA-konfigurationer
ms.openlocfilehash: 7cc67e891bc14dd667c97e9a8b550b33b4c2b874
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706214"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="048f1-103">Registrerar JEA-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="048f1-103">Registering JEA Configurations</span></span>

<span data-ttu-id="048f1-104">När du har skapat dina [roll funktioner](role-capabilities.md) och [konfigurations filen för sessionen](session-configurations.md) är det sista steget att registrera Jea-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="048f1-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="048f1-105">När du registrerar JEA-slutpunkten med systemet blir slut punkten tillgänglig för användning av användare och automatiserings motorer.</span><span class="sxs-lookup"><span data-stu-id="048f1-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="048f1-106">Konfiguration för enskild dator</span><span class="sxs-lookup"><span data-stu-id="048f1-106">Single machine configuration</span></span>

<span data-ttu-id="048f1-107">För små miljöer kan du distribuera JEA genom att registrera sessionens konfigurations fil med hjälp av cmdleten [register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="048f1-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="048f1-108">Innan du börjar bör du kontrol lera att följande krav är uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="048f1-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="048f1-109">En eller flera roller har skapats och placerats i mappen **RoleCapabilities** i en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="048f1-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="048f1-110">En konfigurations fil för sessionen har skapats och testats.</span><span class="sxs-lookup"><span data-stu-id="048f1-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="048f1-111">Användaren som registrerar JEA-konfigurationen har administratörs behörighet på systemet.</span><span class="sxs-lookup"><span data-stu-id="048f1-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="048f1-112">Du har valt ett namn för din JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="048f1-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="048f1-113">Namnet på JEA-slutpunkten krävs när användare ansluter till systemet med hjälp av JEA.</span><span class="sxs-lookup"><span data-stu-id="048f1-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="048f1-114">Cmdlet: en [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) visar namnen på slut punkterna i ett system.</span><span class="sxs-lookup"><span data-stu-id="048f1-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="048f1-115">Slut punkter som börjar med `microsoft` levereras vanligt vis med Windows.</span><span class="sxs-lookup"><span data-stu-id="048f1-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="048f1-116">`microsoft.powershell` slut punkten är standard slut punkten som används vid anslutning till en fjärrslutpunkt av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="048f1-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

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

<span data-ttu-id="048f1-117">Kör följande kommando för att registrera slut punkten.</span><span class="sxs-lookup"><span data-stu-id="048f1-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="048f1-118">Föregående kommando startar om WinRM-tjänsten på systemet.</span><span class="sxs-lookup"><span data-stu-id="048f1-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="048f1-119">Detta avslutar alla PowerShell-fjärrsessioner och pågående DSC-konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="048f1-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="048f1-120">Vi rekommenderar att du tar produktions datorer offline innan du kör kommandot för att undvika avbrott i affärs åtgärder.</span><span class="sxs-lookup"><span data-stu-id="048f1-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="048f1-121">Efter registreringen är du redo att [använda Jea](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="048f1-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="048f1-122">Du kan när som helst ta bort sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="048f1-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="048f1-123">Konfigurations filen används inte efter att slut punkten har registrerats.</span><span class="sxs-lookup"><span data-stu-id="048f1-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="048f1-124">Konfiguration av flera datorer med DSC</span><span class="sxs-lookup"><span data-stu-id="048f1-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="048f1-125">När du distribuerar JEA på flera datorer använder den enklaste distributions modellen JEA [-resursen (Desired State Configuration)](../../../dsc/overview/overview.md) för att snabbt och konsekvent distribuera Jea på varje dator.</span><span class="sxs-lookup"><span data-stu-id="048f1-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="048f1-126">För att distribuera JEA med DSC kontrollerar du att följande krav är uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="048f1-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="048f1-127">En eller flera roll funktioner har skapats och lagts till i en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="048f1-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="048f1-128">PowerShell-modulen som innehåller rollerna lagras på en (skrivskyddad) fil resurs som är tillgänglig för varje dator.</span><span class="sxs-lookup"><span data-stu-id="048f1-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="048f1-129">Inställningarna för konfigurationen av sessionen har fastställts.</span><span class="sxs-lookup"><span data-stu-id="048f1-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="048f1-130">Du behöver inte skapa en konfigurations fil för sessionen när du använder JEA DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="048f1-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="048f1-131">Du har autentiseringsuppgifter som tillåter administrativa åtgärder på varje dator eller åtkomst till DSC-pull-servern som används för att hantera datorerna.</span><span class="sxs-lookup"><span data-stu-id="048f1-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="048f1-132">Du har laddat ned [Jea DSC-resursen](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="048f1-132">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="048f1-133">Skapa en DSC-konfiguration för din JEA-slutpunkt på en måldator eller hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="048f1-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="048f1-134">I den här konfigurationen definierar **JustEnoughAdministration** DSC-resursen sessionens konfigurations fil och **fil** resursen kopierar roll funktionerna från fil resursen.</span><span class="sxs-lookup"><span data-stu-id="048f1-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="048f1-135">Följande egenskaper kan konfigureras med hjälp av DSC-resursen:</span><span class="sxs-lookup"><span data-stu-id="048f1-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="048f1-136">Rolldefinitioner</span><span class="sxs-lookup"><span data-stu-id="048f1-136">Role Definitions</span></span>
- <span data-ttu-id="048f1-137">Virtuella konto grupper</span><span class="sxs-lookup"><span data-stu-id="048f1-137">Virtual account groups</span></span>
- <span data-ttu-id="048f1-138">Grupphanterat tjänst konto namn</span><span class="sxs-lookup"><span data-stu-id="048f1-138">Group-managed service account name</span></span>
- <span data-ttu-id="048f1-139">Avskrifts katalog</span><span class="sxs-lookup"><span data-stu-id="048f1-139">Transcript directory</span></span>
- <span data-ttu-id="048f1-140">Användar enhet</span><span class="sxs-lookup"><span data-stu-id="048f1-140">User drive</span></span>
- <span data-ttu-id="048f1-141">Regler för villkorlig åtkomst</span><span class="sxs-lookup"><span data-stu-id="048f1-141">Conditional access rules</span></span>
- <span data-ttu-id="048f1-142">Start skript för JEA-sessionen</span><span class="sxs-lookup"><span data-stu-id="048f1-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="048f1-143">Syntaxen för var och en av dessa egenskaper i en DSC-konfiguration är konsekvent med konfigurations filen för PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="048f1-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="048f1-144">Nedan visas en exempel-DSC-konfiguration för en generell server underhålls modul.</span><span class="sxs-lookup"><span data-stu-id="048f1-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="048f1-145">Det förutsätter att en giltig PowerShell-modul som innehåller roll funktioner finns på den `\\myfileshare\JEA` fil resursen.</span><span class="sxs-lookup"><span data-stu-id="048f1-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

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

<span data-ttu-id="048f1-146">Därefter tillämpas konfigurationen på ett system genom att direkt anropa den [lokala Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) eller uppdatera konfigurationen för pull- [servern](/powershell/scripting/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="048f1-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="048f1-147">DSC-resursen låter dig också ersätta standard slut punkten för **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="048f1-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="048f1-148">När den ersätts registrerar resursen automatiskt en säkerhets kopierings slut punkt med namnet **Microsoft. PowerShell. restricted**.</span><span class="sxs-lookup"><span data-stu-id="048f1-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="048f1-149">Slut punkten för säkerhets kopieringen har standard-WinRM ACL som tillåter att fjärrhanterings användare och lokala administratörer kan komma åt den.</span><span class="sxs-lookup"><span data-stu-id="048f1-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="048f1-150">JEA-konfigurationer avregistreras</span><span class="sxs-lookup"><span data-stu-id="048f1-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="048f1-151">[Unregister-PSSessionConfiguration-](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet: en tar bort en Jea-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="048f1-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="048f1-152">När du avregistrerar en JEA-slutpunkt hindras nya användare från att skapa nya JEA-sessioner i systemet.</span><span class="sxs-lookup"><span data-stu-id="048f1-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="048f1-153">Du kan också uppdatera en JEA-konfiguration genom att registrera en uppdaterad sessions konfigurations fil på nytt med samma slut punkts namn.</span><span class="sxs-lookup"><span data-stu-id="048f1-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="048f1-154">När du avregistrerar en JEA-slutpunkt startar WinRM-tjänsten om.</span><span class="sxs-lookup"><span data-stu-id="048f1-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="048f1-155">Detta avbryter de flesta pågående hanterings åtgärder, inklusive andra PowerShell-sessioner, WMI-anrop och vissa hanterings verktyg.</span><span class="sxs-lookup"><span data-stu-id="048f1-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="048f1-156">Avregistrera bara PowerShell-slutpunkter under planerat underhålls fönster.</span><span class="sxs-lookup"><span data-stu-id="048f1-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="048f1-157">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="048f1-157">Next steps</span></span>

[<span data-ttu-id="048f1-158">Testa JEA-slutpunkten</span><span class="sxs-lookup"><span data-stu-id="048f1-158">Test the JEA endpoint</span></span>](using-jea.md)
