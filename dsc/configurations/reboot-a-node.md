---
ms.date: 01/17/2019
keywords: DSC, PowerShell, konfiguration, installation
title: Starta om en nod
ms.openlocfilehash: 22c63fab9b6646f522f8531b46a43a94ff883552
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322924"
---
# <a name="reboot-a-node"></a>Starta om en nod

> [!NOTE]
> Det här avsnittet innehåller information om hur du startar om en nod. För att datorn ska kunna starta om måste inställningarna för **ActionAfterReboot** och **RebootNodeIfNeeded** -LCM vara korrekt konfigurerade.
> Läs om lokala Configuration Manager inställningar i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)eller [konfigurera den lokala Configuration Manager (v4)](../managing-nodes/metaConfig4.md).

Noder kan startas om från en resurs med hjälp `$global:DSCMachineStatus` av flaggan. Om du anger den `1` här flaggan `Set-TargetResource` till i funktionen tvingas LCM att starta om noden direkt efter **set** -metoden för den aktuella resursen. Med den här flaggan identifierar **PendingReboot** -resursen i modulen [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) DSC-resurs om en omstart väntar utanför DSC.

Dina [konfigurationer](configurations.md) kan utföra steg som kräver att noden startas om. Detta kan innefatta saker som:

- Windows-uppdateringar
- Program varu installation
- Filen har bytt namn
- Dator namn

**PendingReboot** -resursen kontrollerar vissa dator platser för att avgöra om en omstart väntar. Om noden kräver en omstart utanför DSC, anger `$global:DSCMachineStatus` **PendingReboot** -resursen flaggan för att `1` tvinga fram en omstart och lösa det väntande tillståndet.

> [!NOTE]
> Alla DSC-resurser kan instruera LCM att starta om noden genom att ställa in den här `Set-TargetResource` flaggan i funktionen. Mer information finns i [skriva en anpassad DSC-resurs med MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Syntax

```
PendingReboot [String] #ResourceName
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

## <a name="properties"></a>properties

| Egenskap | Description |
| --- | --- |
| Name| Obligatorisk parameter som måste vara unik per instans av resursen inom en konfiguration.|
| SkipComponentBasedServicing | Hoppa över omstarter som utlösts av komponent-Based Servicing-komponenten. |
| SkipWindowsUpdate | Hoppa över omstarter som utlösts av Windows Update.|
| SkipPendingFileRename | Hoppa över väntande fil namn omstarter. |
| SkipCcmClientSDK | Hoppa över omstarter som utlösts av ConfigMgr-klienten. |
| SkipComputerRename | Hoppa över omstarter som utlöses av dator namn. |
| PSDSCRunAsCredential | Stöds i v5. Kör resursen som den angivna användaren. |
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är **resourceName** och dess typ är **resourcetype**, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. Mer information finns i [using DependsOn](resource-depends-on.md)|

## <a name="example"></a>Exempel

I följande exempel installeras Microsoft Exchange med hjälp av [xExchange](https://github.com/PowerShell/xExchange) -resursen.
Under installationen används **PendingReboot** -resursen för att starta om noden.

> [!NOTE]
> Det här exemplet kräver autentiseringsuppgifterna för ett konto som har behörighet att lägga till en Exchange-Server i skogen. Mer information om hur du använder autentiseringsuppgifter i DSC finns i [Hantera autentiseringsuppgifter i DSC](../configurations/configDataCredentials.md)

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
    Import-DscResource -Module ComputerManagementDsc

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
        PendingReboot BeforeExchangeInstall
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
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> I det här exemplet förutsätts att du har konfigurerat din lokala Configuration Manager att tillåta omstarter och fortsätta konfigurationen efter en omstart.

## <a name="where-to-download"></a>Var du vill ladda ned

Du kan hämta resurserna som används i det här avsnittet på följande platser eller med hjälp av PowerShell-galleriet.

- [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc)
- [xExchange](https://github.com/PowerShell/xExchange)
