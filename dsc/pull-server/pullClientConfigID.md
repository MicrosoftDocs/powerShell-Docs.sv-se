---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en Pull-klient som använder konfigurations-ID i PowerShell 5.0 och senare
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079497"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Konfigurera en Pull-klient som använder konfigurations-ID i PowerShell 5.0 och senare

> Gäller för: Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).

Innan du konfigurerar en pullklient, bör du ställa in en pull-server. Även om den här ordningen inte är obligatoriskt, hjälper till med felsökning och hjälper dig att säkerställa att registreringen har lyckats. Om du vill konfigurera en pull-server kan du använda följande guider:

- [Konfigurera en DSC SMB-Hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-Hämtningsserver](pullServer.md)

Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen. I avsnitten nedan visar hur du konfigurerar en hämtningsklient med en SMB-resursen eller HTTP DSC-Hämtningsservern. När nodens LCM uppdaterar kommer det att kontakta konfigurerade platsen för att hämta alla tilldelade konfigurationer. Om alla nödvändiga resurser inte finns på noden, kommer den automatiskt hämta dem från den konfigurerade platsen. Om noden är konfigurerad med en [Report Server](reportServer.md), kommer den sedan att rapportera status för åtgärden.

> [!NOTE]
> Det här avsnittet gäller för PowerShell 5.0. Information om hur du konfigurerar en pullklient i PowerShell 4.0 finns i [konfigurera en hämtningsklient med konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Konfigurera en pullklient LCM

Kör något av exemplen nedan skapar en ny utdata-mapp med namnet **PullClientConfigID** och det placerar en metaconfiguration MOF-fil. I det här fallet metaconfiguration MOF-filen namnet `localhost.meta.mof`.

Om du vill tillämpa konfigurationen av genom att anropa den **Set-DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metaconfiguration MOF-filen. Till exempel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Konfigurations-ID

Exemplen nedan anger den **ConfigurationID** egenskapen för MGM om du vill en **Guid** som tidigare hade skapats för detta ändamål. Den **ConfigurationID** är vad LCM används för att hitta lämplig konfiguration på hämtningsservern. MOF-konfigurationsfilen på hämtningsservern måste ha namnet `ConfigurationID.mof`, där *ConfigurationID* är värdet för den **ConfigurationID** egenskapen för den målnoden MGM. Mer information finns i [publicera konfigurationer för att en Pull-servern (v4/v5)](publishConfigs.md).

Du kan skapa ett slumpmässigt **Guid** i exemplet nedan eller genom att använda den [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Mer information om hur du använder **GUID** i din miljö, se [planera för GUID](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Konfigurera en Pull-klient för att ladda ned konfigurationer

Varje klient måste konfigureras i **Pull** läge och angivna pull-serveradress där dess konfiguration lagras. Då har du konfigurerar den lokala Configuration Manager (LCM) med informationen som krävs. Om du vill konfigurera LCM måste du skapa en särskild typ av konfiguration, dekorerad med den **DSCLocalConfigurationManager** attribut. Läs mer om hur du konfigurerar LCM [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>HTTP DSC Pull Server

Följande skript konfigurerar LCM pull konfigurationer från en server med namnet ”CONTOSO-PullSrv”.

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

I skriptet den **ConfigurationRepositoryWeb** block definierar hämtningsservern. Den **ServerUrl** anger URL: en för DSC-Pull

### <a name="smb-share"></a>SMB Share

Följande skript konfigurerar LCM pull konfigurationer från SMB-resurs `\\SMBPullServer\Pull`.

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

I skriptet den **ConfigurationRepositoryShare** block definierar pull-servern, som i det här fallet är bara en SMB-resurs.

## <a name="set-up-a-pull-client-to-download-resources"></a>Konfigurera en Pull-klient för att hämta resurser

Om du anger bara den **ConfigurationRepositoryWeb** eller **ConfigurationRepositoryShare** blockera i din LCM-konfiguration (som i föregående exempel), pull-klienten hämtar resurser från samma plats som den hämtar dess konfigurationer. Du kan också ange olika platser för resurser. Om du vill ange en plats för resurser som en separat server, använder den **ResourceRepositoryWeb** block. Om du vill ange en plats för resurser som en SMB-filresurs, använder den **ResourceRepositoryShare** block.

> [!NOTE]
> Du kan kombinera **ConfigurationRepositoryWeb** med **ResourceRepositoryShare** eller **ConfigurationRepositoryShare** med **ResourceRepositoryWeb** . Exempel på detta visas inte nedan.

### <a name="http-dsc-pull-server"></a>HTTP DSC Pull Server

Följande metaconfiguration konfigurerar en pullklient för att få dess konfigurationerna från **CONTOSO PullSrv** och dess resurser från **CONTOSO ResourceSrv**.

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

### <a name="smb-share"></a>SMB Share

I följande exempel visas en metaconfiguration som ställer in en klient ska pull konfigurationer från SMB-resurs `\\SMBPullServer\Configurations`, och resurser från SMB-resurs `\\SMBPullServer\Resources`.

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

#### <a name="automatically-download-resources-in-push-mode"></a>Hämta automatiskt resurser i Push-läge

Från och med PowerShell 5.0, pull-klienter kan ladda ned moduler från en SMB-resurs, även när de är konfigurerade för **Push** läge. Detta är särskilt användbart i scenarier där du inte vill konfigurera en Pull-servern. Den **ResourceRepositoryShare** block kan användas utan att ange en **ConfigurationRepositoryShare**. I följande exempel visas en metaconfiguration som ställer in en klient till pull-resurser från en SMB-resurs `\\SMBPullServer\Resources`. När noden är **PUSHED** en konfiguration för den hämtar automatiskt alla nödvändiga resurser från den resurs som anges.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Ställa in en Pull-klient för att rapportera status

Som standard skickar noder inte rapporter till en konfigurerad Pull-Server. Du kan använda en enda pull-server för konfigurationer, resurser och rapportering, men du måste skapa en **ReportRepositoryWeb** förhindra om du vill konfigurera rapportering.

### <a name="http-dsc-pull-server"></a>HTTP DSC Pull Server

I följande exempel visas en metaconfiguration som ställer in en klient till pull-konfigurationer och resurser och skicka rapportdata till en enda pull-server.

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

Om du vill ange en rapportserver som du använder en **ReportRepositoryWeb** block. En rapportserver får inte vara en SMB-server.
Följande metaconfiguration konfigurerar en pullklient för att få dess konfigurationerna från **CONTOSO PullSrv** och dess resurser från **CONTOSO ResourceSrv**, samt skicka statusrapporter till  **CONTOSO-ReportSrv**:

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

### <a name="smb-share"></a>SMB Share

En rapportserver får inte vara en SMB-resurs.

## <a name="next-steps"></a>Nästa steg

När pull-klienten har konfigurerats kan använda du följande guider för att utföra nästa steg:

- [Publicera konfigurationer till en Pull-Server (v4/v5)](publishConfigs.md)
- [Paket- och ladda upp resurser till en Pull-Server (v4)](package-upload-resources.md)

## <a name="see-also"></a>Se även

* [Konfigurera en hämtningsklient med konfigurationsnamn](pullClientConfigNames.md)
