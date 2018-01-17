---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Installera en pull-klient med hjälp av konfigurations-ID"
ms.openlocfilehash: 6e3dda1de0bfbf52fb876fdcd2dd2e99da4583dd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a>Installera en pull-klient med hjälp av konfigurations-ID

> Gäller för: Windows PowerShell 5.0

Varje målnoden måste vara ett meddelande om att använda pull-läge och de angivna URL: en där den kontaktar pull-servern för att hämta konfigurationer. Du måste konfigurera lokala Configuration Manager (MGM) med informationen som behövs för att göra detta. Om du vill konfigurera MGM om du skapar en särskild typ av konfiguration, med den **DSCLocalConfigurationManager** attribut. Mer information om hur du konfigurerar MGM finns [konfigurera den lokala Configuration Manager](metaConfig.md).

> **Obs**: det här avsnittet gäller PowerShell 5.0. Information om hur du skapar en pull-klient i PowerShell 4.0 finns [installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md)

Följande skript konfigurerar MGM pull konfigurationer från en server med namnet ”CONTOSO-PullSrv”.

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

I skriptet på **ConfigurationRepositoryWeb** block definierar pull-servern. Den **ServerURL**

När skriptet körs, skapas en ny utdatamapp med namnet **PullClientConfigID** och det placerar en metakonfigurationen MOF-fil. I det här fallet metakonfigurationen MOF-filen får namnet `localhost.meta.mof`.

Om du vill tillämpa konfigurationen genom att anropa den **Set DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metakonfigurationen MOF-filen. Exempelvis: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## <a name="configuration-id"></a>Konfigurations-ID

Script-anger den **ConfigurationID** -egenskapen för MGM till ett GUID som tidigare hade skapats för detta ändamål (du kan skapa ett GUID med hjälp av den **ny Guid** cmdlet). Den **ConfigurationID** är vad MGM om du använder för att hitta rätt konfiguration på hämtningsservern. Konfigurationen MOF-filen på hämtningsservern måste ha namnet _ConfigurationID_MOF, där _ConfigurationID_ är värdet för den **ConfigurationID** -egenskapen för målet nodens MGM.

## <a name="smb-pull-server"></a>SMB pull-servern

Om du vill konfigurera en klient till pull konfigurationer från en SMB-server, använder en **ConfigurationRepositoryShare** block. I en **ConfigurationRepositoryShare** block du ange sökvägen till servern genom att ange den **SourcePath** egenskapen. Följande metakonfigurationen konfigurerar målnoden ska ta emot från en SMB-pull-server med namnet **SMBPullServer**.

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
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a>Resurs- och -servrar

Om du bara anger en **ConfigurationRepositoryWeb** eller **ConfigurationRepositoryShare** blockera i konfigurationen MGM (som i föregående exempel), pull-klienten hämtar resurser från den angiven server, men det kommer inte skicka rapporter till den. Du kan använda en enda hämtningsservern för konfigurationer, resurser och rapportering, men du måste skapa en **ReportRepositoryWeb** block att konfigurera rapportering. 

I följande exempel visas en metakonfigurationen som ställer in en klient till pull konfigurationer och resurser och skicka rapportdata till en enda pull-server.

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

Du kan också ange olika pull-servrar för resurser och rapportering. Om du vill ange en resurs-server du använder antingen en **ResourceRepositoryWeb** (för en webbserver pull) eller en **ResourceRepositoryShare** block (för en SMB-pull-server).
Om du vill ange en rapportserver som du använder en **ReportRepositoryWeb** block. En rapportserver får inte vara en SMB-server.
Följande metakonfigurationen konfigurerar en pull-klient för att få sina konfigurationer från **CONTOSO PullSrv** och dess resurser från **CONTOSO ResourceSrv**, och för att skicka statusrapporter till  **CONTOSO-ReportSrv**:

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

## <a name="see-also"></a>Se även

* [Installera en pull-klient med konfigurationsnamn](pullClientConfigNames.md)

