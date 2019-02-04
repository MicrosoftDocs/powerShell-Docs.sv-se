---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 28f4f8ae2bbddc8fb5ef9d95d3061a91fcc8ffe2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687365"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="8e05e-102">Att tillåta identiska duplicerade resurser i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="8e05e-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="8e05e-103">DSC Tillåt inte och hantera motstridiga resursdefinitionerna i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="8e05e-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="8e05e-104">Istället för att försöka lösa konflikten, helt enkelt misslyckas det.</span><span class="sxs-lookup"><span data-stu-id="8e05e-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="8e05e-105">Eftersom konfigurationen återanvändning blir mer används via sammansatta resurser, inträffar etc. konflikter oftare.</span><span class="sxs-lookup"><span data-stu-id="8e05e-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="8e05e-106">När motstridiga resursdefinitionerna är identiska, ska DSC vara smart och ge detta.</span><span class="sxs-lookup"><span data-stu-id="8e05e-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="8e05e-107">Den här versionen har stöder vi att ha flera resursinstanser som har identiska definitioner:</span><span class="sxs-lookup"><span data-stu-id="8e05e-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="8e05e-108">I tidigare versioner blir resultatet en misslyckad sammanställning på grund av en konflikt mellan WindowsFeature FE_IIS och WindowsFeature Worker_IIS instanser försöker se till att ”webbserver-rollen är installerad.</span><span class="sxs-lookup"><span data-stu-id="8e05e-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="8e05e-109">Observera att *alla* egenskaper som konfigureras är identiska i dessa två konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="8e05e-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="8e05e-110">Eftersom *alla* egenskaper i dessa två resurser är identiska, detta resulterar i en lyckad sammanställning nu.</span><span class="sxs-lookup"><span data-stu-id="8e05e-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="8e05e-111">Om någon av egenskaperna skiljer sig mellan de två resurserna, anses inte vara identiska och kompilering misslyckas:</span><span class="sxs-lookup"><span data-stu-id="8e05e-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

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

<span data-ttu-id="8e05e-112">Den här mycket lik konfigurationen misslyckas eftersom WindowsFeature FE_IIS och resurserna som WindowsFeature Worker_IIS inte längre är identiska och därför står i konflikt.</span><span class="sxs-lookup"><span data-stu-id="8e05e-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
