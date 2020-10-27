---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Importera en specifik version av en installerad resurs
description: Den här artikeln visar hur du installerar och importerar vissa versioner av resurspooler till dina konfigurationer.
ms.openlocfilehash: bb7b3273a5a3fed94fecd90dd3ea1e623fbc332b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645050"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importera en specifik version av en installerad resurs

> Gäller för: Windows PowerShell 5,0

I PowerShell 5,0 kan separata versioner av DSC-resurser installeras på en dator sida vid sida. En resurs-modul kan lagra separata versioner av en resurs i versions namn mappar.

## <a name="installing-separate-resource-versions-side-by-side"></a>Installera separata resurs versioner sida vid sida

Du kan använda parametrarna **MinimumVersion** , **MaximumVersion** och **RequiredVersion** för cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att ange vilken version av en modul som ska installeras. Att anropa **install-module** utan att ange en version installerar den senaste versionen.

Det finns till exempel flera versioner av **xFailOverCluster** -modulen, som var och en innehåller en **xCluster** -resurs. Anrop av **install-module** utan att ange versions numret installerar den senaste versionen av modulen.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName           Version    Properties
-------------   ----          ----------           -------    ----------
PowerShell      xCluster      xFailOverCluster     1.2.0.0    {DomainAdministratorCredential, ...
```

Om du vill installera en angiven version av en modul anger du en **RequiredVersion** för 1.1.0.0. Detta installerar den angivna versionen sida vid sida med den installerade versionen.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Nu ser du båda versionerna av modulen som visas när du använder `Get-DSCResource` .

```powershell
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName            Version    Properties
-------------   ----          ----------            -------    ----------
PowerShell      xCluster      xFailOverCluster      1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster      xFailOverCluster      1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Ange en resurs version i en konfiguration

Om du har separata resurs versioner installerade på en dator måste du ange den här resursens version när du använder den i en konfiguration. Du gör detta genom att ange parametern **ModuleVersion** för nyckelordet **import-dscresource Keyword Supports** . Om du inte anger versionen av en resurspool för en resurs där du har mer än en version installerad, genererar konfigurationen ett fel.

Följande konfiguration visar hur du anger vilken version av resursen som ska anropas:

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

ModuleVersion-parametern för Import-DscResource är inte tillgänglig i PowerShell 4,0. I PowerShell 4,0 kan du ange en modul version genom att skicka ett modul Specifikations objekt till Modulnamn-parametern för import-Dscresource Keyword Supports. Ett modul Specifikations objekt är en hash-tabell som innehåller Modulnamn-och RequiredVersion-nycklar. Exempel:

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

Detta fungerar även i PowerShell 5,0, men vi rekommenderar att du använder parametern **ModuleVersion** .

## <a name="see-also"></a>Se även

- [DSC-konfigurationer](configurations.md)
- [DSC-resurser](../resources/resources.md)
