---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 28f4f8ae2bbddc8fb5ef9d95d3061a91fcc8ffe2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058734"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Att tillåta identiska duplicerade resurser i en konfiguration

DSC Tillåt inte och hantera motstridiga resursdefinitionerna i en konfiguration. Istället för att försöka lösa konflikten, helt enkelt misslyckas det. Eftersom konfigurationen återanvändning blir mer används via sammansatta resurser, inträffar etc. konflikter oftare. När motstridiga resursdefinitionerna är identiska, ska DSC vara smart och ge detta. Den här versionen har stöder vi att ha flera resursinstanser som har identiska definitioner:

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

I tidigare versioner blir resultatet en misslyckad sammanställning på grund av en konflikt mellan WindowsFeature FE_IIS och WindowsFeature Worker_IIS instanser försöker se till att ”webbserver-rollen är installerad. Observera att *alla* egenskaper som konfigureras är identiska i dessa två konfigurationer. Eftersom *alla* egenskaper i dessa två resurser är identiska, detta resulterar i en lyckad sammanställning nu.

Om någon av egenskaperna skiljer sig mellan de två resurserna, anses inte vara identiska och kompilering misslyckas:

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

Den här mycket lik konfigurationen misslyckas eftersom WindowsFeature FE_IIS och resurserna som WindowsFeature Worker_IIS inte längre är identiska och därför står i konflikt.
