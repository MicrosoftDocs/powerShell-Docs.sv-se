---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadline
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: 15295ffaac320d24a3c9c24c0419118ef2644f90
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273195"
---
# Set-PSReadLineOption

## Sammanfattning
Anpassar beteendet för kommando rads redigering i **PSReadLine**.

## Syntax

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [<CommonParameters>]
```

## Beskrivning

`Set-PSReadLineOption`Cmdleten anpassar beteendet för **PSReadLine** -modulen när du redigerar kommando raden. Använd om du vill visa **PSReadLine** -inställningarna `Get-PSReadLineOption` .

## Exempel

### Exempel 1: Ange förgrunds-och bakgrunds färger

I det här exemplet anges **PSReadLine** för att visa **kommentars** -token med grön förgrunds text på en grå bakgrund. I Escape-sekvensen som används i exemplet representerar **32** förgrunds färgen och **47** representerar bakgrunds färgen.

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="$([char]0x1b)[32;47m" }
```

Du kan välja att bara ange en förgrunds text färg. Till exempel en ljus grön förgrunds text färg för **kommentarens** token: `"Comment"="$([char]0x1b)[92m"` .

### Exempel 2: Ange klock format

I det här exemplet kommer **PSReadLine** att svara på fel eller villkor som kräver åtgärder från användaren.
**BellStyle** har ställts in för att avge en ljud signal vid 1221 Hz för 60 MS.

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> Den här funktionen kanske inte fungerar på alla värdar på plattformar.

### Exempel 3: ange flera alternativ

`Set-PSReadLineOption` kan ange flera alternativ med en hash-tabell.

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

`$PSReadLineOptions`Hash-tabellen anger nycklar och värden. `Set-PSReadLineOption` använder nycklar och värden med `@PSReadLineOptions` för att uppdatera **PSReadLine** -alternativen.

Du kan visa nycklar och värden som anger namnet på hash-tabellen `$PSReadLineOptions` på PowerShell-kommandoraden.

### Exempel 4: ange flera färg alternativ

Det här exemplet visar hur du ställer in fler än ett färg värde i ett enda kommando.

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### Exempel 5: Ange färg värden för flera typer

Det här exemplet visar tre olika metoder för hur du ställer in färgen på tokens som visas i **PSReadLine**.

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### Exempel 6: Använd ViModeChangeHandler för att Visa läges ändringar i vi

Det här exemplet ger en markör ändring VT Escape som svar på en ändring i ändrings läget i **vi** .

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "$([char]0x1b)[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "$([char]0x1b)[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

Funktionen **OnViModeChange** anger markör alternativen **för lägen för** lägen: INSERT och Command.
**ViModeChangeHandler** använder `Function:` providern för att referera till **OnViModeChange** som ett skript Blocks objekt.

Mer information finns i [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## Parametrar

### -AddToHistoryHandler

Anger en **script block** som styr vilka kommandon som läggs till i **PSReadLine** -historiken.

**Script block** tar emot kommando raden som inmatad. Om **script block** returnerar `$True` läggs kommando raden till i historiken.

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AnsiEscapeTimeout

Det här alternativet är endast för Windows när indatatypen omdirigeras, till exempel när du kör under `tmux` eller `screen` .

Vid Omdirigerad inaktivitet i Windows skickas många nycklar som en sekvens med tecken som börjar med Escape-tecknet. Det är omöjligt att skilja mellan ett enda escape-tecken följt av fler tecken och en giltig escape-sekvens.

Antagandet är att terminalen kan skicka tecknen snabbare än en användar typ. **PSReadLine** väntar för denna timeout innan den tar emot en komplett escape-sekvens.

Om du ser slumpmässiga eller oväntade tecken när du skriver kan du justera denna tids gräns.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -BellStyle

Anger hur **PSReadLine** reagerar på olika fel och tvetydiga villkor.

Giltiga värden är följande:

- **Hörbar** : en kort signal.
- **Visuellt** : text blinkar en kort stund.
- **Ingen** : ingen feedback.

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### – Färger

Parametern **Colors** anger olika färger som används av **PSReadLine**.

Argumentet är en hash-tabell där nycklarna anger vilka element och värden som anger färgen.
Mer information finns i [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Färger kan vara antingen ett värde från **ConsoleColor** , till exempel `[ConsoleColor]::Red` eller en giltig ANSI-escape-sekvens. Giltiga escape-sekvenser beror på terminalen. I PowerShell 5,0 är ett exempel på en escape-sekvens för röd text `$([char]0x1b)[91m` . I PowerShell 6 och senare är samma escape-sekvens `` `e[91m`` . Du kan ange andra escape-sekvenser, inklusive följande typer:

- 256-färg
- 24-bitars färg
- Förgrund, bakgrund eller både och
- Invertera, fet

Mer information om ANSI Color-koder finns i [ANSI Escape Code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in wikipedia.

Giltiga nycklar är:

- **ContinuationPrompt** : färgen på fortsättnings frågan.
- **Betoning** : betonings färgen. Till exempel den matchande texten vid sökning efter historik.
- **Fel** : fel färgen. Till exempel i prompten.
- **Markering** : färgen för att markera meny markeringen eller den markerade texten.
- **Standard** : standardvärdet för token.
- **Comment** : kommentarens token-färg.
- **Nyckelord** : token för nyckelord.
- **Sträng** : strängens token-färg.
- **Operator** : operatorns token-färg.
- **Variabel** : variabelns token-färg.
- **Kommando** : kommando-token-färg.
- **Parameter** : parameterns token-färg.
- **Skriv** : typens token-färg.
- **Number** : standardvärdet för token.
- **Medlem** : medlems namnets token-färg.

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

### -CommandValidationHandler

Anger en **script block** som anropas från **ValidateAndAcceptLine**. Om ett undantag genereras Miss lyckas valideringen och felet rapporteras.

Innan ett undantag utlöses kan validerings hanteraren placera markören vid fel punkten så att den blir lättare att åtgärda. En verifierings hanterare kan också ändra kommando raden, till exempel för att korrigera vanliga typografiska fel.

**ValidateAndAcceptLine** används för att undvika att historiken rensas med kommandon som inte fungerar.

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompletionQueryItems

Anger det maximala antalet slutförda objekt som visas utan att fråga.

Om antalet objekt som ska visas är större än det här värdet visas **PSReadLine** **Ja/Nej** innan slut för ande objekt visas.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContinuationPrompt

Anger den sträng som visas i början av efterföljande rader när flera rader skrivs in. Standardvärdet är Double större än-tecken ( `>>` ). En tom sträng är giltig.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingDuration

Anger längden på pip när **BellStyle** är inställd på **hörbar**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingTone

Anger tonen i Hertz (Hz) för pip när **BellStyle** är inställt på **hörbar**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### – EditMode

Anger kommando rads redigerings läge. Om du använder den här parametern återställs alla nyckel bindningar som anges av `Set-PSReadLineKeyHandler` .

Giltiga värden är följande:

- **Windows** : nyckel bindningar emulerar PowerShell, cmd och Visual Studio.
- **Emacs** : nyckel bindningar emulerar bash eller emacs.
- **Vi** : nyckel bindningar emulerar vi.

Används `Get-PSReadLineKeyHandler` för att se nyckel bindningarna för den aktuella konfigurerade **EditMode**.

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExtraPromptLineCount

Anger antalet extra rader.

Om din prompt omfattar fler än en rad anger du ett värde för den här parametern. Använd det här alternativet om du vill att extra rader ska vara tillgängliga när **PSReadLine** visar frågan när du har visat några utdata. **PSReadLine** returnerar till exempel en lista över slut för ande.

Det här alternativet krävs mindre än i tidigare versioner av **PSReadLine** , men är användbart när `InvokePrompt` funktionen används.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistoryNoDuplicates

Det här alternativet styr återställnings beteendet. Dubbla kommandon läggs fortfarande till i historik filen.
När det här alternativet är inställt visas bara det senaste anropet när du anropar kommandon. Upprepade kommandon läggs till i historiken för att bevara ordning under återkallning. Du vill dock vanligt vis inte se kommandot flera gånger vid återanrop eller sökning i historiken.

Som standard är egenskapen **HistoryNoDuplicates** för det globala **PSConsoleReadLineOptions** -objektet inställt på `True` . Om du använder den här **SwitchParameter** anges egenskap svärdet till `True` . Om du vill ändra egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-HistoryNoDuplicates:$False` .

Med hjälp av följande kommando kan du ange egenskap svärdet direkt:

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySavePath

Anger sökvägen till filen där historiken sparas. Datorer som kör Windows-eller icke-Windows-plattformar lagrar filen på olika platser. Fil namnet lagras i en variabel `$($host.Name)_history.txt` , till exempel `ConsoleHost_history.txt` .

Om du inte använder den här parametern är standard Sök vägen följande:

**Windows**

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

**icke-Windows**

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySaveStyle

Anger hur **PSReadLine** sparas i historiken.

Giltiga värden är följande:

- **SaveIncrementally** : spara historik när varje kommando körs och delas över flera instanser av PowerShell.
- **SaveAtExit** : Lägg till historik fil när PowerShell avslutas.
- **SaveNothing** : Använd inte en historik fil.

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCaseSensitive

Anger att historik sökning är Skift läges känsligt i funktioner som **ReverseSearchHistory** eller **HistorySearchBackward**.

Som standard är egenskapen **HistorySearchCaseSensitive** för det globala **PSConsoleReadLineOptions** -objektet inställt på `False` . Om du använder den här **SwitchParameter** anges egenskap svärdet till `True` . Om du vill ändra tillbaka egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-HistorySearchCaseSensitive:$False` .

Med hjälp av följande kommando kan du ange egenskap svärdet direkt:

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCursorMovesToEnd

Anger att markören flyttas till slutet av de kommandon som du läser in från historiken med hjälp av en sökning.
När den här parametern är inställd på `$False` stannar markören kvar på den plats där du tryckte på uppåt-eller nedpilarna.

Som standard är egenskapen **HistorySearchCursorMovesToEnd** för det globala **PSConsoleReadLineOptions** -objektet inställt på `False` . Med den här **SwitchParameter** anger du egenskap svärdet till `True` . Om du vill ändra tillbaka egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-HistorySearchCursorMovesToEnd:$False` .

Med hjälp av följande kommando kan du ange egenskap svärdet direkt:

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumHistoryCount

Anger det maximala antalet kommandon som ska sparas i **PSReadLine** historik.

**PSReadLine** -historiken är separat från PowerShell-historiken.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumKillRingCount

Anger det maximala antalet objekt som lagras i stopp ringen.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -PromptText

När ett parsningsfel uppstår ändrar **PSReadLine** en del av meddelandet Red. **PSReadLine** analyserar funktionen prompt för att bestämma hur du bara vill ändra färgen på en del av din prompt. Den här analysen är inte 100% tillförlitlig.

Använd det här alternativet om **PSReadLine** ändrar din prompt på oväntade sätt. Ta med eventuella avslutande blank steg.

Exempel: om din prompt-funktion såg ut som i följande exempel:

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

Ange sedan:

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowToolTips

När du visar möjliga kompletteringar visas knapp beskrivningar i listan med slutförda.

Det här alternativet är aktiverat som standard. Det här alternativet är inte aktiverat som standard i tidigare versioner av **PSReadLine**. Om du vill inaktivera aktiverar du det här alternativet `$False` .

Som standard är egenskapen **ShowToolTips** för det globala **PSConsoleReadLineOptions** -objektet inställt på `True` . Om du använder den här **SwitchParameter** anges egenskap svärdet till `True` . Om du vill ändra egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-ShowToolTips:$False` .

Med hjälp av följande kommando kan du ange egenskap svärdet direkt:

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeChangeHandler

När **ViModeIndicator** är inställt på `Script` , anropas det angivna skript blocket varje gång läget ändras. Skript blocket anges med ett argument av typen `ViMode` .

Den här parametern introducerades i PowerShell 7.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeIndicator

Det här alternativet anger den visuella indikationen för det aktuella läget i **vi** . Antingen infognings läge eller kommando läge.

Giltiga värden är följande:

- **Ingen** : det finns ingen indikation.
- **Prompt** : färg ändrings färgen visas.
- **Markör** : markören ändrar storlek.
- **Skript** : Användardefinierad text skrivs ut.

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WordDelimiters

Anger tecken som begränsar ord för funktioner som **ForwardWord** eller **KillWord**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"---
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Indata

### Inget

Du kan inte skicka pipe-objekt till `Set-PSReadLineOption.`

## Utdata

### Inget

Denna cmdlet genererar inga utdata.

## Kommentarer

## Relaterade länkar

[about_PSReadLine](./About/about_PSReadLine.md)

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
