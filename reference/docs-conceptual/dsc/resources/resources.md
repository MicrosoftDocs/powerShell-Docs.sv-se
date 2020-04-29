---
ms.date: 02/28/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 863898d910cc3c75c3e5977a5b6b0657ba7ed512
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278262"
---
# <a name="dsc-resources"></a>DSC-resurser

> Gäller för Windows PowerShell 4,0 och uppåt.

## <a name="overview"></a>Översikt

DSC-resurser (Desired State Configuration) tillhandahåller Bygg stenar för en DSC-konfiguration. En resurs exponerar egenskaper som kan konfigureras (schema) och innehåller PowerShell-skript som de lokala Configuration Manager (LCM) anropar för att göra det.

En resurs kan modellera något som generiskt som en fil eller som en inställning för IIS-servern. Grupper av resurser som är kombinerade i till en DSC-modul som organiserar alla nödvändiga filer i en struktur som är portabel och innehåller metadata för att identifiera hur resurserna är avsedda att användas.

Varje resurs har ett *-schema som avgör den syntax som behövs för att använda resursen i en [konfiguration](../configurations/configurations.md).
En resurs schema kan definieras på följande sätt:

- **Schema. MOF** -fil: de flesta resurser definierar deras _schema_ i en schema. MOF-fil med hjälp av [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- **'\<Resurs namn\>. schema. psm1 '** -fil: [sammansatta resurser](../configurations/compositeConfigs.md) definierar *schemat* i<ResourceName>en. schema. psm1-fil med hjälp av ett [parameter block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **'\<Resurs namn\>. psm1 '** -fil: klassbaserade DSC-resurser definierar deras _schema_ i klass definitionen. Objekt betecknas som klass egenskaper. Mer information finns i [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Om du vill hämta syntaxen för en DSC-resurs använder du cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) med `-Syntax` parametern. Den här användningen liknar att använda [Get-Command](/powershell/module/microsoft.powershell.core/get-command) med `-Syntax` parametern för att hämta cmdlet-syntaxen. De utdata som visas visar den mall som används för ett resurs block för den resurs som du anger.

```powershell
Get-DscResource -Syntax Service
```

De utdata du ser liknar utdata nedan, men den här resursens syntax kan ändras i framtiden. Precis som cmdlet-syntaxen är de _nycklar_ som visas i hakparenteser valfria. Typerna anger vilken typ av data varje nyckel förväntar sig.

> [!NOTE]
> Nyckeln **säkerställer att** nyckeln är valfri eftersom den används som standard.

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

I en konfiguration kan ett **tjänst** resurs block se ut så här för att **säkerställa** att Spooler-tjänsten körs.

> [!NOTE]
> Innan du använder en resurs i en konfiguration måste du importera den med hjälp av [import-dscresource Keyword Supports](../configurations/import-dscresource.md).

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

Konfigurationer kan innehålla flera instanser av samma resurs typ. Varje instans måste ha ett unikt namn. I följande exempel läggs ett andra **tjänst** resurs block till för att konfigurera tjänsten "DHCP".

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> Från och med PowerShell 5,0 lades IntelliSense till för DSC. Med den här nya funktionen kan du <kbd>TAB</kbd> använda TABB <kbd>-och</kbd>+<kbd>rymd utrymme</kbd> för att komplettera nyckel namn automatiskt.

![Slut för ande av resurs flik](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a>Typer av resurser

Windows levereras med inbyggda resurser och Linux har leverantörsspecifika resurser. Det finns resurser för [över-nod-beroenden](../configurations/crossNodeDependencies.md), paket hanterings resurser samt[ägda och bevarade resurser](https://github.com/dsccommunity). Du kan använda ovanstående steg för att fastställa syntaxen för dessa resurser och hur du använder dem. De sidor som hanterar dessa resurser har arkiverats under **referens**.

### <a name="windows-built-in-resources"></a>Inbyggda resurser i Windows

- [Arkivera resursen](../reference/resources/windows/archiveResource.md)
- [Miljöresurs](../reference/resources/windows/environmentResource.md)
- [Filresurs](../reference/resources/windows/fileResource.md)
- [Gruppresurs](../reference/resources/windows/groupResource.md)
- [GroupSet-resurs](../reference/resources/windows/groupSetResource.md)
- [Loggresurs](../reference/resources/windows/logResource.md)
- [Paketresurs](../reference/resources/windows/packageResource.md)
- [ProcessSet-resurs](../reference/resources/windows/ProcessSetResource.md)
- [Registerresurser](../reference/resources/windows/registryResource.md)
- [Skriptresurs](../reference/resources/windows/scriptResource.md)
- [Tjänstresurs](../reference/resources/windows/serviceResource.md)
- [ServiceSet-resurs](../reference/resources/windows/serviceSetResource.md)
- [Användarresurs](../reference/resources/windows/userResource.md)
- [WindowsFeature-resurs](../reference/resources/windows/windowsFeatureResource.md)
- [WindowsFeatureSet-resurs](../reference/resources/windows/windowsFeatureSetResource.md)
- [WindowsOptionalFeature-resurs](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [WindowsOptionalFeatureSet-resurs](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [WindowsPackageCabResource-resurs](../reference/resources/windows/windowsPackageCabResource.md)
- [WindowsProcess-resurs](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a>Beroende resurser mellan noder

- [WaitForAll-resurs](../reference/resources/windows/waitForAllResource.md)
- [WaitForSome-resurs](../reference/resources/windows/waitForSomeResource.md)
- [WaitForAny-resurs](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a>Paket hanterings resurser

- [PackageManagement-resurs](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [PackageManagementSource-resurs](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a>Linux-resurser

- [Linux-Arkiv resurs](../reference/resources/linux/lnxArchiveResource.md)
- [Linux-miljö resurs](../reference/resources/linux/lnxEnvironmentResource.md)
- [Linux FileLine-resurs](../reference/resources/linux/lnxFileLineResource.md)
- [Linux-filresurs](../reference/resources/linux/lnxFileResource.md)
- [Linux-grupp resurs](../reference/resources/linux/lnxGroupResource.md)
- [Linux-paket resurs](../reference/resources/linux/lnxPackageResource.md)
- [Linux-skript resurs](../reference/resources/linux/lnxScriptResource.md)
- [Linux-Tjänsteresurs](../reference/resources/linux/lnxServiceResource.md)
- [Linux SshAuthorizedKeys-resurs](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [Linux-användar resurs](../reference/resources/linux/lnxUserResource.md)
