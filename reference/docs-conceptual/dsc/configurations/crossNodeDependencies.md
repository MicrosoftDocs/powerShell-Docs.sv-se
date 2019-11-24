---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Ange beroenden mellan noder
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942057"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="b9930-103">Ange beroenden mellan noder</span><span class="sxs-lookup"><span data-stu-id="b9930-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="b9930-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="b9930-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b9930-105">DSC tillhandahåller särskilda resurser, **WaitForAll**, **WaitForAny**och **WaitForSome** som kan användas i konfigurationer för att ange beroenden för konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="b9930-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="b9930-106">Funktionerna för dessa resurser är följande:</span><span class="sxs-lookup"><span data-stu-id="b9930-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="b9930-107">**WaitForAll**: lyckas om den angivna resursen har önskat tillstånd på alla målnod som definierats i egenskapen **nodnamn** .</span><span class="sxs-lookup"><span data-stu-id="b9930-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="b9930-108">**WaitForAny**: lyckas om den angivna resursen har önskat tillstånd på minst en av de målattribut som definierats i egenskapen **nodnamn** .</span><span class="sxs-lookup"><span data-stu-id="b9930-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="b9930-109">**WaitForSome**: anger en **NodeCount** -egenskap, förutom en **nodnamn** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="b9930-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="b9930-110">Resursen slutförs om resursen har önskat tillstånd på ett minsta antal noder (anges av **NodeCount**) som definieras av egenskapen **nodnamn** .</span><span class="sxs-lookup"><span data-stu-id="b9930-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9930-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9930-111">Syntax</span></span>

<span data-ttu-id="b9930-112">**WaitForAll** -och **WaitForAny** -resurserna delar samma syntax.</span><span class="sxs-lookup"><span data-stu-id="b9930-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="b9930-113">Ersätt \<ResourceType\> i exemplet nedan med antingen **WaitForAny** eller **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="b9930-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="b9930-114">Precis som nyckelordet **DependsOn** måste du formatera namnet som "[resourcetype] resourcename".</span><span class="sxs-lookup"><span data-stu-id="b9930-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="b9930-115">Om resursen tillhör en separat [konfiguration](configurations.md)inkluderar du **ConfigurationName** i den formaterade strängen "[resourcetype] resourceName:: [ConfigurationName]:: [ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="b9930-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="b9930-116">**Nodnamn** är den dator eller nod som den aktuella resursen ska vänta på.</span><span class="sxs-lookup"><span data-stu-id="b9930-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="b9930-117">**WaitForSome** -resursen har samma syntax som i exemplet ovan, men lägger till **NodeCount** -nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b9930-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="b9930-118">**NodeCount** anger hur många noder den aktuella resursen ska vänta på.</span><span class="sxs-lookup"><span data-stu-id="b9930-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="b9930-119">Alla **WaitForXXXX** delar följande syntax nycklar.</span><span class="sxs-lookup"><span data-stu-id="b9930-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="b9930-120">Egenskap</span><span class="sxs-lookup"><span data-stu-id="b9930-120">Property</span></span>|  <span data-ttu-id="b9930-121">Description</span><span class="sxs-lookup"><span data-stu-id="b9930-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="b9930-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="b9930-122">RetryIntervalSec</span></span>| <span data-ttu-id="b9930-123">Antalet sekunder innan nytt försök.</span><span class="sxs-lookup"><span data-stu-id="b9930-123">The number of seconds before retrying.</span></span> <span data-ttu-id="b9930-124">Minimivärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="b9930-124">Minimum is 1.</span></span>|
| <span data-ttu-id="b9930-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="b9930-125">RetryCount</span></span>| <span data-ttu-id="b9930-126">Det maximala antalet försök att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="b9930-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="b9930-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b9930-127">ThrottleLimit</span></span>| <span data-ttu-id="b9930-128">Antal datorer som ska anslutas samtidigt.</span><span class="sxs-lookup"><span data-stu-id="b9930-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="b9930-129">Standardvärdet är `New-CimSession` standard.</span><span class="sxs-lookup"><span data-stu-id="b9930-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="b9930-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b9930-130">DependsOn</span></span> | <span data-ttu-id="b9930-131">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="b9930-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b9930-132">Mer information finns i [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="b9930-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="b9930-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b9930-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="b9930-134">Se [använda DSC med](./runAsUser.md) användarautentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="b9930-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="b9930-135">Använda WaitForXXXX-resurser</span><span class="sxs-lookup"><span data-stu-id="b9930-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="b9930-136">Varje **WaitForXXXX** -resurs väntar på att de angivna resurserna ska slutföras på den angivna noden.</span><span class="sxs-lookup"><span data-stu-id="b9930-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="b9930-137">Andra resurser i samma konfiguration kan sedan *vara beroende* av **WaitForXXXX** -resursen med hjälp av **DependsOn** -nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b9930-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="b9930-138">I följande konfiguration väntar målnoden till exempel på att **xADDomain** -resursen ska avslutas på **MyDC** -noden med maximalt antal 30 återförsök, med 15 sekunders intervall, innan målnoden kan ansluta till domänen.</span><span class="sxs-lookup"><span data-stu-id="b9930-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="b9930-139">Som standard försöker **WaitForXXX** -resurserna en gång och sedan misslyckats.</span><span class="sxs-lookup"><span data-stu-id="b9930-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="b9930-140">Även om det inte är obligatoriskt, vill du normalt ange en **RetryCount** och **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="b9930-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

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

<span data-ttu-id="b9930-141">När du kompilerar konfigurationen genereras två ". MOF"-filer.</span><span class="sxs-lookup"><span data-stu-id="b9930-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="b9930-142">Tillämpa båda filerna ". MOF" på målnoden med cmdleten [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)</span><span class="sxs-lookup"><span data-stu-id="b9930-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="b9930-143">**WaitForXXX** -resurser använder Windows Remote Management för att kontrol lera status för andra noder.</span><span class="sxs-lookup"><span data-stu-id="b9930-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="b9930-144">Mer information om port-och säkerhets krav för WinRM finns i [säkerhets överväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="b9930-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9930-145">Se även</span><span class="sxs-lookup"><span data-stu-id="b9930-145">See Also</span></span>

- [<span data-ttu-id="b9930-146">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="b9930-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="b9930-147">Använd resurs beroenden</span><span class="sxs-lookup"><span data-stu-id="b9930-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="b9930-148">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="b9930-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="b9930-149">Konfigurera den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="b9930-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
