---
ms.date: 1/17/2019
keywords: DSC, powershell, konfiguration, installation
title: Starta om en nod
ms.openlocfilehash: 015b82a32caefc420973651c72e272fd85baf880
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054738"
---
# <a name="reboot-a-node"></a>Starta om en nod

> [!NOTE]
> Det här avsnittet vi berättar hur du starta om en nod. För att omstart ska lyckas den **ActionAfterReboot** och **RebootNodeIfNeeded** LCM inställningar måste konfigureras korrekt.
> Mer information om lokala Configuration Manager-inställningar, se [konfigurera den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md), eller [konfigurera den lokala Konfigurationshanteraren (v4)](../managing-nodes/metaConfig4.md).

Noder kan startas från inom en resurs med hjälp av den `$global:DSCMachineStatus` flaggan. Ställa in den här flaggan `1` i den `Set-TargetResource` funktionen tvingar MGM om du vill starta om noden direkt efter den **ange** -metoden för den aktuella resursen. Med den här flaggan den **xPendingReboot** resurs identifierar om en omstart väntar utanför DSC.

Din [konfigurationer](configurations.md) kan utföra åtgärder som kräver noden ska startas om. Det kan innefatta saker som:

- Windows-uppdateringar
- Programinstallation
- Byter namn på fil
- Byt namn på datorn

Den **xPendingReboot** resource kontrollerar specifik dator platser för att avgöra om en omstart väntar. Om noden måste startas om utanför DSC, den **xPendingReboot** resurs anger den `$global:DSCMachineStatus` flaggan till `1` tvingar fram en omstart och lösa väntande villkoret.

> [!NOTE]
> Alla DSC-resurser kan instruera MGM om du vill starta om noden genom att ange den här flaggan i den `Set-TargetResource` funktion. Mer information finns i [skriva en anpassad DSC-resurs med MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Syntax

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>Egenskaper

| Egenskap | Beskrivning |
| --- | --- |
| Namn| Den obligatoriska parametern måste vara unikt för varje instans av resurs i en konfiguration.|
| SkipComponentBasedServicing | Hoppa över omstarter som utlöses av komponenten Component-Based Servicing. |
| SkipWindowsUpdate | Hoppa över omstarter som utlöses av Windows Update.|
| SkipPendingFileRename | Hoppa över väntar på Byt namn på omstarter. |
| SkipCcmClientSDK | Hoppa över omstarter som utlöses av ConfigMgr-klienten. |
| SkipComputerRename | Hoppa över omstarter som utlöses av datorn byter namn på. |
| PSDSCRunAsCredential | Stöd i v5. Kör resursen som den angivna användaren. |
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`. Mer information finns i [använder DependsOn](resource-depends-on.md)|

## <a name="example"></a>Exempel

I följande exempel installeras Microsoft Exchange med hjälp av den [xExchange](https://github.com/PowerShell/xExchange) resurs.
Under installationen den **xPendingReboot** resursen används för att starta om noden.

> [!NOTE]
> Det här exemplet kräver autentiseringsuppgifter för ett konto som har behörighet att lägga till en Exchange-server i skogen. Mer information om hur du använder autentiseringsuppgifter i DSC finns [hantering av autentiseringsuppgifter i DSC](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> Det här exemplet förutsätts att du har konfigurerat din lokala Configuration Manager för att tillåta omstarter och fortsätta konfigurationen efter en omstart.

## <a name="where-to-download"></a>Var du hämtar

Du kan hämta de resurser som används i det här avsnittet på följande platser eller med hjälp av PowerShell-galleriet.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
