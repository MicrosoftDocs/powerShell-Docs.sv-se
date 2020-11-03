---
description: Beskriver skriptets internationaliserings funktioner som gör det enkelt för skript att visa meddelanden och instruktioner till användare i användar gränssnittets språk.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: 51772eeb7517b5c61d9bc7a4333642684de6c37e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271425"
---
# <a name="about-script-internationalization"></a>Om skript internationalisering

## <a name="short-description"></a>Kort beskrivning
Beskriver skriptets internationaliserings funktioner som gör det enkelt för skript att visa meddelanden och instruktioner till användare i användar gränssnittets språk.

## <a name="long-description"></a>Lång beskrivning

Med PowerShell-skriptets internationella funktioner kan du bättre betjäna användare i hela världen genom att visa hjälp och användar meddelanden på användarens språk.

Skriptets internationaliserings funktioner frågar användar GRÄNSSNITTs kulturen för operativ systemet under körningen, importerar lämpliga översatta text strängar och visar dem för användaren. Med data avsnittet kan du lagra text strängar separat från kod så att de enkelt kan identifieras och extraheras. En ny cmdlet, `ConvertFrom-StringData` konverterar text strängar till ord listor, till exempel hash-tabeller, för att under lätta översättning.

För att stödja internationell hjälp text innehåller PowerShell följande funktioner:

- Ett data avsnitt som avgränsar text strängar från kod instruktioner. Mer information om data avsnittet finns [about_Data_Sections](about_Data_Sections.md).

- Nya automatiska variabler `$PSCulture` och `$PSUICulture` . `$PSCulture` lagrar namnet på det GRÄNSSNITTs språk som används i systemet för element som datum, tid och valuta. `$PSUICulture`Variabeln lagrar namnet på det gränssnitts språk som används i systemet för användar gränssnitts element som menyer och text strängar.

- En-cmdlet, `ConvertFrom-StringData` som konverterar text strängar till en ordbok, till exempel hash-tabeller, för att under lätta översättning. Mer information finns i [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).

- En ny filtyp, `.psd1` som lagrar översatta text strängar. `.psd1`Filerna lagras i språkspecifika under kataloger i skript katalogen.

- En cmdlet, `Import-LocalizedData` som importerar översatta text strängar för ett angivet språk till ett skript vid körning. Denna cmdlet känner igen och importerar strängar på ett språk som stöds av Windows. Mer information finns i [import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).

### <a name="the-data-section-storing-default-strings"></a>Data avsnittet: lagra standard strängar

Använd ett data avsnitt i skriptet för att lagra text strängarna på standard språket. Ordna strängarna i nyckel/värde-par i en här-sträng. Varje nyckel/värde-par måste finnas på en separat rad. Om du inkluderar kommentarer måste kommentarerna finnas på separata rader.

`ConvertFrom-StringData`Cmdleten konverterar nyckel/värde-par i denna-sträng till en ordbok, t. ex. hash-tabell som lagras i värdet för data avsnitts variabeln.

I följande exempel innehåller data avsnittet i `World.ps1` skriptet English-United tillstånds uppsättning (en-US) med prompt-meddelanden för ett skript. `ConvertFrom-StringData`Cmdleten konverterar strängarna till en hash-tabell och lagrar dem i `$msgtable` variabeln.

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

Mer information om här – strängar finns [about_Quoting_Rules](about_Quoting_Rules.md).

### <a name="psd1-files-storing-translated-strings"></a>PSD1-filer: lagra översatta strängar

Spara skript meddelanden för varje GRÄNSSNITTs språk i separata textfiler med samma namn som skriptet och `.psd1` fil namns tillägget. Lagra filerna i under kataloger i skript katalogen med namn på kulturer i följande format:

`<language>-<region>`

Exempel: de-DE, AR-SA och zh-hans

Om skriptet till exempel `World.ps1` lagras i `C:\Scripts` katalogen skapar du en fil katalog struktur som liknar följande:

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

`World.psd1`Filen i under katalogen indata för skript katalogen kan innehålla följande instruktion:

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

På samma sätt `World.psd1` kan filen i under katalogen ar-sa i skript katalogen innehålla följande instruktion:

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a>Import-LocalizedData: dynamisk hämtning av översatta strängar

Använd cmdleten för att hämta strängarna i användar gränssnitts språket för den aktuella användaren `Import-LocalizedData` .

`Import-LocalizedData` söker efter värdet för den `$PSUICulture` automatiska variabeln och importerar innehållet i `<script-name>.psd1` filerna i under katalogen som matchar `$PSUICulture` värdet. Sedan sparas det importerade innehållet i variabeln som anges av värdet för parametern **BindingVariable** .

```powershell
Import-LocalizedData -BindingVariable msgTable
```

Om kommandot till exempel `Import-LocalizedData` visas i `C:\Scripts\World.ps1` skriptet och värdet för `$PSUICulture` är "ar-sa" `Import-LocalizedData` hittar du följande fil:

`C:\Scripts\ar-SA\World.psd1`

Sedan importerar den de arabiska text strängarna från filen till `$msgTable` variabeln och ersätter eventuella standard strängar som kan definieras i data avsnittet i `World.ps1` skriptet.

Det innebär att när skriptet använder `$msgTable` variabeln för att Visa användar meddelanden visas meddelandena i arabiska.

Följande skript visar t. ex. meddelandet "Ange ditt användar namn" i arabiska:

```powershell
if (!($username)) { $msgTable.promptMsg }
```

Om `Import-LocalizedData` det inte går att hitta en `.psd1` fil som matchar värdet för `$PSUIculture` , `$msgTable` ersätts inte värdet för, och anropet `$msgTable.promptMsg` visar en-US-strängar för återställningen.

## <a name="examples"></a>Exempel

Det här exemplet visar hur skriptets internationaliserings funktioner används i ett skript för att visa en veckodag för användare på det språk som har angetts på datorn.

Följande är en fullständig lista över Sample1.ps1 skript filen.

Skriptet börjar med ett data avsnitt med namnet dag ($Day) som innehåller ett `ConvertFrom-StringData` kommando. Uttrycket som skickas till `ConvertFrom-StringData` är en här-sträng som innehåller dag namnen i standard kulturen för användar gränssnittet, en-US, i nyckel/värde-par. `ConvertFrom-StringData`Cmdleten konverterar nyckel/värde-par i denna-sträng till en hash-tabell och sparar den i `$Day` variabeln värde.

`Import-LocalizedData`Kommandot importerar innehållet i `.psd1` filen i katalogen som matchar värdet för den `$PSUICulture` automatiska variabeln och sparar det i `$Day` variabeln och ersätter värdena i `$Day` som definieras i avsnittet data.

De återstående kommandona läser in strängarna i en matris och visar dem.

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

`.psd1`Filerna som stöder skriptet sparas i under kataloger i skript katalogen med namn som matchar `$PSUICulture` värdena.

Följande är en komplett lista över `.\de-DE\sample1.psd1` :

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

Det innebär att när du kör Sample.ps1 på ett system där värdet för är inde `$PSUICulture` , är utdata för skriptet:

```Output
Heute ist Freitag
```

## <a name="see-also"></a>Se även

- [about_Data_Sections](about_Data_Sections.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [Importera – LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
