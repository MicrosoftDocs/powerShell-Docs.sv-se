---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 542a210ab47c650eac625108a78e76bc2cd55572
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404816"
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

![Tabbifyllning för resursen](/media/resource-tabcompletion.png)
