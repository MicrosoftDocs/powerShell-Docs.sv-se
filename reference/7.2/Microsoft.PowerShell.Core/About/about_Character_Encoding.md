---
description: Beskriver hur PowerShell använder tecken kodning för indata och utdata av sträng data.
Locale: en-US
ms.date: 10/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Character_Encoding
ms.openlocfilehash: 3b47a528b0beae5e8142157454cbc676ffd7e795
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96349826"
---
# <a name="about_character_encoding"></a>about_Character_Encoding

## <a name="short-description"></a>Kort beskrivning
Beskriver hur PowerShell använder tecken kodning för indata och utdata av sträng data.

## <a name="long-description"></a>Lång beskrivning

Unicode är en global tecken kodnings standard. Systemet använder Unicode enbart för tecken-och sträng manipulation. En detaljerad beskrivning av alla aspekter av Unicode finns i Unicode- [standarden](https://www.unicode.org/standard/standard.html).

Windows stöder Unicode och traditionella teckenuppsättningar. Traditionella teckenuppsättningar, t. ex. Windows tecken tabeller, använder 8-bitars värden eller kombinationer av 8-bitars värden för att representera de tecken som används i ett särskilt språk eller geografiskt regions inställningar.

I PowerShell används Unicode-tecken som standard. Flera cmdlets har dock en **encoding** -parameter som kan ange encoding för en annan teckenuppsättning. Med den här parametern kan du välja den speciella tecken kodning som du behöver för att samverka med andra system och program.

Följande cmdletar har parametern **encoding** :

- Microsoft. PowerShell. Management
  - Add-Content
  - Get-Content
  - Set-Content
- Microsoft.PowerShell.Utility
  - Export-Clixml
  - Export-Csv
  - Export-PSSession
  - Format-Hex
  - Import-Csv
  - Out-File
  - Select-String
  - Send-MailMessage

## <a name="the-byte-order-mark"></a>Byte-ordning-markering

Byte-order-markering (BOM) är en _Unicode-signatur_ i de första byten i en fil eller text ström som anger vilken Unicode-kodning som används för data. Mer information finns i dokumentationen [för byte-ordnings märkning](/globalization/encoding/byte-order-mark) .

I Windows PowerShell skapar Unicode-kodning, förutom `UTF7` , alltid en struktur. PowerShell-kärnan är standardvärdet `utf8NoBOM` för alla text utdata.

Undvik att använda strukturer i UTF-8-filer för bästa möjliga kompatibilitet. UNIX-plattformar och UNIX-arvs verktyg som också används på Windows-plattformar stöder inte strukturer.

`UTF7`Kodningen bör också undvikas. UTF-7 är inte en standard Unicode-kodning och skrivs utan någon struktur i alla versioner av PowerShell.

Att skapa PowerShell-skript på en UNIX-liknande plattform eller med ett plattforms oberoende redigerare i Windows, till exempel Visual Studio Code, resulterar i en fil som kodas med `UTF8NoBOM` . De här filerna fungerar bra på PowerShell-kärnan, men kan brytas i Windows PowerShell om filen innehåller icke-ASCII-tecken.

Om du behöver använda icke-ASCII-tecken i skripten kan du spara dem som UTF-8 med BOM. Utan strukturen tolkar Windows PowerShell ditt skript som kodat i den äldre "ANSI"-tecken tabellen. Filer som har UTF-8-strukturen kan däremot vara problematiska på UNIX-liknande plattformar. Många UNIX-verktyg som `cat` , `sed` , `awk` och vissa redigerare, till exempel `gedit` inte vet hur du ska behandla strukturen.

## <a name="character-encoding-in-windows-powershell"></a>Tecken kodning i Windows PowerShell

I PowerShell 5,1 stöder **encoding** -parametern följande värden:

- `Ascii` Använder ASCII-teckenuppsättning (7-bitars).
- `BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.
- `BigEndianUTF32` Använder UTF-32 med big-endian byte-ordningen.
- `Byte` Kodar en uppsättning tecken i en sekvens med byte.
- `Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).
- `Oem` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.
- `String` Samma som `Unicode` .
- `Unicode` Använder UTF-16 med en liten-endian-order.
- `Unknown` Samma som `Unicode` .
- `UTF32` Använder UTF-32 med en liten-endian-order.
- `UTF7` Använder UTF-7.
- `UTF8` Använder UTF-8 (med struktur).

I allmänhet använder Windows PowerShell Unicode [UTF-16LE-](https://wikipedia.org/wiki/UTF-16) kodning som standard. Standard kodningen som används av cmdlets i Windows PowerShell är dock inte konsekvent.

> [!NOTE]
> Om Unicode-kodning används, förutom `UTF7` , skapas alltid en struktur.

För cmdletar som skriver utdata till filer:

- `Out-File` och omdirigerings operatörerna `>` och `>>` skapar UTF-16LE, som särskilt skiljer sig från `Set-Content` och `Add-Content` .

- `New-ModuleManifest``Export-CliXml`Dessutom skapar du UTF-16LE-filer.

- När målfilen är tom eller inte finns, `Set-Content` och `Add-Content` Använd `Default` encoding. `Default` är den kodning som anges av den aktiva system språket för den gamla ANSI-kodsidan.

- `Export-Csv` skapar `Ascii` filer men använder olika kodning när du använder parametern **APPEND** (se nedan).

- `Export-PSSession` skapar UTF-8-filer med struktur som standard.

- `New-Item -Type File -Value` skapar en struktur lös UTF-8-fil.

- `Send-MailMessage` använder `Default` kodning som standard.

- `Start-Transcript` skapar `Utf8` filer med en struktur. När parametern **APPEND** används kan kodningen vara olika (se nedan).

För kommandon som lägger till i en befintlig fil:

- `Out-File -Append` och `>>` omdirigerings operatorn inte gör något försök att matcha kodningen för den befintliga mål filens innehåll. I stället använder de standard kodningen om inte **encoding** -parametern används. Du måste använda filens ursprungliga kodning när du lägger till innehåll.

- Om en explicit **encoding** -parameter saknas `Add-Content` identifierar den befintliga kodningen och tillämpar den automatiskt på det nya innehållet. Om det befintliga innehållet saknar struktur `Default` används ANSI-kodning. Beteendet i `Add-Content` är detsamma i PowerShell Core (V6 och högre) förutom standard kodningen `Utf8` .

- `Export-Csv -Append` matchar den befintliga kodningen när mål filen innehåller en struktur. Om en struktur saknas används `Utf8` kodning.

- `Start-Transcript -Append` matchar den befintliga kodningen av filer som innehåller en struktur. Om det inte finns någon struktur är standardvärdet `Ascii` kodning. Den här kodningen kan leda till data förlust eller tecken skada när data i avskriften innehåller flera byte-tecken.

För cmdletar som läser sträng data i avsaknad av en struktur:

- `Get-Content` och `Import-PowerShellDataFile` använder `Default` ANSI-kodning. ANSI är också vad PowerShell-motorn använder när den läser käll koden från filer.

- `Import-Csv`, `Import-CliXml` och `Select-String` anta `Utf8` att ingen struktur saknas.

## <a name="character-encoding-in-powershell-core"></a>Tecken kodning i PowerShell Core

I PowerShell Core (V6 och högre) stöder **encoding** -parametern följande värden:

- `ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).
- `bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.
- `oem`: Använder standard kodning för MS-DOS-och-konsol program.
- `unicode`: Kodar i UTF-16-format med lite-endian-dataordning.
- `utf7`: Kodar i UTF-7-format.
- `utf8`: Kodar i UTF-8-format (ingen struktur).
- `utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)
- `utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)
- `utf32`: Kodar i UTF-32-format.

PowerShell-kärnan är standardvärdet `utf8NoBOM` för alla utdata.

Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ). Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage).

## <a name="changing-the-default-encoding"></a>Ändra standard kodning

PowerShell har två standardvariabler som kan användas för att ändra standard kodnings beteendet.

- `$PSDefaultParameterValues`
- `$OutputEncoding`

Mer information finns i [about_Preference_Variables](about_Preference_Variables.md).

Från och med PowerShell 5,1 anropar omdirigerings operatörerna ( `>` och `>>` ) `Out-File` cmdlet: en. Därför kan du ange standard kodningen för dem med hjälp av `$PSDefaultParameterValues` Preference-variabeln som visas i det här exemplet:

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

Använd följande instruktion för att ändra standard kodningen för alla cmdletar som har **kodnings** parametern.

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> Genom att lägga till det här kommandot i din PowerShell-profil blir inställningen en session – global inställning som påverkar alla kommandon och skript som inte uttryckligen anger en kodning.
>
> På samma sätt bör du inkludera sådana kommandon i dina skript eller moduler som du vill använda på samma sätt. Med dessa kommandon ser du till att cmdletar fungerar på samma sätt även när de körs av en annan användare, på en annan dator eller i en annan version av PowerShell.

Den automatiska variabeln `$OutputEncoding` påverkar kodnings-PowerShell-användningen för att kommunicera med externa program. Det har ingen effekt på kodningen att operatörerna för utgående omdirigering och PowerShell-cmdlet: ar använder för att spara filer.

## <a name="see-also"></a>Se även

- [Introduktion till tecken kodning i .NET](/dotnet/standard/base-types/character-encoding-introduction)
- [Tecken tabeller – Win32-appar](/windows/win32/intl/code-pages)
- [Unicode-standarden](https://www.unicode.org/standard/standard.html)
- [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage)
- [UTF-16LE](https://wikipedia.org/wiki/UTF-16)
- [Markering av byte ordning](https://wikipedia.org/wiki/Byte_order_mark)
- [about_Preference_Variables](about_Preference_Variables.md)
