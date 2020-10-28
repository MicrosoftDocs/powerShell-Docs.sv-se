---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera LCM i PowerShell 4.0
description: Den lokala Configuration Manager (LCM) körs på varje målnod och ansvarar för att parsa och tillämpa konfigurationer som skickas till noden.
ms.openlocfilehash: cf4d8cffdb6492f9f8cdde4cbb82ba5843427cee
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646966"
---
# <a name="configuring-the-lcm-in-powershell-40"></a>Konfigurera LCM i PowerShell 4.0

>Gäller för: Windows PowerShell 4,0

**Information som rör Windows PowerShell 5,0 och senare finns i [Konfigurera den lokala Configuration Manager](metaConfig.md).**

Local Configuration Manager är DSC-motorn (Desired State Configuration) för Windows PowerShell. Den körs på alla målnod och ansvarar för att anropa konfigurations resurserna som ingår i ett DSC-konfigurations skript. I det här avsnittet visas egenskaperna för lokala Configuration Manager och hur du kan ändra de lokala Configuration Manager inställningarna på en målnod.

## <a name="local-configuration-manager-properties"></a>Egenskaper för lokal Configuration Manager

I följande lista visas de lokala Configuration Manager egenskaper som du kan ange eller hämta.

- **AllowModuleOverwrite** : styr om nya konfigurationer som hämtas från konfigurations tjänsten tillåts skriva över de gamla på målnoden. Möjliga värden är true och false.
- **CertificateID** : tumavtrycket för ett certifikat som används för att skydda autentiseringsuppgifter som skickas i en konfiguration. Mer information finns i [vill du skydda autentiseringsuppgifter i Windows PowerShell Desired State Configuration?](https://devblogs.microsoft.com/powershell/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).
- **ConfigurationID** : anger ett GUID som används för att hämta en viss konfigurations fil från en pull-tjänst. GUID ser till att rätt konfigurations fil används.
- **ConfigurationMode** : anger hur den lokala Configuration Manager faktiskt tillämpar konfigurationen på målnoden. Det kan ha följande värden:
  - **ApplyOnly** : med det här alternativet tillämpar DSC konfigurationen och sker inte ytterligare om inte en ny konfiguration identifieras, antingen genom att du skickar en ny konfiguration direkt till målnoden eller om du ansluter till en pull-tjänst och DSC identifierar en ny konfiguration när den kontrollerar pull-tjänsten. Ingen åtgärd vidtas om nodens konfigurations riktning används.
  - **ApplyAndMonitor** : med det här alternativet (som är standard) använder DSC alla nya konfigurationer, oavsett om de skickas direkt till målnoden eller identifieras i en pull-tjänst.
    Därefter, om konfigurationen av mål noden går från konfigurations filen, rapporterar DSC den avvikelsen i loggarna. Mer information om DSC-loggning finns i [använda händelse loggar för att diagnostisera fel i önskad tillstånds konfiguration](https://devblogs.microsoft.com/powershell/using-event-logs-to-diagnose-errors-in-desired-state-configuration/).
  - **ApplyAndAutoCorrect** : med det här alternativet använder DSC alla nya konfigurationer, oavsett om de skickas direkt till målnoden eller identifieras i en pull-tjänst. Därefter, om konfigurationen av mål noden går från konfigurations filen, rapporterar DSC den avvikelsen i loggarna och försöker sedan justera konfigurationen för målnoden så att konfigurations filen är kompatibel.
- **ConfigurationModeFrequencyMins** : representerar den frekvens (i minuter) som bakgrunds programmet för DSC försöker implementera den aktuella konfigurationen på målnoden. Standardvärdet är 15. Det här värdet kan anges tillsammans med RefreshMode. När RefreshMode är inställt på Hämta kontaktar målnoden konfigurations tjänsten med ett intervall som anges av RefreshFrequencyMins och hämtar den aktuella konfigurationen. Oavsett RefreshMode-värdet, med det intervall som anges av ConfigurationModeFrequencyMins, tillämpar konsekvens motorn den senaste konfigurationen som hämtades till målnoden. RefreshFrequencyMins ska anges till ett heltals multipel av ConfigurationModeFrequencyMins.
- **Autentiseringsuppgift** : anger autentiseringsuppgifter (som med Get-Credential) som krävs för att komma åt fjär resurser, t. ex. för att kontakta konfigurations tjänsten.
- **DownloadManagerCustomData** : representerar en matris som innehåller anpassade data som är speciella för hämtnings hanteraren.
- **DownloadManagerName** : anger namnet på konfigurations-och modulens hämtnings hanterare.
- **RebootNodeIfNeeded** : Ställ in på `$true` för att tillåta att resurser startar om noden med hjälp av `$global:DSCMachineStatus` flaggan. Annars måste du starta om noden manuellt för alla konfigurationer som kräver det. Standardvärdet är `$false`. Om du vill använda den här inställningen när ett villkor för omstart utförs av något annat än DSC (till exempel Windows Installer) kombinerar du den här inställningen med [xPendingReboot](https://github.com/powershell/xpendingreboot) -modulen.
- **RefreshFrequencyMins** : används när du har konfigurerat en pull-tjänst. Representerar den frekvens (i minuter) som den lokala Configuration Manager kontaktar en pull-tjänst för att hämta den aktuella konfigurationen. Det här värdet kan anges tillsammans med ConfigurationModeFrequencyMins. När RefreshMode är inställt på Hämta kontaktar målnoden den pull-tjänst med ett intervall som anges av RefreshFrequencyMins och hämtar den aktuella konfigurationen. Vid det intervall som anges av ConfigurationModeFrequencyMins tillämpar konsekvens motorn den senaste konfigurationen som hämtades till målnoden. Om RefreshFrequencyMins inte är inställt på ett heltals multipel av ConfigurationModeFrequencyMins, kommer systemet att avrundas. Standardvärdet är 30.
- **RefreshMode** : möjliga värden är **push** (standard) och **pull** . I "push"-konfigurationen måste du placera en konfigurations fil på varje målnod med valfri klient dator.
  I läget "pull" måste du konfigurera en pull-tjänst för lokala Configuration Manager att kontakta och komma åt konfigurationsfilerna.

> [!NOTE]
> LCM startar **ConfigurationModeFrequencyMins** -cykeln baserat på:
>
> - En ny Metaconfig tillämpas med hjälp av `Set-DscLocalConfigurationManager`
> - Omstart av datorn
>
> För alla villkor där timer-processen upplever en krasch, kommer den att identifieras inom 30 sekunder och cykeln startas om. En samtidig åtgärd kan fördröja cykeln från att startas, om den här åtgärdens varaktighet överskrider den konfigurerade cykel frekvensen, kommer nästa timer inte att starta.
>
> Metaconfig konfigureras till exempel med en frekvens på 15 minuter och hämtning sker vid T1. Noden slutförs inte i 16 minuter. Den första 15 minuters cykeln ignoreras och nästa hämtning sker vid T1 + 15 + 15.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Exempel på uppdatering av inställningar för lokala Configuration Manager

Du kan uppdatera de lokala Configuration Manager inställningarna för en målnod genom att inkludera ett **LocalConfigurationManager** -block inuti Node-blocket i ett konfigurations skript, som du ser i följande exempel.

```powershell
Configuration ExampleConfig
{
    Node "Server001"
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called
# Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

Att köra skriptet i föregående exempel genererar en MOF-fil som anger och lagrar önskade inställningar. Om du vill tillämpa inställningarna kan du använda cmdleten **set-DscLocalConfigurationManager** , som visas i följande exempel.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> För parametern **Path** måste du ange samma sökväg som du angav för parametern **OutputPath** när du anropade konfigurationen i föregående exempel.

Du kan använda cmdleten **Get-DscLocalConfigurationManager** för att se de aktuella inställningarna för lokal Configuration Manager. Om du anropar denna cmdlet utan parametrar hämtas de lokala Configuration Manager inställningarna för den nod som du kör den på som standard. Om du vill ange en annan nod använder du parametern **CimSession** med denna cmdlet.
