---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Ange beroenden mellan noder
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942057"
---
# <a name="specifying-cross-node-dependencies"></a>Ange beroenden mellan noder

> Gäller för: Windows PowerShell 5,0

DSC tillhandahåller särskilda resurser, **WaitForAll**, **WaitForAny**och **WaitForSome** som kan användas i konfigurationer för att ange beroenden för konfigurationer på andra noder. Funktionerna för dessa resurser är följande:

- **WaitForAll**: lyckas om den angivna resursen har önskat tillstånd på alla målnod som definierats i egenskapen **nodnamn** .
- **WaitForAny**: lyckas om den angivna resursen har önskat tillstånd på minst en av de målattribut som definierats i egenskapen **nodnamn** .
- **WaitForSome**: anger en **NodeCount** -egenskap, förutom en **nodnamn** -egenskap. Resursen slutförs om resursen har önskat tillstånd på ett minsta antal noder (anges av **NodeCount**) som definieras av egenskapen **nodnamn** .

## <a name="syntax"></a>Syntax

**WaitForAll** -och **WaitForAny** -resurserna delar samma syntax. Ersätt \<ResourceType\> i exemplet nedan med antingen **WaitForAny** eller **WaitForAll**.
Precis som nyckelordet **DependsOn** måste du formatera namnet som "[resourcetype] resourcename". Om resursen tillhör en separat [konfiguration](configurations.md)inkluderar du **ConfigurationName** i den formaterade strängen "[resourcetype] resourceName:: [ConfigurationName]:: [ConfigurationName]". **Nodnamn** är den dator eller nod som den aktuella resursen ska vänta på.

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

**WaitForSome** -resursen har samma syntax som i exemplet ovan, men lägger till **NodeCount** -nyckeln. **NodeCount** anger hur många noder den aktuella resursen ska vänta på.

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

Alla **WaitForXXXX** delar följande syntax nycklar.

|Egenskap|  Description   |
|---------|---------------------|
| RetryIntervalSec| Antalet sekunder innan nytt försök. Minimivärdet är 1.|
| RetryCount| Det maximala antalet försök att försöka igen.|
| ThrottleLimit| Antal datorer som ska anslutas samtidigt. Standardvärdet är `New-CimSession` standard.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Mer information finns i [DependsOn](resource-depends-on.md)|
| PsDscRunAsCredential | Se [använda DSC med](./runAsUser.md) användarautentiseringsuppgifter |

## <a name="using-waitforxxxx-resources"></a>Använda WaitForXXXX-resurser

Varje **WaitForXXXX** -resurs väntar på att de angivna resurserna ska slutföras på den angivna noden.
Andra resurser i samma konfiguration kan sedan *vara beroende* av **WaitForXXXX** -resursen med hjälp av **DependsOn** -nyckeln.

I följande konfiguration väntar målnoden till exempel på att **xADDomain** -resursen ska avslutas på **MyDC** -noden med maximalt antal 30 återförsök, med 15 sekunders intervall, innan målnoden kan ansluta till domänen.

Som standard försöker **WaitForXXX** -resurserna en gång och sedan misslyckats. Även om det inte är obligatoriskt, vill du normalt ange en **RetryCount** och **RetryIntervalSec**.

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

När du kompilerar konfigurationen genereras två ". MOF"-filer. Tillämpa båda filerna ". MOF" på målnoden med cmdleten [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)

> [!NOTE]
> **WaitForXXX** -resurser använder Windows Remote Management för att kontrol lera status för andra noder.
> Mer information om port-och säkerhets krav för WinRM finns i [säkerhets överväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="see-also"></a>Se även

- [DSC-konfigurationer](configurations.md)
- [Använd resurs beroenden](resource-depends-on.md)
- [DSC-resurser](../resources/resources.md)
- [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)
