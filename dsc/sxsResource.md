---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Använder resurser med flera versioner"
ms.openlocfilehash: 8bd8b1dab9418c6d8cf64cd682c527a7f039cdb4
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="using-resources-with-multiple-versions"></a>Använder resurser med flera versioner

> Gäller för: Windows PowerShell 5.0

I PowerShell 5.0 DSC-resurser kan ha flera versioner och versioner kan installeras på en dator sida-vid-sida. Det har implementerats genom att låta flera versioner av en Resursmodul som ingår i samma modul mapp.

## <a name="installing-multiple-resource-versions-side-by-side"></a>Installera flera resurs versioner sida-vid-sida

Du kan använda den **MinimumVersion**, **MaximumVersion**, och **RequiredVersion** parametrarna för den [installera modulen](https://technet.microsoft.com/en-us/library/dn807162.aspx) för att ange vilken version av en modul som ska installeras. Anropar **installera modulen** utan att ange en version som installerar den senaste versionen.

Det finns till exempel flera versioner av den **xFailOverCluster** modul, som innehåller en **xCluster** resurs. Resultatet av anropar **installera modulen** utan att ange versionen numret är följande:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Nu om du anropar **installera modulen** igen, men anger en **RequiredVersion** av 1.1.0.0, den resulterar i följande:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Ange en resurs-version i en konfiguration

Om du har flera resurser som är installerad på en dator, måste du ange versionen av den här resursen när du använder den i en konfiguration. Det gör du genom att ange den **ModuleVersion** parameter för den **importera DscResource** nyckelord. Om du inte ange version för en Resursmodul för en resurs som du har mer än en version som är installerad, genererar ett fel i konfigurationen.

Följande konfiguration visas hur du anger versionen av resursen ska anropa:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

>Obs: Parametern ModuleVersion för Import-DscResource är inte tillgänglig i PowerShell 4.0. Du kan ange en Modulversion genom att skicka en specifikation Modulobjekt till ModuleName-parametern för Import-DscResource i PowerShell 4.0. En modul specifikation objektet är en hash-tabell som innehåller Modulnamn och RequiredVersion nycklar. Till exempel:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

Detta fungerar också i PowerShell 5.0, men det rekommenderas att du använder den **ModuleVersion** parameter.

## <a name="see-also"></a>Se även
* [DSC-konfigurationer](configurations.md)
* [DSC-resurser](resources.md)

