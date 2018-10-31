---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: Registrera JEA-konfigurationer
ms.openlocfilehash: 160aa95283da57a10aad5fdd4043adb1354a5db5
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002914"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="d0e3b-103">Registrera JEA-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="d0e3b-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="d0e3b-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d0e3b-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d0e3b-105">När du har din [rollfunktioner](role-capabilities.md) och [session konfigurationsfilen](session-configurations.md) skapas, det sista steget innan du kan använda JEA är att registrera JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="d0e3b-106">Registrera JEA-slutpunkt med systemet gör slutpunkten som är tillgängliga för användning av användare och automation-motorer.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="d0e3b-107">Konfiguration av enkel dator</span><span class="sxs-lookup"><span data-stu-id="d0e3b-107">Single machine configuration</span></span>

<span data-ttu-id="d0e3b-108">För små miljöer kan du distribuera JEA genom att registrera session configuration filen med den [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="d0e3b-109">Innan du börjar måste du kontrollera att följande krav är uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="d0e3b-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="d0e3b-110">En eller flera roller har skapats och placeras i mappen ”RoleCapabilities” av en giltig PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="d0e3b-111">En konfigurationsfil för sessionen har skapats och testats.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="d0e3b-112">Den användare som registrerar JEA-konfigurationen har administratörsbehörighet på systemen.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="d0e3b-113">Du måste också välja ett namn för din JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="d0e3b-114">Namnet på JEA-slutpunkt krävs när du vill ansluta till systemet med JEA.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="d0e3b-115">Du kan använda den [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet för att kontrollera namnen på befintliga slutpunkter i systemet.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="d0e3b-116">Slutpunkter som börjar med 'microsoft' vanligtvis medföljer Windows.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="d0e3b-117">'Microsoft.powershell'-slutpunkten är standardslutpunkten användas vid anslutning till en PowerShell-fjärrslutpunkten.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="d0e3b-118">När du har bestämt ett lämpligt namn för din JEA-slutpunkt, kör du följande kommando för att registrera slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="d0e3b-119">Ovanstående kommando startar om WinRM-tjänsten i systemet.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="d0e3b-120">Detta avslutar alla PowerShell-fjärrkommunikation sessioner, samt eventuella pågående DSC-konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="d0e3b-121">Vi rekommenderar att du ägnar några produktion datorer offline innan du kör kommandot för att undvika störningar verksamheten.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="d0e3b-122">Om registreringen lyckas du är redo att [använda JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="d0e3b-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="d0e3b-123">Du kan ta bort konfigurationsfilen som sessionen när som helst; den används inte när registrering av slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="d0e3b-124">Konfiguration för flera datorer med DSC</span><span class="sxs-lookup"><span data-stu-id="d0e3b-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="d0e3b-125">Om du distribuerar JEA på flera datorer, den enklaste modellen är att använda JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resursen för att snabbt och enhetligt distribuera JEA på varje dator.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="d0e3b-126">Om du vill distribuera JEA med DSC, måste du se till att följande krav är uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="d0e3b-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="d0e3b-127">En eller flera rollfunktioner har skapats och lagts till i en giltig PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="d0e3b-128">PowerShell-modulen som innehåller rollerna som lagras på en (skrivskyddad)-filresursen som är tillgängliga med varje dator.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="d0e3b-129">Inställningar för sessionskonfigurationen har visats.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="d0e3b-130">Du behöver inte skapa en konfigurationsfil för sessionen när du använder JEA DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="d0e3b-131">Du har autentiseringsuppgifter så att du kan utföra administrativa åtgärder på varje dator eller har åtkomst till en DSC-hämtningsserver som används för att hantera datorerna.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="d0e3b-132">Du har hämtat den [JEA DSC-resurs](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="d0e3b-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="d0e3b-133">Skapa en DSC-konfiguration för JEA-slutpunkt på ett mål dator (eller pull-servern, om du använder en).</span><span class="sxs-lookup"><span data-stu-id="d0e3b-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="d0e3b-134">I den här konfigurationen använder du JustEnoughAdministration DSC-resurs du ställer in konfigurationsfilen sessionen och File-resursen ska kopieras över rollfunktioner från filresursen.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="d0e3b-135">Följande egenskaper kan konfigureras med hjälp av DSC-resurs:</span><span class="sxs-lookup"><span data-stu-id="d0e3b-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="d0e3b-136">Rolldefinitioner</span><span class="sxs-lookup"><span data-stu-id="d0e3b-136">Role Definitions</span></span>
- <span data-ttu-id="d0e3b-137">Virtuella kontogrupper</span><span class="sxs-lookup"><span data-stu-id="d0e3b-137">Virtual Account groups</span></span>
- <span data-ttu-id="d0e3b-138">Gruppnamn för Hanterat tjänstkonto</span><span class="sxs-lookup"><span data-stu-id="d0e3b-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="d0e3b-139">Avskriften directory</span><span class="sxs-lookup"><span data-stu-id="d0e3b-139">Transcript directory</span></span>
- <span data-ttu-id="d0e3b-140">Enheten</span><span class="sxs-lookup"><span data-stu-id="d0e3b-140">User drive</span></span>
- <span data-ttu-id="d0e3b-141">Regler för villkorlig åtkomst</span><span class="sxs-lookup"><span data-stu-id="d0e3b-141">Conditional access rules</span></span>
- <span data-ttu-id="d0e3b-142">Startskript för JEA-sessionen</span><span class="sxs-lookup"><span data-stu-id="d0e3b-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="d0e3b-143">Syntaxen för var och en av de här egenskaperna i en DSC-konfiguration är konsekvent med PowerShell-session konfigurationsfil.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="d0e3b-144">Nedan visas en exempelkonfiguration DSC för en modul för underhåll av allmänna.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="d0e3b-145">Det förutsätts att en giltig PowerShell-modul som innehåller rollfunktioner i en undermapp som ”RoleCapabilities” finns på den '\\\\myfileshare\\JEA-filresurs.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="d0e3b-146">Den här konfigurationen kan sedan tillämpas på ett system av [direkt anropar den lokala Konfigurationshanteraren](https://msdn.microsoft.com/powershell/dsc/metaconfig) eller uppdatera den [pull-serverkonfiguration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="d0e3b-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="d0e3b-147">DSC-resurs kan du ersätta standardslutpunkten Microsoft.PowerShell fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="d0e3b-148">Om du gör det, registrerar resursen automatiskt en säkerhetskopiering unconstrainted slutpunkt med namnet ”Microsoft.PowerShell.Restricted” som har standard WinRM ACL (som tillåter Fjärrhanteringsanvändare och lokala administratörer gruppmedlemmar att komma åt den).</span><span class="sxs-lookup"><span data-stu-id="d0e3b-148">If you do this, the resource automatically registers a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="d0e3b-149">Avregistrerar JEA-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="d0e3b-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="d0e3b-150">Ta bort en JEA-slutpunkt på ett system med den [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="d0e3b-151">Avregistrera en JEA-slutpunkt förhindrar att nya användare skapa nya JEA-sessioner på systemet.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="d0e3b-152">Du kan också uppdatera en JEA-konfiguration genom att registrera en konfigurationsfil för uppdaterade session med samma slutpunktnamn.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="d0e3b-153">Avregistrera en JEA gör endpoint att WinRM-tjänsten startas om.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="d0e3b-154">Detta avbryter yttersta hanteringsåtgärder pågår, inklusive andra PowerShell-sessioner, WMI-anrop och vissa hanteringsverktyg.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="d0e3b-155">Avregistrera endast PowerShell slutpunkter under planerat underhållsfönster.</span><span class="sxs-lookup"><span data-stu-id="d0e3b-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d0e3b-156">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="d0e3b-156">Next steps</span></span>

- [<span data-ttu-id="d0e3b-157">Testa JEA-slutpunkt</span><span class="sxs-lookup"><span data-stu-id="d0e3b-157">Test the JEA endpoint</span></span>](using-jea.md)
