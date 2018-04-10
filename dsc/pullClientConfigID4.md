---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0
ms.openlocfilehash: 7074d842b7b99ef3fb6498b6dbc1e561b14caf16
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a>Installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Varje målnoden måste vara ett meddelande om att använda pull-läge och de angivna URL: en där den kontaktar pull-servern för att hämta konfigurationer. Du måste konfigurera lokala Configuration Manager (MGM) med informationen som behövs för att göra detta. Om du vill konfigurera MGM om skapar du en särskild typ av konfiguration som kallas ”metakonfigurationen”. Mer information om hur du konfigurerar MGM finns [Windows PowerShell 4.0 önskad tillstånd Configuration Local Configuration Manager](metaConfig4.md)

Följande skript konfigurerar MGM pull konfigurationer från en server med namnet ”PullServer”:

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

I skriptet **DownloadManagerCustomData** överför Webbadressen för pull-servern och (för det här exemplet) kan en osäker anslutning.

När skriptet körs, skapas en ny utdatamapp kallas **SimpleMetaConfigurationForPull** och det placerar en metakonfigurationen MOF-fil.

Om du vill tillämpa konfigurationen genom att använda **Set DscLocalConfigurationManager** med parametrar för **ComputerName** (använda ”localhost”) och **sökväg** (sökvägen till platsen för den rikta nodens localhost.meta.mof-fil). Till exempel:
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a>Konfigurations-ID
Script-anger den **ConfigurationID** -egenskapen för MGM till ett GUID som tidigare hade skapats för detta ändamål (du kan skapa ett GUID med hjälp av den **ny Guid** cmdlet). Den **ConfigurationID** är vad MGM om du använder för att hitta rätt konfiguration på hämtningsservern. Konfigurationen MOF-filen på hämtningsservern måste ha namnet `ConfigurationID.mof`, där *ConfigurationID* är värdet för den **ConfigurationID** -egenskapen för nodens target MGM.

## <a name="pulling-from-an-smb-server"></a>Dra från en SMB-server

Om den pull-servern har konfigurerats som en SMB-filresursen i stället för en webbtjänst, anger du den **DscFileDownloadManager** snarare än den **WebDownLoadManager**.
Den **DscFileDownloadManager** tar en **SourcePath** egenskapen i stället för **ServerUrl**. Följande skript konfigurerar MGM om du vill dra konfigurationer från en SMB-resurs med namnet ”SmbDscShare” på en server med namnet ”CONTOSO-SERVER”:

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a>Se även

- [Ställer in en pull webbserver DSC](pullServer.md)
- [Konfigurera en DSC SMB-pullserver](pullServerSMB.md)