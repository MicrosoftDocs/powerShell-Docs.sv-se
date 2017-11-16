---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: d3a625d05eaf4e7448b4abf90499f6a94e2f7718
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="1d2c7-102">För identiska duplicerade resurser i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="1d2c7-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="1d2c7-103">DSC Tillåt inte och hantera motstridiga resursdefinitionerna i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="1d2c7-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="1d2c7-104">Istället för att försöka lösa konflikten bara misslyckas.</span><span class="sxs-lookup"><span data-stu-id="1d2c7-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="1d2c7-105">Eftersom configuration återanvändning blir mer utnyttjade genom sammansatta resurser, inträffar etc. konflikter oftare.</span><span class="sxs-lookup"><span data-stu-id="1d2c7-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="1d2c7-106">När motstridiga resursdefinitionerna är identiska bör DSC smart och att detta.</span><span class="sxs-lookup"><span data-stu-id="1d2c7-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="1d2c7-107">Med den här versionen stöder med flera instanser av resurs som har identiska definitioner:</span><span class="sxs-lookup"><span data-stu-id="1d2c7-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="1d2c7-108">I tidigare versioner av blir resultatet en misslyckad sammanställning på grund av en konflikt mellan WindowsFeature FE_IIS och WindowsFeature Worker_IIS instanser försöker kontrollera 'webbserver-rollen är installerad.</span><span class="sxs-lookup"><span data-stu-id="1d2c7-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="1d2c7-109">Observera att *alla* egenskaper som konfigureras är identiska i dessa två konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="1d2c7-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="1d2c7-110">Eftersom *alla* egenskaper i dessa två resurser är identiska, resulterar detta i en lyckad sammanställning nu.</span><span class="sxs-lookup"><span data-stu-id="1d2c7-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span> 

<span data-ttu-id="1d2c7-111">Om någon av egenskaperna skiljer sig mellan de båda resurserna de anses inte vara identiska och kompilering misslyckas:</span><span class="sxs-lookup"><span data-stu-id="1d2c7-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="1d2c7-112">Den här mycket lik konfigurationen misslyckas eftersom WindowsFeature FE_IIS WindowsFeature Worker_IIS resurser inte längre är identiska och därför är i konflikt.</span><span class="sxs-lookup"><span data-stu-id="1d2c7-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>

