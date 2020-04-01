---
ms.date: 08/23/2017
keywords: PowerShell, cmdlet
title: Använd den webbaserade Windows PowerShell-konsolen
ms.openlocfilehash: 29aa123049884004dd4e1a8f042783538d80abc6
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500872"
---
# <a name="use-the-web-based-windows-powershell-console"></a>Användning av den webbaserade Windows PowerShell-konsolen

Uppdaterad: 24 juni 2013

Gäller för: Windows Server 2012 R2, Windows Server 2012

Med Windows PowerShell-webbåtkomsten kan användarna logga in på en skyddad webbplats. för att kunna använda Windows PowerShell-sessioner,-cmdletar och-skript för att hantera en fjärrdator.

Eftersom Windows PowerShell-konsolen körs i en webbläsare, kan den öppnas från en mängd olika klient enheter. nästan alla enheter med en webbläsare fungerar.

Den webbaserade Windows PowerShell-konsolen riktas mot en fjärrdator som anges av användarna som en del av inloggnings processen.

I det här avsnittet beskrivs hur du loggar in på och börjar använda Windows PowerShell-webbbaserad konsol.

I det här avsnittet beskrivs inte hur du använder Windows PowerShell eller kör cmdletar eller skript. Information om hur du använder Windows PowerShell och skript resurser finns i avsnittet [Se även](#see-also) i slutet av det här avsnittet.

## <a name="supported-browsers-and-client-devices"></a>Webbläsare och klientenheter som stöds

Windows PowerShell-webbåtkomsten stöder följande webbläsare i Internet. Även om mobila webbläsare inte stöds officiellt, kan många kunna köra den webbaserade Windows PowerShell-konsolen. Andra webbläsare som accepterar cookies, kör JavaScript och kör HTTPS-webbplatser förväntas fungera, men är inte testade officiellt.

### <a name="supported-desktop-computer-browsers"></a>Datorwebbläsare som stöds

- Windows Internet Explorer för Microsoft Windows 8,0, 9,0, 10,0 och 11,0
- Mozilla Firefox-10.0.2
- Google Chrome 17.0.963.56 m för Windows
- Apple Safari 5.1.2 för Windows
- Apple Safari 5.1.2 för Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Minimalt testade mobila enheter eller webbläsare

- Windows Phone 7 och 7,5
- Google Android WebKit 3,1 Browser Android 2.2.1 (kernel 2,6)
- Apple Safari för iPhones operativsystem 5.0.1
- Operativ systemet Apple Safari för iPad 2 5.0.1

### <a name="browser-requirements"></a>Krav för webbläsare

Om du vill använda webb åtkomst till Windows PowerShell-webbbaserad konsol måste webbläsare göra följande.

- Tillåt cookies från webbplatsen för gateway för Windows PowerShell-webbåtkomst.
- Kunna öppna och läsa HTTPS-sidor.
- Öppna och köra webbplatser som använder JavaScript.

## <a name="signing-in-to-windows-powershell-web-access"></a>Logga in på Windows PowerShell Web Access

Din administratör för Windows PowerShell-webbåtkomsten bör ge dig en URL som är adressen till din organisations webbplats för Windows PowerShell-webbåtkomsten. Som standard är den här webbplats adressen `https://<server_name>/pswa`.

Innan du loggar in på Windows PowerShell-webbåtkomsten måste du kontrol lera att du har namnet eller IP-adressen för den fjärrdator som du vill hantera. Du måste vara en behörig användare på fjärrdatorn och den måste vara konfigurerad för att tillåta fjärrhantering. Mer information om hur du konfigurerar din dator för att tillåta fjärrhantering finns i [Aktivera och använda fjärrkommandon i Windows PowerShell](/powershell/module/microsoft.powershell.core/enable-psremoting).

Den enklaste metoden att konfigurera datorn för att tillåta fjärrhantering är att köra cmdleten `Enable-PSRemoting -force` på datorn, i en Windows PowerShell-session som har öppnats med utökade användar rättigheter (**Kör som administratör**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Så här loggar du in på Windows PowerShell Web Access

1. Öppna webbplatsen för Windows PowerShell-webbåtkomst i ett webbläsarfönster eller en flik i Internet.

1. På inloggnings sidan för Windows PowerShell-webbåtkomsten anger du ditt nätverks användar namn, lösen ord och namnet på den dator som du vill hantera (och där du är en auktoriserad användare). Om administratör för Windows PowerShell-webbåtkomsten har instruerat dig att använda en URI för en anpassad webbplats eller proxyserver i stället för ett dator namn väljer du **anslutnings-URI** i fältet **Anslutnings typ** och anger sedan URI.

   > [!NOTE]
   > - Om mål datorn finns i en arbets grupp använder du följande syntax för att ange ditt användar namn och logga in på datorn: `<workgroup_name>\<user_name>`
   > - Om mål datorn är Gateway-servern kan du ange `localhost` i fältet dator namn
   > - Om mål datorn är Gateway-servern och Gateway-servern finns i en arbets grupp måste du använda `<workgroup name>\<user_name>` i det arkiverade användar namnet. Du kan använda `localhost` i fältet dator namn.

1. Avsnittet **Valfria anslutningsinställningar** relaterar till behörighetskraven för den fjärrdator som du vill hantera. Mer information om de parametrar som motsvarar valfria anslutnings inställningar finns i hjälpen för cmdleten [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .

   Normalt är de autentiseringsuppgifter som du använder för att skicka genom Windows PowerShell-webbåtkomst-gatewayen samma som identifieras av den fjärrdator som du vill hantera. Men om du vill använda olika autentiseringsuppgifter för att hantera fjärrdatorn som du angav i steg 2, expanderar du avsnittet **Valfria anslutningsinställningar** och anger de alternativa autentiseringsuppgifterna. Annars går du till steg 6.

1. Om Windows PowerShell Web Access-administratören har skapat en anpassad sessionsnyckel för Windows PowerShell Web Access-användare skriver du namnet på sessionens konfigurations namn i fältet **konfigurations namn** . Mer information om sessionsinställningar finns [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Behåll **autentiseringstypen** inställd på **standard** om du inte har instruerats att göra det av Windows PowerShell-administratören för webb åtkomst.

1. Klicka på **Logga in**.

## <a name="signing-out-and-timing-out"></a>Logga ut och uppnådd tidsgräns

Något av följande loggar in dig från en webbaserad Windows PowerShell-session.

- När du klickar på **Logga ut** i det nedre högra hörnet av konsolen. (Endast Windows Server 2012)
- Klicka på **Spara** eller **Avsluta** i det nedre högra hörnet i konsolen (endast Windows Server 2012 R2). När du klickar på **Spara** sparas och stängs din Windows PowerShell-webbåtkomst-session. Du kan återansluta till sessionen senare. När du loggar in på Windows PowerShell-webbåtkomsten igen, visar Windows PowerShell-webbåtkomsten en lista över dina sparade sessioner. Du kan antingen välja och återansluta till en sparad session eller starta en ny session. Det maximala antalet öppna sessioner som användare tillåts ha, både sparade och aktiva, har konfigurerats av gateway-administratören.

  Om du klickar på **Stäng** loggas du ut från Windows PowerShell-webbåtkomsten utan att spara den.

- Om du försöker logga in för att hantera en annan fjärrdator i samma webbläsarsession eller i en ny flik i samma webbläsarsession. (Detta gäller inte om Gateway-servern kör Windows Server 2012 R2; Windows PowerShell-webbåtkomsten som körs på Windows Server 2012 R2 tillåter flera användarsessioner på nya flikar i samma webbläsarsession.) Mer information om hur du använder mer än en aktiv session på samma dator finns i avsnittet ansluta till flera mål datorer samtidigt i [begränsningarna i den webbaserade konsolen](#limitations-of-the-web-based-console) i det här avsnittet.

- 20 minuters inaktivitet i sessionen. Gateway-administratören kan anpassa tids gränsen för inaktivitet; Mer information finns i [hantering av sessioner](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

  - Om du är frånkopplad från en-session i den webbaserade konsolen på grund av ett nätverks fel eller en annan oplanerad avstängning eller fel, och inte eftersom du har stängt sessionen själv, fortsätter Windows PowerShell-webbåtkomsten att köras, ansluten till målet datorn tills timeout-tiden på klient sidan går ut. Denna tidsgräns är som standard är 20 minuter och har konfigurerats av gateway-administratören. Sessionen kopplas från när antingen standardvärdet 20 minuter eller den tidsperiod som angetts av gateway-administratören uppnås, beroende på vilken som är kortast.

    Om Gateway-servern kör Windows Server 2012 R2 gör Windows PowerShell-webbåtkomsten att användarna återansluter till sparade sessioner vid ett senare tillfälle, men du kan inte se eller återansluta till sparade sessioner förrän tids gränsen som angetts av Gateway-administratören har uppnåtts.

- Stänga webbläsarfönster eller flikar.

- Stäng av klientenheten där webbläsaren körs eller koppla bort den från nätverket.

- Kör kommandot **Avsluta** i webbkonsolen. Det här kommandot fungerar inte om den sessionsinformation som du är ansluten till har kon figurer ATS för att stöda i läget [nolanguage](/dotnet/api/system.management.automation.pslanguagemode) eller i en begränsad körnings utrymme.

Om du vill logga in igen öppnar du webb sidan för Windows PowerShell-webbåtkomsten igen och loggar in genom att följa anvisningarna i [Logga in på Windows PowerShell-webbåtkomst](#signing-in-to-windows-powershell-web-access) i den här artikeln.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Skillnader i den webbaserade Windows PowerShell-konsolen

När du har loggat in på Windows PowerShell-webbåtkomst öppnas en webbaserad Windows PowerShell-konsol i webbläsarens fönster eller flik. Eftersom konsolen är ansluten till den fjärrdator som du angav under inloggnings processen, kan endast de Windows PowerShell-cmdletar eller skript som är tillgängliga på fjärrdatorn användas i-konsolen. I det här avsnittet beskrivs andra begränsningar i Windows PowerShell-webbåtkomst konsoler och skillnader mellan Windows PowerShell-konsoler för webb åtkomst och den installerade **PowerShell. exe** -konsolen.

### <a name="functional-disparity-with-powershellexe"></a>Funktionella skillnader med PowerShell.exe

Majoriteten av funktionerna i Windows PowerShell-värden finns i den webbaserade Windows PowerShell-konsolen, men det finns vissa funktioner som inte är tillgängliga.

- Kapslade förloppet visas.

  Windows PowerShell-webbåtkomsten visar ett förlopps gränssnitt för cmdlets som rapporterar förlopp, men endast information om förloppet på den översta nivån visas.

- Ändring av indatafärg.

  Indatafärgen (både förgrund och bakgrund) går inte att ändra. Utdatastilen för varningar, utförligt läge och felmeddelanden går att ändra genom att köra ett skript.

- PSHostRawUserInterface.

  Windows PowerShell-webbåtkomst implementeras via fjärrhantering i Windows PowerShell och använder en fjärran sluten körnings utrymme. Windows PowerShell-webbåtkomsten implementerar inte vissa metoder i det här gränssnittet. till exempel alla kommandon som skriver till Windows-konsolen. Kommandon som **PowerTab** fungerar inte i Windows PowerShell-webbåtkomst.

- Funktions tangenter.

  Windows PowerShell-webbåtkomsten har inte stöd för vissa funktions nycklar, i många fall eftersom kommandona är reserverade av webbläsaren.

### <a name="unsupported-shortcut-keys"></a>Kortkommandon som inte stöds

 Funktions nyckel   |                                                                                         Åtgärd
--------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
CTRL + C          | I Windows PowerShell-webbåtkomsten används **CTRL + C** av webbläsaren för att kopiera innehåll. Konsolen har en **Avbryt**-knapp och användarna kan även använda **Ctrl+Q** för att avbryta kommandon.
Alt-mellanslag, e, l | Bläddrar genom skärmbufferten
Alt+mellanslag, e, f | Söker efter text i skärmbufferten
Alt+mellanslag, e, k | Markerar text som ska kopieras från skärmbufferten
Alt+mellanslag, e, p | Klistra in innehållet i Urklipp i Windows PowerShell-konsolen
Alt+mellanslag, c    | Stäng Windows PowerShell-konsolen
Ctrl+Break      | Tvinga Windows PowerShell-fönstret att stängas
Ctrl+Home       | Raderar från början av den aktuella kommandoraden
Ctrl+End        | Raderar till slutet av kommandoraden
F1              | Flyttar markören ett tecken till höger på kommandoraden
Ändras              | Skapar ett nytt kommando genom att kopiera ditt senaste kommando upp till det tecken som du skriver
F3              | Slutför kommandoraden med innehåll från din senaste kommandorad
F4              | Tar bort tecken från markörens position
F5              | Söker bakåt genom kommandohistoriken. Om du vill komma åt kommandon i kommando historiken i Windows PowerShell-webbåtkomsten klickar du på rullnings knapparna **Historik** i den webbaserade konsolen.
F7              | Väljer ett kommando interaktivt från kommandohistoriken
F8              | Skanningshistoriken visar kommandon som matchar aktuell text
Höj              | Kör ett visst numrerat kommando från historiken
PGUP         | Kör det första kommandot i historiken
PGDN       | Kör det sista kommandot i historiken
Alt+F7          | Rensar listan med kommandohistorik

### <a name="limitations-of-the-web-based-console"></a>Begränsningar i den webbaserade konsolen

- Dubbla hopp

  Om du försöker skapa eller arbeta i en ny session med hjälp av Windows PowerShell-webbåtkomsten kan du stöta på en begränsning av dubbel hopp (eller ansluta till en andra dator från den första anslutningen).
  Windows PowerShell-webbåtkomsten använder en fjärran sluten körnings utrymme, och för närvarande stöder inte **PowerShell. exe** etablering av en fjärr anslutning till en andra dator från en fjärran sluten körnings utrymme. Om du försöker ansluta till en andra fjärrdator från en befintlig anslutning med hjälp av cmdleten **Enter-PSSession** kan du till exempel få olika fel, till exempel &euro;œCannot Hämta nätverks resurser.

  För att undvika fel med dubbla hopp bör administratören konfigurera CredSSP-autentisering i organisationens nätverks miljö. Mer information om hur du konfigurerar CredSSP-autentisering finns i [CredSSP för fjärr kommunikation med andra hopp](https://devblogs.microsoft.com/powershell/credssp-for-second-hop-remoting/) i PowerShell-bloggen. Du kan också ange explicita autentiseringsuppgifter när du vill hantera en andra fjärrdator. Implicita autentiseringsuppgifter kommer troligen inte att tillåta ett andra hopp.

- Tjänst

  Windows PowerShell-webbåtkomsten använder och har samma begränsningar som en fjärran sluten Windows PowerShell-session. Kommandon som direkt anropar Windows-konsolens API:er, till exempel för konsolbaserade redigerare eller textbaserade menyprogram, fungerar inte eftersom kommandona inte kan läsas eller skrivas till standardindata, utdata och fel-pipes. Därför fungerar inte kommandon som startar en körbar fil, t. ex **. Notepad. exe**eller visa ett grafiskt användar gränssnitt, till exempel `OpenGridView` eller `ogv`. Din upplevelse påverkas av detta beteende. till dig visas det att Windows PowerShell-webbåtkomsten inte svarar på ditt kommando.

- Slut för ande flik

  TABB-slutförande fungerar inte i en sessionshantering med en begränsad körnings utrymme eller en som är i läget **nolanguage** . Även om administratörer kan konfigurera en session att stödja flikavslutande, rekommenderas det inte av säkerhetsskäl eftersom det kan exponera följande information för obehöriga användare.

  - Interna sökvägar till systemfiler
  - Delade mappar på interna datorer
  - Variabler i körningsutrymmet
  - Inlästa typer eller .NET Framework-namnområden
  - Miljövariabler

- **Nolanguage** -session, eller begränsat körnings utrymme

  Användare som är inloggade på en konfiguration av en **Nolanguage** -session eller en begränsad körnings utrymme i Windows PowerShell-webbåtkomsten kan inte köra **exit** -kommandot för att avsluta sessionen. För att logga ut måste användarna klicka på **Logga ut** på konsolsidan.

- Ansluta till flera måldatorer samtidigt.

  Om Gateway-servern kör Windows Server 2012 tillåter Windows PowerShell-webbåtkomsten bara en fjärran sluten dator anslutning per webbläsarsession. den tillåter inte att användare loggar in en gång och ansluter till flera fjärrdatorer genom att använda separata flikar i webbläsaren. När du öppnar en ny flik eller ett nytt webbläsarfönster, begär Windows PowerShell-webbåtkomsten att du kopplar från den aktuella sessionen och startar en ny session, så att du kan ansluta till den nya (eller samma) fjärrdatorn. Om två eller flera separata sessioner till olika fjärrdatorer önskas, kan du använda en funktion i Internet Explorer för att skapa en ny session. Starta en ny webbläsarsession i Internet Explorer genom att trycka på **Alt**, öppna menyn **Arkiv** och välja **ny session**. Öppna sedan webbplatsen för Windows PowerShell-webbåtkomsten i den nya sessionen och logga in för att få åtkomst till en annan fjärran sluten dator.

  När gatewayen för Windows PowerShell-webbåtkomsten körs på Windows Server 2012 R2 kan användare öppna flera anslutningar till fjärrdatorer på olika flikar i webbläsaren. Om du vill öppna fler än en anslutning till en fjärrdator med hjälp av den webbaserade Windows PowerShell-konsolen, kontrollerar du om den här funktionen stöds av Gateway-servern med hjälp av Windows PowerShell-webbåtkomsten Gateway-administratören.

- Beständiga Windows PowerShell-sessioner (åter anslutning).

  När du har nått tids gränsen för Windows PowerShell-webbåtkomsten stängs fjärr anslutningen mellan gatewayen och mål datorn. Detta stoppar alla cmdletar eller skript som för närvarande används. Du uppmanas att använda Windows PowerShell **-jobb-** infrastrukturen när du utför långvariga uppgifter, så att du kan starta jobb, koppla från datorn, återansluta senare och låta jobben vara kvar. En annan fördel med cmdletar för att använda **-jobb** är att du kan starta dem med hjälp av Windows PowerShell-webbåtkomst, logga ut och sedan återansluta senare, antingen genom att köra Windows PowerShell-webbåtkomst eller en annan värd (till exempel Windows PowerShell ISE (Integrated Scripting Environment)).

- Ändra storlek på konsolen.

  Konsolfönstret **PowerShell.exe** kan ändras i storlek på följande tre sätt.

  - Dra och justera storleken på konsolfönstret med musen
  - Ändra höjd- och breddegenskaperna med ett grafiskt användargränssnitt för konsolegenskaper
  - Ändra höjden och bredden på konsolfönstren med en cmdlet

    Konsol fönstret för Windows PowerShell-webbåtkomsten kan konfigureras med hjälp av cmdletarna på följande sätt. I följande exempel ändrar en användare bredden på Windows PowerShell-konsolen för webb åtkomst till **20**.

    ```powershell
    $newSize = $Host.UI.RawUI.WindowSize
    $newSize.Width = $newSize.Width - 20
    $oldSize = $Host.UI.RawUI.WindowSize
    $Host.UI.RawUI.WindowSize = $newSize
    ```

    Du kan ändra höjden på konsolen på ett liknande sätt.

    Ytterligare exempel för att anpassa konsol visningen finns i [Windows PowerShell-teamets blogg](h https://devblogs.microsoft.com/powershell).

## <a name="see-also"></a>Se även

- [Hej, Scripting Guy!](https://devblogs.microsoft.com/scripting/)
- [PowerShell-teamets blogg](https://devblogs.microsoft.com/powershell/)