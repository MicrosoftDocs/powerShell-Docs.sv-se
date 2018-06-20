---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en hämtningsklient med konfigurationsnamn
ms.openlocfilehash: d71376d84b9d4b0e74fdccab4b9249b2ca4263cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188099"
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a>Konfigurera en hämtningsklient med konfigurationsnamn

> Gäller för: Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-Server (Windows-funktionen *DSC-Service*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att börja övergång hanteras klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (omfattar funktioner utöver Pull-Server på Windows Server) eller någon av community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Varje målnoden måste vara ett meddelande om att använda pull-läge och de angivna URL: en där den kontaktar pull-servern för att hämta konfigurationer.
Du måste konfigurera lokala Configuration Manager (MGM) med informationen som behövs för att göra detta.
Om du vill konfigurera MGM om du skapar en särskild typ av konfiguration, med den **DSCLocalConfigurationManager** attribut.
Mer information om hur du konfigurerar MGM finns [konfigurera den lokala Configuration Manager](metaConfig.md).

> **Obs**: det här avsnittet gäller PowerShell 5.0.
Information om hur du skapar en pull-klient i PowerShell 4.0 finns [installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md)

Följande skript konfigurerar MGM pull konfigurationer från en server med namnet ”CONTOSO-PullSrv”:

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

I skriptet på **ConfigurationRepositoryWeb** block definierar pull-servern.
Den **ServerURL** egenskapen anger slutpunkten för pull-servern.

Den **RegistrationKey** -egenskapen är en delad nyckel mellan alla klientnoder för en pull-server och den pull-servern.
Samma värde lagras i en fil på hämtningsservern.

Den **ConfigurationNames** är en matris som anger namnen på de konfigurationer som är avsedda för klientnod.
På hämtningsservern i MOF konfigurationsfilen för den här klientnoden måste ha namnet *ConfigurationNames*MOF, där *ConfigurationNames* överensstämmer med värdet för den **ConfigurationNames**  egenskapsuppsättningen i den här metakonfigurationen.

>**Obs:** om du anger fler än ett värde i den **ConfigurationNames**, måste du också ange **PartialConfiguration** blockerar i konfigurationen.
Information om konfigurationer som delvis finns [PowerShell Desired State Configuration partiella konfigurationer](partialConfigs.md).

När skriptet körs, skapas en ny utdatamapp med namnet **PullClientConfigNames** och det placerar en metakonfigurationen MOF-fil.
I det här fallet metakonfigurationen MOF-filen får namnet `localhost.meta.mof`.

Om du vill tillämpa konfigurationen genom att anropa den **Set DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metakonfigurationen MOF-filen.

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> **Obs**: registreringsnycklar fungerar bara med pull-webbservrar.
Du måste använda **ConfigurationID** med en SMB-pull-server.
Information om hur du konfigurerar en pull-server med hjälp av **ConfigurationID**, se [installera en pull-klient med hjälp av konfigurations-ID](PullClientConfigNames.md)

## <a name="resource-and-report-servers"></a>Resurs- och -servrar

Om du bara anger en **ConfigurationRepositoryWeb** eller **ConfigurationRepositoryShare** blockera i konfigurationen MGM (som i föregående exempel), pull-klienten hämtar resurser från den angiven server, men det kommer inte skicka rapporter till den.
Du kan använda en enda hämtningsservern för konfigurationer, resurser och rapportering, men du måste skapa en **ReportRepositoryWeb** block att konfigurera rapportering.
I följande exempel visas en metakonfigurationen som ställer in en klient till pull konfigurationer och resurser och skicka rapportdata till en enda pull-server.

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
        }
    }
}
PullClientConfigNames
```

Du kan också ange olika pull-servrar för resurser och rapportering.
Om du vill ange en resurs-server du använder antingen en **ResourceRepositoryWeb** (för en webbserver pull) eller en **ResourceRepositoryShare** block (för en SMB-pull-server).
Om du vill ange en rapportserver som du använder en **ReportRepositoryWeb** block.
En rapportserver får inte vara en SMB-server.
Följande metakonfigurationen konfigurerar en pull-klient för att få sina konfigurationer från **CONTOSO PullSrv** och dess resurser från **CONTOSO ResourceSrv**, och för att skicka statusrapporter till  **CONTOSO-ReportSrv**:

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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Se även

* [Installera en pull-klient med konfigurations-ID](PullClientConfigNames.md)
* [Ställer in en pull webbserver DSC](pullServer.md)