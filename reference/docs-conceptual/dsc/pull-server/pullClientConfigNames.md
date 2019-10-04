---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en pull-klient med hjälp av konfigurations namn i PowerShell 5,0 och senare
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941721"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Konfigurera en pull-klient med hjälp av konfigurations namn i PowerShell 5,0 och senare

> Gäller för: Windows PowerShell 5,0

> [!IMPORTANT]
> Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Innan du konfigurerar en pull-klient bör du konfigurera en hämtnings Server. Även om den här ordningen inte krävs, hjälper den med fel sökning och hjälper dig att se till att registreringen lyckades. Om du vill konfigurera en hämtnings Server kan du använda följande guider:

- [Konfigurera en DSC SMB-pull-server](pullServerSmb.md)
- [Konfigurera en DSC HTTP-pull-server](pullServer.md)

Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status. I avsnitten nedan visas hur du konfigurerar en pull-klient med en SMB-resurs eller HTTP DSC-pull-server. När nodens LCM uppdateras, kommer den att kontakta den konfigurerade platsen för att ladda ned alla tilldelade konfigurationer. Om det inte finns några nödvändiga resurser på noden hämtas de automatiskt från den konfigurerade platsen. Om noden har kon figurer ATS med en [rapport Server](reportServer.md), kommer den att rapportera statusen för åtgärden.

> [!NOTE]
> Det här avsnittet gäller för PowerShell 5,0.
> Information om hur du konfigurerar en pull-klient i PowerShell 4,0 finns i [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Konfigurera LCM för pull-klienten

Om du kör något av exemplen nedan skapas en ny mapp med namnet **PullClientConfigName** och en metaconfiguration MOF-fil placeras där. I det här fallet får MOF-filen metaconfiguration namnet `localhost.meta.mof`.

Om du vill använda konfigurationen anropar du cmdleten **set-DscLocalConfigurationManager** med **sökvägen** inställd på platsen för MOF-filen för metaconfiguration. Exempel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Konfigurations namn

I exemplen nedan anges egenskapen **ConfigurationName** för LCM till namnet på en tidigare kompilerad konfiguration som skapats för det här ändamålet. **ConfigurationName** är vad LCM använder för att hitta rätt konfiguration på hämtnings servern. MOF-konfigurationsfilen på hämtnings servern måste ha namnet `<ConfigurationName>.mof`, i det här fallet "ClientConfig. MOF". Mer information finns i [publicera konfigurationer till en pull-server (v4/V5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Konfigurera en pull-klient för att hämta konfigurationer

Varje klient måste konfigureras i **pull** -läge och tilldelas URL-adressen till pull-servern där konfigurationen lagras. Om du vill göra detta måste du konfigurera den lokala Configuration Manager (LCM) med nödvändig information. Om du vill konfigurera LCM skapar du en särskild typ av konfiguration, dekorerat med attributet **DSCLocalConfigurationManager** . Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md).

Följande skript konfigurerar LCM att hämta konfigurationer från en server med namnet CONTOSO-PullSrv.

- I skriptet definierar **ConfigurationRepositoryWeb** -blocket hämtnings servern. Egenskapen **ServerURL** anger slut punkten för hämtnings servern.

- Egenskapen **RegistrationKey** är en delad nyckel mellan alla klient-noder för en pull-server och den hämtnings servern. Samma värde lagras i en fil på hämtnings servern.
  > [!NOTE]
  > Registrerings nycklar fungerar bara med **webb** hämtnings servrar. Du måste fortfarande använda **ConfigurationID** med en **SMB** -pull-server.
  > Information om hur du konfigurerar en pull-server med hjälp av **ConfigurationID**finns i [Konfigurera en pull-klient med konfigurations-ID](pullClientConfigId.md)

- Egenskapen **ConfigurationNames** är en matris som anger namnen på de konfigurationer som är avsedda för-klient-noden.
  >**Obs:** Om du anger fler än ett värde i **ConfigurationNames**måste du också ange **PartialConfiguration** -block i konfigurationen.
  >Information om ofullständiga konfigurationer finns i [PowerShell Desired State Configuration del konfigurationer](partialConfigs.md).

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

## <a name="set-up-a-pull-client-to-download-resources"></a>Konfigurera en pull-klient för att ladda ned resurser

Om du bara anger ett **ConfigurationRepositoryWeb** -eller **ConfigurationRepositoryShare** -block i LCM-konfigurationen (som i föregående exempel) hämtar pull-klienten resurser från samma plats där dina ". MOF"-filer lagras. Du kan också ange olika platser där klienter kan ladda ned resurser. Om du vill ange en resurs Server använder du antingen en **ResourceRepositoryWeb** (för en webb hämtnings Server) eller ett **ResourceRepositoryShare** -block (för en SMB-pull-server).

I följande exempel visas en metaconfiguration som konfigurerar en-klient för att hämta konfigurationer från en pull-server och resurser från en SMB-resurs.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Konfigurera en pull-klient för att rapportera status

Du kan använda en enda hämtnings Server för konfigurationer, resurser och rapportering. Rapportering är inte konfigurerat för klienter som standard. Om du vill konfigurera en klient så att den rapporterar status måste du skapa ett **ReportRepositoryWeb** -block. I följande exempel visas en metaconfiguration som konfigurerar en klient för att hämta konfigurationer och resurser och skicka rapporterings data till en enda pull-server.

> [!NOTE]
> En rapport Server kan inte vara en SMB-resurs.

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

* [Konfigurera en pull-klient med konfigurations-ID](PullClientConfigNames.md)
* [Konfigurera en DSC-webb hämtnings Server](pullServer.md)
