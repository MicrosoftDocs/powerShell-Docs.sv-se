---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: c81c50152209a922c486005b5919ac4a1e7295a2
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490323"
---
# Register-ArgumentCompleter

## SAMMANFATTNING

Registrerar en anpassad argument slutförare.

## SYNTAX

### NativeSet

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### PowerShellSet

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## BESKRIVNING

`Register-ArgumentCompleter`Cmdleten registrerar en anpassad argument slutförare. Med en argument slutförd kan du ange dynamisk ifyllning av flikar, vid körning för alla kommandon som du anger.

## EXEMPEL

### Exempel 1: registrera en anpassad argument slutförare

I följande exempel registreras en argument slutförre för cmdletens **ID-** parameter `Set-TimeZone` .

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

Det första kommandot skapar ett-skript block som tar de nödvändiga parametrarna som skickas i när användaren trycker på <kbd>fliken</kbd>. Mer information finns i Beskrivning av **script block** -parametern.

I-skript blocket hämtas de tillgängliga värdena för **ID** med hjälp av `Get-TimeZone` cmdleten. Egenskapen **ID** för varje tidszon är skickas till `Where-Object` cmdleten. `Where-Object`Cmdlet: en filtrerar bort alla ID: n som inte börjar med värdet som anges av `$wordToComplete` , som representerar texten som användaren skrev innan de tryckte på <kbd>fliken</kbd>. Filtrerade ID: n är skickas till `ForEach-Object` cmdleten som innesluter varje värde i citationstecken, om värdet innehåller blank steg.

Det andra kommandot registrerar argumentet completer genom att skicka script block, **ParameterName** **-ID** och **commandname** `Set-TimeZone` .

### Exempel 2: Lägg till information i dina värden för att slutföra din flik

I följande exempel skrivs fliken ifyllning för cmdlet-parameterns **namn** -parameter `Stop-Service` och returnerar endast tjänster som körs.

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

Det första kommandot skapar ett-skript block som tar de nödvändiga parametrarna som skickas i när användaren trycker på <kbd>fliken</kbd>. Mer information finns i Beskrivning av **script block** -parametern.

I-skript blocket hämtar det första kommandot alla tjänster som körs med hjälp av `Where-Object` cmdleten. Tjänsterna är skickas till `ForEach-Object` cmdleten. `ForEach-Object`Cmdleten skapar ett nytt [system. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) -objekt och fyller det med namnet på den aktuella tjänsten (representeras av pipeline-variabeln `$_.Name` ).

Med **CompletionResult** -objektet kan du ge ytterligare information till varje returnerat värde:

- **completionText** (sträng) – den text som ska användas som resultat av automatisk komplettering. Detta är värdet som skickas till kommandot.
- **listItemText** (sträng) – texten som ska visas i en lista, t. ex. när användaren trycker på <kbd>CTRL</kbd>- + <kbd>blank steg</kbd>. Detta används endast för visning och skickas inte till kommandot när det är markerat.
- **resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) – typen av slut för ande resultat.
- **knapp Beskrivning** (sträng) – text för knapp beskrivningen med information som ska visas om objektet.
  Detta visas när användaren väljer ett objekt efter att ha tryckt på <kbd>CTRL</kbd>- + <kbd>ytan</kbd>.

Det sista kommandot visar att de stoppade tjänsterna fortfarande kan skickas manuellt till `Stop-Service` cmdlet: en. Fliken slut för ande är den enda aspekt som påverkas.

### Exempel 3: registrera en anpassad intern argument slutförare

Du kan använda den **inbyggda** parametern för att ange att en flik ska slutföras för ett internt kommando. I följande exempel lägger du till TABB-slutförande för `dotnet` kommando rads gränssnittet (CLI).

> [!NOTE]
> `dotnet complete`Kommandot är endast tillgängligt i version 2,0 och senare av Dotnet cli.

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

Det första kommandot skapar ett-skript block som tar de nödvändiga parametrarna som skickas i när användaren trycker på <kbd>fliken</kbd>. Mer information finns i Beskrivning av **script block** -parametern.

I-skript blocket `dotnet complete` används kommandot för att utföra slut för ande av fliken.
Resultaten är skickas till `ForEach-Object` cmdleten som använder den **nya** statiska metoden i klassen [system. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) för att skapa ett nytt **CompletionResult** -objekt för varje värde.

## PARAMETRAR

### – CommandName

Anger namnet på kommandona som en matris.

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Inbyggd

Anger att argumentet är slutfört för ett internt kommando där PowerShell inte kan slutföra parameter namn.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – ParameterName

Anger namnet på den parameter vars argument slutförs. Det angivna parameter namnet får inte vara ett uppräknat värde, till exempel **ForegroundColor** -parametern för `Write-Host` cmdleten.

Mer information om uppräkningar finns i [about_Enum](./About/about_Enum.md).

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Script block

Anger vilka kommandon som ska köras för att utföra slut för ande av tabbar. Det skript block som du anger ska returnera värdena som slutför indatamängden. Skript blocket måste avregistrera värdena med hjälp av pipelinen ( `ForEach-Object` , `Where-Object` osv.) eller någon annan lämplig metod. Om du returnerar en matris med värden kan PowerShell behandla hela matrisen som **ett** värde för sista tabb.

Skript blocket måste acceptera följande parametrar i den ordning som anges nedan. Namnen på parametrarna är inte viktiga eftersom PowerShell passerar i värdena efter position.

- `$commandName` (Position 0) – den här parametern anges till namnet på det kommando som skript blocket tillhandahåller för att slutföra tabben.
- `$parameterName` (Position 1) – den här parametern har angetts till den parameter vars värde kräver att tabbtangenten slutförs.
- `$wordToComplete` (Position 2) – den här parametern är inställd på värde som användaren har angett innan de tryckte på <kbd>fliken</kbd>. Skript blocket ska använda det här värdet för att fastställa värden för tabbar.
- `$commandAst` (Position 3) – den här parametern har angetts till det abstrakta Syntaxs trädet (AST) för den aktuella indatamängden. Mer information finns i [AST-klass](/dotnet/api/system.management.automation.language.ast).
- `$fakeBoundParameters` (Position 4) – den här parametern anges till en hash-text som innehåller `$PSBoundParameters` för cmdleten innan användaren tryckte på <kbd>fliken</kbd>. Mer information finns i [about_Automatic_Variables](./About/about_Automatic_Variables.md).

När du anger den **interna** parametern måste skript blocket ta följande parametrar i den angivna ordningen. Namnen på parametrarna är inte viktiga eftersom PowerShell passerar i värdena efter position.

- `$wordToComplete` (Position 0) – den här parametern är inställd på värde som användaren har angett innan de tryckte på <kbd>fliken</kbd>. Skript blocket ska använda det här värdet för att fastställa värden för tabbar.
- `$commandAst` (Position 1) – den här parametern har angetts till det abstrakta Syntaxs trädet (AST) för den aktuella indatamängden. Mer information finns i [AST-klass](/dotnet/api/system.management.automation.language.ast).
- `$cursorPosition` (Position 2) – den här parametern anges till positionen för markören när användaren tryckte på <kbd>fliken</kbd>.

Du kan också ange ett **ArgumentCompleter** som parameter-attribut. Mer information finns i [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR
