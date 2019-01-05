---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046699"
---
# <a name="dsc-resources"></a>DSC-resurser

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Desired State Configuration (DSC) resurser innehåller byggstenarna för en DSC-konfiguration. En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som lokala Configuration Manager (LCM)-anrop till ”gör den det”.

En resurs kan utforma något som allmän som en fil eller så specifik som en inställning för IIS-server.  Grupper av som resurser kombineras till en DSC-modul som organiserar alla filerna som krävs i att en struktur som är portabelt och innehåller metadata för att identifiera hur resurserna är avsedda att användas i.

Varje resurs har en * schema som anger den syntax som krävs för att använda resursen i en [Configuration](../configurations/configurations.md). Schemat för en resurs kan definieras på följande sätt:

- **'Schema.Mof'** fil: De flesta resurser definiera sina *schemat* i en schema.mof fil, använda [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- **”\<Resursnamn\>. schema.psm1'** fil: [Sammansatta resurser](../configurations/compositeConfigs.md) definiera sina *schemat* i en ”<ResourceName>. schema.psm1-fil med hjälp av en [Parameterblocket](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **”\<Resursnamn\>.psm1'** fil: Klassen baserat DSC-resurser definiera sina *schemat* i klassdefinitionen. Syntax objekt betecknas som klassegenskaper. Mer information finns i [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Använd för att hämta syntaxen för en DSC-resurs i [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet med den `-Syntax` parametern. Den här användningen är ungefär som att använda [Get-Command](/powershell/module/microsoft.powershell.core/get-command) med den `-Syntax` parametern för att hämta cmdlet-syntax. Du ser utdata visar den mall som användes för en resurs-block för den resurs som du anger.

```powershell
Get-DscResource -Syntax Service
```

Du ser utdata bör likna utdata nedan, även om den här resursen syntax kan ändras i framtiden. Som cmdlet-syntax i *nycklar* visas inom hakparentes är valfria. Typerna ange vilken typ av data som förväntar sig att varje nyckel.

> [!NOTE]
> Den **Kontrollera** nyckeln är valfri eftersom standard ”aktuella”.

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

I en konfiguration för en **Service** resource block kan se ut så här för att **Kontrollera** som tjänsten Spooler körs.

> [!NOTE]
> Innan du använder en resurs i en konfiguration, måste du importera den med hjälp av [Import-DSCResource](../configurations/import-dscresource.md).

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

Konfigurationer kan innehålla flera instanser av samma resurstypen. Varje instans måste vara unika namn. I följande exempel visas en andra **Service** resource block har lagts till för att konfigurera tjänsten ”DHCP”.

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
> Från och med PowerShell 5.0, intellisense lades till för DSC. Den här nya funktionen kan du använda \<FLIKEN\> och \<Ctrl + blanksteg\> till automatisk komplettering nyckelnamn.

![Tabbifyllning för resursen](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>Inbyggda resurser

Förutom community-resurser finns inbyggda resurser för Windows, Linux-resurser och resurser för beroenden mellan noder. Du kan använda stegen ovan för att fastställa syntaxen för dessa resurser och hur de används. De sidor som betjänar dessa resurser har arkiverats **referens**.

Inbyggda resurser för Windows

* [Arkivera resursen](../reference/resources/windows/archiveResource.md)
* [Miljöresurs](../reference/resources/windows/environmentResource.md)
* [Filresurs](../reference/resources/windows/fileResource.md)
* [Gruppresurs](../reference/resources/windows/groupResource.md)
* [GroupSet-resurs](../reference/resources/windows/groupSetResource.md)
* [Loggresurs](../reference/resources/windows/logResource.md)
* [Paketresurs](../reference/resources/windows/packageResource.md)
* [ProcessSet-resurs](../reference/resources/windows/ProcessSetResource.md)
* [Registerresurser](../reference/resources/windows/registryResource.md)
* [Skriptresurs](../reference/resources/windows/scriptResource.md)
* [Tjänstresurs](../reference/resources/windows/serviceResource.md)
* [ServiceSet-resurs](../reference/resources/windows/serviceSetResource.md)
* [Användarresurs](../reference/resources/windows/userResource.md)
* [WindowsFeature-resurs](../reference/resources/windows/windowsFeatureResource.md)
* [WindowsFeatureSet-resurs](../reference/resources/windows/windowsFeatureSetResource.md)
* [WindowsOptionalFeature-resurs](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [WindowsOptionalFeatureSet-resurs](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [WindowsPackageCabResource resurs](../reference/resources/windows/windowsPackageCabResource.md)
* [WindowsProcess-resurs](../reference/resources/windows/windowsProcessResource.md)

[Mellan noder beroende](../configurations/crossNodeDependencies.md) resurser

* [WaitForAll resurs](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome resurs](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny resurs](../reference/resources/windows/waitForAnyResource.md)

Paketet Management-resurser

* [PackageManagement-resurs](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [PackageManagementSource resurs](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Linux-resurser

* [Linux Arkivera resursen](../reference/resources/linux/lnxArchiveResource.md)
* [Miljöresurs för Linux](../reference/resources/linux/lnxEnvironmentResource.md)
* [Linux FileLine resurs](../reference/resources/linux/lnxFileLineResource.md)
* [Linux-filresurs](../reference/resources/linux/lnxFileResource.md)
* [Linux Gruppresurs](../reference/resources/linux/lnxGroupResource.md)
* [Linux Paketresurs](../reference/resources/linux/lnxPackageResource.md)
* [Skriptresurs på Linux](../reference/resources/linux/lnxScriptResource.md)
* [Linux-tjänstresurs](../reference/resources/linux/lnxServiceResource.md)
* [Linux SshAuthorizedKeys resurs](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Linux användarresurs](../reference/resources/linux/lnxUserResource.md)
