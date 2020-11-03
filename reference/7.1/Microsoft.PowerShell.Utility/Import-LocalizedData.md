---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: d19279133a42e3aea17f02348e44aec161ba5a23
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93273632"
---
# Import-LocalizedData

## SAMMANFATTNING
Importerar språkspecifika data till skript och funktioner baserat på den användar gränssnitts kultur som valts för operativ systemet.

## SYNTAX

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Import-LocalizedData`Cmdlet: en hämtar dynamiskt strängar från en under katalog vars namn matchar gränssnittets språk uppsättning för den aktuella användaren av operativ systemet. Det är utformat för att göra det möjligt för skript att Visa användar meddelanden i det GRÄNSSNITTs språk som valts av den aktuella användaren.

`Import-LocalizedData` importerar data från `.psd1` filer i språkspecifika under kataloger i skript katalogen och sparar dem i en lokal variabel som anges i kommandot. Cmdleten väljer under katalogen och filen baserat på värdet för den `$PSUICulture` automatiska variabeln. När du använder den lokala variabeln i skriptet för att visa ett användar meddelande visas meddelandet i användarens GRÄNSSNITTs språk.

Du kan använda parametrarna för `Import-LocalizedData` för att ange en alternativ kultur, sökväg och fil namn för användar gränssnittet för att lägga till kommandon som stöds och för att utelämna det fel meddelande som visas om `.psd1` filerna inte hittas.

`Import-LocalizedData`Cmdleten stöder skriptet internationaliserings initiativ som introducerades i Windows PowerShell 2,0. Det här initiativet syftar till att bättre hantera användare i hela världen genom att göra det enkelt för skript att Visa användar meddelanden på användar GRÄNSSNITTs språket för den aktuella användaren. Mer information om detta och om formatet för `.psd1` filerna finns [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).

## EXEMPEL

### Exempel 1: Importera text strängar

I det här exemplet importeras text strängar till `$Messages` variabeln. Standardvärdena för alla andra cmdlet-parametrar används.

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

Om kommandot ingår i Archives.ps1-skriptet i `C:\Test` katalogen och värdet för den `$PsUICulture` automatiska variabeln är zh-CN `Import-LocalizedData` importeras `Archives.psd1` filen i `C:\test\zh-CN` katalogen till `$Messages` variabeln.

### Exempel 2: importera lokaliserade data strängar

Det här exemplet körs på kommando raden som inte är i ett skript. Den hämtar lokaliserade data strängar från filen Test.psd1 och visar dem på kommando raden. Eftersom kommandot inte används i ett skript, krävs parametern **filename** . Kommandot använder parametern **värdet** för att ange en-US-kultur.

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

`Import-LocalizedData` Returnerar en hash-tabell som innehåller de lokaliserade data strängarna.

### Exempel 3: importera GRÄNSSNITTs kultur strängar

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

Det här kommandot importerar text strängar till `$MsgTbl` variabeln för ett skript.

Den använder parametern **värdet** för att dirigera cmdleten för att importera data från `Simple.psd1` filen i under `ar-SA` katalogen i `C:\Data\Localized` .

### Exempel 4: importera lokaliserade data till ett skript

Det här exemplet visar hur du använder lokaliserade data i ett enkelt skript.

```powershell
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

Den första delen av exemplet visar innehållet i `Test.psd1` filen. Det innehåller ett `ConvertFrom-StringData` kommando som konverterar en serie med namngivna text strängar till en hash-tabell. `Test.psd1`Filen finns i under katalogen en-us i `C:\Test` katalogen som innehåller skriptet.

Den andra delen av exemplet visar innehållet i `Test.ps1` skriptet. Det innehåller ett `Import-LocalizedData` kommando som importerar data från den matchande `.psd1` filen till `$Messages` variabeln och ett `Write-Host` kommando som skriver ett av meddelandena i `$Messages` variabeln till värd programmet.

Den sista delen av exemplet kör skriptet. Utdata visar att det visar rätt användar meddelande i användar GRÄNSSNITTets språk uppsättning för den aktuella användaren av operativ systemet.

### Exempel 5: Ersätt standard text strängar i ett skript

Det här exemplet visar hur du `Import-LocalizedData` ersätter standard text strängar som definierats i data avsnittet i ett skript.

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

I det här exemplet innehåller DATA avsnittet i TestScript.ps1-skriptet ett `ConvertFrom-StringData` kommando som konverterar innehållet i data avsnittet till en hash-tabell och lagrar i värdet för `$UserMessages` variabeln.

Skriptet innehåller också ett `Import-LocalizedData` kommando, som importerar en hash-tabell med översatta text strängar från filen TestScript.psd1 i den under katalog som anges av `$PsUICulture` variabelns värde. Om kommandot hittar `.psd1` filen sparas de översatta strängarna från filen i värdet för samma `$UserMessages` variabel, vilket skriver över hash-tabellen som sparats av logiken för data avsnitt.

Det tredje kommandot visar det första meddelandet i `$UserMessages` variabeln.

Om `Import-LocalizedData` kommandot hittar en `.psd1` fil för `$PsUICulture` språket, innehåller värdet för `$UserMessages` variabeln de översatta text strängarna. Om kommandot Miss lyckas av någon anledning visar kommandot de standard text strängar som definierats i DATA avsnittet i skriptet.

### Exempel 6: utelämna fel meddelanden om UI-kulturen inte hittas

Det här exemplet visar hur du ignorerar de fel meddelanden som visas när det `Import-LocalizedData` inte går att hitta de kataloger som matchar användarens gränssnitts kultur eller inte kan hitta en `.psd1` fil för skriptet i dessa kataloger.

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

Du kan använda den gemensamma parametern **ErrorAction** med värdet SilentlyContinue för att ignorera fel meddelandet. Detta är särskilt användbart när du har angett användar meddelanden på ett standard-eller återställnings språk och inget fel meddelande krävs.

I det här exemplet jämförs två skript `Day1.ps1` och Day2.ps1, som innehåller ett `Import-LocalizedData` kommando. Skripten är identiska, förutom att Day2 använder **ErrorAction** common-parametern med värdet `SilentlyContinue` .

Exempel resultatet visar resultatet av att köra båda skripten när användar gränssnitts kulturen är inställt på `fr-BE` och det inte finns några matchande filer eller kataloger för denna användar gränssnitts kultur. `Day1.ps1` visar ett fel meddelande och engelska utdata. `Day2.ps1` visar bara de engelska utdata.

## PARAMETRAR

### -BaseDirectory

Anger bas katalogen där filerna finns `.psd1` . Standardvärdet är den katalog där skriptet finns. `Import-LocalizedData` söker efter `.psd1` filen för skriptet i en språkspecifik under katalog i bas katalogen.

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

### -BindingVariable

Anger den variabel som text strängarna importeras till. Ange ett variabel namn utan ett dollar tecken ( `$` ).

Den här parametern krävs i Windows PowerShell 2,0. Den här parametern är valfri i Windows PowerShell 3,0. Om du utelämnar den här parametern `Import-LocalizedData` returnerar en hash-tabell för text strängarna. Hash-tabellen har passerat pipelinen eller visas på kommando raden.

När `Import-LocalizedData` du använder för att ersätta standard text strängar som anges i data avsnittet i ett skript, tilldelar du data avsnittet till en variabel och anger namnet på data sektions variabeln i värdet för parametern **BindingVariable** . När `Import-LocalizedData` sparar det importerade innehållet i **BindingVariable** ersätts standard text strängarna av importerade data. Om du inte anger standard text strängar kan du välja ett variabel namn.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FileName

Anger namnet på data filen ( `.psd1)` som ska importeras. Ange ett fil namn. Du kan ange ett fil namn som inte innehåller `.psd1` fil namns tillägget, eller så kan du ange fil namnet inklusive `.psd1` fil namns tillägget. Datafiler ska sparas som Unicode eller UTF-8.

Parametern **filename** krävs när används `Import-LocalizedData` inte i ett skript.
Annars är parametern valfri och standardvärdet är bas namnet för skriptet. Du kan använda den här parametern för att dirigera för `Import-LocalizedData` att söka efter en annan `.psd1` fil.

Om **fil namnet** exempelvis utelämnas och skript namnet är FindFiles.ps1, `Import-LocalizedData` söker efter data filen FindFiles.psd1.

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

### -SupportedCommand

Anger cmdletar och funktioner som endast genererar data.

Använd den här parametern om du vill inkludera cmdlets och funktioner som du har skrivit eller testat. Mer information finns i [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).

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

### – Värdet

Anger en alternativ kultur för användar gränssnittet.
Standardinställningen är värdet för den `$PsUICulture` automatiska variabeln.
Ange en användar gränssnitts kultur i `<language>-<region>` formatet, till exempel, `en-US` `de-DE` eller `ar-SA` .

Värdet för parametern **värdet** bestämmer den språkspecifika under katalogen (i bas katalogen) från vilken `Import-LocalizedData` hämtar `.psd1` filen för skriptet.

Cmdleten söker efter en under katalog med samma namn som värdet för parametern **värdet** eller den `$PsUICulture` automatiska variabeln, till exempel `de-DE` eller `ar-SA` . Om det inte går att hitta katalogen, eller om katalogen inte innehåller någon `.psd1` fil för skriptet, söker den efter en under katalog med namnet på språk koden, t. ex. de eller p.a.. Om det inte går att hitta under katalogen eller `.psd1` filen, Miss lyckas kommandot och data visas på standard språket som anges i skriptet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Collections. hash

`Import-LocalizedData` sparar hash-tabellen i variabeln som anges av värdet för parametern **BindingVariable** .

## ANTECKNINGAR

- `Import-LocalizedData`Lokalisera dina användar meddelanden innan du använder dem. Formatera meddelandena för varje språk (UI-kultur) i en hash-tabell med nyckel/värde-par och spara hash-tabellen i en fil med samma namn som skriptet och ett `.psd1` fil namns tillägg. Skapa en katalog under skript katalogen för varje GRÄNSSNITTs kultur som stöds och spara sedan `.psd1` filen för varje användar gränssnitts kultur i katalogen med kultur namnet för användar gränssnittet.

  Du kan till exempel lokalisera dina användar meddelanden för de nationella inställningarna och formatera dem i en hash-tabell.
  Spara hash-tabellen i en `<ScriptName>.psd1` fil. Skapa sedan en `de-DE` under katalog under skript katalogen och spara den tyska `<ScriptName\>.psd1` filen i under `de-DE` katalogen.
  Upprepa den här metoden för varje språk som du stöder.

- `Import-LocalizedData` utför en strukturerad sökning efter de lokaliserade användar meddelandena för ett skript.

  `Import-LocalizedData` startar sökningen i den katalog där skript filen finns (eller värdet för parametern **BaseDirectory** ). Den söker sedan i bas katalogen efter en under katalog med samma namn som `$PsUICulture` variabelns värde (eller värdet för parametern **värdet** ), till exempel `de-DE` eller `ar-SA` . Sedan söker den i under katalogen efter en `.psd1` fil med samma namn som skriptet (eller värdet för parametern **filename** ).

  Om `Import-LocalizedData` det inte går att hitta en under katalog med namnet på användar gränssnitts kulturen, eller om under katalogen inte innehåller någon `.psd1` fil för skriptet, söker den efter en `.psd1` fil för skriptet i en under katalog med namnet på språk koden, t. ex. de eller p.a.. Om det inte går att hitta under katalogen eller `.psd1` filen, Miss lyckas kommandot, data visas på standard språket i skriptet och ett fel meddelande visas som förklarar att det inte gick att importera data. Om du inte vill att meddelandet ska ignoreras kan du använda den gemensamma parametern **ErrorAction** med värdet SilentlyContinue.

  Om `Import-LocalizedData` hittar under katalogen och `.psd1` filen importeras hash-tabellen för användar meddelanden till värdet för parametern **BindingVariable** i kommandot. När du sedan visar ett meddelande från hash-tabellen i variabeln, visas det lokaliserade meddelandet.

  Mer information finns i [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md).

## RELATERADE LÄNKAR

[Skriv värd](Write-Host.md)

[Importera – PowerShellDataFile](Import-PowerShellDataFile.md)

