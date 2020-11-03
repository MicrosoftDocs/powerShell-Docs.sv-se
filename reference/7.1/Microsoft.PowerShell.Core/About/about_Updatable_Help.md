---
description: Beskriver det uppdaterings bara hjälp systemet i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: cf528451e17ecdfd7fa53f99ed29a5d6d4abf075
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270146"
---
# <a name="about-updatable-help"></a>Om uppdaterbar hjälp

## <a name="short-description"></a>Kort beskrivning
Beskriver det uppdaterings bara hjälp systemet i PowerShell.

## <a name="long-description"></a>Lång beskrivning

PowerShell tillhandahåller flera olika sätt att komma åt de mest aktuella hjälp avsnitten för PowerShell-cmdletar och-koncept.

Det uppdaterings bara hjälp systemet, som introducerades i PowerShell 3,0, är utformat för att säkerställa att du alltid har de senaste hjälp avsnitten på den lokala datorn så att du kan läsa dem på kommando raden. Det gör det enkelt att hämta och installera hjälpfiler och att uppdatera dem när nya hjälpfiler blir tillgängliga.

Om du vill tillhandahålla uppdaterad hjälp för flera datorer i ett företag och för datorer som inte har åtkomst till Internet, kan du hämta hjälp filen till en fil Systems katalog eller fil resurs och sedan installera hjälpfilerna från fil resursen.

I PowerShell 4,0 bevaras egenskapen **HelpInfoUri** över Windows PowerShell-fjärrkommunikation, som gör `Save-Help` att du kan arbeta med moduler som är installerade på en fjärrdator, men som inte nödvändigt vis är installerade på den lokala datorn. Du kan spara ett **PSModuleInfo** -objekt på en disk eller ett flyttbart medium (till exempel en USB-enhet) genom `Export-Clixml` att köra på en dator som inte har Internet åtkomst, importera **PSModuleInfo** -objektet på en dator som har Internet åtkomst och sedan köra `Save-Help` på **PSModuleInfo** -objektet. Den sparade hjälpen kan kopieras till fjärrdatorn, frånkopplad dator med hjälp av ett flyttbart medium och sedan installeras genom att köra `Update-Help` . Med de här förbättringarna av `Save-Help` funktioner kan du installera hjälp på datorer som inte har någon typ av nätverks åtkomst. Ett exempel på hur du använder de nya `Save-Help` funktionerna finns i [så här uppdaterar du hjälpen från en fil resurs](#how-to-update-help-from-a-file-share) i det här avsnittet.

Uppdaterings bar hjälp stöder också online-åtkomst till de senaste hjälp avsnitten och Basic-hjälpen för cmdlets, även om det inte finns några hjälpfiler på datorn.

PowerShell 3,0 kommer inte med hjälpfilerna. Du kan använda funktionen uppdaterbar hjälp för att installera hjälpfilerna för alla kommandon som ingår som standard i PowerShell och för alla Windows-moduler.

## <a name="updatable-help-cmdlets"></a>Uppdaterings bara hjälp-cmdletar

- `Update-Help`: Laddar ned de senaste hjälpfilerna från Internet eller en fil resurs och installerar dem på den lokala datorn.

- `Save-Help`: Laddar ned de senaste hjälpfilerna från Internet och sparar dem i fil system katalogen eller fil resursen. Om du vill installera hjälpfilerna på datorer använder du `Update-Help` .

- `Get-Help`: Visar hjälp avsnitt på kommando raden. Hämtar hjälp från hjälp filen på datorn. Visar automatiskt genererad hjälp för cmdletar och funktioner som inte har hjälpfiler. Öppnar direkt hjälp avsnitt för cmdlets, functions, scripts och arbets flöden i din standard webbläsare.

## <a name="auto-generated-help-help-without-help-files"></a>Automatiskt genererad hjälp: hjälp utan hjälp filer

Om du inte har hjälp filen för en cmdlet, funktion eller ett arbets flöde på datorn, `Get-Help` visar cmdlet: en automatiskt genererad hjälp och du uppmanas att hämta hjälpfilerna eller läsa dem online.

Automatiskt genererad hjälp innehåller syntax och alias och kommentarer som förklarar hur du använder de uppdaterbara hjälp-cmdletarna och för att få åtkomst till hjälp avsnitten online.

Följande kommando hämtar till exempel grundläggande hjälp för `Get-Culture` cmdleten. Utdata visar `Get-Help` visningen när det inte finns några hjälpfiler på datorn.

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a>Hjälp filer för moduler

Den minsta enheten med uppdaterings bara hjälp är hjälp för en modul. I modulen hjälp finns hjälp för alla cmdletar, funktioner, arbets flöden, providrar, skript och koncept i en modul. Du kan uppdatera hjälpen för alla moduler som är installerade på datorn, även om de inte importeras till den aktuella sessionen.

Du kan uppdatera hjälpen för hela modulen, men du kan inte uppdatera hjälpen för enskilda cmdlets.

Om du vill hitta modulen som innehåller en viss cmdlet använder du följande kommando format:

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

Om du till exempel vill hitta modulen som innehåller `Set-ExecutionPolicy` cmdleten skriver du:

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

Om du vill uppdatera hjälpen för en viss modul skriver du:

```powershell
Update-Help -Module <ModuleName>
```

Om du till exempel vill uppdatera hjälpen för den modul som innehåller Set-ExecutionPolicy-cmdlet skriver du:

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a>Behörigheter för uppdaterbar hjälp

Om du vill uppdatera hjälpen för modulerna i katalogen `$pshome/Modules` måste du vara medlem i gruppen Administratörer på datorn.

Om du inte är medlem i gruppen Administratörer kan du inte uppdatera hjälpen för de här modulerna. men om du har till gång till Internet kan du Visa hjälp online.

Att uppdatera hjälpen för moduler i katalogen `$home/Documents/PowerShell/Modules` eller modulerna i andra under kataloger i `$home` katalogen kräver inte särskilda behörigheter.

`Update-Help` `Save-Help` Cmdletarna och har en **UseDefaultCredentials** -parameter som ger den aktuella användarens uttryckliga autentiseringsuppgifter. Den här parametern är utformad för att komma åt säkra Internet-platser.

`Update-Help` `Save-Help` Cmdletarna och har också en parameter för **autentiseringsuppgifter** som gör att du kan köra kommandot på en fjärrdator och komma åt en fil resurs på en tredje dator. Parametern **Credential** är bara giltig när du använder SourcePath-eller **LiteralPath** -parametrarna i `Update-Help` och **DestinationPath** -eller **LiteralPath** -parametrarna för `Save-Help` .

## <a name="how-to-install-and-update-help-files"></a>Installera och uppdatera hjälpfiler

Om du vill hämta och installera hjälpfiler för första gången, eller om du vill uppdatera hjälpfilerna på datorn, använder du `Update-Help` cmdleten.

`Update-Help`Cmdleten gör allt det hårda arbetet åt dig, inklusive följande uppgifter.

- Avgör vilka moduler som stöder uppdaterbar hjälp.
- Söker efter Internet-platsen där varje modul lagrar de uppdaterbara hjälpfilerna.
- Jämför hjälpfilerna för varje modul på datorn med de senaste hjälpfilerna som är tillgängliga för varje modul.
- Laddar ned de nya filerna från Internet.
- Avbryter hjälp fils paketet.
- Kontrollerar att filerna är giltiga hjälpfiler.
- Installerar hjälpfilerna i den språkspecifika under katalogen i modulens katalog.

Använd cmdleten för att få åtkomst till de nya hjälp avsnitten `Get-Help` . Du behöver inte starta om PowerShell.

Om du vill installera eller uppdatera hjälpen för alla moduler på datorn som stöder uppdaterings bar hjälp skriver du:

```powershell
Update-Help
```

Om du vill uppdatera hjälpen för vissa moduler lägger du till **modulen modul** för `Update-Help` . Jokertecken tillåts i modulnamnet.

Om du till exempel vill uppdatera hjälp för ServerManager-modulen skriver du:

```powershell
Update-Help -Module ServerManager
```

Utan parametrar kan du `Update-Help` Uppdatera hjälpen för alla moduler i sessionen och för alla installerade moduler som stöder uppdaterbar hjälp. Moduler måste installeras i kataloger som anges i värdet för PSModulePath-miljövariabeln för att tas med. Dessa är också moduler som returneras av kommandot "Get-Help-ListAvailable".

Om värdet för **modulen modul** är `*` (alla) `Update-Help` försöker att uppdatera hjälpen för alla installerade moduler, inklusive moduler som inte stöder uppdaterbar hjälp. Det här kommandot genererar vanligt vis många fel eftersom cmdleten påträffar moduler som inte stöder uppdaterbar hjälp.

## <a name="how-to-update-help-from-a-file-share"></a>Så här uppdaterar du hjälpen från en fil resurs

Om du vill ha stöd för datorer som inte är anslutna till Internet, eller om du vill styra eller effektivisera hjälp med att uppdatera i ett företag, använder du `Save-Help` cmdleten. `Save-Help`Cmdlet: en laddar ned hjälpfiler från Internet och sparar dem i en fil Systems katalog som du anger.

`Save-Help` Jämför hjälpfilerna i den angivna katalogen med de senaste hjälpfilerna som är tillgängliga för varje modul. Om katalogen inte innehåller några hjälpfiler eller om det finns nyare hjälpfiler för modulen, `Save-Help` laddar cmdleten ned de nya filerna från Internet. Men det går inte att packa upp eller installera hjälpfilerna.

Om du vill installera eller uppdatera hjälpfilerna på en dator från hjälpfiler som sparats i en fil Systems katalog använder du cmdlet: en **SourcePath** -parameter `Update-Help` . `Update-Help`Cmdleten identifierar de senaste hjälpfilerna, avbryter och validerar dem och installerar dem i språkspecifika under kataloger i modulernas kataloger.

Om du till exempel vill spara hjälpen för alla installerade moduler till `\\Server\Share` katalogen skriver du:

```powershell
Save-Help -DestinationPath \\Server\Share
```

Om du vill uppdatera hjälpen från `\\Server\Share` katalogen skriver du:

```powershell
Update-Help -SourcePath \\Server\Share
```

I följande exempel visas användningen av `Save-Help` för att spara hjälp för moduler som inte är installerade på den lokala datorn. I det här exemplet körs administratören för `Save-Help` att spara hjälpen för modulen DHCP server från en Internet-ansluten klient dator, utan att installera den DHCP-modul eller DHCP-serverrollen på den lokala datorn.

Alternativ 1: kör `Invoke-Command` för att hämta **PSModuleInfo** -objektet för fjärrmodulen, spara det i en variabel `$m` och kör sedan `Save-Help` på **PSModuleInfo** -objektet genom att ange variabeln `$m` som modulnamn.

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

Alternativ 2: öppna en PSSession som är riktad mot den dator som kör DHCP-server-modulen för att hämta **PSModuleInfo** -objektet för modulen, spara den i en variabel `$m` och sedan köra `Save-Help` på det objekt som har sparats i `$m` variabeln.

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

Alternativ 3: öppna en CIM-session, riktad mot den dator som kör DHCP-server-modulen, för att hämta **PSModuleInfo** -objektet för modulen, spara den i en variabel `$m` och kör sedan `Save-Help` på det objekt som har sparats i `$m` variabeln.

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

I följande exempel installerar administratören hjälp för DHCP-modulen på en dator som inte har nätverks åtkomst.

Kör först `Export-Clixml` för att exportera **PSModuleInfo** -objektet till en delad mapp eller till ett flyttbart medium.

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

Nu ska du transportera det flyttbara mediet till en dator som har Internet åtkomst och sedan importera **PSModuleInfo** -objektet med `Import-Clixml` . Kör för `Save-Help` att spara hjälpen för **PSModuleInfo** -objektet importerad DHCP-modul.

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

Slutligen kan du överföra det flyttbara mediet till datorn som inte har nätverks åtkomst och sedan installera hjälpen genom att köra `Update-Help` .

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

Utan parametrar kan du `Save-Help` Hämta hjälpen för alla moduler i sessionen och för alla installerade moduler som stöder uppdaterbar hjälp. Moduler måste installeras i kataloger som anges i värdet för `$env:PSModulePath` miljövariabeln, antingen på den lokala datorn eller på en fjärrdator som du vill spara hjälpen för. Dessa är också moduler som returneras genom att köra ett `Get-Help -ListAvailable` kommando.

## <a name="how-to-update-help-files-in-different-languages"></a>Så här uppdaterar du hjälpfiler på olika språk

Som standard `Update-Help` `Save-Help` laddar cmdletarna ned hjälpen i användar gränssnitts kulturen och språket som är inställda för Windows på den lokala datorn. Om hjälpfilerna för de angivna modulerna inte är tillgängliga i den lokala användar gränssnitts kulturen, `Update-Help` och `Save-Help` Använd Windows språk återställnings regler för att hitta det språk som stöds bäst.

Du kan dock använda **värdet** -parametrarna för `Update-Help` `Save-Help` cmdletarna och för att hämta och installera hjälpfiler i alla användar gränssnitts kulturer där de är tillgängliga.

Om du till exempel vill spara de senaste hjälpfilerna för alla moduler i sessionen på japanska (ja-JP) och franska (fr-FR) skriver du:

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

Om hjälpfilerna för modulerna inte är tillgängliga på de språk som du har angett `Update-Help` `Save-Help` returnerar cmdletarna och ett fel meddelande som visar de språk som hjälpen för varje modul är tillgänglig för, så att du kan välja det alternativ som bäst passar dina behov.

> [!NOTE]
> Uppdaterings bara hjälp innehåll publiceras för närvarande bara på engelska (en-US). På vissa icke-Windows-system måste du använda parametern **värdet** för att begära `en-US` innehållet explicit.

## <a name="how-to-use-online-help"></a>Så här använder du onlinehjälpen

Om du inte kan eller väljer att inte uppdatera hjälpfilerna på den lokala datorn kan du fortfarande hämta de senaste hjälpfilerna online.

Om du vill öppna onlinehjälpen för en cmdlet eller funktion använder du cmdleten **online** för `Get-Help` cmdleten.

Följande kommando öppnar exempelvis onlinehjälpen för `Get-Job` cmdlet: en i din standard webbläsare:

```powershell
Get-Help Get-Job -Online
```

Om du vill ha Onlinehjälp för ett skript använder du parametern **online** och den fullständiga sökvägen till skriptet.

Parametern **online** fungerar inte med about-ämnen. Om du vill se avsnitten om PowerShell, inklusive hjälp avsnitt om PowerShell-språket, kan du läsa mer i [PowerShell om ämnen](about.md).

## <a name="how-to-minimize-or-prevent-internet-downloads"></a>Minimera eller förhindra Internet hämtningar

Använd cmdleten för att minimera hämtning av Internet och tillhandahålla uppdaterings bar hjälp till användare som inte är anslutna till Internet. `Save-Help` Hämta hjälpen från Internet och spara den på en nätverks resurs. Skapa sedan en grupprincip inställning eller ett schemalagt jobb som kör ett `Update-Help` kommando på alla datorer. Ange värdet för cmdlet- **parametern för** `Update-Help` cmdlet: en till nätverks resursen.

Om du vill förhindra att användare som har Internet åtkomst laddar ned uppdaterings bar hjälp från Internet använder du inställningen **Ange standard Sök väg för uppdatering – hjälp** Grupprincip.

Den här grupprincip inställningen lägger implicit till **SourcePath** -parametern, med den fil Systems plats som du anger, till alla `Update-Help` kommandon på varje dator som påverkas. Användare kan använda **SourcePath** -parametern explicit för att ange en annan plats för fil systemet, men de kan inte utesluta **SourcePath** -parametern och hämta hjälpen från Internet.

> [!NOTE]
> Inställningen **Ange standard käll Sök väg för uppdatering – hjälp för** grup princip visas under **dator konfiguration** och **användar konfiguration**. Men endast princip inställningen under **dator konfiguration** är effektiv. Princip inställningen under **användar konfiguration** ignoreras.

Mer information finns i [about_Group_Policy_Settings](about_Group_Policy_Settings.md).

## <a name="how-to-update-help-for-non-standard-modules"></a>Så här uppdaterar du hjälpen för moduler som inte är standard

Om du vill uppdatera eller spara hjälp för en modul som inte returneras av **ListAvailable** -parametern för `Get-Module` cmdleten importerar du modulen till den aktuella sessionen innan du kör ett `Update-Help` eller- `Save-Help` kommando. `Save-Help`Importera modulen till den aktuella sessionen eller `Invoke-Command` skript blocket som är anslutet till fjärrdatorn innan du kör kommandot på en fjärrdator.

När modulen är i den aktuella sessionen kör du `Update-Help` `Save-Help` cmdletarna eller utan parametrar eller använder parametern **module** för att ange modulnamnet.

**Modul** parametrarna för `Update-Help` `Save-Help` cmdletarna och accepterar bara ett modulnamn. De accepterar inte sökvägen till en modul-fil.

Använd den här metoden för att uppdatera eller spara hjälp för en modul som inte returneras av **ListAvailable** -parametern för `Get-Module` cmdleten, till exempel en modul som är installerad på en plats som inte finns med i `$env:PSModulePath` miljövariabeln, eller en modul som inte är korrekt formaterad (modulens katalog innehåller inte minst en fil vars basename är samma som katalog namnet).

## <a name="how-to-support-updatable-help"></a>Så här stöder du uppdaterings bar hjälp

Om du skapar en modul kan du använda onlinehjälp och uppdaterings bar hjälp för dina moduler. Mer information finns i [support uppdaterings bar hjälp](/powershell/scripting/developer/help/supporting-updatable-help) och [support online](/powershell/scripting/developer/module/supporting-online-help) i Microsoft docs.

Uppdaterings bar hjälp är inte tillgänglig för PowerShell-snapin-moduler eller kommenterings-baserad hjälp.

## <a name="remarks"></a>Kommentarer

`Update-Help` `Save-Help` Cmdletarna och stöds inte på Windows Preinstallation Environment (Windows PE).

## <a name="see-also"></a>Se även

[Get – hjälp](xref:Microsoft.PowerShell.Core.Get-Help)

[Spara – hjälp](xref:Microsoft.PowerShell.Core.Save-Help)

[Uppdatera – hjälp](xref:Microsoft.PowerShell.Core.Update-Help)
