---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: 'Konfigurera en pull-klient med konfigurations-ID: n i PowerShell 4,0'
description: 'Den här artikeln förklarar hur du konfigurerar en pull-klient med hjälp av konfigurations-ID: n i PowerShell 4,0'
ms.openlocfilehash: 2a3d7b79f29030620cddc2b2131cb4432e41e4eb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649016"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Konfigurera en pull-klient med konfigurations-ID: n i PowerShell 4,0

>Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

> [!IMPORTANT]
> Hämtnings servern (Windows Feature *DSC-tjänst* ) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Innan du konfigurerar en pull-klient bör du konfigurera en hämtnings Server. Även om den här ordningen inte krävs, hjälper den med fel sökning och hjälper dig att se till att registreringen lyckades. Om du vill konfigurera en hämtnings Server kan du använda följande guider:

- [Konfigurera en DSC SMB-hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-hämtningsserver](pullServer.md)

Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status. I avsnitten nedan visas hur du konfigurerar en pull-klient med en SMB-resurs eller HTTP DSC-pull-server. När nodens LCM uppdateras, kommer den att kontakta den konfigurerade platsen för att ladda ned alla tilldelade konfigurationer. Om det inte finns några nödvändiga resurser på noden hämtas de automatiskt från den konfigurerade platsen. Om noden har kon figurer ATS med en [rapport Server](reportServer.md), kommer den att rapportera statusen för åtgärden.

## <a name="configure-the-pull-client-lcm"></a>Konfigurera LCM för pull-klienten

Om du kör något av exemplen nedan skapas en ny mapp med namnet **PullClientConfigID** och en metaconfiguration MOF-fil placeras där. I det här fallet får MOF-filen metaconfiguration namnet `localhost.meta.mof` .

Om du vill använda konfigurationen anropar du cmdleten **set-DscLocalConfigurationManager** med **sökvägen** inställd på platsen för MOF-filen för metaconfiguration. Exempel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Konfigurations-ID

I exemplen nedan anges egenskapen **ConfigurationID** för LCM till ett **GUID** som tidigare har skapats för detta ändamål. **ConfigurationID** är vad LCM använder för att hitta rätt konfiguration på hämtnings servern. MOF-konfigurationsfilen på hämtnings servern måste namnges `ConfigurationID.mof` , där *ConfigurationID* är värdet för egenskapen **ConfigurationID** för målnoden LCM. Mer information finns i [publicera konfigurationer till en pull-server (v4/V5)](publishConfigs.md).

Du kan skapa ett slumpmässigt **GUID** med hjälp av exemplet nedan.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Konfigurera en pull-klient för att hämta konfigurationer

Varje klient måste konfigureras i **pull** -läge och tilldelas URL-adressen till pull-servern där konfigurationen lagras. Om du vill göra detta måste du konfigurera den lokala Configuration Manager (LCM) med nödvändig information. Om du vill konfigurera LCM skapar du en särskild typ av konfiguration med ett **LocalConfigurationManager** -block. Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>HTTP DSC-hämtnings Server

Om hämtnings servern har kon figurer ATS som en webb tjänst ställer du in **DownloadManagerName** på **WebDownloadManager** . **WebDownloadManager** kräver att du anger en **ServerURL** till **DownloadManagerCustomData** -nyckeln. Du kan också ange ett värde för **AllowUnsecureConnection** , som i exemplet nedan. Följande skript konfigurerar LCM för att hämta konfigurationer från en server med namnet "PullServer".

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB-resurs

Om hämtnings servern har kon figurer ATS som en SMB-filresurs i stället för en webb tjänst anger du **DownloadManagerName** till **DscFileDownloadManager** snarare än **WebDownLoadManager** . **DscFileDownloadManager** kräver att du anger en **SourcePath** -egenskap i **DownloadManagerCustomData** . Följande skript konfigurerar LCM för att hämta konfigurationer från en SMB-resurs med namnet "SmbDscShare" på en server med namnet "CONTOSO-SERVER".

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Efterföljande moment

När pull-klienten har kon figurer ATS kan du använda följande guider för att utföra nästa steg:

- [Publicera konfigurationer till en hämtningsserver (v4/v5)](publishConfigs.md)
- [Paketera och ladda upp resurser till en hämtningsserver (v4)](package-upload-resources.md)

## <a name="see-also"></a>Se även

- [Konfigurera en DSC-webb hämtnings Server](pullServer.md)
- [Konfigurera en DSC SMB-pull-server](pullServerSMB.md)
