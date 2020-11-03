---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 1a4a3f7050c3da2a73ae0d5319938117284076b7
ms.sourcegitcommit: 05f578d3fca0d9663bb1e4f76e2f14604f5303ae
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/04/2020
ms.locfileid: "93269421"
---
# Get-Help

## SAMMANFATTNING
Visar information om PowerShell-kommandon och-koncept.

## SYNTAX

### AllUsersView (standard)

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### DetailedView

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Detailed
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### Exempel

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Examples
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### Parametrar

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### Online

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### ShowWindow

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## BESKRIVNING

`Get-Help`Cmdleten visar information om PowerShell-begrepp och kommandon, inklusive cmdlets, functions, Common Information Model (CIM), arbets flöden, providers, alias och skript.

Om du vill ha hjälp med en PowerShell-cmdlet skriver du `Get-Help` följt av cmdlet-namnet, t `Get-Help Get-Process` . ex.:.

Konceptuell hjälp artiklar i PowerShell börjar med **about_** , till exempel **about_Comparison_Operators**. Om du vill se alla **about_** artiklar skriver du `Get-Help about_*` . Om du vill se en viss artikel skriver du `Get-Help about_<article-name>` , till exempel `Get-Help about_Comparison_Operators` .

Om du vill ha hjälp med en PowerShell-Provider skriver du `Get-Help` följt av namnet på providern. Om du till exempel vill få hjälp med certifikat leverantören skriver du `Get-Help Certificate` .

Du kan också skriva `help` eller `man` , som visar en skärm med text i taget. Eller, `<cmdlet-name> -?` som är identisk med `Get-Help` , men endast fungerar för-cmdletar.

`Get-Help` hämtar hjälp innehållet som det visar från hjälp filer på din dator. Utan hjälpfilerna `Get-Help` visar endast grundläggande information om cmdletar. Några PowerShell-moduler innehåller hjälpfiler. Från och med PowerShell 3,0 innehåller modulerna som medföljer operativ systemet Windows inte hjälpfilerna. Om du vill hämta eller uppdatera hjälpfilerna för en modul i PowerShell 3,0 använder du `Update-Help` cmdleten.

Du kan också Visa PowerShell-hjälp dokument online i Microsoft Docs. Om du vill hämta online-versionen av en hjälpfil använder du parametern **online** , t. ex `Get-Help Get-Process -Online` .:. Läs mer om PowerShell-dokumentationen i Microsoft Docs PowerShell- [dokumentationen](/powershell).

Om du skriver `Get-Help` följt av det exakta namnet på en hjälp artikel, eller ett ord som är unikt för en hjälp artikel, `Get-Help` visar artikelns innehåll. Om du anger det exakta namnet på ett kommando alias `Get-Help` visar hjälpen för det ursprungliga kommandot. Om du anger ett ord-eller ord mönster som visas i flera hjälp artikel rubriker `Get-Help` visas en lista över matchande rubriker. Om du anger text som inte visas i någon hjälp artikel titlar, `Get-Help` visar en lista över artiklar som innehåller texten i innehållet.

`Get-Help` kan få hjälp artiklar för alla språk som stöds och nationella inställningar. `Get-Help` börja med att leta efter hjälpfiler i språk uppsättningen för Windows och sedan i det överordnade språket, till exempel **PT** för **pt-br** , och sedan i ett återställnings språk. Från och med PowerShell 3,0, om det `Get-Help` inte finns hjälp i reserv språket, söker det efter hjälp artiklar på engelska, **en-US** , innan det returnerar ett fel meddelande eller visar automatiskt genererad hjälp.

Information om symbolerna som `Get-Help` visas i syntaxen för kommandosyntaxen finns [about_Command_Syntax](./About/about_Command_Syntax.md).
Information om attributvärden, till exempel **obligatorisk** och **Position** , finns [about_Parameters](./About/about_Parameters.md).

>[!NOTE]
> I PowerShell 3,0 och PowerShell 4,0 `Get-Help` går det inte **About** att hitta artiklar i moduler om modulen inte har importer ATS till den aktuella sessionen. Detta är ett känt fel. **Om** du vill hämta artiklar i en modul importerar du modulen antingen med hjälp av `Import-Module` cmdleten eller genom att köra en cmdlet som ingår i modulen.

## EXEMPEL

### Exempel 1: Visa grundläggande hjälp information om en cmdlet

I de här exemplen visas grundläggande hjälp information om `Format-Table` cmdleten.

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

`Get-Help <cmdlet-name>` är den enklaste och standardsyntaxen för `Get-Help` cmdlet. Du kan utelämna parametern **Name** .

Syntaxen `<cmdlet-name> -?` fungerar bara för-cmdletar.

### Exempel 2: Visa grundläggande information en sida i taget

I de här exemplen visas grundläggande hjälp information om `Format-Table` cmdleten en sida i taget.

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

`help` är en funktion som kör `Get-Help` cmdlet internt och visar resultatet en sida i taget.

`man` är ett alias för `help` funktionen.

`Get-Help Format-Table` skickar objektet nedåt i pipelinen. `Out-Host -Paging` tar emot utdata från pipelinen och visar en sida i taget. Mer information finns i [out-Host](Out-Host.md).

### Exempel 3: Visa mer information om en cmdlet

I de här exemplen visas mer detaljerad hjälp information om `Format-Table` cmdleten.

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

Den **detaljerade** parametern visar hjälp artikelns detaljerade vy som innehåller parameter beskrivningar och exempel.

Den **fullständiga** parametern visar hjälp artikelns fullständiga vy som innehåller parameter beskrivningar, exempel, indata och utdata för objekt och ytterligare anteckningar.

De **detaljerade** och **fullständiga** parametrarna gäller endast för kommandon som har hjälpfiler installerade på datorn. Parametrarna gäller inte för de konceptuella ( **about_** ) hjälp artiklarna.

### Exempel 4: Visa valda delar av en cmdlet med hjälp av parametrar

I de här exemplen visas valda delar av `Format-Table` cmdlet-hjälpen.

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

I **exempel** parametern visas hjälp filens **namn** och **sammanfattnings** avsnitt och alla exempel. Du kan inte ange ett exempel nummer eftersom **exempel** parametern är en switch-parameter.

**Parametern parameter** visar bara beskrivningarna av de angivna parametrarna. Om du bara anger jokertecknet asterisk ( `*` ) visas beskrivningarna för alla parametrar.
När **parametern** anger ett parameter namn, till exempel **groupby** , visas information om den parametern.

Dessa parametrar är inte effektiva för de konceptuella ( **about_** ) hjälp artiklarna.

### Exempel 5: Visa onlineversionen av hjälp

I det här exemplet visas onlineversionen av hjälp artikeln för `Format-Table` cmdleten i din standard webbläsare.

```powershell
Get-Help Format-Table -Online
```

### Exempel 6: Visa hjälp om hjälp systemet

`Get-Help`Cmdlet utan parametrar visar information om PowerShell-hjälpen.

```powershell
Get-Help
```

### Exempel 7: Visa tillgängliga hjälp artiklar

I det här exemplet visas en lista över alla hjälp artiklar som är tillgängliga på din dator.

```powershell
Get-Help *
```

### Exempel 8: Visa en lista med konceptuella artiklar

I det här exemplet visas en lista över de konceptuella artiklarna som ingår i PowerShell-hjälpen. Alla dessa artiklar börjar med de tecken som **about_**. Om du vill visa en viss hjälp fil skriver du till `Get-Help \<about_article-name\>` exempel `Get-Help about_Signing` .

Endast de konceptuella artiklarna som innehåller hjälpfiler som är installerade på datorn visas. Information om hur du hämtar och installerar hjälpfiler i PowerShell 3,0 finns i [Update-Help](Update-Help.md).

```powershell
Get-Help about_*
```

### Exempel 9: Sök efter ett ord i cmdlet-hjälpen

Det här exemplet visar hur du söker efter ett ord i en hjälp artikel för cmdlet.

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

`Get-Help` använder den **fullständiga** parametern för att få hjälp information för `Add-Member` . **MamlCommandHelpInfo** -objektet skickas ned pipelinen. `Out-String` använder **Stream** -parametern för att konvertera objektet till en sträng. `Select-String` använder **mönster** parametern för att söka i strängen efter **CliXml**.

### Exempel 10: Visa en lista över artiklar som innehåller ett ord

I det här exemplet visas en lista över artiklar som innehåller Word- **fjärrkommunikation**.

När du anger ett ord som inte visas i någon artikel rubrik, `Get-Help` visar en lista över artiklar som innehåller ordet.

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### Exempel 11: Visa leverantörsspecifik hjälp

I det här exemplet visas två sätt att hämta den providerspecifika hjälpen för `Get-Item` . De här kommandona får hjälp som förklarar hur du använder `Get-Item` cmdleten i PowerShell-SQL Server-providerns **DataCollection** -nod.

I det första exemplet används `Get-Help` parametern **Path** för att ange SQL Server providerns sökväg.
Eftersom providerns sökväg har angetts kan du köra kommandot från alla Sök vägs platser.

Det andra exemplet använder `Set-Location` för att navigera till SQL Server leverantörs sökväg. Från den platsen behövs inte **Sök vägs** parametern för `Get-Help` att hämta den providerspecifika hjälpen.

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### Exempel 12: Visa hjälp för ett skript

I det här exemplet får du hjälp med `MyScript.ps1 script` . Information om hur du skriver hjälp för dina funktioner och skript finns [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## PARAMETRAR

### – Kategori

Visar hjälp endast för objekt i den angivna kategorin och deras alias. Konceptuella artiklar finns i kategorin **Hjälpfil** .

De acceptabla värdena för den här parametern är följande:

- Alias
- Cmdlet
- Leverantör
- Allmänt
- VANLIGA FRÅGOR OCH SVAR
- Ordlista
- Hjälpfil
- ScriptCommand
- Funktion
- Filtrera
- ExternalScript
- Alla
- DefaultHelp
- Arbetsflöde
- Dscresource Keyword Supports
- Klass
- Konfiguration

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Komponent

Visar kommandon med det angivna komponent svärdet, till exempel **Exchange**. Ange ett komponent namn.
Jokertecken är tillåtna. Den här parametern har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.

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

### -Detaljerad

Lägger till parameter beskrivningar och exempel i den grundläggande hjälp visningen. Den här parametern är endast effektiv när hjälpfilerna är installerade på datorn. Den har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Exempel

Visar endast namn, Sammanfattning och exempel. Om du bara vill visa exemplen skriver du `(Get-Help \<cmdlet-name\>).Examples` .

Den här parametern är endast effektiv när hjälpfilerna är installerade på datorn. Den har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Fullständig

Visar hela hjälp artikeln för en cmdlet. **Fullständig** innehåller parameter beskrivningar och attribut, exempel, indata och utdata och ytterligare anteckningar.

Den här parametern är endast effektiv när hjälpfilerna är installerade på datorn. Den har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Funktioner

Visar hjälp för objekt med de angivna funktionerna. Ange funktionerna. Jokertecken är tillåtna. Den här parametern har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.

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

### -Name

Hämtar hjälp om det angivna kommandot eller konceptet. Ange namnet på en cmdlet, funktion, Provider, skript eller ett arbets flöde, till exempel `Get-Member` ett konceptuellt artikel namn, till exempel `about_Objects` eller ett alias, till exempel `ls` . Jokertecken tillåts i cmdlet-och Provider-namn, men du kan inte använda jokertecken för att hitta namnen på hjälp artiklar om funktioner och skript.

Om du vill ha hjälp med ett skript som inte finns i en sökväg som anges i `$env:Path` miljövariabeln, anger du Skriptets sökväg och fil namn.

Om du anger det exakta namnet på en hjälp artikel, `Get-Help` visar innehållet i artikeln.

Om du anger ett ord-eller ord mönster som visas i flera hjälp artikel rubriker `Get-Help` visas en lista över matchande rubriker.

Om du anger text som inte matchar någon rubrik för hjälp artiklar, `Get-Help` visar en lista över artiklar som innehåller texten i innehållet.

Namn på konceptuella artiklar, till exempel `about_Objects` , måste anges på engelska, även i icke-engelska versioner av PowerShell.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – Online

Visar onlineversionen av en hjälp artikel i standard webbläsaren. Den här parametern är endast giltig för hjälp artiklar för cmdlet, Function, Workflow och script. Du kan inte använda parametern **online** med `Get-Help` i en fjärrsession.

Information om hur du får stöd för den här funktionen i hjälp artiklar som du skriver, finns [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)och [stöder onlinehjälp](/powershell/scripting/developer/module/supporting-online-help)och [Skriv hjälp för PowerShell-cmdletar](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Parameter

Visar endast de detaljerade beskrivningarna av de angivna parametrarna. Jokertecken är tillåtna. Den här parametern har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

Hämtar hjälp som förklarar hur cmdleten fungerar i den angivna providerns sökväg. Ange en sökväg till PowerShell-providern.

Den här parametern hämtar en anpassad version av en cmdlets hjälp artikel som förklarar hur cmdleten fungerar i den angivna PowerShell-providerns sökväg. Den här parametern är endast effektiv för hjälp om en provider-cmdlet och bara när providern innehåller en anpassad version av hjälp artikeln Provider-cmdlet i Hjälp filen. Om du vill använda den här parametern installerar du hjälp filen för modulen som innehåller providern.

Om du vill se en anpassad cmdlet-hjälp för en sökväg för en provider går du till platsen för providerns sökväg och anger ett `Get-Help` kommando eller, från valfri sökväg, använder du parametern **Path** för `Get-Help` att ange providerns sökväg. Du kan också hitta anpassad cmdlet-hjälp online i hjälp avsnitten för providern i hjälp artiklarna.

Mer information om PowerShell-leverantörer finns [about_Providers](./About/about_Providers.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Roll

Visar anpassad hjälp för den angivna användar rollen. Ange en roll. Jokertecken är tillåtna.

Ange den roll som användaren spelar i en organisation. Vissa cmdletar visar annan text i sina hjälpfiler baserat på värdet för den här parametern. Den här parametern har ingen inverkan på hjälpen för Core-cmdletar.

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

### -ShowWindow

Visar hjälp avsnittet i ett fönster för enklare läsning. I fönstret **finns en Sök funktion och en** **inställnings** ruta där du kan ange alternativ för visning, inklusive alternativ för att endast Visa valda avsnitt i ett hjälp avsnitt.

**ShowWindow** -parametern stöder hjälp avsnitt för kommandon (cmdlets, functions, CIM-kommandon, skript) och konceptuella **om** artiklar. Den har inte stöd för leverantörs hjälp.

Den här parametern introducerades i PowerShell 7,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka objekt nedåt i pipelinen till `Get-Help` .

## UTDATA

### ExtendedCmdletHelpInfo

Om du kör `Get-Help` på ett kommando som inte har en hjälp fil `Get-Help` returnerar ett **ExtendedCmdletHelpInfo** -objekt som representerar den automatiskt genererade hjälpen.

### System. String

Om du får en konceptuell hjälp artikel `Get-Help` returneras den som en sträng.

### MamlCommandHelpInfo

Om du får ett kommando som har en hjälp fil `Get-Help` returnerar ett **MamlCommandHelpInfo** -objekt.

## ANTECKNINGAR

PowerShell 3,0 innehåller inte hjälpfilerna. Använd cmdleten för att ladda ned och installera hjälpfilerna som `Get-Help` läser `Update-Help` . Du kan använda `Update-Help` cmdleten för att hämta och installera hjälpfiler för de kärn kommandon som ingår i PowerShell och för alla moduler som du installerar. Du kan också använda den för att uppdatera hjälpfilerna så att hjälpen på datorn aldrig är inaktuell.

Du kan också läsa hjälp artiklarna om de kommandon som levereras med PowerShell online från [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

`Get-Help` Visar hjälp i språk uppsättningen för Windows-operativsystemet eller på reserv språket för det aktuella språket. Om du inte har hjälpfilerna för primär-eller fallback-språkvarianten `Get-Help` fungerar det som om det inte finns några hjälpfiler på datorn. Om du vill ha hjälp med ett annat språk kan du använda **region** och **språk** på kontroll panelen för att ändra inställningarna. På Windows 10, **Inställningar** , **tid & språk**.

En fullständig vy över hjälpen innehåller en tabell med information om parametrarna. Tabellen innehåller följande fält:

- **Krävs**. Anger om parametern är obligatorisk (sant) eller valfri (falskt).

- **Position**. Anger om parametern är namngiven eller position (numerisk). Positions parametrar måste finnas på en angiven plats i kommandot.

- **Namngiven** anger att parameter namnet är obligatoriskt, men att parametern kan visas var som helst i kommandot.

- **Numeriskt** anger att parameter namnet är valfritt, men när namnet utelämnas måste parametern vara på den plats som anges i numret. Anger till exempel `2` att om parameter namnet utelämnas måste parametern vara den andra eller enda namnlös parameter i kommandot. När parameter namnet används kan parametern visas var som helst i kommandot.

- **Standardvärde**. Parametervärdet eller standard beteendet som används i PowerShell om du inte inkluderar parametern i kommandot.

- Accepterar pipeline-ininformation. Anger om du kan (sant) eller inte (falskt) skicka objekt till parametern via en pipeline. **Efter egenskaps namn** betyder det att det pipelinade objektet måste ha en egenskap som har samma namn som parameter namnet.

- **Accepterar jokertecken**. Anger om värdet för en parameter kan innehålla jokertecken, till exempel en asterisk ( `*` ) eller frågetecken ( `?` ).

## RELATERADE LÄNKAR

[about_Command_Syntax](About/about_Command_Syntax.md)

[about_Comment_Based_Help](./About/about_Comment_Based_Help.md)

[Get-Command](Get-Command.md)

[Stöd för uppdateringsbar hjälp](/powershell/scripting/developer/module/supporting-updatable-help)

[Uppdatera – hjälp](Update-Help.md)

[Skriva kommentarsbaserade hjälpavsnitt](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[Skriva hjälp för PowerShell-cmdletar](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)

