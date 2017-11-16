---
ms.date: 2017-10-12
author: eslesar;mgreenegit
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager (MGM)
ms.openlocfilehash: d46862f9ea0f8e3206c596af7232160fc4a97939
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2017
---
# <a name="windows-powershell-40-desired-state-configuration-local-configuration-manager-lcm"></a>Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager (MGM)

>Gäller för: Windows PowerShell 4.0

Local Configuration Manager är Windows PowerShell önskad tillstånd Configuration DSC ()-motorn.
Den körs på alla målnoder och är ansvarig för att anropa configuration-resurser som ingår i ett DSC-konfigurationsskript.
Det här avsnittet visas egenskaperna för Local Configuration Manager och beskriver hur du kan ändra inställningarna för lokala Configuration Manager på målnoden.

## <a name="local-configuration-manager-properties"></a>Egenskaper för lokal Configuration Manager

Här nedan listas de lokala Configuration Manager-egenskaper som du kan ange eller hämta.

- **AllowModuleOverwrite**: styr huruvida nya konfigurationer som laddats ned från konfigurationstjänsten ska skriva över gamla på målnoden. Möjliga värden är True och False.
- **CertificateID**: tumavtrycket för ett certifikat som används för att säkra autentiseringsuppgifter skickas i en konfiguration. Mer information finns i [vill skydda autentiseringsuppgifter i Windows PowerShell Desired State Configuration?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).
- **ConfigurationID**: anger ett GUID som används för att få en viss konfigurationsfil från en pull-tjänsten. GUID garanterar att rätt konfigurationsfil kan nås.
- **ConfigurationMode**: Anger hur Local Configuration Manager faktiskt gäller konfigurationen för målnoder. Det kan ha följande värden:
  - **ApplyOnly**: med det här alternativet DSC gäller konfigurationen av och inget ytterligare såvida inte en ny konfiguration har identifierats av du skicka en ny konfiguration direkt till målnoden eller om du ansluter till en pull-tjänst och DSC identifierar en ny konfiguration för att kontrollera med pull-tjänsten. Om mål nodkonfiguration drifts utförs ingen åtgärd.
  - **ApplyAndMonitor**: med det här alternativet (som är standard), DSC gäller alla nya konfigurationer om skickades av du direkt till målnoden eller identifierats på en pull-tjänst. Om konfigurationen av målnoden drifts i konfigurationsfilen, rapporterar DSC därefter diskrepans i loggarna. Mer information om DSC loggning finns [med hjälp av händelseloggar för att diagnostisera fel i Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: med det här alternativet gäller DSC eventuella nya konfigurationer om skickades av du direkt till målnoden eller identifierats på en pull-tjänst. Därefter om konfigurationen av målnoden drifts i konfigurationsfilen, DSC rapporterar diskrepans i loggarna och försöker sedan att justera mål nodkonfiguration återinföra efterlever konfigurationsfilen.
- **ConfigurationModeFrequencyMins**: representerar frekvens (i minuter) som bakgrundsprogrammet för DSC ska försöka införa den aktuella konfigurationen på målnoden. Standardvärdet är 15. Det här värdet kan anges tillsammans med RefreshMode. När RefreshMode anges till PULL målnoden kontaktar konfigurationstjänsten vid ett intervall som anges av RefreshFrequencyMins och hämtar den aktuella konfigurationen. Oavsett RefreshMode-värde gäller med det intervall som anges av ConfigurationModeFrequencyMins, konsekvens motorn den senaste konfigurationen som hämtades till målnoden. RefreshFrequencyMins ska anges till ett heltal multipel av ConfigurationModeFrequencyMins.
- **Autentiseringsuppgifter**: Anger autentiseringsuppgifter (som Get-Credential) krävs för att komma åt fjärresurser, såsom för att kontakta tjänsten för konfiguration.
- **DownloadManagerCustomData**: representerar en matris som innehåller anpassade data som är specifika för Hämtningshanteraren.
- **DownloadManagerName**: Anger namnet på konfigurationen och modulen Hämtningshanteraren.
- **RebootNodeIfNeeded**: vissa konfigurationsändringar på målnoden kan kräva att startas om för att ändringarna ska tillämpas. Med värdet **SANT**, den här egenskapen ska starta om noden när konfigurationen har helt gäller utan ytterligare varning. Om **FALSKT** (standardvärdet) konfiguration kommer att slutföras, men noden måste startas om manuellt för att ändringarna ska börja gälla.
- **RefreshFrequencyMins**: används när du har ställt in en pull-tjänst. Visar frekvens (i minuter) som Local Configuration Manager kontaktar en pull-tjänst för att hämta den aktuella konfigurationen. Det här värdet kan anges tillsammans med ConfigurationModeFrequencyMins. När RefreshMode anges till PULL målnoden kontaktar pull-tjänsten vid ett intervall som anges av RefreshFrequencyMins och hämtar den aktuella konfigurationen. Vid det intervall som anges av ConfigurationModeFrequencyMins gäller konsekvenskontroll motorn sedan den senaste konfigurationen som hämtades till målnoden. Om RefreshFrequencyMins inte har angetts till ett heltal multipel av ConfigurationModeFrequencyMins systemet att avrunda. Standardvärdet är 30.
- **RefreshMode**: möjliga värden är **Push** (standard) och **hämtar**. I ”push”-konfigurationen måste du placera en konfigurationsfil på varje målnoden med hjälp av alla klientdatorer. I ”pull”-läge måste du ställa in en pull-tjänst för Local Configuration Manager för att kontakta och komma åt konfigurationsfiler.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Exempel för att uppdatera inställningarna för Local Configuration Manager

Du kan uppdatera Local Configuration Manager-inställningarna för en målnod genom att inkludera en **LocalConfigurationManager** blockera i nod-block i ett konfigurationsskript som visas i följande exempel.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
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

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

Kör skriptet i föregående exempel genererar en MOF-fil som anger och lagrar de önskade inställningarna.
Om du vill använda inställningarna du kan använda den **Set DscLocalConfigurationManager** cmdlet, som visas i följande exempel.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Obs**: för de **sökväg** parameter, måste du ange samma sökväg som angetts för den **OutputPath** parameter när du startade konfigurationen i föregående exempel.

Om du vill se de aktuella inställningarna för Local Configuration Manager kan du använda den **Get-DscLocalConfigurationManager** cmdlet.
Om du anropar denna cmdlet utan parametrar som standard får den Local Configuration Manager-inställningarna för den nod som du kör den.
Om du vill ange en annan nod i **CimSession** parameter med denna cmdlet.
