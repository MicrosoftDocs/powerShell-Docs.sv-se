---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: 'Publicera till en pull-server med konfigurations-ID: n (v4/V5)'
ms.openlocfilehash: 99c5b89e7d556fa72eaa6a3ba1654936f96a0b9d
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500751"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publicera till en pull-server med konfigurations-ID: n (v4/V5)

I avsnitten nedan förutsätts att du redan har konfigurerat en hämtnings Server. Om du inte har konfigurerat din pull-server kan du använda följande guider:

- [Konfigurera en DSC SMB-hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-hämtningsserver](pullServer.md)

Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status. Den här artikeln visar hur du laddar upp resurser så att de kan laddas ned och konfigurera klienterna så att de automatiskt laddar ned resurser. När noden får en tilldelad konfiguration via **pull** eller **push** (V5) laddar den automatiskt ned eventuella resurser som krävs av konfigurationen från den plats som anges i den lokala Configuration Manager (LCM).

## <a name="compile-configurations"></a>Kompilera konfigurationer

Det första steget för att lagra [konfigurationer](../configurations/configurations.md) på en pull-server är att kompilera dem `.mof` till filer. Om du vill göra en konfiguration generisk och tillämplig på fler klienter använder `localhost` du i Node-blocket. Exemplet nedan visar ett konfigurations gränssnitt som använder `localhost` i stället för ett angivet klient namn.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

När du har kompilerat den allmänna konfigurationen bör du ha en `localhost.mof` -fil.

## <a name="renaming-the-mof-file"></a>Byta namn på MOF-filen

Du kan lagra konfigurationsfiler `.mof` på en pull-server av **ConfigurationName** eller **ConfigurationID**. Beroende på hur du planerar att konfigurera dina pull-klienter kan du välja ett avsnitt nedan för att byta namn på de kompilerade `.mof` filerna på ett korrekt sätt.

### <a name="configuration-ids-guid"></a>Konfigurations-ID (GUID)

Du måste byta namn på `localhost.mof` filen till `<GUID>.mof` fil. Du kan skapa ett slumpmässigt **GUID** med hjälp av exemplet nedan eller med hjälp av cmdleten [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .

```powershell
[System.Guid]::NewGuid()
```

Exempel på utdata

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Du kan sedan byta namn `.mof` på filen med en acceptabel metod. Exemplet nedan använder cmdleten [rename-item](/powershell/module/microsoft.powershell.management/rename-item) .

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Mer information om hur du använder **GUID** i din miljö finns i [Planera för GUID](secureServer.md#guids).

### <a name="configuration-names"></a>Konfigurations namn

Du måste byta namn på `localhost.mof` filen till `<Configuration Name>.mof` fil. I följande exempel används konfigurations namnet från föregående avsnitt. Du kan sedan byta namn `.mof` på filen med en acceptabel metod. Exemplet nedan använder cmdleten [rename-item](/powershell/module/microsoft.powershell.management/rename-item) .

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Skapa kontroll summan

Varje `.mof` fil som lagras på en pull-server eller SMB-resurs måste ha en `.checksum` associerad fil.
Den här filen låter klienter veta när den `.mof` associerade filen har ändrats och ska laddas ned igen.

Du kan skapa en **kontroll Summa** med cmdleten [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) . Du kan också köra `New-DSCCheckSum` mot en katalog med filer med hjälp `-Path` av parametern.
Om det redan finns en kontroll summa kan du tvinga den att skapas igen med `-Force` parametern. I följande exempel angavs en katalog som `.mof` innehåller filen från föregående avsnitt och använder- `-Force` parametern.

```powershell
New-DscChecksum -Path '.\' -Force
```

Inga utdata visas, men nu bör du se en `<GUID or Configuration Name>.mof.checksum` fil.

## <a name="where-to-store-mof-files-and-checksums"></a>Var du ska lagra MOF-filer och kontroll summor

### <a name="on-a-dsc-http-pull-server"></a>På en DSC HTTP-pull-server

När du konfigurerar din HTTP-pull-server, enligt beskrivningen i [Konfigurera en DSC HTTP-pull-server](pullServer.md), anger du kataloger för nycklarna **ModulePath** och **ConfigurationPath** . Nyckeln **ModulePath** anger var en moduls paketerade `.zip` filer ska lagras. **ConfigurationPath** anger var `.mof` filer och `.checksum` filer ska lagras.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>På en SMB-resurs

När du konfigurerar en pull-klient för att använda en SMB-resurs anger du en **ConfigurationRepositoryShare**.
Alla `.mof` filer och `.checksum` filer ska lagras i katalogen **SourcePath** från **ConfigurationRepositoryShare** -blocket.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Nästa steg

Härnäst ska du konfigurera pull-klienter för att hämta den angivna konfigurationen. Mer information finns i någon av följande guider:

- [Konfigurera en pull-klient med hjälp av konfigurations-ID: n (v4)](pullClientConfigId4.md)
- [Konfigurera en pull-klient med konfigurations-ID: n (V5)](pullClientConfigId.md)
- [Konfigurera en pull-klient med konfigurations namn (V5)](pullClientConfigNames.md)

## <a name="see-also"></a>Se även

- [Konfigurera en DSC SMB-hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-hämtningsserver](pullServer.md)
- [Paketera och ladda upp resurser till en hämtnings Server](package-upload-resources.md)
