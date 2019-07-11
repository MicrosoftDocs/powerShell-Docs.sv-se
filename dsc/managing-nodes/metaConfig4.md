---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera LCM i PowerShell 4.0
ms.openlocfilehash: a7d8a1d8dea5ca4c2cdf53b8c02e498be20dab60
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734616"
---
# <a name="configuring-the-lcm-in-powershell-40"></a>Konfigurera LCM i PowerShell 4.0

>Gäller för: Windows PowerShell 4.0

**Information relaterad till Windows PowerShell 5.0 och senare finns i [konfigurerar den lokala Konfigurationshanteraren](metaConfig.md).**

Lokal konfigurationshanterare är Windows PowerShell Desired State Configuration (DSC)-motor.
Den körs på alla målnoder och den är ansvarig för att anropa configuration-resurser som ingår i ett DSC-konfigurationsskript.
Det här avsnittet visar en lista över egenskaper för lokal konfigurationshanterare och beskriver hur du kan ändra inställningarna för lokala Konfigurationshanteraren på målnoden.

## <a name="local-configuration-manager-properties"></a>Egenskaper för lokala Configuration Manager

Här nedan listas de lokala Configuration Manager-egenskaper som du kan ange eller hämta.

- **AllowModuleOverwrite**: Styr huruvida nya konfigurationer som laddats ned från konfigurationstjänsten ska kunna skriva över gamla på målnoden. Möjliga värden är True och False.
- **CertificateID**: Tumavtrycket för ett certifikat som används för att skydda autentiseringsuppgifter som angavs i en konfiguration. Mer information finns i [behöver du säkra autentiseringsuppgifter i Windows PowerShell Desired State Configuration?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).
- **ConfigurationID**: Anger ett GUID som används för att hämta en viss fil från en pull-tjänsten. GUID som säkerställer att rätt konfigurationsfilen är tillgänglig.
- **ConfigurationMode**: Anger hur den lokala Konfigurationshanteraren faktiskt tillämpar konfigurationen målnoder. Det kan ta följande värden:
  - **ApplyOnly**: Med det här alternativet DSC gäller konfigurationen av och gör ingenting ytterligare såvida inte en ny konfiguration har identifierats, antingen genom att du skicka en ny konfiguration direkt till målet nod eller om du ansluter till en pull-tjänst och DSC identifierar en ny konfiguration när den kontaktar pull-tjänsten. Om målet nodkonfiguration drifts, utförs ingen åtgärd.
  - **ApplyAndMonitor**: Med det här alternativet (som är standard), DSC gäller alla nya konfigurationer, oavsett om skickas av dig direkt till målnoden eller identifierats på en pull-tjänst. Om konfigurationen av målnoden drifts från konfigurationsfilen, rapporterar DSC därefter avvikelse i loggarna. Mer information om DSC-loggning finns i [med hjälp av händelseloggar för att diagnostisera fel i Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: Med det här alternativet gäller DSC eventuella nya konfigurationer om skickas av dig direkt till målnoden eller identifierats på en pull-tjänst. Därefter om konfigurationen av målnoden drifts från konfigurationsfilen, DSC rapporterar avvikelse i loggarna och försöker sedan justera nodkonfiguration mål att ta med konfigurationsfilen.
- **ConfigurationModeFrequencyMins**: Visar frekvens (i minuter) som bakgrundsprogrammet för DSC försöka införa den aktuella konfigurationen på målnoden. Standardvärdet är 15. Det här värdet kan anges tillsammans med RefreshMode. När RefreshMode har angetts till PULL målnoden kontaktar tjänsten för konfiguration vid ett intervall som anges av RefreshFrequencyMins och hämtar den aktuella konfigurationen. Oavsett vilket värde för RefreshMode, gäller vid de tider som anges av ConfigurationModeFrequencyMins, konsekvens-motorn den senaste konfigurationen som hämtades till målnoden. RefreshFrequencyMins ska anges till ett heltal multipel av ConfigurationModeFrequencyMins.
- **Autentiseringsuppgifter**: Anger autentiseringsuppgifter (precis som med Get-Credential) krävs för att använda fjärranslutna resurser, till exempel för att kontakta tjänsten för konfiguration.
- **DownloadManagerCustomData**: Representerar en matris som innehåller anpassade data som är specifika för Hämtningshanteraren.
- **DownloadManagerName**: Anger namnet på konfigurationen och modulen Hämtningshanteraren.
- **RebootNodeIfNeeded**: Ställ in på `$true` så att resurser för att starta om en nod med hjälp av den `$global:DSCMachineStatus` flaggan. I annat fall kommer du behöva manuellt starta om noden för alla konfigurationer som kräver. Standardvärdet är `$false`. Om du vill använda den här inställningen när ett villkor för omstart är branschrekommendationer när det gäller av något annat än DSC (till exempel Windows Installer), kombinera den här inställningen med det [xPendingReboot](https://github.com/powershell/xpendingreboot) modulen.
- **RefreshFrequencyMins**: Används när du har ställt in en pull-tjänst. Visar frekvens (i minuter) som den lokala Konfigurationshanteraren kontaktar en pull-tjänst för att hämta den aktuella konfigurationen. Det här värdet kan anges tillsammans med ConfigurationModeFrequencyMins. När RefreshMode har angetts till PULL målnoden kontaktar pull-tjänsten med ett intervall som anges av RefreshFrequencyMins och hämtar den aktuella konfigurationen. Vid de tider som anges av ConfigurationModeFrequencyMins gäller konsekvens motorn sedan den senaste konfigurationen som hämtades till målnoden. Om RefreshFrequencyMins inte har angetts till ett heltal multipel av ConfigurationModeFrequencyMins, systemet kommer avrunda uppåt. Standardvärdet är 30.
- **RefreshMode**: Möjliga värden är **Push** (standard) och **hämta**. I ”push”-konfigurationen måste du placera en fil på varje nod i målet, med hjälp av valfri dator. I ”pull”-läge måste du konfigurera en pull-tjänst för lokala Configuration Manager för att kontakta och få åtkomst till konfigurationsfilerna.

> [!NOTE]
> LCM startar den **ConfigurationModeFrequencyMins** cykel baserat på:
>
> - En ny metaconfig tillämpas med hjälp av `Set-DscLocalConfigurationManager`
> - En omstart av datorn
>
> För alla villkor där en krasch som identifieras inom 30 sekunder och cykeln inträffar i processen för timer startas.
> En samtidig åtgärd kan försena cykeln startas, om varaktigheten för den här åtgärden överskrider den konfigurera cykel frekvensen nästa timern startar inte.
>
> Exempelvis metaconfig är konfigurerad med en 15 minuters pull frekvens och en hämtning uppstår på T1.  Noden inte är klar för 16 minuter.  Den första 15 minuters cykeln ignoreras och nästa pull inträffar vid T1 + 15 + 15.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Exempel för att uppdatera inställningarna för lokala Configuration Manager

Du kan uppdatera Local Configuration Manager-inställningarna för en målnoden genom att inkludera en **LocalConfigurationManager** blockera i blocket nod i ett konfigurationsskript som visas i följande exempel.

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

Köra skript i det förra exemplet genererar en MOF-fil som anger och lagrar sedan önskade inställningar.
Om du vill tillämpa inställningarna, kan du använda den **Set-DscLocalConfigurationManager** cmdlet, enligt följande exempel.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> För den **sökväg** parameter, måste du ange samma sökväg som du angav för den **OutputPath** parameter när du startade konfigurationen i exemplet ovan.

Om du vill visa de aktuella inställningarna för lokala Configuration Manager kan du använda den **Get-DscLocalConfigurationManager** cmdlet.
Om du anropar den här cmdleten utan parametrar, som standard får den Local Configuration Manager-inställningarna för den nod där du kör den.
Om du vill ange en annan nod, använda den **CimSession** parameter med denna cmdlet.
