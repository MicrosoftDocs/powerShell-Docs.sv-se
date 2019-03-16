---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Skriva en anpassad DSC-resurs med MOF
ms.openlocfilehash: f243c3e3297711e6f6346a0f813a9c017fe227c3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059736"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Skriva en anpassad DSC-resurs med MOF

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

I det här avsnittet ska vi definiera schemat för en anpassad resurs i Windows PowerShell Desired State Configuration (DSC) i en MOF-fil och implementera resursen i en Windows PowerShell-skriptfil. Den här anpassade resursen är för att skapa och underhålla en webbplats.

## <a name="creating-the-mof-schema"></a>Skapa MOF-schema

Schemat definierar egenskaperna för din resurs som kan konfigureras med en DSC-konfigurationsskript.

### <a name="folder-structure-for-a-mof-resource"></a>Mappstruktur för en MOF-resurs

Skapa följande mappstruktur för att implementera en anpassad DSC-resurs med en MOF-schema. MOF-schemat har definierats i filen Demo_IISWebsite.schema.mof och resurs-skript har definierats i Demo_IISWebsite.psm1. Alternativt kan du skapa ett manifest (psd1)-filen för modulen.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Observera att det är nödvändigt att skapa en mapp med namnet DSCResources under den översta mappen, och att mapp för varje resurs måste ha samma namn som resursen.

### <a name="the-contents-of-the-mof-file"></a>Innehållet i MOF-filen

Följande är ett exempel MOF-fil som kan användas för en anpassad webbplats-resurs. Om du vill följa det här exemplet sparar det här schemat till en fil och anropa filen *Demo_IISWebsite.schema.mof*.

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Observera följande om den tidigare koden:

* `FriendlyName` Definierar namnet som du kan använda för att referera till den här anpassade resursen i DSC-konfigurationsskript. I det här exemplet `Website` motsvarar det egna namnet `Archive` för inbyggt Arkiv-resursen.
* Den klass som du definierar för din anpassade resurs måste komma från `OMI_BaseResource`.
* Typ-kvalificerare `[Key]`på en egenskap som anger att den här egenskapen är en unik identifikation resursinstans. Minst en `[Key]` egenskapen måste anges.
* Den `[Required]` kvalificerare anger att egenskapen krävs (ett värde måste anges i alla konfigurationsskript som använder den här resursen).
* Den `[write]` kvalificerare anger att den här egenskapen är valfri när du använder den anpassade resursen i ett konfigurationsskript. Den `[read]` kvalificerare tyder på att en egenskap inte kan anges av en konfiguration är enbart för rapportering.
* `Values` begränsar vilka värden som kan tilldelas till egenskapen i listan över värden som definierats i `ValueMap`. Mer information finns i [ValueMap och värdet kvalificerare](/windows/desktop/WmiSdk/value-map).
* Inklusive en egenskap kallas `Ensure` med värden `Present` och `Absent` i din resurs bör som ett sätt att bibehålla en konsekvent format med inbyggda DSC-resurser.
* Namnge schemafilen för anpassade på följande sätt: `classname.schema.mof`, där `classname` är den identifierare som följer den `class` nyckelord i din schemadefinition.

### <a name="writing-the-resource-script"></a>Skriva skript för resursen

Skriptet resource implementerar logiken för resursen. I den här modulen måste du inkludera tre funktioner som kallas **Get-TargetResource**, **Set-TargetResource**, och **Test-TargetResource**. Alla tre funktioner måste vidta en parameteruppsättning som är identisk med uppsättningen egenskaper som definieras i MOF-schemat som du skapade för din resurs. I detta dokument kallas den här uppsättningen egenskaper ”resursegenskaper”. Dessa tre funktioner i en fil med namnet Store <ResourceName>.psm1. I följande exempel lagras funktionerna i en fil med namnet Demo_IISWebsite.psm1.

> [!NOTE]
> När du kör samma konfigurationsskript på resursen mer än en gång, får du några fel och resursen ska befinna sig i samma tillstånd som körs skriptet en gång. För att åstadkomma detta måste du kontrollera att din **Get-TargetResource** och **Test-TargetResource** functions Låt resursen inte ändrats och den anropar den **Set-TargetResource**fungerar mer än en gång i en sekvens med samma parameter värden motsvarar alltid att anropa den en gång.

I den **Get-TargetResource** fungera implementering, använda nyckelresurs egenskapsvärdena som tillhandahålls som parametrar för att kontrollera status för den angivna resurs-instansen. Den här funktionen måste returnera en hash-tabell som listar alla resursegenskaper som nycklar och de faktiska värdena för dessa egenskaper som motsvarande värden. Följande kod innehåller ett exempel.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

Beroende på de värden som har angetts för resursegenskaper i konfigurationsskript, den **Set-TargetResource** måste göra något av följande:

* Skapa en ny webbplats
* Uppdatera en befintlig webbplats
* Ta bort en befintlig webbplats

I följande exempel illustrerar detta.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

Slutligen den **Test-TargetResource** funktion måste vidta samma parameter anges som **Get-TargetResource** och **Set-TargetResource**. I din implementering av **Test-TargetResource**, kontrollera status för resursinstans som har angetts i parametrarna för viktiga. Om den aktuella statusen för resursinstansen inte matchar de värden som anges i parameteruppsättningen, returnerar **$false**. Annars returneras **$true**.

I följande kod implementerar den **Test TargetResource** funktion.

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

**Obs**: För enklare felsökning kan använda den **Write-Verbose** cmdlet i din implementering av föregående tre funktioner.
>Denna cmdlet skriver text till den utförliga meddelandeströmmen.
>Som standard visas inte den utförliga meddelandeströmmen, men du kan visa den genom att ändra värdet för den **$VerbosePreference** variabel eller med hjälp av den **utförlig** parameter i DSC-cmdlet: ar = ny.

### <a name="creating-the-module-manifest"></a>Skapa modulmanifestet

Använd slutligen den **New-ModuleManifest** cmdlet för att definiera en <ResourceName>.psd1 fil för anpassad resurs. När du anropar denna cmdlet, referera till skriptfilen för modulen (.psm1) som beskrivs i föregående avsnitt. Inkludera **Get-TargetResource**, **Set-TargetResource**, och **Test TargetResource** i listan med funktioner för att exportera. Följande är en exempel-manifestfilen.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a>Stöd för PsDscRunAsCredential

>**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5.0 och senare.

Den **PsDscRunAsCredential** egenskapen kan användas i [DSC-konfigurationer](../configurations/configurations.md) resource förhindra om du vill ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.
Mer information finns i [kör DSC med autentiseringsuppgifterna för användaren](../configurations/runAsUser.md).

Du kan använda automatiska variabeln för att komma åt användarkontext från inom en anpassad resurs `$PsDscContext`.

Följande kod skulle till exempel skriva användarkontext där resursen körs till en dataström med utförliga utdata:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a>Starta om noden

Om de åtgärder som vidtas din `Set-TargetResource` funktionen kräver en omstart kan du använda en global flagga som talar om MGM om du vill starta om noden. Den här omstarten sker direkt efter den `Set-TargetResource` funktionen har slutförts.

I din `Set-TargetResource` fungera, Lägg till följande rad med kod.

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

För att MGM om du vill starta om noden, den **RebootNodeIfNeeded** flaggan måste anges till `$true`. Den **ActionAfterReboot** inställningen bör också anges till **ContinueConfiguration**, vilket är standard. Läs mer om hur du konfigurerar LCM [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md), eller [konfigurerar den lokala Konfigurationshanteraren (v4)](../managing-nodes/metaConfig4.md).
