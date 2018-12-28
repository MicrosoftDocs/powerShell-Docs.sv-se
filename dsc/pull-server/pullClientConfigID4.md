---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Ställa in en Pull-klient med hjälp av konfigurations-ID i PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405278"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Ställa in en Pull-klient med hjälp av konfigurations-ID i PowerShell 4.0

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).

Innan du konfigurerar en pullklient, bör du ställa in en pull-server. Även om den här ordningen inte är obligatoriskt, hjälper till med felsökning och hjälper dig att säkerställa att registreringen har lyckats. Om du vill konfigurera en pull-server kan du använda följande guider:

- [Konfigurera en DSC SMB-Hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-Hämtningsserver](pullServer.md)

Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen. I avsnitten nedan visar hur du konfigurerar en hämtningsklient med en SMB-resursen eller HTTP DSC-Hämtningsservern. När nodens LCM uppdaterar kommer det att kontakta konfigurerade platsen för att hämta alla tilldelade konfigurationer. Om alla nödvändiga resurser inte finns på noden, kommer den automatiskt hämta dem från den konfigurerade platsen. Om noden är konfigurerad med en [Report Server](reportServer.md), kommer den sedan att rapportera status för åtgärden.

## <a name="configure-the-pull-client-lcm"></a>Konfigurera en pullklient LCM

Kör något av exemplen nedan skapar en ny utdata-mapp med namnet **PullClientConfigID** och det placerar en metaconfiguration MOF-fil. I det här fallet metaconfiguration MOF-filen namnet `localhost.meta.mof`.

Om du vill tillämpa konfigurationen av genom att anropa den **Set-DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metaconfiguration MOF-filen. Till exempel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Konfigurations-ID

Exemplen nedan set den **ConfigurationID** egenskapen för MGM om du vill en **Guid** som tidigare hade skapats för detta ändamål. Den **ConfigurationID** är vad LCM används för att hitta lämplig konfiguration på hämtningsservern. MOF-konfigurationsfilen på hämtningsservern måste ha namnet `ConfigurationID.mof`, där *ConfigurationID* är värdet för den **ConfigurationID** egenskapen för den målnoden MGM. Mer information finns i [publicera konfigurationer för att en Pull-servern (v4/v5)](publishConfigs.md).

Du kan skapa ett slumpmässigt **Guid** med hjälp av exemplet nedan.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Konfigurera en Pull-klient för att ladda ned konfigurationer

Varje klient måste konfigureras i **Pull** läge och angivna pull-serveradress där dess konfiguration lagras. Då har du konfigurerar den lokala Configuration Manager (LCM) med informationen som krävs. Om du vill konfigurera LCM måste du skapa en särskild typ av konfiguration med en **LocalConfigurationManager** block. Läs mer om hur du konfigurerar LCM [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>HTTP-DSC-Hämtningsserver

Om pull-servern har konfigurerats som en webbtjänst kan du ställa in den **DownloadManagerName** till **WebDownloadManager**. Den **WebDownloadManager** kräver att du anger en **ServerUrl** till den **DownloadManagerCustomData** nyckel. Du kan också ange ett värde för **AllowUnsecureConnection**, som i exemplet nedan. Följande skript konfigurerar LCM pull konfigurationer från en server med namnet ”PullServer”.

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB-resurs

Om pull-servern har konfigurerats som en SMB-filresurs, i stället för en webbtjänst kan du ställa in den **DownloadManagerName** till **DscFileDownloadManager** snarare än **WebDownLoadManager**. Den **DscFileDownloadManager** kräver att du anger en **SourcePath** -egenskapen i den **DownloadManagerCustomData**. Följande skript konfigurerar MGM om du vill dra konfigurationer från en SMB-filresurs som heter ”SmbDscShare” på en server med namnet ”CONTOSO-SERVER”.

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

## <a name="next-steps"></a>Nästa steg

När pull-klienten har konfigurerats kan använda du följande guider för att utföra nästa steg:

- [Publicera konfigurationer till en Pull-Server (v4/v5)](publishConfigs.md)
- [Paket- och ladda upp resurser till en Pull-Server (v4)](package-upload-resources.md)

## <a name="see-also"></a>Se även

- [Konfigurera en DSC-webbpullserver](pullServer.md)
- [Konfigurera en DSC SMB-hämtningsserver](pullServerSMB.md)
