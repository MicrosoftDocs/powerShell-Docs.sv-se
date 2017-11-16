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
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>För identiska duplicerade resurser i en konfiguration

DSC Tillåt inte och hantera motstridiga resursdefinitionerna i en konfiguration. Istället för att försöka lösa konflikten bara misslyckas. Eftersom configuration återanvändning blir mer utnyttjade genom sammansatta resurser, inträffar etc. konflikter oftare. När motstridiga resursdefinitionerna är identiska bör DSC smart och att detta. Med den här versionen stöder med flera instanser av resurs som har identiska definitioner:

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

I tidigare versioner av blir resultatet en misslyckad sammanställning på grund av en konflikt mellan WindowsFeature FE_IIS och WindowsFeature Worker_IIS instanser försöker kontrollera 'webbserver-rollen är installerad. Observera att *alla* egenskaper som konfigureras är identiska i dessa två konfigurationer. Eftersom *alla* egenskaper i dessa två resurser är identiska, resulterar detta i en lyckad sammanställning nu. 

Om någon av egenskaperna skiljer sig mellan de båda resurserna de anses inte vara identiska och kompilering misslyckas:

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

Den här mycket lik konfigurationen misslyckas eftersom WindowsFeature FE_IIS WindowsFeature Worker_IIS resurser inte längre är identiska och därför är i konflikt.

