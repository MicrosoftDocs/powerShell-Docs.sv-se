---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 81c58a09cb6c4e6cedcc7abfa832af7bb694b0e1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267927"
---
# Update-ModuleManifest

## SAMMANFATTNING
Uppdaterar en modul manifest fil.

## SYNTAX

### Alla

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Update-ModuleManifest`Cmdleten uppdaterar en modul manifest `.psd1` fil ()-fil.

## EXEMPEL

### Exempel 1: uppdatera ett modul manifest

Det här exemplet uppdaterar en befintlig modul manifest fil. Ihopbuntning används för att skicka parameter värden till `Update-ModuleManifest` . Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

`$Parms` är en splat som lagrar parameter värden för **sökväg** , **författare** , **företags namn** och **Copyright**. `Update-ModuleManifest` hämtar parameter värden från `@Parms` och uppdaterar modulens manifest **TestManifest.psd1**.

## PARAMETRAR

### -AliasesToExport

Anger de alias som modulen exporterar. Jokertecken är tillåtna.

Använd den här parametern om du vill begränsa de alias som exporteras av modulen. **AliasesToExport** kan ta bort alias från listan över exporterade alias, men det går inte att lägga till alias i listan.

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

### – Författare

Anger modulens författare.

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

### -ClrVersion

Anger den lägsta versionen av CLR (Common Language Runtime) för Microsoft .NET Framework som modulen kräver.

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

### -CmdletsToExport

Anger de cmdletar som modulen exporterar. Jokertecken är tillåtna.

Använd den här parametern om du vill begränsa de cmdletar som exporteras av modulen. **CmdletsToExport** kan ta bort cmdletar från listan över exporterade cmdlets, men det går inte att lägga till cmdletar i listan.

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

### -Företags namn

Anger företaget eller leverantören som skapade modulen.

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

### -CompatiblePSEditions

Anger den kompatibla **PSEditions** för modulen. Information om **PSEdition** finns i [moduler med kompatibla PowerShell-versioner](/powershell/scripting/gallery/concepts/module-psedition-support).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Du uppmanas att bekräfta innan du kör `Update-ModuleManifest` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Copyright

Anger en Copyright-instruktion för modulen.

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

### -DefaultCommandPrefix

Anger standard kommandots prefix.

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

Anger en beskrivning av modulen.

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

### -DotNetFrameworkVersion

Anger den lägsta version av Microsoft .NET Framework som modulen kräver.

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

### -DscResourcesToExport

Anger de DSC-resurser (Desired State Configuration) som modulen exporterar. Jokertecken är tillåtna.

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

### -ExternalModuleDependencies

Anger en matris med beroenden för externa moduler.

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

### – FileList

Anger alla objekt som ingår i modulen.

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

### -FormatsToProcess

Anger de formateringsattribut ( `.ps1xml` ) som körs när modulen importeras.

När du importerar en modul kör PowerShell `Update-FormatData` cmdleten med de angivna filerna.
Eftersom filer som inte är begränsade påverkar formateringen alla sessionstillstånd i sessionen.

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

### -FunctionsToExport

Anger de funktioner som modulen exporterar. Jokertecken är tillåtna.

Använd den här parametern om du vill begränsa vilka funktioner som exporteras av modulen. **FunctionsToExport** kan ta bort funktioner från listan över exporterade alias, men det går inte att lägga till funktioner i listan.

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

### -GUID

Anger en unik identifierare för modulen. GUID kan användas för att skilja mellan moduler med samma namn.

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

### -HelpInfoUri

Anger Internet adressen för modulens **HelpInfo XML-** fil. Ange en Uniform Resource Identifier (URI) som börjar med **http** eller **https**.

**XML-filen HelpInfo** stöder den uppdaterbara hjälp funktionen som introducerades i PowerShell version 3,0. Den innehåller information om platsen för modulens nedladdnings bara hjälpfiler och versions numren för de senaste hjälpfilerna för varje språk som stöds.

Information om uppdaterbar hjälp finns [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).
Information om **XML-HelpInfo** finns i [stöd uppdaterings bar hjälp](/powershell/scripting/developer/module/supporting-updatable-help).

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – IconUri

Anger URL-adressen till en ikon för modulen. Den angivna ikonen visas på Galleri webb sidan för modulen.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseUri

Anger URL: en för licens villkoren för modulen.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleList

Anger en matris med moduler som ingår i modulen.

Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar. Hash-tabellen kan också ha en valfri **GUID** -nyckel. Du kan kombinera strängar och hash-tabeller i parametervärdet.

Den här nyckeln är utformad för att fungera som en modul. Modulerna som anges i värdet för den här nyckeln bearbetas inte automatiskt.

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

### – ModuleVersion

Anger versionen för modulen.

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

### -NestedModules

Anger skript moduler ( `.psm1` ) och binära moduler ( `.dll` ) som importeras till modulens sessionstillstånd. Filerna i **NestedModules** -nyckeln körs i den ordning som de är listade i värdet.

Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar. Hash-tabellen kan också ha en valfri **GUID** -nyckel. Du kan kombinera strängar och hash-tabeller i parametervärdet.

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

### -PackageManagementProviders

Anger en matris med paket hanterings leverantörer.

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

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med. Som standard `Update-ModuleManifest` genererar inga utdata.

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

Anger sökvägen och fil namnet för modulens manifest. Ange en sökväg och ett fil namn med ett `.psd1` fil namns tillägg, till exempel `$PSHOME\Modules\MyModule\MyModule.psd1` .

Om du anger sökvägen till en befintlig fil `Update-ModuleManifest` ersätts filen utan varning om inte filen har attributet skrivskyddad.

Manifestet ska finnas i modulens katalog och manifest filens namn ska vara samma som modulens katalog namn, men med ett `.psd1` tillägg.

Du kan inte använda variabler, t `$PSHOME` . ex. eller `$HOME` , som svar på en prompt för värdet för en **Sök vägs** parameter. Om du vill använda en variabel inkluderar du parametern **Path** i kommandot.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PowerShellHostName

Anger namnet på PowerShell-värdservern som modulen kräver. Ange namnet på värd programmet, till exempel PowerShell ISE värd eller ConsoleHost. Jokertecken är inte tillåtna.

Om du vill hitta namnet på ett värd program skriver du i programmet `$Host.Name` .

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

### -PowerShellHostVersion

Anger den lägsta versionen av PowerShell-värd programmet som fungerar med modulen. Ange ett versions nummer, till exempel 1,1.

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

### – PowerShellVersion

Anger den lägsta version av PowerShell som kommer att fungera med den här modulen. Du kan till exempel ange 3,0, 4,0 eller 5,0 som värde för den här parametern.

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

### -För hands version

Anger att modulen är för hands version.

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

### -PrivateData

Anger data som skickas till modulen när den importeras.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessorArchitecture

Anger den processor arkitektur som modulen kräver.

De acceptabla värdena för den här parametern är:

- Amd64
- Koppling
- IA64
- MSIL
- Ingen (okänd eller ospecificerad)
- X86

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProjectUri

Anger webb adressen till en webb sida om projektet.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReleaseNotes

Anger en sträng mat ris som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för den här versionen av skriptet.

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

### -RequiredAssemblies

Anger de Assembly ( `.dll` )-filer som modulen kräver. Ange sammansättnings fil namnen.
PowerShell läser in de angivna sammansättningarna innan du uppdaterar typer eller format, importerar kapslade moduler eller importerar filen som anges i värdet för nyckeln **RootModule** .

Använd den här parametern för att ange alla sammansättningar som modulen kräver, inklusive sammansättningar som måste läsas in för att uppdatera all formatering eller skriva filer som listas i **FormatsToProcess** -eller **TypesToProcess** -nycklarna, även om dessa sammansättningar också visas som binära moduler i **NestedModules** -nyckeln.

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

### -RequiredModules

Anger moduler som måste vara i det globala sessionstillståndet. Om de moduler som krävs inte är i det globala sessionstillståndet importeras de av PowerShell. Om de moduler som krävs inte är tillgängliga, `Import-Module` Miss lyckas kommandot.

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

### -RequireLicenseAcceptance

Anger att licens godkännande krävs för modulen.

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

### -RootModule

Anger modulens primära eller rot fil. Ange fil namnet för ett skript ( `.ps1` ), en skriptbaserad modul ( `.psm1` ), ett modul manifest ( `.psd1` ), en sammansättning ( `.dll` ), en XML-fil () för cmdlet-definition ( `.cdxml` ) eller ett arbets flöde ( `.xaml` ). När modulen importeras importeras medlemmar som exporteras från rot-modul filen till anroparens sessionstillstånd.

Om en modul har en manifest fil och ingen rot fil har angetts i **RootModule** -nyckeln blir manifestet den primära filen för modulen. Och är modulen en manifest-modul (ModuleType = manifest).

För att exportera medlemmar från `.psm1` eller `.dll` filer i en modul som har ett manifest, måste namnen på filerna anges i värdena för **RootModule** -eller **NestedModules** -nycklarna i manifestet. Annars exporteras inte deras medlemmar.

I PowerShell 2,0 kallades den här nyckeln för **ModuleToProcess**.

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

### -ScriptsToProcess

Anger skript ( `.ps1` )-filer som körs i anroparens sessionstillstånd när modulen importeras.
Du kan använda dessa skript för att förbereda en miljö, precis som du kan använda ett inloggnings skript.

Använd nyckeln **NestedModules** för att ange skript som körs i modulens sessionstillstånd.

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

### – Taggar

Anger en matris med taggar.

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

Anger de typ filer ( `.ps1xml` ) som körs när modulen importeras.

När du importerar modulen kör PowerShell `Update-TypeData` cmdleten med de angivna filerna.
Eftersom filtypen inte är begränsad, påverkar de alla sessionstillstånd i sessionen.

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

### -VariablesToExport

Anger de variabler som modulen exporterar. Jokertecken är tillåtna.

Använd den här parametern om du vill begränsa de variabler som exporteras av modulen. **VariablesToExport** kan ta bort variabler från listan över exporterade variabler, men det går inte att lägga till variabler i listan.

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

### -WhatIf

Visar vad som händer om `Update-ModuleManifest` körs. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

## UTDATA

### System. Object

## ANTECKNINGAR

## RELATERADE LÄNKAR
