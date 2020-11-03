---
description: Innehåller en kort introduktion till DSC-funktionen (Desired State Configuration).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_desiredstateconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_DesiredStateConfiguration
ms.openlocfilehash: 2f043104c67078b98355b3e54171a8993e534837
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273189"
---
# <a name="about_desiredstateconfiguration"></a><span data-ttu-id="de227-104">about_DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="de227-104">about_DesiredStateConfiguration</span></span>

## <a name="short-description"></a><span data-ttu-id="de227-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="de227-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="de227-106">Innehåller en kort introduktion till DSC-funktionen (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="de227-106">Provides a brief introduction to the PowerShell Desired State Configuration (DSC) feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="de227-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="de227-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="de227-108">DSC är en hanterings plattform i PowerShell som gör det möjligt att distribuera och hantera konfigurations data för program varu tjänster och hantera miljön där de här tjänsterna körs.</span><span class="sxs-lookup"><span data-stu-id="de227-108">DSC is a management platform in PowerShell that enables deploying and managing configuration data for software services, and managing the environment in which these services run.</span></span>

<span data-ttu-id="de227-109">DSC tillhandahåller en uppsättning PowerShell-språktillägg, nya cmdletar och resurser som du kan använda för att ange hur du vill att program varu miljöns tillstånd ska konfigureras.</span><span class="sxs-lookup"><span data-stu-id="de227-109">DSC provides a set of PowerShell language extensions, new cmdlets, and resources that you can use to declaratively specify how you want the state of your software environment to be configured.</span></span> <span data-ttu-id="de227-110">Det är också ett sätt att underhålla och hantera befintliga konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="de227-110">It also provides a means to maintain and manage existing configurations.</span></span>

<span data-ttu-id="de227-111">DSC introduceras i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="de227-111">DSC is introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="de227-112">Detaljerad information om DSC finns i [PowerShell Desired State Configuration-översikt](/powershell/scripting/dsc/overview/overview) i TechNet-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="de227-112">For detailed information about DSC, see [PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview) in the TechNet Library.</span></span>

## <a name="developing-dsc-resources-with-classes"></a><span data-ttu-id="de227-113">UTVECKLA DSC-RESURSER MED KLASSER</span><span class="sxs-lookup"><span data-stu-id="de227-113">DEVELOPING DSC RESOURCES WITH CLASSES</span></span>

<span data-ttu-id="de227-114">Från och med PowerShell 5,0 kan du utveckla DSC-resurser med hjälp av klasser.</span><span class="sxs-lookup"><span data-stu-id="de227-114">Starting in PowerShell 5.0, you can develop DSC resources by using classes.</span></span>
<span data-ttu-id="de227-115">Mer information finns i [about_Classes](about_Classes.md)och [skriva en anpassad DSC-resurs med PowerShell-klasser](/previous-versions//dn948461(v=technet.10)) på Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="de227-115">For more information, see [about_Classes](about_Classes.md), and [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)) on Microsoft TechNet.</span></span>

## <a name="using-dsc"></a><span data-ttu-id="de227-116">ANVÄNDA DSC</span><span class="sxs-lookup"><span data-stu-id="de227-116">USING DSC</span></span>

<span data-ttu-id="de227-117">Om du vill använda DSC för att konfigurera din miljö måste du först definiera ett PowerShell-skript block med hjälp av nyckelordet konfiguration, följt av en identifierare, som i sin tur följs av paret klammerparenteser som avgränsar blocket.</span><span class="sxs-lookup"><span data-stu-id="de227-117">To use DSC to configure your environment, first define a PowerShell script block using the Configuration keyword, followed by an identifier, which is in turn followed by the pair of curly braces delimiting the block.</span></span> <span data-ttu-id="de227-118">I konfigurations blocket kan du definiera Node-block som anger det önskade konfigurations läget för varje nod (dator) i miljön.</span><span class="sxs-lookup"><span data-stu-id="de227-118">Inside the configuration block you can define node blocks that specify the desired configuration state for each node (computer) in the environment.</span></span> <span data-ttu-id="de227-119">Ett Node-block börjar med nyckelordet Node, följt av namnet på mål datorn, som kan vara en variabel.</span><span class="sxs-lookup"><span data-stu-id="de227-119">A node block starts with the Node keyword, followed by the name of the target computer, which can be a variable.</span></span> <span data-ttu-id="de227-120">Efter datorns namn, kommer klammerparenteser som begränsar Node-blocket.</span><span class="sxs-lookup"><span data-stu-id="de227-120">After the computer name, come the curly braces that delimit the node block.</span></span> <span data-ttu-id="de227-121">Inuti Node-blocket kan du definiera resurs block för att konfigurera vissa resurser.</span><span class="sxs-lookup"><span data-stu-id="de227-121">Inside the node block, you can define resource blocks to configure specific resources.</span></span> <span data-ttu-id="de227-122">Ett resurs block börjar med typ namnet för resursen följt av den identifierare som du vill ange för detta block, följt av klammerparenteserna som begränsar blocket, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="de227-122">A resource block starts with the type name of the resource, followed by the identifier you want to specify for that block, followed by the curly braces that delimit the block, as shown in the following example.</span></span>

```powershell
Configuration MyWebConfig {
    # Parameters are optional
    param ($MachineName, $WebsiteFilePath)
    # A Configuration block can have one or more Node blocks
    Node $MachineName
    {
        # Next, specify one or more resource blocks
        # WindowsFeature is one of the resources you can use in a Node block
        # This example ensures the Web Server (IIS) role is installed
        WindowsFeature IIS
        {
            # To ensure that the role is not installed, set Ensure to "Absent"
            Ensure = "Present"
            Name = "Web-Server" # Use the Name property from Get-WindowsFeature
        }

        # You can use the File resource to create files and folders
        # "WebDirectory" is the name you want to use to refer to this instance
        File WebDirectory
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File"
            Recurse = $true
            SourcePath = $WebsiteFilePath
            DestinationPath = "C:\inetpub\wwwroot"

            # Ensure that the IIS block is successfully run first before
            # configuring this resource
            DependsOn = "[WindowsFeature]IIS"  # Use for dependencies
        }
    }
}
```

<span data-ttu-id="de227-123">Om du vill skapa en konfiguration anropar du konfigurations blocket på samma sätt som du anropar en PowerShell-funktion, skickar in förväntade parametrar som du kan ha definierat (två i exemplet ovan).</span><span class="sxs-lookup"><span data-stu-id="de227-123">To create a configuration, invoke the Configuration block the same way you would invoke a PowerShell function, passing in any expected parameters you may have defined (two in the example above).</span></span> <span data-ttu-id="de227-124">I det här fallet kan du till exempel:</span><span class="sxs-lookup"><span data-stu-id="de227-124">For example, in this case:</span></span>

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

<span data-ttu-id="de227-125">Detta genererar en MOF-fil per nod på den sökväg som du anger.</span><span class="sxs-lookup"><span data-stu-id="de227-125">This generates a MOF file per node at the path you specify.</span></span> <span data-ttu-id="de227-126">Dessa MOF-filer anger önskad konfiguration för varje nod.</span><span class="sxs-lookup"><span data-stu-id="de227-126">These MOF files specify the desired configuration for each node.</span></span> <span data-ttu-id="de227-127">Använd sedan följande cmdlet för att parsa konfigurations-MOF-filerna, skicka varje nod till motsvarande konfiguration och tillämpar dessa konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="de227-127">Next, use the following cmdlet to parse the configuration MOF files, send each node its corresponding configuration, and enact those configurations.</span></span> <span data-ttu-id="de227-128">Observera att du inte behöver skapa en separat MOF-fil för klassbaserade DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="de227-128">Note that you do not need to create a separate MOF file for class-based DSC resources.</span></span>

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a><span data-ttu-id="de227-129">ANVÄNDA DSC FÖR ATT UNDERHÅLLA KONFIGURATIONS STATUS</span><span class="sxs-lookup"><span data-stu-id="de227-129">USING DSC TO MAINTAIN CONFIGURATION STATE</span></span>

<span data-ttu-id="de227-130">Med DSC är konfigurationen idempotenta.</span><span class="sxs-lookup"><span data-stu-id="de227-130">With DSC, configuration is idempotent.</span></span> <span data-ttu-id="de227-131">Det innebär att om du använder DSC för att införa samma konfiguration mer än en gång, blir det resulterande konfigurations statusen alltid densamma.</span><span class="sxs-lookup"><span data-stu-id="de227-131">This means that if you use DSC to enact the same configuration more than once, the resulting configuration state will always be the same.</span></span> <span data-ttu-id="de227-132">På grund av detta kan du använda samma DSC-konfiguration igen för att återställa dem till önskat tillstånd om du misstänker att alla noder i din miljö kan ha varit i det önskade konfigurations läget.</span><span class="sxs-lookup"><span data-stu-id="de227-132">Because of this, if you suspect that any nodes in your environment may have drifted from the desired state of configuration, you can enact the same DSC configuration again to bring them back to the desired state.</span></span> <span data-ttu-id="de227-133">Du behöver inte ändra konfigurations skriptet för att bara hantera de resurser vars tillstånd har varit i önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="de227-133">You do not need to modify the configuration script to address only those resources whose state has drifted from the desired state.</span></span>

<span data-ttu-id="de227-134">I följande exempel visas hur du kan kontrol lera om det faktiska konfigurations läget på en nod har inträffat från den senaste DSC-konfigurationen som har angivits på noden.</span><span class="sxs-lookup"><span data-stu-id="de227-134">The following example shows how you can verify whether the actual state of configuration on a given node has drifted from the last DSC configuration enacted on the node.</span></span> <span data-ttu-id="de227-135">I det här exemplet kontrollerar vi konfigurationen av den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="de227-135">In this example we are checking the configuration of the local computer.</span></span>

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a><span data-ttu-id="de227-136">INBYGGDA DSC-RESURSER</span><span class="sxs-lookup"><span data-stu-id="de227-136">BUILT-IN DSC RESOURCES</span></span>

<span data-ttu-id="de227-137">Du kan använda följande inbyggda resurser i konfigurations skripten:</span><span class="sxs-lookup"><span data-stu-id="de227-137">You can use the following built-in resources in your configuration scripts:</span></span>

|<span data-ttu-id="de227-138">Name</span><span class="sxs-lookup"><span data-stu-id="de227-138">Name</span></span>                  |<span data-ttu-id="de227-139">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="de227-139">Properties</span></span>                                         |
|----------------------|---------------------------------------------------|
|<span data-ttu-id="de227-140">Fil</span><span class="sxs-lookup"><span data-stu-id="de227-140">File</span></span>                  |<span data-ttu-id="de227-141">{DestinationPath, attribut, kontroll summa, innehåll...}</span><span class="sxs-lookup"><span data-stu-id="de227-141">{DestinationPath, Attributes, Checksum, Content...}</span></span>|
|<span data-ttu-id="de227-142">Arkiv</span><span class="sxs-lookup"><span data-stu-id="de227-142">Archive</span></span>               |<span data-ttu-id="de227-143">{Destination, sökväg, kontroll summa, autentiseringsuppgift...}</span><span class="sxs-lookup"><span data-stu-id="de227-143">{Destination, Path, Checksum, Credential...}</span></span>       |
|<span data-ttu-id="de227-144">Miljö</span><span class="sxs-lookup"><span data-stu-id="de227-144">Environment</span></span>           |<span data-ttu-id="de227-145">{Name, DependsOn, se sökväg...}</span><span class="sxs-lookup"><span data-stu-id="de227-145">{Name, DependsOn, Ensure, Path...}</span></span>                 |
|<span data-ttu-id="de227-146">Group</span><span class="sxs-lookup"><span data-stu-id="de227-146">Group</span></span>                 |<span data-ttu-id="de227-147">{GroupName, Credential, DependsOn, Description...}</span><span class="sxs-lookup"><span data-stu-id="de227-147">{GroupName, Credential, DependsOn, Description...}</span></span> |
|<span data-ttu-id="de227-148">Loggas</span><span class="sxs-lookup"><span data-stu-id="de227-148">Log</span></span>                   |<span data-ttu-id="de227-149">{Message, DependsOn, PsDscRunAsCredential}</span><span class="sxs-lookup"><span data-stu-id="de227-149">{Message, DependsOn, PsDscRunAsCredential}</span></span>         |
|<span data-ttu-id="de227-150">Paket</span><span class="sxs-lookup"><span data-stu-id="de227-150">Package</span></span>               |<span data-ttu-id="de227-151">{Namn, sökväg, ProductId, argument...}</span><span class="sxs-lookup"><span data-stu-id="de227-151">{Name, Path, ProductId, Arguments...}</span></span>              |
|<span data-ttu-id="de227-152">Register</span><span class="sxs-lookup"><span data-stu-id="de227-152">Registry</span></span>              |<span data-ttu-id="de227-153">{Key, ValueName, DependsOn, se...}</span><span class="sxs-lookup"><span data-stu-id="de227-153">{Key, ValueName, DependsOn, Ensure...}</span></span>             |
|<span data-ttu-id="de227-154">Skript</span><span class="sxs-lookup"><span data-stu-id="de227-154">Script</span></span>                |<span data-ttu-id="de227-155">{GetScript, SetScript, TestScript, Credential...}</span><span class="sxs-lookup"><span data-stu-id="de227-155">{GetScript, SetScript, TestScript, Credential...}</span></span>  |
|<span data-ttu-id="de227-156">Tjänst</span><span class="sxs-lookup"><span data-stu-id="de227-156">Service</span></span>               |<span data-ttu-id="de227-157">{Name, BuiltInAccount, Credential,-beroenden...}</span><span class="sxs-lookup"><span data-stu-id="de227-157">{Name, BuiltInAccount, Credential, Dependencies...}</span></span>|
|<span data-ttu-id="de227-158">Användare</span><span class="sxs-lookup"><span data-stu-id="de227-158">User</span></span>                  |<span data-ttu-id="de227-159">{UserName, DependsOn, beskrivning, inaktive rad...}</span><span class="sxs-lookup"><span data-stu-id="de227-159">{UserName, DependsOn, Description, Disabled...}</span></span>    |
|<span data-ttu-id="de227-160">WaitForAll</span><span class="sxs-lookup"><span data-stu-id="de227-160">WaitForAll</span></span>            |<span data-ttu-id="de227-161">{Nodnamn, ResourceName, DependsOn, PsDscRunAsC...}</span><span class="sxs-lookup"><span data-stu-id="de227-161">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="de227-162">WaitForAny</span><span class="sxs-lookup"><span data-stu-id="de227-162">WaitForAny</span></span>            |<span data-ttu-id="de227-163">{Nodnamn, ResourceName, DependsOn, PsDscRunAsC...}</span><span class="sxs-lookup"><span data-stu-id="de227-163">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="de227-164">WaitForSome</span><span class="sxs-lookup"><span data-stu-id="de227-164">WaitForSome</span></span>           |<span data-ttu-id="de227-165">{NodeCount, nodnamn, ResourceName, DependsOn...}</span><span class="sxs-lookup"><span data-stu-id="de227-165">{NodeCount, NodeName, ResourceName, DependsOn...}</span></span>  |
|<span data-ttu-id="de227-166">WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="de227-166">WindowsFeature</span></span>        |<span data-ttu-id="de227-167">{Name, Credential, DependsOn, se...}</span><span class="sxs-lookup"><span data-stu-id="de227-167">{Name, Credential, DependsOn, Ensure...}</span></span>           |
|<span data-ttu-id="de227-168">WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="de227-168">WindowsOptionalFeature</span></span>|<span data-ttu-id="de227-169">{Name, DependsOn, se, LogLevel...}</span><span class="sxs-lookup"><span data-stu-id="de227-169">{Name, DependsOn, Ensure, LogLevel...}</span></span>             |
|<span data-ttu-id="de227-170">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="de227-170">WindowsProcess</span></span>        |<span data-ttu-id="de227-171">{Argument, sökväg, autentiseringsuppgift, DependsOn...}</span><span class="sxs-lookup"><span data-stu-id="de227-171">{Arguments, Path, Credential, DependsOn...}</span></span>        |

<span data-ttu-id="de227-172">Kör cmdleten om du vill hämta en lista över tillgängliga DSC-resurser i systemet `Get-DscResource` .</span><span class="sxs-lookup"><span data-stu-id="de227-172">To get a list of available DSC resources on your system, run the `Get-DscResource` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="de227-173">I PowerShell-versioner under 7,0 `Get-DscResource` hittar du inte klassbaserade DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="de227-173">In PowerShell versions below 7.0, `Get-DscResource` does not find Class based DSC resources.</span></span>

<span data-ttu-id="de227-174">Exemplet i det här avsnittet visar hur du använder fil-och WindowsFeature-resurserna.</span><span class="sxs-lookup"><span data-stu-id="de227-174">The example in this topic demonstrates how to use the File and WindowsFeature resources.</span></span> <span data-ttu-id="de227-175">Om du vill se alla egenskaper som du kan använda med en resurs, infogar du markören i nyckelordet resurs (till exempel fil) i konfigurations skriptet i PowerShell ISE, håller ned <kbd>CTRL</kbd>- + <kbd>blanksteg</kbd></span><span class="sxs-lookup"><span data-stu-id="de227-175">To see all properties that you can use with a resource, insert the cursor in the resource keyword (for example, File) within your configuration script in PowerShell ISE, hold down <kbd>CTRL</kbd>+<kbd>SPACEBAR</kbd></span></span>

## <a name="find-more-resources"></a><span data-ttu-id="de227-176">HITTA FLER RESURSER</span><span class="sxs-lookup"><span data-stu-id="de227-176">FIND MORE RESOURCES</span></span>

<span data-ttu-id="de227-177">Du kan ladda ned, installera och lära dig mer om många andra tillgängliga DSC-resurser som har skapats av PowerShell-och DSC-användarens community, och av Microsoft.</span><span class="sxs-lookup"><span data-stu-id="de227-177">You can download, install, and learn about many other available DSC resources that have been created by the PowerShell and DSC user community, and by Microsoft.</span></span> <span data-ttu-id="de227-178">Besök [PowerShell-galleriet](https://www.powershellgallery.com/) för att söka efter och lära dig mer om tillgängliga DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="de227-178">Visit the [PowerShell Gallery](https://www.powershellgallery.com/) to browse and learn about available DSC resources.</span></span>

## <a name="see-also"></a><span data-ttu-id="de227-179">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="de227-179">SEE ALSO</span></span>

[<span data-ttu-id="de227-180">Översikt över Desired State Configuration för PowerShell</span><span class="sxs-lookup"><span data-stu-id="de227-180">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="de227-181">Inbyggda PowerShell-resurser för önskad tillstånds konfiguration</span><span class="sxs-lookup"><span data-stu-id="de227-181">Built-In PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/resources)

[<span data-ttu-id="de227-182">Bygg anpassade PowerShell-resurser för Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="de227-182">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)
