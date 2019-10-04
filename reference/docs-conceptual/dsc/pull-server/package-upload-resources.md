---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Paketera och ladda upp resurser till en hämtnings Server
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942246"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Paketera och ladda upp resurser till en hämtnings Server

I avsnitten nedan förutsätts att du redan har konfigurerat en hämtnings Server. Om du inte har konfigurerat din pull-server kan du använda följande guider:

- [Konfigurera en DSC SMB-pull-server](pullServerSmb.md)
- [Konfigurera en DSC HTTP-pull-server](pullServer.md)

Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status. Den här artikeln visar hur du laddar upp resurser så att de kan laddas ned och konfigurera klienterna att ladda ned resurser automatiskt. När noden tar emot en tilldelad konfiguration via **pull** eller **push** (V5) laddar den automatiskt ned eventuella resurser som krävs av konfigurationen från den plats som anges i LCM.

## <a name="package-resource-modules"></a>Paketera resurs moduler

Varje resurs som är tillgänglig för en klient som ska laddas ned måste lagras i en zip-fil. I exemplet nedan visas de steg som krävs med hjälp av [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) -resursen.

> [!NOTE]
> Om du har några klienter som använder PowerShell 4,0 måste du göra en plan för resurs mappstrukturen och ta bort alla versioner av mappar. Mer information finns i [flera resurs versioner](../configurations/import-dscresource.md#multiple-resource-versions).

Du kan komprimera resurs katalogen med valfritt verktyg, skript eller metod som du föredrar. I Windows kan du *högerklicka* på katalogen "xPSDesiredStateConfiguration" och välja "Skicka till" och sedan "komprimerad mapp".

![Högerklicka](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>Namnge resurs arkivet

Resurs arkivet måste ha namnet med följande format:

```
{ModuleName}_{Version}.zip
```

I exemplet ovan ska "xPSDesiredStateConfiguration. zip" byta namn till "xPSDesiredStateConfiguration_ 8.4.4.0. zip".

### <a name="create-checksums"></a>Skapa kontroll summor

När modulen har komprimerats och bytt namn måste du skapa en **kontroll Summa**.  **Kontroll summan** används av LCM på klienten för att avgöra om resursen har ändrats och måste laddas ned igen. Du kan skapa en **kontroll Summa** med cmdleten [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) , som visas i exemplet nedan.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Inga utdata visas, men nu bör du se en "xPSDesiredStateConfiguration_-8.4.4.0. zip. kontroll Summa". Du kan också köra `New-DSCCheckSum` mot en katalog med filer med hjälp av parametern `-Path`. Om det redan finns en kontroll summa kan du tvinga den att skapas igen med parametern `-Force`.

### <a name="where-to-store-resource-archives"></a>Var resurs Arkiv ska lagras

#### <a name="on-a-dsc-http-pull-server"></a>På en DSC HTTP-pull-server

När du konfigurerar din HTTP-pull-server, enligt beskrivningen i [Konfigurera en DSC HTTP-pull-server](pullServer.md), anger du kataloger för nycklarna **ModulePath** och **ConfigurationPath** . **ConfigurationPath** -nyckeln anger var alla ". MOF"-filer ska lagras. **ModulePath** anger var DSC-resurspooler ska lagras.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>På en SMB-resurs

Om du har angett en **ResourceRepositoryShare**när du konfigurerar din pull-klient, lagrar Arkiv och kontroll summor i katalogen **SourcePath** från **ResourceRepositoryShare** -blocket.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Om du bara har angett en **ConfigurationRepositoryShare**, när du konfigurerar din pull-klient, lagrar Arkiv och kontroll summor i **SourcePath** -katalogen från **ConfigurationRepositoryShare** -blocket.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Uppdaterar resurser

Du kan tvinga en nod att uppdatera sina resurser genom att ändra versions numret i arkivets namn, eller genom att skapa en ny kontroll summa. Hämtnings klienten söker efter nyare versioner av nödvändiga resurser, samt uppdaterade kontroll summor, när dess LCM uppdateras.

## <a name="see-also"></a>Se även

- [Konfigurera en DSC SMB-pull-server](pullServerSmb.md)
- [Konfigurera en DSC HTTP-pull-server](pullServer.md)
