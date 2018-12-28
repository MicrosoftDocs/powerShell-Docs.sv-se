---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Paket- och ladda upp resurser till en Pull-Server
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404757"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Paket- och ladda upp resurser till en Pull-Server

I avsnitten nedan förutsätter att du har ställt in en Pull-servern. Om du inte har konfigurerat din Pull-servern kan du använda följande guider:

- [Konfigurera en DSC SMB-Hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-Hämtningsserver](pullServer.md)

Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen. Den här artikeln visar hur du laddar upp resurser så att de blir tillgängliga för att hämta och konfigurera klienter för att hämta resurser automatiskt. När nod som tar emot en tilldelade konfiguration via **hämta** eller **Push** (v5) hämtas automatiskt alla resurser som krävs av konfigurationen från den plats som anges i LCM.

## <a name="package-resource-modules"></a>Paketet Resource moduler

Varje resurs som är tillgängliga för en klient för att ladda ned måste lagras i en ”ZIP”-fil. Exemplet nedan visar de steg som krävs med hjälp av den [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resurs.

> [!NOTE]
> Om du har alla klienter som använder PowerShell 4.0, du behöver flaten mappstrukturen för resursen och ta bort alla version mappar. Mer information finns i [flera versioner av resursen](../configurations/import-dscresource.md#multiple-resource-versions).

Du kan komprimera resursbiblioteket med hjälp av verktyg, skript eller metod som du föredrar. I Windows, kan du *högerklickar du på* på ”xPSDesiredStateConfiguration” katalog- och välj ”Skicka till” och sedan ”komprimerade mappen”.

![Högerklicka på](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>Namnge resursen arkivet

Resurs-arkivet måste ha namnet med följande format:

```
{ModuleName}_{Version}.zip
```

I exemplet ovan ska ”xPSDesiredStateConfiguration.zip” omdöpt ”xPSDesiredStateConfiguration_8.4.4.0.zip”.

### <a name="create-checksums"></a>Skapa kontrollsummor

När modulen resurs har komprimeras och byta namn på, måste du skapa en **kontrollsumma**.  Den **kontrollsumma** används av LCM på klienten för att avgöra om resursen har ändrats och måste hämtas igen. Du kan skapa en **kontrollsumma** med den [New DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, enligt exemplet nedan.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Inga utdata visas, men du bör nu se en ”xPSDesiredStateConfiguration_8.4.4.0.zip.checksum”. Du kan också köra `New-DSCCheckSum` mot en katalog med filer med hjälp av den `-Path` parametern. Om det finns redan en kontrollsumma, kan du tvinga den återskapas med den `-Force` parametern.

### <a name="where-to-store-resource-archives"></a>Var du vill lagra Resource Arkiv

#### <a name="on-a-dsc-http-pull-server"></a>På en DSC HTTP-Hämtningsserver

När du konfigurerar http-Pull-servern, enligt beskrivningen i [konfigurera en DSC HTTP-Hämtningsserver](pullServer.md), anger du kataloger för den **ModulePath** och **ConfigurationPath** nycklar. Den **ConfigurationPath** nyckel anger där alla MOF-filerna ska sparas. Den **ModulePath** anger där alla moduler för DSC-resurs ska sparas.

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

Om du har angett en **ResourceRepositoryShare**, när konfigurationen av din Pull-klienten lagrar Arkiv och kontrollsummor i den **SourcePath** katalogen från den **ResourceRepositoryShare** block.

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

Om du bara anges en **ConfigurationRepositoryShare**, när konfigurationen av din Pull-klienten lagrar Arkiv och kontrollsummor i den **SourcePath** katalogen från den  **ConfigurationRepositoryShare** block.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Uppdatera resurser

Du kan tvinga en nod för att uppdatera dess resurser genom att ändra versionsnumret i den arkivnamn eller genom att skapa en ny kontrollsumma. Hämta klienten ska söka efter nyare versioner av resurser som krävs samt uppdateras kontrollsummor, när dess LCM uppdateras.

## <a name="see-also"></a>Se även

- [Konfigurera en DSC SMB-Hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-Hämtningsserver](pullServer.md)
