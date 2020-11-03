---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: daa58a732dafb11fa8f6ce3c20965aebcce55844
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263631"
---
# Get-Command

## SAMMANFATTNING
Hämtar alla kommandon.

## SYNTAX

### CmdletSet (standard)

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### AllCommandSet

```
Get-Command [[-Name] <String[]>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-CommandType <CommandTypes>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>]
 [-All] [-ListImported] [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en `Get-Command` hämtar alla kommandon som är installerade på datorn, inklusive cmdlets, alias, funktioner, filter, skript och program. `Get-Command` hämtar kommandon från PowerShell-moduler och kommandon som har importer ATS från andra sessioner. Om du bara vill hämta kommandon som har importer ATS till den aktuella sessionen använder du parametern **ListImported** .

Utan parametrar `Get-Command` hämtar alla cmdletar, funktioner och alias som är installerade på datorn. `Get-Command *` hämtar alla typer av kommandon, inklusive alla icke-PowerShell-filer i Path-miljövariabeln ( `$env:Path` ) som visas i program kommando typen.

`Get-Command` som använder kommandots exakta namn, utan jokertecken, importerar automatiskt den modul som innehåller kommandot så att du kan använda kommandot direkt. Om du vill aktivera, inaktivera och konfigurera automatisk import av moduler använder du `$PSModuleAutoLoadingPreference` Preference-variabeln. Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).

`Get-Command` hämtar data direkt från kommando koden, till skillnad `Get-Help` från, som hämtar information från hjälp avsnitten.

Från och med Windows PowerShell 5,0 visar resultatet av `Get-Command` cmdleten **versions** kolumnen som standard. En ny **versions** egenskap har lagts till i **CommandInfo** -klassen.

## EXEMPEL

### Exempel 1: Hämta cmdlets, Functions och alias

Det här kommandot hämtar PowerShell-cmdletar, funktioner och alias som är installerade på datorn.

```powershell
Get-Command
```

### Exempel 2: Hämta kommandon i den aktuella sessionen

Det här kommandot använder parametern **ListImported** för att bara hämta kommandon i den aktuella sessionen.

```powershell
Get-Command -ListImported
```

### Exempel 3: Hämta cmdletar och visa dem i ordning

Det här kommandot hämtar alla cmdletar, sorterar dem i alfabetisk ordning efter Substantiv i cmdlet-namnet och visar dem i Substantiv-baserade grupper. Den här visningen kan hjälpa dig att hitta cmdletar för en uppgift.

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### Exempel 4: Hämta kommandon i en modul

Detta kommando använder **modulen modul** för att hämta kommandon i modulerna Microsoft. PowerShell. Security och Microsoft. PowerShell. Utility.

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### Exempel 5: Hämta information om en cmdlet

Det här kommandot hämtar information om `Get-AppLockerPolicy` cmdleten. Den importerar även **AppLocker** -modulen, som lägger till alla kommandon i **AppLocker** -modulen i den aktuella sessionen.

```powershell
Get-Command Get-AppLockerPolicy
```

När en modul importeras automatiskt är det samma sak som att använda Import-Module-cmdleten.
Modulen kan lägga till kommandon, typer och formatering av filer och köra skript i sessionen. Om du vill aktivera, inaktivera och konfigurera automatisk import av moduler använder du `$PSModuleAutoLoadingPreference` Preference-variabeln. Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

### Exempel 6: Hämta syntaxen för en cmdlet

Det här kommandot använder parametrarna **argument List** och **syntax** för att hämta syntaxen för `Get-ChildItem` cmdleten när den används i certifikatet: enhet. Certifikatet: enheten är en PowerShell-enhet som certifikat leverantören lägger till i sessionen.

```powershell
Get-Command Get-Childitem -Args Cert: -Syntax
```

När du jämför den syntax som visas i utdata med den syntax som visas när du utelämnar parametern **args** ( **argument List** ) ser du att **certifikat leverantören** lägger till en dynamisk parameter, **CodeSigningCert** , till `Get-ChildItem` cmdleten.

Mer information om certifikat leverantören finns [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).

### Exempel 7: hämta dynamiska parametrar

Kommandot i exemplet använder `Get-DynamicParameters` funktionen för att hämta de dynamiska parametrar som certifikat leverantören lägger till i `Get-ChildItem` cmdleten när den används i certifikatet: enhet.

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

`Get-DynamicParameters`Funktionen i det här exemplet hämtar dynamiska parametrar för en cmdlet. Detta är ett alternativ till den metod som användes i föregående exempel. Dynamisk parameter kan läggas till i en cmdlet av en annan cmdlet eller en provider.

### Exempel 8: Hämta alla kommandon av alla typer

Det här kommandot hämtar alla kommandon för alla typer på den lokala datorn, inklusive körbara filer i sökvägar i miljövariabeln **Path** ( `$env:path` ).

```powershell
Get-Command *
```

Den returnerar ett **ApplicationInfo** -objekt (system. Management. Automation. ApplicationInfo) för varje fil, inte ett **fileinfo** -objekt (system. io. fileinfo).

### Exempel 9: Hämta cmdlets med hjälp av ett parameter namn och en typ

Detta kommando hämtar cmdletar som har en parameter vars namn inkluderar auth och vars typ är **AuthenticationMechanism**.

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

Du kan använda ett kommando som det här för att hitta cmdletar som låter dig ange den metod som används för att autentisera användaren.

Parametern **ParameterType** särskiljer parametrar som tar ett **AuthenticationMechanism** -värde från de som tar en **AuthenticationLevel** -parameter, även om de har liknande namn.

### Exempel 10: Hämta ett alias

Det här exemplet visar hur du använder `Get-Command` cmdleten med ett alias.

```powershell
Get-Command dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

Även om det vanligt vis används på cmdlets och functions, `Get-Command` hämtar även skript, funktioner, alias och körbara filer.

Kommandots utdata visar den särskilda vyn för **namn** egenskap svärdet för alias. I vyn visas alias och det fullständiga kommando namnet.

### Exempel 11: Hämta alla instanser av anteckningar-kommandot

I det här exemplet används parametern **all** för `Get-Command` cmdleten för att visa alla instanser av kommandot "notepad" på den lokala datorn.

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

Parametern **all** är användbar när det finns mer än ett kommando med samma namn i sessionen.

Från och med Windows PowerShell 3,0, som standard, när sessionen innehåller flera kommandon med samma namn, `Get-Command` hämtas bara det kommando som körs när du skriver kommandots namn. Med parametern **all** `Get-Command` hämtar alla kommandon med det angivna namnet och returnerar dem i prioritetsordning för körning. Om du vill köra ett annat kommando än det första i listan, anger du den fullständiga sökvägen till kommandot.

Mer information om kommando prioritet finns [about_Command_Precedence](About/about_Command_Precedence.md).

### Exempel 12: Hämta namnet på en modul som innehåller en cmdlet

Det här kommandot hämtar namnet på modulen där `Get-Date` cmdleten kommer.
Kommandot använder egenskapen **Modulnamn** för alla kommandon.

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

Det här kommando formatet fungerar med kommandon i PowerShell-moduler, även om de inte importeras till sessionen.

### Exempel 13: Hämta cmdletar och funktioner som har en utdatatyp

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

Det här kommandot hämtar de cmdletar och funktioner som har en utdatatyp och den typ av objekt som de returnerar.

Den första delen av kommandot hämtar alla cmdletar.
En pipeline-operator (|) skickar cmdletarna till `Where-Object` cmdleten, som bara väljer de där egenskapen **OutputType** är ifylld.
En annan pipeline-operator skickar de valda cmdlet-objekten till `Format-List` cmdleten, som visar namn och Utdatatyp för varje cmdlet i en lista.

Egenskapen **outputtype** för ett **CommandInfo** -objekt har ett värde som inte är null när cmdlet-koden definierar attributet **OutputType** för cmdleten.

### Exempel 14: Hämta cmdletar som tar en speciell objekt typ som inmatade

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

Det här kommandot hittar cmdletar som tar net adapter-objekt som inmatade. Du kan använda det här kommando formatet för att hitta de cmdlet: ar som godkänner den typ av objekt som returneras av ett kommando.

Kommandot använder egenskapen **PSTypeNames** inre för alla objekt, som hämtar de typer som beskriver objektet. För att hämta egenskapen **PSTypeNames** för ett nät kort och inte egenskapen **PSTypeNames** för en uppsättning nätverkskort, använder kommandot mat ris notation för att hämta det första nätverkskortet som cmdleten returnerar.
För att hämta egenskapen **PSTypeNames** för ett nät kort och inte egenskapen **PSTypeNames** för en uppsättning nätverkskort, använder kommandot mat ris notation för att hämta det första nätverkskortet som cmdleten returnerar.

## PARAMETRAR

### – Alla

Anger att denna cmdlet hämtar alla kommandon, inklusive kommandon av samma typ som har samma namn. Som standard `Get-Command` hämtar bara de kommandon som körs när du skriver kommandots namn.

Mer information om metoden som PowerShell använder för att välja kommandot som ska köras när flera kommandon har samma namn finns i [about_Command_Precedence](About/about_Command_Precedence.md).
Information om moduler-kvalificerade kommando namn och körning av kommandon som inte körs som standard på grund av en namn konflikt finns i [about_Modules](About/about_Modules.md).

Den här parametern introducerades i Windows PowerShell 3,0.

I Windows PowerShell 2,0 `Get-Command` hämtar alla kommandon som standard.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Argument List

Anger en matris med argument. Denna cmdlet hämtar information om en cmdlet eller funktion när den används med de angivna parametrarna ("argument"). Aliaset för **argument List** är **argument**.

Om du vill identifiera dynamiska parametrar som bara är tillgängliga när vissa andra parametrar används ställer du in värdet för **argument List** på de parametrar som utlöser de dynamiska parametrarna.

För att identifiera de dynamiska parametrar som en provider lägger till i en cmdlet, ange värdet för parametern **argument List** till en sökväg i leverantörs enheten, till exempel WSMan:, HKLM: eller cert:. När kommandot är en PowerShell-Provider-cmdlet anger du bara en sökväg i varje kommando. Providerns cmdlets returnerar bara dynamiska parametrar för den första sökvägen till värdet för **argument List**. Information om Provider-cmdletar finns i [about_Providers](About/about_Providers.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

Anger vilka typer av kommandon som denna cmdlet hämtar. Ange en eller flera kommando typer. Använd **CommandType** eller dess alias och **Skriv**. Som standard `Get-Command` hämtar alla cmdletar, funktioner och alias.

De acceptabla värdena för den här parametern är:

- Aliasuppsättning. Hämtar alias för alla PowerShell-kommandon. Mer information finns i [about_Aliases](About/about_Aliases.md).
- Vissa. Hämtar alla kommando typer. Detta parameter värde motsvarar `Get-Command *` .
- Applicering. Hämtar icke-PowerShell-filer i sökvägar som anges i miljövariabeln **Path** ($env:p ökväg), inklusive. txt-,. exe-och. dll-filer. Mer information om **Path** -miljövariabeln finns about_Environment_Variables.
- Kommandon. Hämtar alla cmdletar.
- ExternalScript. Hämtar alla. ps1-filer i Sök vägarna som anges i miljövariabeln **Path** ($env:p ökväg).
- Filter och funktion. Hämtar alla PowerShell-avancerade och enkla funktioner och filter.
- Över. Hämtar alla skript block. Använd ExternalScript-värdet för att hämta PowerShell-skript (. ps1-filer).
- Arbets flöde. Hämtar alla arbets flöden. Mer information om arbets flöden finns i Introduktion till Windows PowerShell-arbetsflöde.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FullyQualifiedModule

Anger moduler med namn som anges i form av **ModuleSpecification** -objekt, som beskrivs i avsnittet **anmärkningar** i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).
**FullyQualifiedModule** -parametern accepterar till exempel ett modulnamn som anges i något av följande format:

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.

Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter. De två parametrarna kan inte anges samtidigt.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListImported

Anger att denna cmdlet endast hämtar kommandon i den aktuella sessionen.

Från och med PowerShell 3,0 hämtar som standard `Get-Command` alla installerade kommandon, inklusive, men inte begränsat till, kommandona i den aktuella sessionen. I PowerShell 2,0 får du bara kommandon i den aktuella sessionen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Modul

Anger en matris med moduler. Denna cmdlet hämtar de kommandon som kom från de angivna modulerna eller snapin-modulerna. Ange namnen på moduler eller snapin-moduler.

Den här parametern använder sträng värden, men värdet för den här parametern kan också vara ett **PSModuleInfo** -eller **PSSnapinInfo** -objekt, till exempel de objekt som `Get-Module` `Get-PSSnapin` cmdletarna, och `Import-PSSession` returnerar.

Du kan referera till den här parametern med dess namn, **modul** eller dess alias, **PSSnapin**.
Parameter namnet som du väljer har ingen effekt på kommandots utdata.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Name

Anger en matris med namn. Denna cmdlet hämtar endast kommandon med det angivna namnet. Ange ett namn eller namn mönster. Jokertecken är tillåtna.

Om du vill hämta kommandon med samma namn använder du parametern **all** . När två kommandon har samma namn, hämtas som standard `Get-Command` kommandot som körs när du skriver kommandots namn.

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Substantiv

Anger en matris med kommando substantiv. Denna cmdlet hämtar kommandon, som innehåller cmdlets, Functions och alias, som har namn som innehåller angivet substantiv. Ange ett eller flera Substantiv-eller Substantiv-mönster. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – ParameterName

Anger en matris med parameter namn. Denna cmdlet hämtar kommandon i sessionen som har de angivna parametrarna. Ange parameter namn eller parameter-alias. Jokertecken stöds.

Parametrarna **ParameterName** och **ParameterType** söker bara efter kommandon i den aktuella sessionen.

Den här parametern introducerades i Windows PowerShell 3,0.

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

### – ParameterType

Anger en matris med parameter namn. Denna cmdlet hämtar kommandon i sessionen som har parametrar av den angivna typen. Ange det fullständiga namnet eller del namnet för en parameter typ. Jokertecken stöds.

Parametrarna **ParameterName** och **ParameterType** söker bara efter kommandon i den aktuella sessionen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowCommandInfo

Anger att denna cmdlet visar kommando information.

Den här parametern introducerades i Windows PowerShell 5,0.

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

### -Syntax

Anger att denna cmdlet endast hämtar följande angivna data om kommandot:

- Alias. Hämtar standard namnet.
- Cmdletar. Hämtar syntaxen.
- Funktioner och filter. Hämtar funktions definitionen.
- Skript och program eller filer. Hämtar sökvägen och fil namnet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – TotalCount

Anger antalet kommandon som ska hämtas. Du kan använda den här parametern för att begränsa utdata från ett kommando.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Verb

Anger en matris med kommando-verb. Denna cmdlet hämtar kommandon, som innehåller cmdlets, Functions och alias, som har namn som innehåller det angivna verbet. Ange ett eller flera verb eller verb-mönster. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka pipe-kommando namn till denna cmdlet.

## UTDATA

### System. Management. Automation. CommandInfo

Denna cmdlet returnerar objekt som härletts från klassen **CommandInfo** . Vilken typ av objekt som returneras beror på vilken typ av kommando som `Get-Command` hämtas.

### System. Management. Automation. AliasInfo

Representerar alias.

### System. Management. Automation. ApplicationInfo

Representerar program och filer.

### System. Management. Automation. CmdletInfo

Representerar cmdletar.

### System. Management. Automation. FunctionInfo

Representerar funktioner och filter.

### System. Management. Automation. WorkflowInfo

Representerar arbets flöden.

## ANTECKNINGAR

* Om mer än ett kommando med samma namn är tillgängligt för sessionen, `Get-Command` returnerar kommandot som körs när du skriver kommandots namn. Om du vill hämta kommandon med samma namn, som anges i körnings ordning, använder du parametern **all** . Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).
* När en modul importeras automatiskt är det samma sak som att använda `Import-Module` cmdleten. Modulen kan lägga till kommandon, typer och formatering av filer och köra skript i sessionen.
  Om du vill aktivera, inaktivera och konfigurera automatisk import av moduler använder du `$PSModuleAutoLoadingPreference` Preference-variabeln. Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

## RELATERADE LÄNKAR

[Exportera – PSSession](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[Get – hjälp](Get-Help.md)

[Hämta medlem](../Microsoft.PowerShell.Utility/Get-Member.md)

[Get-PSDrive](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[Importera – PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[about_Command_Precedence](About/about_Command_Precedence.md)
