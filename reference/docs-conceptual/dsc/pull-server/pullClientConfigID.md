---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: 'Konfigurera en pull-klient med hjälp av konfigurations-ID: n i PowerShell 5,0 och senare'
ms.openlocfilehash: a014e04fc5fbf2e813d9b0d79f39fe5aa3836f86
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500741"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Konfigurera en pull-klient med hjälp av konfigurations-ID: n i PowerShell 5,0 och senare

> Gäller för: Windows PowerShell 5,0

> [!IMPORTANT]
> Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Innan du konfigurerar en pull-klient bör du konfigurera en hämtnings Server. Även om den här ordningen inte krävs, hjälper den med fel sökning och hjälper dig att se till att registreringen lyckades. Om du vill konfigurera en hämtnings Server kan du använda följande guider:

- [Konfigurera en DSC SMB-hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-hämtningsserver](pullServer.md)

Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status. I avsnitten nedan visas hur du konfigurerar en pull-klient med en SMB-resurs eller HTTP DSC-pull-server. När nodens LCM uppdateras, kommer den att kontakta den konfigurerade platsen för att ladda ned alla tilldelade konfigurationer. Om det inte finns några nödvändiga resurser på noden hämtas de automatiskt från den konfigurerade platsen. Om noden har kon figurer ATS med en [rapport Server](reportServer.md), kommer den att rapportera statusen för åtgärden.

> [!NOTE]
> Det här avsnittet gäller för PowerShell 5,0. Information om hur du konfigurerar en pull-klient i PowerShell 4,0 finns i [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Konfigurera LCM för pull-klienten

Om du kör något av exemplen nedan skapas en ny mapp med namnet **PullClientConfigID** och en metaconfiguration MOF-fil placeras där. I det här fallet får MOF-filen metaconfiguration namnet `localhost.meta.mof`.

Om du vill använda konfigurationen anropar du cmdleten **set-DscLocalConfigurationManager** med **sökvägen** inställd på platsen för MOF-filen för metaconfiguration. Ett exempel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Konfigurations-ID

I exemplen nedan anges egenskapen **ConfigurationID** för LCM till ett **GUID** som tidigare har skapats för detta ändamål. **ConfigurationID** är vad LCM använder för att hitta rätt konfiguration på hämtnings servern. MOF-konfigurationsfilen på hämtnings servern måste namnges `ConfigurationID.mof`, där *ConfigurationID* är värdet för egenskapen **ConfigurationID** för målnoden LCM. Mer information finns i [publicera konfigurationer till en pull-server (v4/V5)](publishConfigs.md).

Du kan skapa ett slumpmässigt **GUID** med hjälp av exemplet nedan eller med hjälp av cmdleten [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .

```powershell
[System.Guid]::NewGuid()
```

Mer information om hur du använder **GUID** i din miljö finns i [Planera för GUID](secureserver.md#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Konfigurera en pull-klient för att hämta konfigurationer

Varje klient måste konfigureras i **pull** -läge och tilldelas URL-adressen till pull-servern där konfigurationen lagras. Om du vill göra detta måste du konfigurera den lokala Configuration Manager (LCM) med nödvändig information. Om du vill konfigurera LCM skapar du en särskild typ av konfiguration, dekorerat med attributet **DSCLocalConfigurationManager** . Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>HTTP DSC-hämtnings Server

Följande skript konfigurerar LCM att hämta konfigurationer från en server med namnet CONTOSO-PullSrv.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

I skriptet definierar **ConfigurationRepositoryWeb** -blocket hämtnings servern. **ServerURL** anger URL: en för DSC-pull

### <a name="smb-share"></a>SMB-resurs

Följande skript konfigurerar LCM för att hämta konfigurationer från SMB-resursen `\\SMBPullServer\Pull`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

I skriptet definierar **ConfigurationRepositoryShare** -blocket pull-servern, som i det här fallet bara är en SMB-resurs.

## <a name="set-up-a-pull-client-to-download-resources"></a>Konfigurera en pull-klient för att ladda ned resurser

Om du bara anger **ConfigurationRepositoryWeb** -eller **ConfigurationRepositoryShare** -blocket i LCM-konfigurationen (som i föregående exempel) hämtar pull-klienten resurser från samma plats som den hämtar sina konfigurationer. Du kan också ange separata platser för resurser. Om du vill ange en resurs plats som en separat server använder du **ResourceRepositoryWeb** -blocket. Om du vill ange en resurs plats som en SMB-resurs använder du **ResourceRepositoryShare** -blocket.

> [!NOTE]
> Du kan kombinera **ConfigurationRepositoryWeb** med **ResourceRepositoryShare** eller **ConfigurationRepositoryShare** med **ResourceRepositoryWeb**. Exempel på detta visas inte nedan.

### <a name="http-dsc-pull-server"></a>HTTP DSC-hämtnings Server

Följande metaconfiguration konfigurerar en pull-klient för att hämta konfigurationerna från **contoso-PullSrv** och dess resurser från **contoso-ResourceSrv**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB-resurs

I följande exempel visas en metaconfiguration som konfigurerar en-klient för att hämta konfigurationer från SMB- `\\SMBPullServer\Configurations`resursen och resurser från SMB-resursen `\\SMBPullServer\Resources`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Hämta resurser automatiskt i push-läge

Från och med PowerShell 5,0 kan pull-klienter Ladda ned moduler från en SMB-resurs, även när de har kon figurer ATS för **push** -läge. Detta är särskilt användbart i scenarier där du inte vill konfigurera en hämtnings Server. **ResourceRepositoryShare** -blocket kan användas utan att ange en **ConfigurationRepositoryShare**. I följande exempel visas en metaconfiguration som konfigurerar en-klient för att hämta resurser från en SMB `\\SMBPullServer\Resources`-resurs. När noden överförs till **en konfiguration** hämtas alla nödvändiga resurser automatiskt från den angivna resursen.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Konfigurera en pull-klient för att rapportera status

Som standard skickar noder inte rapporter till en konfigurerad hämtnings Server. Du kan använda en enda hämtnings Server för konfigurationer, resurser och rapportering, men du måste skapa ett **ReportRepositoryWeb** -block för att ställa in rapportering.

### <a name="http-dsc-pull-server"></a>HTTP DSC-hämtnings Server

I följande exempel visas en metaconfiguration som konfigurerar en klient för att hämta konfigurationer och resurser och skicka rapporterings data till en enda pull-server.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Om du vill ange en rapport Server använder du ett **ReportRepositoryWeb** -block. En rapport Server kan inte vara en SMB-server. Följande metaconfiguration konfigurerar en pull-klient för att hämta konfigurationerna från **contoso-PullSrv** och dess resurser från **contoso-ResourceSrv**, och för att skicka status rapporter till **contoso-ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB-resurs

En rapport Server kan inte vara en SMB-resurs.

## <a name="next-steps"></a>Nästa steg

När pull-klienten har kon figurer ATS kan du använda följande guider för att utföra nästa steg:

- [Publicera konfigurationer till en hämtningsserver (v4/v5)](publishConfigs.md)
- [Paketera och ladda upp resurser till en hämtningsserver (v4)](package-upload-resources.md)

## <a name="see-also"></a>Se även

* [Konfigurera en pull-klient med konfigurations namn](pullClientConfigNames.md)
