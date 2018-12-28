---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Ange beroenden mellan noder
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404684"
---
# <a name="specifying-cross-node-dependencies"></a>Ange beroenden mellan noder

> Gäller för: Windows PowerShell 5.0

DSC tillhandahåller särskilda resurser **WaitForAll**, **WaitForAny**, och **WaitForSome** som kan användas i konfigurationer ange beroenden på konfigurationer på andra noder. Beteendet för dessa resurser är följande:

- **WaitForAll**: Lyckas om den angivna resursen är i önskat läge på alla målnoder som definierats i den **nodnamn** egenskapen.
- **WaitForAny**: Lyckas om den angivna resursen är i önskat läge på minst en av målnoder som definierats i den **nodnamn** egenskapen.
- **WaitForSome**: Anger en **NodeCount** egenskapen förutom en **nodnamn** egenskapen. Resursen lyckas om resursen ligger i önskat läge på minsta antalet noder (anges av **NodeCount**) definieras av den **nodnamn** egenskapen.

## <a name="syntax"></a>Syntax

Den **WaitForAll** och **WaitForAny** resurser dela samma syntax. Ersätt \<ResourceType\> i exemplet nedan med antingen **WaitForAny** eller **WaitForAll**.
Som den **DependsOn** nyckelord, måste du formatera namn som ”[ResourceType] ResourceName”. Om resursen som hör till en separat [Configuration](configurations.md), innehåller den **ConfigurationName** i den formaterade strängen ”[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]”. Den **nodnamn** är datorn eller noden där den aktuella resursen ska vänta.

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

Den **WaitForSome** resurs har en liknande syntax i exemplet ovan, men lägger till den **NodeCount** nyckel. Den **NodeCount** anger hur många noder som den aktuella resursen ska vänta på.

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

Alla **WaitForXXXX** dela följande syntax nycklar.

|  Egenskapen |  Beskrivning av || RetryIntervalSec | Antal sekunder innan du försöker igen. Minimum är 1. | | RetryCount | Det maximala antalet nya försök. | | ThrottleLimit | Antal datorer kan ansluta samtidigt. Standardvärdet är `New-CimSession` standard. | | DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Mer information finns i [DependsOn](resource-depends-on.md)|| PsDscRunAsCredential | Se [med hjälp av DSC med autentiseringsuppgifterna för användaren](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>Använda WaitForXXXX resurser

Varje **WaitForXXXX** resurs ska vänta tills de angivna resurserna skulle bli klart på den angivna noden. Andra resurser i samma konfiguration kan sedan *beror på* den **WaitForXXXX** resursen med hjälp av den **DependsOn** nyckel.

Till exempel i följande konfiguration målnoden väntar på den **xADDomain** resurs ska slutföras på den **MyDC** nod med maximalt antal 30 återförsök, med 15-sekunder intervall, innan den målnoden kan ansluta till domänen.

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

När du kompilera konfigurationen, genereras två MOF-filerna. Gäller både MOF-filerna för Målnoder med hjälp av den [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet

>**Obs:** Som standard WaitForXXX resurser försök en gång och sedan misslyckas. Även om det inte krävs, vill du förmodligen att ange en **RetryCount** och **RetryIntervalSec**.

## <a name="see-also"></a>Se även

- [DSC-konfigurationer](configurations.md)
- [Använda resursberoenden](resource-depends-on.md)
- [DSC-resurser](../resources/resources.md)
- [Konfigurera den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md)
