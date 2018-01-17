---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Ange beroenden mellan noder
ms.openlocfilehash: f4411161d819d96803f57600646409d5bfe827b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="6cd75-103">Ange beroenden mellan noder</span><span class="sxs-lookup"><span data-stu-id="6cd75-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="6cd75-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6cd75-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6cd75-105">DSC innehåller särskilda resurser **WaitForAll**, **WaitForAny**, och **WaitForSome** som kan användas i konfigurationerna för att ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="6cd75-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="6cd75-106">Beteendet för dessa resurser är följande:</span><span class="sxs-lookup"><span data-stu-id="6cd75-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="6cd75-107">**WaitForAll**: lyckas om den angivna resursen är i tillståndet önskade på alla målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6cd75-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="6cd75-108">**WaitForAny**: lyckas om den angivna resursen är i tillståndet önskade på minst en av målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6cd75-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="6cd75-109">**WaitForSome**: Anger en **NodeCount** egenskapen förutom en **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6cd75-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="6cd75-110">Resursen lyckas om resursen är i ett minsta antal noder önskade tillstånd (anges av **NodeCount**) definieras av den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6cd75-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="6cd75-111">Använda WaitForXXXX resurser</span><span class="sxs-lookup"><span data-stu-id="6cd75-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="6cd75-112">Att använda den **WaitForXXXX** resurser, som du skapar en resurs block på den resurstyp som anger DSC-resurs och noderna vänta.</span><span class="sxs-lookup"><span data-stu-id="6cd75-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="6cd75-113">Du sedan använda den **DependsOn** egenskap i någon annan resurs blockerar i konfigurationen för de villkor som anges i den **WaitForXXXX** noden ska lyckas.</span><span class="sxs-lookup"><span data-stu-id="6cd75-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="6cd75-114">Till exempel i följande konfiguration målnoden väntar på den **xADDomain** resurs till slut på den **MyDC** nod med maximalt antal 30 återförsök, med 15 sekunder intervall, innan den målnoden kan ansluta till domänen.</span><span class="sxs-lookup"><span data-stu-id="6cd75-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

><span data-ttu-id="6cd75-115">**Obs:** som standard WaitForXXX resurser försök en gång och sedan inte.</span><span class="sxs-lookup"><span data-stu-id="6cd75-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="6cd75-116">Även om det inte krävs, vill du förmodligen ange återförsöksintervall och count.</span><span class="sxs-lookup"><span data-stu-id="6cd75-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cd75-117">Se även</span><span class="sxs-lookup"><span data-stu-id="6cd75-117">See Also</span></span>
* [<span data-ttu-id="6cd75-118">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6cd75-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="6cd75-119">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="6cd75-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="6cd75-120">Konfigurera den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="6cd75-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

