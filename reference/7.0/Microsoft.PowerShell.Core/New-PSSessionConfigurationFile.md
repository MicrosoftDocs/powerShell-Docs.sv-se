---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: f2d5613b97e784fc9e1096d3687c156a77d21908
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343104"
---
# New-PSSessionConfigurationFile

## SAMMANFATTNING
Skapar en fil som definierar en sessions konfiguration.

## SYNTAX

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## BESKRIVNING

`New-PSSessionConfigurationFile`Cmdleten skapar en fil med inställningar som definierar en sessions konfiguration och miljön för de sessioner som skapas med hjälp av konfigurationen av sessionen.
Om du vill använda filen i en konfiguration av en session **Path** använder du parametern Path `Register-PSSessionConfiguration` i `Set-PSSessionConfiguration` cmdletarna eller.

Den konfigurations fil för sessionen som `New-PSSessionConfigurationFile` skapar är en läsbar textfil som innehåller en hash-tabell av konfigurations egenskaper och värden för sessioner. Filen har fil `.pssc` namns tillägget.

Alla parametrar för `New-PSSessionConfigurationFile` är valfria, förutom parametern **Path** .
Om du utelämnar en parameter kommenteras motsvarande nyckel i konfigurations filen för sessionen, förutom där anges i parameter beskrivningen.

En sessionsinformation, som även kallas slut punkt, är en samling inställningar på den lokala datorn som definierar miljön för PowerShell-sessioner ( **PSSessions** ) som ansluter till datorn. Alla **PSSessions** använder en konfiguration av sessionen. Om du vill ange en viss sessionsinformation använder du parametern **ConfigurationName** för cmdletar som skapar en session, t. ex `New-PSSession` . cmdleten.

En konfigurations fil för sessionen gör det enkelt att definiera en sessions konfiguration utan komplicerade skript eller kod sammansättningar. Inställningarna i filen används med valfritt start skript och eventuella sammansättningar i konfigurationen för sessionen.

Mer information om sessionsinställningar och konfigurationsfiler för sessioner finns i [about_Session_Configurations](About/about_Session_Configurations.md) och [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

Denna cmdlet introducerades i PowerShell 3,0.

## EXEMPEL

### Exempel 1: skapa och använda en nolanguage-session

Det här exemplet visar hur du skapar och effekterna av att använda en icke-språk-session.

Stegen är:

1. Skapa en ny konfigurations fil.
1. Registrera konfigurationen.
1. Skapa en ny session som använder-konfigurationen.
1. Kör kommandon i den nya sessionen.

Om du vill köra kommandona i det här exemplet startar du PowerShell med alternativet Kör som administratör. Det här alternativet krävs för att köra `Register-PSSessionConfiguration` cmdleten.

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

I det här exemplet `Invoke-Command` Miss lyckas det eftersom **LanguageMode** är inställt på **nolanguage**.

### Exempel 2: skapa och använda en RestrictedLanguage-session

Det här exemplet visar hur du skapar och effekterna av att använda en icke-språk-session.

Stegen är:

1. Skapa en ny konfigurations fil.
1. Registrera konfigurationen.
1. Skapa en ny session som använder-konfigurationen.
1. Kör kommandon i den nya sessionen.

Om du vill köra kommandona i det här exemplet startar du PowerShell med alternativet Kör som administratör. Det här alternativet krävs för att köra `Register-PSSessionConfiguration` cmdleten.

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

I det här exemplet `Invoke-Command` lyckas det eftersom **LanguageMode** är inställt på **RestrictedLanguage**.

### Exempel 3: ändra en konfigurations fil för sessionen

Det här exemplet visar hur du ändrar den konfigurations fil för sessionen som används i en befintlig session med namnet "ITTasks". Tidigare hade dessa sessioner bara de viktigaste modulerna och en intern **ITTasks** -modul. Administratören vill lägga till **PSScheduledJob** -modulen i sessioner som skapats med hjälp av ITTasks-sessionens konfiguration.

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

`New-PSSessionConfigurationFile`Cmdleten för att skapa en konfigurations fil för sessionen som importerar de nödvändiga modulerna. `Set-PSSessionConfiguration`Cmdlet: en ersätter den aktuella konfigurations filen med den nya. Den här nya konfigurationen påverkar endast nya sessioner som skapats efter ändringen.
Befintliga "ITTasks"-sessioner påverkas inte.

### Exempel 4: redigera en konfigurations fil för sessionen

Det här exemplet visar hur du ändrar en sessionsinformation genom att redigera den aktiva sessionens konfigurations kopia av konfigurations filen. Om du vill ändra konfigurations filen för sessionen måste du ha fullständig behörighet till filen. Detta kan kräva att du ändrar behörigheterna för filen.

I det här scenariot vill vi lägga till ett nytt alias för `Select-String` cmdleten genom att redigera den aktiva konfigurations filen.

Exempel koden nedan utför följande steg för att göra den här ändringen:

1. Hämta konfigurations filens sökväg för ITConfig-sessionen.
1. Användaren redigerar konfigurations filen med **Notepad.exe** för att ändra **AliasDefinitions** -värdet enligt följande: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` .
1. Testa den uppdaterade konfigurations filen.

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

Använd **verbose** -parametern med `Test-PSSessionConfigurationFile` för att visa eventuella fel som har identifierats. Cmdleten returnerar `$True` om inga fel har identifierats i filen.

### Exempel 5: skapa en exempel konfigurations fil

I det här exemplet visas ett `New-PSSessionConfigurationFile` kommando som använder alla cmdlet-parametrar.
Den ingår för att visa rätt indataformat för varje parameter.

Den resulterande SampleFile. PSSC visas i utdata.

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## PARAMETRAR

### -AliasDefinitions

Lägger till angivna alias till sessioner som använder sessionen. Ange en hash-tabell med följande nycklar:

- Namn – namnet på aliaset. Den här nyckeln är obligatorisk.
- Value – kommandot som aliaset representerar. Den här nyckeln är obligatorisk.
- Beskrivning – en text sträng som beskriver aliaset. Den här nyckeln är valfri.
- Alternativ-Alternativ för alias. Den här nyckeln är valfri. Standardvärdet är **none**. De acceptabla värdena för den här parametern är: none, ReadOnly, Constant, Private eller AllScope.

Exempelvis: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

Anger de sammansättningar som ska läsas in i de sessioner som använder-konfigurationen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Författare

Anger författaren till sessionen eller konfigurations filen. Standard är den aktuella användaren. Värdet för den här parametern visas i konfigurations filen för sessionen, men det är inte en egenskap för sessionens konfigurations objekt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Företags namn

Anger det företag som skapade konfigurationen av sessionen eller konfigurations filen. Standardvärdet är **Okänt**. Värdet för den här parametern visas i konfigurations filen för sessionen, men det är inte en egenskap för sessionens konfigurations objekt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### – Copyright

Anger en Copyright-sessionens konfigurations fil. Värdet för den här parametern visas i konfigurations filen för sessionen, men det är inte en egenskap för sessionens konfigurations objekt.

Om du utelämnar den här parametern `New-PSSessionConfigurationFile` genererar en Copyright-instruktion med hjälp av värdet för parametern **Author** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beskrivning

Anger en beskrivning av konfigurationen av sessionen eller sessionens konfigurations fil. Värdet för den här parametern visas i konfigurations filen för sessionen, men det är inte en egenskap för sessionens konfigurations objekt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – EnvironmentVariables

Lägger till miljövariabler i sessionen. Ange en hash-tabell där nycklarna är miljö variabel namnen och värdena är Miljövariabelns värden.

Exempelvis: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – ExecutionPolicy

Anger körnings principen för sessioner som använder sessionen. Om du utelämnar den här parametern, är värdet för **ExecutionPolicy** -nyckeln i konfigurations filen för sessionen **begränsad**. Information om körnings principer i PowerShell finns [about_Execution_Policies](about/about_Execution_Policies.md).

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

Anger de formateringsattribut (. ps1xml) som körs i sessioner som använder sessionen.
Värdet för den här parametern måste vara en fullständig eller absolut sökväg till filerna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Fullständig

Anger att den här åtgärden innehåller alla möjliga konfigurations egenskaper i sessionens konfigurations fil.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FunctionDefinitions

Lägger till angivna funktioner till sessioner som använder-sessionen. Ange en hash-tabell med följande nycklar:

- Namn – namnet på funktionen. Den här nyckeln är obligatorisk.
- Script block – Function-brödtext. Ange ett skript block. Den här nyckeln är obligatorisk.
- Alternativ-funktions alternativ. Den här nyckeln är valfri. Standardvärdet är **none**. De acceptabla värdena för den här parametern är: none, ReadOnly, Constant, Private eller AllScope.

Exempelvis: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – GroupManagedServiceAccount

Konfigurerar sessioner som använder den här konfigurationen för att köras under kontexten för det angivna grupphanterade tjänst kontot. Datorn där den här konfigurationen för sessionen registreras måste ha behörighet att begära gMSA-lösenordet för att sessioner ska kunna skapas. Det går inte att använda det här fältet med parametern **RunAsVirtualAccount** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GUID

Anger en unik identifierare för sessionens konfigurations fil. Om du utelämnar den här parametern `New-PSSessionConfigurationFile` genererar ett GUID för filen. Om du vill skapa ett nytt GUID i PowerShell skriver du `New-Guid` .

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LanguageMode

Bestämmer vilka element i PowerShell-språket som tillåts i sessioner som använder den här konfigurationen. Du kan använda den här parametern för att begränsa vilka kommandon som specifika användare kan köra på datorn.

De acceptabla värdena för den här parametern är:

- FullLanguage – alla språk element är tillåtna.
- ConstrainedLanguage-kommandon som innehåller skript som ska utvärderas tillåts inte. ConstrainedLanguage-läget begränsar användar åtkomsten till Microsoft .NET Ramverks typer, objekt eller metoder.
- Nolanguage – användarna kan köra cmdlets och functions, men får inte använda några språk element, till exempel skript block, variabler eller operatörer.
- RestrictedLanguage – användarna kan köra cmdlets och functions, men får inte använda skript block eller variabler förutom följande tillåtna variabler: `$PSCulture` , `$PSUICulture` ,, `$True` `$False` , och `$Null` . Användare får bara använda de grundläggande jämförelse operatorerna ( `-eq` , `-gt` , `-lt` ). Tilldelnings instruktioner, egenskaps referenser och metod anrop är inte tillåtna.

Standardvärdet för parametern **LanguageMode** är beroende av värdet för parametern **SessionType** .

- Tomt – inget språk
- RestrictedRemoteServer – inget språk
- Standard – FullLanguage

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Anger moduler och snapin-moduler som importeras automatiskt till sessioner som använder-sessionen.

Som standard importeras bara snapin-modulen **Microsoft. PowerShell. Core** till fjärrsessioner, men om inte cmdletarna undantas kan användarna använda `Import-Module` `Add-PSSnapin` cmdletarna och för att lägga till moduler och snapin-moduler till sessionen.

Varje modul eller snapin-modul i värdet för den här parametern kan representeras av en sträng eller som en hash-tabell. En modul sträng består bara av namnet på modulen eller snapin-modulen. En modul hash-tabell kan innehålla **Modulnamn** , **ModuleVersion** och **GUID** -nycklar. Endast nyckeln **Modulnamn** krävs.

Följande värde består till exempel av en sträng och en hash-tabell. En valfri kombination av strängar och hash-tabeller, i vilken ordning som helst, är giltig.

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

Värdet för **ModulesToImport** -parametern för `Register-PSSessionConfiguration` cmdleten har företräde framför värdet för **ModulesToImport** -nyckeln i sessionens konfigurations fil.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MountUserDrive

Konfigurerar sessioner som använder den här sessionen för att exponera `User:` PSDrive. Användar enheter är unika för varje användare som ansluter och låter användare kopiera data till och från PowerShell-slutpunkter även om fil system leverantören inte visas. Användar enhets rötter skapas under `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` . För varje användare som ansluter till slut punkten skapas en mapp med namnet `$env:USERDOMAIN_$env:USERNAME` .

Innehållet i användar enheten behålls över användarsessioner och tas inte bort automatiskt. Som standard kan användare bara lagra upp till 50 MB data i användar enheten. Detta kan anpassas med parametern **UserDriveMaximumSize** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen och fil namnet för sessionens konfigurations fil. Filen måste ha ett `.pssc` fil namns tillägg.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PowerShellVersion

Anger versionen för PowerShell-motorn i sessioner som använder-sessionen. De acceptabla värdena för den här parametern är: 2,0 och 3,0. Om du utelämnar den här parametern är **PowerShellVersion** -nyckeln kommenterad och den senaste versionen av PowerShell körs i sessionen.

Värdet för **PSVersion** -parametern för `Register-PSSessionConfiguration` cmdleten har företräde framför värdet för **PowerShellVersion** -nyckeln i sessionens konfigurations fil.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredGroups

Anger villkorliga åtkomst regler för användare som ansluter till sessioner som använder den här konfigurationen.

Ange en hash-tabell om du vill skapa en lista över regler med endast 1 nyckel per hash-tabell, "och" eller "eller", och ange värdet till en matris med säkerhets grupp namn eller ytterligare hash.

Exempel som kräver att användare ansluter användare till medlemmar i en enda grupp: `@{ And = 'MyRequiredGroup' }`

Exempel som kräver att användare tillhöra grupp A, eller både grupper B och C, för att få åtkomst till slut punkten: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RoleDefinitions

Anger mappningen mellan säkerhets grupper (eller användare) och roll funktioner. Användarna beviljas åtkomst till alla roll funktioner som gäller för deras grupp medlemskap vid tidpunkten då sessionen skapas.

Ange en hash-tabell där nycklarna är namnet på säkerhets gruppen och värdena är hash-tabeller som innehåller en lista över roll funktioner som ska göras tillgängliga för säkerhets gruppen.

Exempelvis: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsVirtualAccount

Konfigurerar sessioner som använder den här sessionen att köras som datorns (virtuellt) administratörs konto. Det går inte att använda det här fältet med parametern **GroupManagedServiceAccount** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsVirtualAccountGroups

Anger de säkerhets grupper som ska associeras med det virtuella kontot när en session som använder sessionen körs som ett virtuellt konto. Om det utelämnas tillhör det virtuella kontot domän administratörer på domän kontroller och administratörer på alla andra datorer.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Schema

Anger versionen för fil schema för sessions konfiguration. Standardvärdet är "1.0.0.0".

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

Lägger till angivna skript till sessioner som använder-sessionen. Ange sökväg och fil namn för skripten. Värdet för den här parametern måste vara en fullständig eller absolut sökväg till skript fil namn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionType

Anger vilken typ av session som skapas med hjälp av konfigurationen av sessionen. Standardvärdet är default. De acceptabla värdena för den här parametern är:

- Tom-inga moduler läggs till i sessionen som standard. Använd parametrarna för denna cmdlet för att lägga till moduler, funktioner, skript och andra funktioner i sessionen. Det här alternativet är utformat för att skapa anpassade sessioner genom att lägga till valda kommandon. Om du inte lägger till kommandon i en tom session är sessionen begränsad till uttryck och kanske inte kan användas.
- Standard – lägger till Microsoft. PowerShell. Core-modulen i sessionen. Den här modulen innehåller den `Import-Module` cmdlet som användare kan använda för att importera andra moduler om du inte uttryckligen tillåter denna cmdlet.
- RestrictedRemoteServer. Innehåller endast följande proxy-funktioner:,,,,, `Exit-PSSession` `Get-Command` `Get-FormatData` `Get-Help` `Measure-Object` `Out-Default` och `Select-Object` .
  Använd parametrarna för denna cmdlet för att lägga till moduler, funktioner, skript och andra funktioner i sessionen.

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TranscriptDirectory

Anger katalog för att placera sessions avskrifter för sessioner som använder den här sessionen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypesToProcess

Lägger till de angivna `.ps1xml` exempelfilerna i sessioner som använder-konfigurationen. Ange typ fil namn. Värdet för den här parametern måste vara en fullständig eller absolut sökväg för att ange fil namn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserDriveMaximumSize

Anger den maximala storleken för användar enheter som exponeras i sessioner som använder den här konfigurationen för sessionen.
Vid utelämnad är standard storleken för varje `User:` enhets rot 50 MB.

Den här parametern ska användas med **MountUserDrive**.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariableDefinitions

Lägger till angivna variabler i sessioner som använder sessionen. Ange en hash-tabell med följande nycklar:

- Namn på variabeln. Den här nyckeln är obligatorisk.
- Värde – variabel värde. Den här nyckeln är obligatorisk.
- Alternativ-variabel alternativ. Den här nyckeln är valfri. Standardvärdet är **none**. De acceptabla värdena för den här parametern är: none, ReadOnly, Constant, Private eller AllScope.

Exempelvis: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleAliases

Begränsar alias i sessionen till de som anges i värdet för den här parametern, plus alla alias som du definierar i parametern **AliasDefinition** . Jokertecken stöds. Som standard visas alla alias som definieras av PowerShell-motorn och alla alias som moduler exporterar i sessionen.

Exempelvis: `VisibleAliases='gcm', 'gp'`

När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess ipmo-alias från sessionen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleCmdlets

Begränsar cmdletarna i sessionen till de som anges i värdet för den här parametern. Jokertecken och kvalificerade namn för module stöds.

Som standard visas alla cmdlets som moduler i sessionen exportera i sessionen. Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler och snapin-moduler som importeras till sessionen. Om inga moduler i **ModulesToImport** exponerar cmdleten försöker lämplig modul läsas in automatiskt.

När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess ipmo-alias från sessionen.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleExternalCommands

Begränsar de externa binärfiler, skript och kommandon som kan köras i sessionen till de som anges i värdet för den här parametern. Jokertecken stöds.

Som standard visas inga externa kommandon i sessionen.

När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess ipmo-alias från sessionen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleFunctions

Begränsar funktionerna i sessionen till de som anges i värdet för den här parametern, plus de funktioner som du definierar i parametern **FunctionDefinition** . Jokertecken stöds.

Som standard visas alla funktioner som moduler i sessionen exporterar i sessionen. Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler och snapin-moduler som importeras till sessionen.

När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess ipmo-alias från sessionen.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

Begränsar PowerShell-providern i sessionen till de som anges i värdet för den här parametern.
Jokertecken stöds.

Som standard visas alla providers som moduler i sessionen exportera i sessionen. Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler som importeras till sessionen.

När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Det går inte att skicka några objekt till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

- Parametrar, till exempel **VisibleCmdlets** och **VisibleProviders** , importerar inte objekt till sessionen. De väljer i stället bland de objekt som har importer ATS till sessionen. Om värdet för **VisibleProviders** -parametern till exempel är certifikat leverantören, men parametern **ModulesToImport** inte anger den **Microsoft. PowerShell. Security** -modul som innehåller certifikat leverantören, visas inte certifikat leverantören i sessionen.
- `New-PSSessionConfigurationFile` skapar en konfigurations fil för sessionen som har fil namns tillägget. PSSC i den sökväg som du anger i parametern **Path** . När du använder sessionens konfigurations fil för att skapa en konfiguration av sessionen, `Register-PSSessionConfiguration` kopierar cmdleten konfigurations filen och sparar en aktiv kopia av filen i katalogen **SessionConfig** i `$PSHOME` katalogen.

  **ConfigFilePath** -egenskapen för sessionen innehåller den fullständigt kvalificerade sökvägen till den aktiva sessionens konfigurations fil. Du kan ändra den aktiva konfigurations filen i `$PSHOME` katalogen när som helst med valfri text redigerare. De ändringar du gör påverkar alla nya sessioner som använder sessionen, men inte befintliga sessioner.

  Använd `Test-PSSessionConfigurationFile` cmdleten för att kontrol lera att konfigurations filens poster är giltiga innan du använder en redige rad konfigurations fil för sessionen.

## RELATERADE LÄNKAR

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Aktivera – PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Avregistrera-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
