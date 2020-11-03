---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3dca5f922f31690bb78ccc610b4ed44b7423ca47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264231"
---
# New-PSRoleCapabilityFile

## SAMMANFATTNING
Skapar en fil som definierar en uppsättning funktioner som ska exponeras via en konfiguration av sessionen.

## SYNTAX

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## BESKRIVNING

`New-PSRoleCapabilityFile`Cmdleten skapar en fil som definierar en uppsättning användar funktioner som kan exponeras genom konfigurationsfiler för sessioner. Detta omfattar att bestämma vilka cmdletar, funktioner och skript som är tillgängliga för användare. Funktions filen är en läsbar textfil som innehåller en hash-tabell av konfigurations egenskaper och värden för sessioner. Filen har fil namns tillägget. psrc och kan användas av mer än en-session-konfiguration.

Alla parametrar för `New-PSRoleCapabilityFile` är valfria förutom för **Sök vägs** parametern, som anger fil Sök vägen för filen. Om du inte tar med en parameter när du kör cmdleten, kommenteras motsvarande nyckel i konfigurations filen för sessionen, förutom där anges i parameter beskrivningen. Om du t. ex. inte inkluderar parametern **AssembliesToLoad** , kommenteras avsnittet i konfigurations filen för sessionen ut.

Om du vill använda roll funktions filen i en konfiguration av sessionen måste du först placera filen i en **RoleCapabilities** -undermapp i en giltig PowerShell-modul. Referera sedan till filen efter namn i fältet **RoleDefinitions** i en PowerShell-session konfigurations fil (. PSSC).

Den här cmdleten introducerades i Windows PowerShell 5,0.

## EXEMPEL

### Exempel 1: skapa en tom roll funktions fil

I det här exemplet skapas en ny roll funktions fil som använder standardvärdena (tomma). Filen kan senare redige ras i en text redigerare för att ändra konfigurations inställningarna.

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### Exempel 2: skapa en roll funktions fil som gör det möjligt för användare att starta om tjänster och valfri VDI-dator

I det här exemplet skapas en funktions fil för exempel rollen som gör det möjligt för användare att starta om tjänster och datorer som matchar ett särskilt namn mönster. Namn filtrering definieras genom att ange parametern **ValidatePattern** till det reguljära uttrycket `VDI\d+` .

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## PARAMETRAR

### -AliasDefinitions

Lägger till angivna alias till sessioner som använder roll funktions filen. Ange en hash-tabell med följande nycklar:

- Namn. Aliasets namn. Den här nyckeln är obligatorisk.
- Värde. Kommandot som aliaset representerar. Den här nyckeln är obligatorisk.
- Beskrivning. En text sträng som beskriver aliaset. Den här nyckeln är valfri.
- Alternativ. Alternativ för alias. Den här nyckeln är valfri. Standardvärdet är none. De acceptabla värdena för den här parametern är: none, ReadOnly, Constant, Private eller AllScope.

Exempelvis: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`

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

Anger de sammansättningar som ska läsas in i de sessioner som använder roll funktions filen.

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

Anger den användare som skapade roll kapacitets filen.

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

Identifierar det företag som skapade roll kapacitets filen.
Standardvärdet är okänt.

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

### – Copyright

Anger en upphovs rätt för roll funktions filen. Om du utelämnar den här parametern `New-PSRoleCapabilityFile` genererar en Copyright-instruktion med hjälp av värdet för parametern **Author** .

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

Anger en beskrivning av roll kapacitets filen.

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

Anger miljövariabler för sessioner som exponerar den här roll funktions filen. Ange en hash-tabell där nycklarna är miljö variabel namnen och värdena är Miljövariabelns värden.

Exempelvis: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`

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

### -FormatsToProcess

Anger de formateringsattribut (. ps1xml) som körs i sessioner som använder sig av roll funktions filen. Värdet för den här parametern måste vara en fullständig eller absolut sökväg till filerna.

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

### -FunctionDefinitions

Lägger till angivna funktioner till sessioner som visar roll kapaciteten. Ange en hash-tabell med följande nycklar:

- Namn. Namnet på funktionen. Den här nyckeln är obligatorisk.
- Script block. Funktions text. Ange ett skript block. Den här nyckeln är obligatorisk.
- Alternativ. Funktions alternativ. Den här nyckeln är valfri. Standardvärdet är none. De acceptabla värdena för den här parametern är: är ingen, ReadOnly, konstant, privat eller AllScope.

Ett exempel:

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

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

### -GUID

Anger en unik identifierare för roll funktions filen. Om du utelämnar den här parametern `New-PSRoleCapabilityFile` genererar ett GUID för filen. Om du vill skapa ett nytt GUID i PowerShell skriver du `[guid]::NewGuid()` .

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

### -ModulesToImport

Anger de moduler som importeras automatiskt till sessioner som använder roll funktions filen. Som standard visas alla kommandon i de moduler som visas. När det används med **VisibleCmdlets** eller **VisibleFunctions** kan de kommandon som visas i de angivna modulerna begränsas.

Varje modul som används i värdet för den här parametern kan representeras av en sträng eller en hash-tabell. En modul sträng består bara av namnet på modulen. En modul hash-tabell kan innehålla **Modulnamn** , **ModuleVersion** och **GUID** -nycklar. Endast nyckeln **Modulnamn** krävs.

Följande värde består till exempel av en sträng och en hash-tabell. En valfri kombination av strängar och hash-tabeller, i vilken ordning som helst, är giltig.

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

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

### -Path

Anger sökväg och fil namn för roll funktions filen. Filen måste ha ett `.psrc` fil namns tillägg.

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

### -ScriptsToProcess

Anger skript som ska läggas till i sessioner som använder en roll funktions fil. Ange sökväg och fil namn för skripten. Värdet för den här parametern måste vara en fullständig eller absolut sökväg till skript fil namnen.

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

### -TypesToProcess

Anger typ filer (. ps1xml) som ska läggas till i sessioner som använder sig av roll kapacitets filen. Ange typ fil namn. Värdet för den här parametern måste vara en fullständig eller absolut sökväg av typ fil namnen.

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

### -VariableDefinitions

Anger variabler som ska läggas till i sessioner som använder sig av roll funktions filen. Ange en hash-tabell med följande nycklar:

- Namn. Variabelns namn. Den här nyckeln är obligatorisk.
- Värde. Variabel värde. Den här nyckeln är obligatorisk.
- Alternativ. Variabel alternativ. Den här nyckeln är valfri. Standardvärdet är none. De acceptabla värdena för den här parametern är: är ingen, ReadOnly, konstant, privat eller AllScope.

Exempelvis: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`

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

Begränsar alias i sessionen till de alias som anges i värdet för den här parametern, plus alla alias som du definierar i parametern **AliasDefinition** . Jokertecken stöds.
Som standard visas alla alias som definieras av PowerShell-motorn och alla alias som moduler exporterar i sessionen.

Om du till exempel vill begränsa tillgängliga alias till GM och GCM använder du följande syntax: `VisibleAliases="gcm", "gp"`

När en **Visible** -parameter ingår i roll funktions filen, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.

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

Som standard visas alla cmdletar som modulerna i sessionen exporterar i sessionen. Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler och snapin-moduler som importeras till sessionen. Om inga moduler i **ModulesToImport** exponerar cmdleten `New-PSRoleCapabilityFile` försöker läsa in lämplig modul.

När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.

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

### -VisibleExternalCommands

Begränsar de externa binärfilerna, skripten och kommandona som kan köras i sessionen till de som anges i värdet för den här parametern.

Som standard visas inga externa kommandon i den här sessionen.

När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.

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

### -VisibleFunctions

Begränsar funktionerna i sessionen till de som anges i värdet för den här parametern, plus de funktioner som du definierar i parametern **FunctionDefinitions** . Jokertecken stöds.

Som standard visas alla funktioner som exporteras av moduler i sessionen i den sessionen. Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler som importeras till sessionen.

När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.

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

Som standard visas alla providrar som exporteras av en modul i sessionen i sessionen. Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler som importeras till sessionen.

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

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Get-PSSessionCapability](Get-PSSessionCapability.md)
