---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Importera en specifik version av en resurs som är installerade
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404690"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importera en specifik version av en resurs som är installerade

> Gäller för: Windows PowerShell 5.0

Olika versioner av DSC-resurser kan installeras på en dator sida vid sida i PowerShell 5.0. En Resursmodul kan lagra olika versioner av en resurs i version med namnet mappar.

## <a name="installing-separate-resource-versions-side-by-side"></a>Installation av separat resurs versioner sida vid sida

Du kan använda den **MinimumVersion**, **MaximumVersion**, och **RequiredVersion** parametrarna för den [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet för att ange vilken version av en modul för att installera. Anropa **Install-Module** utan att ange en version som installerar den senaste versionen.

Exempel: det finns flera versioner av den **xFailOverCluster** modulen, som innehåller en **xCluster** resurs. Anropa **Install-Module** utan att ange versionen tal installerar den senaste versionen av modulen.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Om du vill installera en specifik version av en modul, ange en **RequiredVersion** av 1.1.0.0. Då installeras den angivna versionen sida vid sida med den installerade versionen.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Nu kan du se både versionen av modulen visas när du använder `Get-DSCResource`.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Ange en resurs-version i en konfiguration

Om du har en separat resurs versioner installerade på en dator, måste du ange vilken version av den här resursen när du använder den i en konfiguration. Du gör detta genom att ange den **ModuleVersion** -parametern för den **Import-DscResource** nyckelord. Om du inte ange versionen av en Resursmodul för en resurs som du har mer än en version som är installerad, genereras ett fel i konfigurationen.

Följande konfiguration visar hur du anger versionen av resursen att anropa:

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

>Obs! ModuleVersion-parametern för Import-DscResource är inte tillgänglig i PowerShell 4.0. Du kan ange en Modulversion genom att skicka ett objekt för specifikation av modulen till ModuleName-parametern för Import-DscResource i PowerShell 4.0. Ett objekt för specifikation av modulen är en hashtabell som innehåller ModuleName och RequiredVersion nycklar. Till exempel:

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

Detta fungerar även i PowerShell 5.0, men vi rekommenderar att du använder den **ModuleVersion** parametern.

## <a name="see-also"></a>Se även

- [DSC-konfigurationer](configurations.md)
- [DSC-resurser](../resources/resources.md)
