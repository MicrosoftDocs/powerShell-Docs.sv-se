---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Ställa in en Pull-klient med konfigurationsnamn i PowerShell 5.0 och senare
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688079"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Ställa in en Pull-klient med konfigurationsnamn i PowerShell 5.0 och senare

> Gäller för: Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).

Innan du konfigurerar en pullklient, bör du ställa in en pull-server. Även om den här ordningen inte är obligatoriskt, hjälper till med felsökning och hjälper dig att säkerställa att registreringen har lyckats. Om du vill konfigurera en pull-server kan du använda följande guider:

- [Konfigurera en DSC SMB-Hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-Hämtningsserver](pullServer.md)

Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen. I avsnitten nedan visar hur du konfigurerar en hämtningsklient med en SMB-resursen eller HTTP DSC-Hämtningsservern. När nodens LCM uppdaterar kommer det att kontakta konfigurerade platsen för att hämta alla tilldelade konfigurationer. Om alla nödvändiga resurser inte finns på noden, kommer den automatiskt hämta dem från den konfigurerade platsen. Om noden är konfigurerad med en [Report Server](reportServer.md), kommer den sedan att rapportera status för åtgärden.

> **Obs**: Det här avsnittet gäller för PowerShell 5.0.
Information om hur du konfigurerar en pullklient i PowerShell 4.0 finns i [konfigurera en hämtningsklient med konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Konfigurera en pullklient LCM

Kör något av exemplen nedan skapar en ny utdata-mapp med namnet **PullClientConfigName** och det placerar en metaconfiguration MOF-fil. I det här fallet metaconfiguration MOF-filen namnet `localhost.meta.mof`.

Om du vill tillämpa konfigurationen av genom att anropa den **Set-DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metaconfiguration MOF-filen. Till exempel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Konfigurationsnamn

Exemplen nedan anger den **ConfigurationName** egenskapen för LCM till namnet på en tidigare kompilerad konfiguration som skapats för detta ändamål. Den **ConfigurationName** är vad LCM används för att hitta lämplig konfiguration på hämtningsservern. MOF-konfigurationsfilen på hämtningsservern måste ha namnet `<ConfigurationName>.mof`, i det här fallet ”ClientConfig.mof”. Mer information finns i [publicera konfigurationer för att en Pull-servern (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Konfigurera en Pull-klient för att ladda ned konfigurationer

Varje klient måste konfigureras i **Pull** läge och angivna pull-serveradress där dess konfiguration lagras. Då har du konfigurerar den lokala Configuration Manager (LCM) med informationen som krävs. Om du vill konfigurera LCM måste du skapa en särskild typ av konfiguration, dekorerad med den **DSCLocalConfigurationManager** attribut. Läs mer om hur du konfigurerar LCM [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md).

Följande skript konfigurerar LCM pull konfigurationer från en server med namnet ”CONTOSO-PullSrv”.

- I skriptet den **ConfigurationRepositoryWeb** block definierar hämtningsservern. Den **ServerURL** egenskap anger slutpunkten för pull-servern.

- Den **RegistrationKey** egenskapen är en delad nyckel mellan alla klientnoder för en pull-server och den pull-servern. Samma värde lagras i en fil på hämtningsservern.
  > **Obs**: Registreringsnycklar fungerar bara med **web** pull-servrar. Du måste fortfarande använda **ConfigurationID** med en **SMB** hämtningsservern.
  > Information om hur du konfigurerar en pull-server med hjälp av **ConfigurationID**, se [konfigurera en hämtningsklient med konfigurations-ID](pullClientConfigId.md)

- Den **ConfigurationNames** egenskapen är en matris som anger namnen på de konfigurationer som är avsedd för klient-nod.
  >**Obs:** Om du anger fler än ett värde i den **ConfigurationNames**, måste du även ange **PartialConfiguration** blockerar i konfigurationen.
  >Läs om hur partiella konfigurationer [PowerShell Desired State Configuration partiella konfigurationer](partialConfigs.md).

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>Konfigurera en Pull-klient för att hämta resurser

Om du anger bara en **ConfigurationRepositoryWeb** eller **ConfigurationRepositoryShare** blockera i din LCM-konfiguration (som i föregående exempel), pull-klienten hämtar resurser från samma plats där MOF-filerna lagras. Du kan också ange olika platser där klienter kan hämta resurser. Om du vill ange resursservern du använda antingen en **ResourceRepositoryWeb** (för en webbpullserver) eller en **ResourceRepositoryShare** block (för SMB-pullserver).

I följande exempel visas en metaconfiguration som ställer in en klient att ladda ned konfigurationer från en Pull-servern och resurser från en SMB-resurs.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Ställa in en Pull-klient för att rapportera status

Du kan använda en enda pull-server för konfigurationer, resurser och rapportering. Rapportering har inte konfigurerats för klienter som standard. Om du vill konfigurera en klient för att rapportera status, måste du skapa en **ReportRepositoryWeb** block. I följande exempel visas en metaconfiguration som ställer in en klient till pull-konfigurationer och resurser och skicka rapportdata till en enda pull-server.

> [!NOTE]
> En rapportserver får inte vara en SMB-resurs.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Se även

* [Konfigurera en hämtningsklient med konfigurations-ID](PullClientConfigNames.md)
* [Konfigurera en DSC-webbpullserver](pullServer.md)
