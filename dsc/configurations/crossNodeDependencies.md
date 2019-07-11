---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Ange beroenden mellan noder
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734683"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="1db66-103">Ange beroenden mellan noder</span><span class="sxs-lookup"><span data-stu-id="1db66-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="1db66-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1db66-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1db66-105">DSC tillhandahåller särskilda resurser **WaitForAll**, **WaitForAny**, och **WaitForSome** som kan användas i konfigurationer ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="1db66-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="1db66-106">Beteendet för dessa resurser är följande:</span><span class="sxs-lookup"><span data-stu-id="1db66-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="1db66-107">**WaitForAll**: Lyckas om den angivna resursen är i önskat läge på alla målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="1db66-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="1db66-108">**WaitForAny**: Lyckas om den angivna resursen är i önskat läge på minst en av målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="1db66-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="1db66-109">**WaitForSome**: Anger en **NodeCount** egenskapen förutom en **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="1db66-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="1db66-110">Resursen lyckas om resursen ligger i önskat läge på minsta antalet noder (anges av **NodeCount**) definieras av den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="1db66-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="1db66-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="1db66-111">Syntax</span></span>

<span data-ttu-id="1db66-112">Den **WaitForAll** och **WaitForAny** resurser dela samma syntax.</span><span class="sxs-lookup"><span data-stu-id="1db66-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="1db66-113">Ersätt \<ResourceType\> i exemplet nedan med antingen **WaitForAny** eller **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="1db66-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="1db66-114">Som den **DependsOn** nyckelord, måste du formatera namn som ”[ResourceType] ResourceName”.</span><span class="sxs-lookup"><span data-stu-id="1db66-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="1db66-115">Om resursen som hör till en separat [Configuration](configurations.md), innehåller den **ConfigurationName** i den formaterade strängen ”[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]”.</span><span class="sxs-lookup"><span data-stu-id="1db66-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="1db66-116">Den **nodnamn** är datorn eller noden där den aktuella resursen ska vänta.</span><span class="sxs-lookup"><span data-stu-id="1db66-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="1db66-117">Den **WaitForSome** resurs har en liknande syntax i exemplet ovan, men lägger till den **NodeCount** nyckel.</span><span class="sxs-lookup"><span data-stu-id="1db66-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="1db66-118">Den **NodeCount** anger hur många noder som den aktuella resursen ska vänta på.</span><span class="sxs-lookup"><span data-stu-id="1db66-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

<span data-ttu-id="1db66-119">Alla **WaitForXXXX** dela följande syntax nycklar.</span><span class="sxs-lookup"><span data-stu-id="1db66-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="1db66-120">Egenskap</span><span class="sxs-lookup"><span data-stu-id="1db66-120">Property</span></span>|  <span data-ttu-id="1db66-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1db66-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="1db66-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="1db66-122">RetryIntervalSec</span></span>| <span data-ttu-id="1db66-123">Antal sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="1db66-123">The number of seconds before retrying.</span></span> <span data-ttu-id="1db66-124">Minimum är 1.</span><span class="sxs-lookup"><span data-stu-id="1db66-124">Minimum is 1.</span></span>|
| <span data-ttu-id="1db66-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="1db66-125">RetryCount</span></span>| <span data-ttu-id="1db66-126">Det maximala antalet gånger att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="1db66-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="1db66-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="1db66-127">ThrottleLimit</span></span>| <span data-ttu-id="1db66-128">Antal datorer kan ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="1db66-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="1db66-129">Standardvärdet är `New-CimSession` standard.</span><span class="sxs-lookup"><span data-stu-id="1db66-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="1db66-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1db66-130">DependsOn</span></span> | <span data-ttu-id="1db66-131">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="1db66-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1db66-132">Mer information finns i [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="1db66-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="1db66-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1db66-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="1db66-134">Se [med hjälp av DSC med autentiseringsuppgifterna för användaren](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="1db66-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="1db66-135">Använda WaitForXXXX resurser</span><span class="sxs-lookup"><span data-stu-id="1db66-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="1db66-136">Varje **WaitForXXXX** resurs ska vänta tills de angivna resurserna skulle bli klart på den angivna noden.</span><span class="sxs-lookup"><span data-stu-id="1db66-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="1db66-137">Andra resurser i samma konfiguration kan sedan *beror på* den **WaitForXXXX** resursen med hjälp av den **DependsOn** nyckel.</span><span class="sxs-lookup"><span data-stu-id="1db66-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="1db66-138">Till exempel i följande konfiguration målnoden väntar på den **xADDomain** resurs ska slutföras på den **MyDC** nod med maximalt antal 30 återförsök, med 15-sekunder intervall, innan den målnoden kan ansluta till domänen.</span><span class="sxs-lookup"><span data-stu-id="1db66-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="1db66-139">Som standard den **WaitForXXX** resurser prova en gång och sedan misslyckas.</span><span class="sxs-lookup"><span data-stu-id="1db66-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="1db66-140">Även om det inte krävs, vill du förmodligen att ange en **RetryCount** och **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="1db66-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="1db66-141">När du kompilera konfigurationen, genereras två MOF-filerna.</span><span class="sxs-lookup"><span data-stu-id="1db66-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="1db66-142">Gäller både MOF-filerna för Målnoder med hjälp av den [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span><span class="sxs-lookup"><span data-stu-id="1db66-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="1db66-143">**WaitForXXX** resurser använda Windows Remote Management för att kontrollera tillståndet hos andra noder.</span><span class="sxs-lookup"><span data-stu-id="1db66-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="1db66-144">Läs mer om port och säkerhetskrav för WinRM [säkerhetsöverväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="1db66-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="1db66-145">Se även</span><span class="sxs-lookup"><span data-stu-id="1db66-145">See Also</span></span>

- [<span data-ttu-id="1db66-146">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="1db66-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="1db66-147">Använda resursberoenden</span><span class="sxs-lookup"><span data-stu-id="1db66-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="1db66-148">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="1db66-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="1db66-149">Konfigurera den lokala Konfigurationshanteraren</span><span class="sxs-lookup"><span data-stu-id="1db66-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
