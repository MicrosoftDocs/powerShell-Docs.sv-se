---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Skriva en anpassad DSC-resurs med MOF
ms.openlocfilehash: 24e9d15bcbe1eddd297daeb04e0713c443e52c38
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941210"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Skriva en anpassad DSC-resurs med MOF

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

I det här avsnittet definierar vi schemat för en anpassad DSC-resurs (Windows PowerShell Desired State Configuration) i en MOF-fil och implementerar resursen i en Windows PowerShell-skriptfil. Den här anpassade resursen används för att skapa och underhålla en webbplats.

## <a name="creating-the-mof-schema"></a>Skapa MOF-schemat

Schemat definierar egenskaperna för din resurs som kan konfigureras med ett DSC-konfigurations skript.

### <a name="folder-structure-for-a-mof-resource"></a>Mappstruktur för en MOF-resurs

Skapa följande mappstruktur om du vill implementera en anpassad DSC-resurs med ett MOF-schema. MOF-schemat definieras i filen Demo_IISWebsite. schema. MOF och resurs skriptet definieras i Demo_IISWebsite. psm1. Du kan också skapa en modul manifest fil (psd1).

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Observera att det är nödvändigt att skapa en mapp med namnet DSCResources under mappen på den översta nivån och att mappen för varje resurs måste ha samma namn som resursen.

### <a name="the-contents-of-the-mof-file"></a>MOF-filens innehåll

Följande är ett exempel på en MOF-fil som kan användas för en anpassad webbplats resurs. Om du vill följa det här exemplet sparar du schemat till en fil och anropar filen *Demo_IISWebsite. schema. MOF*.

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

Observera följande om föregående kod:

* `FriendlyName`definierar det namn som du kan använda för att referera till den här anpassade resursen i DSC-konfigurations skript. I det här exemplet `Website` motsvarar det egna namnet `Archive` för den inbyggda Arkiv resursen.
* Den klass som du definierar för din anpassade resurs måste vara härledd från `OMI_BaseResource`.
* Typen Qualifier, `[Key]`i en egenskap anger att den här egenskapen unikt identifierar resurs instansen. Minst en `[Key]` egenskap krävs.
* `[Required]` Kvalificeraren anger att egenskapen är obligatorisk (ett värde måste anges i alla konfigurations skript som använder den här resursen).
* `[write]` Kvalificeraren anger att den här egenskapen är valfri när du använder den anpassade resursen i ett konfigurations skript. `[read]` Kvalificeraren anger att en egenskap inte kan ställas in av en konfiguration och endast är avsedd för rapportering.
* `Values`begränsar de värden som kan tilldelas till egenskapen till listan över värden som definierats i `ValueMap`. Mer information finns i [ValueMap och värde kvalificerare](/windows/desktop/WmiSdk/value-map).
* Att inkludera en egenskap `Ensure` som kallas `Present` med `Absent` värden och i din resurs rekommenderas som ett sätt att underhålla ett konsekvent format med inbyggda DSC-resurser.
* Namnge schema filen för din anpassade resurs enligt följande: `classname.schema.mof`, där `classname` är identifieraren som följer `class` nyckelordet i schema definitionen.

### <a name="writing-the-resource-script"></a>Skriver resurs skriptet

Resurs skriptet implementerar logiken för resursen. I den här modulen måste du inkludera tre funktioner som kallas **Get-TargetResource**, **set-TargetResource**och **test-TargetResource**. Alla tre funktioner måste ha en parameter uppsättning som är identisk med uppsättningen med egenskaper som definierats i MOF-schemat som du skapade för din resurs. I det här dokumentet kallas den här uppsättningen egenskaper för "resurs egenskaper". Lagra dessa tre funktioner i en fil med <ResourceName>namnet. psm1. I följande exempel lagras funktionerna i en fil med namnet Demo_IISWebsite. psm1.

> [!NOTE]
> När du kör samma konfigurations skript på din resurs mer än en gång, bör du få inga fel och resursen ska finnas kvar i samma tillstånd som att köra skriptet en gång. För att åstadkomma detta måste du se till att funktionerna **Get-TargetResource** och **test-TargetResource** lämnar resursen oförändrade och att anropet till funktionen **set-TargetResource** mer än en gång i en sekvens med samma parameter värden alltid motsvarar att anropa den en gång.

I funktionen **Get-TargetResource** -funktion använder du de nyckel resurs egenskaps värden som anges som parametrar för att kontrol lera status för den angivna resurs instansen. Den här funktionen måste returnera en hash-tabell som visar alla resurs egenskaper som nycklar och de faktiska värdena för dessa egenskaper som motsvarande värden. Följande kod visar ett exempel.

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

Beroende på vilka värden som anges för resurs egenskaperna i konfigurations skriptet måste **set-TargetResource** göra något av följande:

* Skapa en ny webbplats
* Uppdatera en befintlig webbplats
* Ta bort en befintlig webbplats

I följande exempel visas detta.

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

Slutligen måste **test-TargetResource** -funktionen ta samma parameter uppsättning som **Get-TargetResource** och **set-TargetResource**. I din implementering av **test-TargetResource**kontrollerar du statusen för den resurs instans som anges i nyckel parametrarna. Om resurs instansens faktiska status inte matchar värdena som anges i parameter uppsättningen returnerar **$false**. Annars returnerar **$True**.

I följande kod implementeras funktionen **test-TargetResource** .

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

**Obs!** för enklare fel sökning använder du cmdleten **Write-Verbose** i din implementering av föregående tre funktioner.
>Denna cmdlet skriver text till data strömmen för utförliga meddelanden.
>Den utförliga meddelande strömmen visas som standard inte, men du kan visa den genom att ändra värdet för variabeln **$VerbosePreference** eller genom att använda **verbose** -parametern i DSC-cmdletar = ny.

### <a name="creating-the-module-manifest"></a>Skapar modulens manifest

Använd slutligen cmdleten **New-ModuleManifest** för att definiera en <ResourceName>. psd1-fil för din anpassade resurspool. När du anropar denna cmdlet refererar du till script module-filen (. psm1) som beskrivs i föregående avsnitt. Inkludera **Get-TargetResource**, **set-TargetResource**och **test-TargetResource** i listan över funktioner som ska exporteras. Följande är ett exempel på en manifest fil.

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

>**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5,0 och senare.

Du kan använda egenskapen **PsDscRunAsCredential** i resurs blocket [DSC-konfigurationer](../configurations/configurations.md) för att ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.
Mer information finns i [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter.

Om du vill komma åt användar kontexten inifrån en anpassad resurs kan du använda den `$PsDscContext`automatiska variabeln.

Till exempel kan följande kod skriva användar kontexten som resursen körs till i utförlig utdataström:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a>Starta om noden

Om de åtgärder som vidtas `Set-TargetResource` i funktionen kräver omstart kan du använda en global flagga för att instruera LCM att starta om noden. Den här omstarten sker `Set-TargetResource` direkt efter att funktionen har slutförts.

I din `Set-TargetResource` funktion lägger du till följande kodrad.

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

För att LCM ska kunna starta om noden måste flaggan **RebootNodeIfNeeded** anges till `$true`. Inställningen **ActionAfterReboot** bör också ställas in på **ContinueConfiguration**, vilket är standardvärdet. Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)eller [konfigurera den lokala Configuration Manager (v4)](../managing-nodes/metaConfig4.md).
