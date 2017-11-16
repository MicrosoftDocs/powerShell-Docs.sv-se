---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Ange beroenden mellan noder
ms.openlocfilehash: 885c130fb050629aac4c072e18a147d77b9deb8f
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2017
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="f235e-103">Ange beroenden mellan noder</span><span class="sxs-lookup"><span data-stu-id="f235e-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="f235e-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f235e-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f235e-105">DSC innehåller särskilda resurser **WaitForAll**, **WaitForAny**, och **WaitForSome** som kan användas i konfigurationerna för att ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="f235e-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="f235e-106">Beteendet för dessa resurser är följande:</span><span class="sxs-lookup"><span data-stu-id="f235e-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="f235e-107">**WaitForAll**: lyckas om den angivna resursen är i tillståndet önskade på alla målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f235e-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="f235e-108">**WaitForAny**: lyckas om den angivna resursen är i tillståndet önskade på minst en av målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f235e-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="f235e-109">**WaitForSome**: Anger en **NodeCount** egenskapen förutom en **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f235e-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="f235e-110">Resursen lyckas om resursen är i ett minsta antal noder önskade tillstånd (anges av **NodeCount**) definieras av den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f235e-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="f235e-111">Använda WaitForXXXX resurser</span><span class="sxs-lookup"><span data-stu-id="f235e-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="f235e-112">Att använda den **WaitForXXXX** resurser, som du skapar en resurs block på den resurstyp som anger DSC-resurs och noderna vänta.</span><span class="sxs-lookup"><span data-stu-id="f235e-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="f235e-113">Du sedan använda den **DependsOn** egenskap i någon annan resurs blockerar i konfigurationen för de villkor som anges i den **WaitForXXXX** noden ska lyckas.</span><span class="sxs-lookup"><span data-stu-id="f235e-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="f235e-114">Till exempel i följande konfiguration målnoden väntar på den **xADDomain** resurs till slut på den **MyDC** nod med maximalt antal 30 återförsök, med 15 sekunder intervall, innan den målnoden kan ansluta till domänen.</span><span class="sxs-lookup"><span data-stu-id="f235e-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

><span data-ttu-id="f235e-115">**Obs:** som standard WaitForXXX resurser försök en gång och sedan inte.</span><span class="sxs-lookup"><span data-stu-id="f235e-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="f235e-116">Även om det inte krävs, vill du förmodligen ange återförsöksintervall och count.</span><span class="sxs-lookup"><span data-stu-id="f235e-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="f235e-117">Se även</span><span class="sxs-lookup"><span data-stu-id="f235e-117">See Also</span></span>
* [<span data-ttu-id="f235e-118">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="f235e-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="f235e-119">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="f235e-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="f235e-120">Konfigurera den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="f235e-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

