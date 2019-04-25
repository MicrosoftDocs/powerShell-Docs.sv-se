---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Publicera till en Pull-servern med hjälp av konfigurations-ID (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079514"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publicera till en Pull-servern med hjälp av konfigurations-ID (v4/v5)

I avsnitten nedan förutsätter att du har ställt in en Pull-servern. Om du inte har konfigurerat din Pull-servern kan du använda följande guider:

- [Konfigurera en DSC SMB-Hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-Hämtningsserver](pullServer.md)

Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen. Den här artikeln visar hur du laddar upp resurser så att de blir tillgängliga för att hämta och konfigurera klienter för att hämta resurser automatiskt. När nod som tar emot en tilldelade konfiguration via **hämta** eller **Push** (v5) hämtas automatiskt alla resurser som krävs av konfigurationen från den plats som anges i LCM.

## <a name="compile-configurations"></a>Kompilera konfigurationer

Det första steget för att lagra [konfigurationer](../configurations/configurations.md) på en Pull-servern är att sammanställa dem i MOF-filerna. Om du vill göra en konfiguration för allmän och gäller för flera klienter, använda `localhost` i noden-block. Exemplet nedan visar ett Configuration-gränssnitt som använder `localhost` i stället för en viss klient-namn.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

När du har skapat din Allmän konfiguration, bör du ha en ”localhost.mof”-fil.

## <a name="renaming-the-mof-file"></a>Byta namn på MOF-filen

Du kan lagra konfiguration MOF-filerna på en Hämtningsserver av **ConfigurationName** eller **ConfigurationID**. Du kan välja ett avsnitt nedan för att korrekt Byt namn på din kompilerade MOF-filerna beroende på hur du planerar att konfigurera din pull-klienter.

### <a name="configuration-ids-guid"></a>Konfigurations-ID (GUID)

Du måste byta namn på filen ”localhost.mof” till ”<GUID>.mof” fil. Du kan skapa ett slumpmässigt **Guid** i exemplet nedan eller genom att använda den [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Exempel på utdata

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Du kan sedan byta namn på filen ”.mof” med någon godkänd av metoderna. I exemplet nedan, används den [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Mer information om hur du använder **GUID** i din miljö, se [planera för GUID](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Konfigurationsnamn

Du måste byta namn på filen ”localhost.mof” till ”<Configuration Name>.mof” fil. I följande exempel används konfigurationsnamnet i föregående avsnitt. Du kan sedan byta namn på filen ”.mof” med någon godkänd av metoderna. I exemplet nedan, används den [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Skapa kontrollsumman

Varje ”.mof”-fil som lagras på en Pull-servern eller SMB-resursen måste ha en associerad ”.checksum”-fil. Den här filen tillåter klienter att veta när filen associerade ”.mof” har ändrats och ska laddas ned igen.

Du kan skapa en **kontrollsumma** med den [New DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet. Du kan också köra `New-DSCCheckSum` mot en katalog med filer med hjälp av den `-Path` parametern. Om det finns redan en kontrollsumma, kan du tvinga den återskapas med den `-Force` parametern. I följande exempel anges en katalog som innehåller filen ”.mof” i föregående avsnitt och använder den `-Force` parametern.

```powershell
New-DscChecksum -Path '.\' -Force
```

Inga utdata visas, men du bör nu se en ”<GUID or Configuration Name>. mof.checksum” fil.

## <a name="where-to-store-mof-files-and-checksums"></a>Var du vill lagra MOF-filer och kontrollsummor

### <a name="on-a-dsc-http-pull-server"></a>På en DSC HTTP-Hämtningsserver

När du konfigurerar http-Pull-servern, enligt beskrivningen i [konfigurera en DSC HTTP-Hämtningsserver](pullServer.md), anger du kataloger för den **ModulePath** och **ConfigurationPath** nycklar. Den **ConfigurationPath** nyckel anger där alla MOF-filerna ska sparas. Den **ConfigurationPath** anger där alla ”.mof” och ”.checksum”-filer ska sparas.

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

När du har konfigurerat en Pull-klient du använder en SMB-resurs kan du ange en **ConfigurationRepositoryShare**. Alla ”.mof” och ”.checksum”-filer ska sedan lagras i den **SourcePath** katalogen från den **ConfigurationRepositoryShare** block.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Nästa steg

Därefter ska du konfigurera Pull-klienter för att hämta den angivna konfigurationen. Mer information finns i någon av följande guider:

- [Konfigurera en Pull-klient som använder konfigurations-ID (v4)](pullClientConfigId4.md)
- [Konfigurera en Pull-klient som använder konfigurations-ID (v5)](pullClientConfigId.md)
- [Ställa in en Pull-klient med konfigurationsnamn (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Se även

- [Konfigurera en DSC SMB-Hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-Hämtningsserver](pullServer.md)
- [Paket- och ladda upp resurser till en Pull-Server](package-upload-resources.md)
