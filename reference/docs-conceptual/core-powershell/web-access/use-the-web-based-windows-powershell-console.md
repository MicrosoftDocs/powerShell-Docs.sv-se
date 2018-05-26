---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: använda web baserat windows powershell-konsolen
ms.openlocfilehash: 5d29a6f97fddf4b329fcc7097cf7d40d47d22cca
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/25/2018
---
# <a name="use-the-web-based-windows-powershell-console"></a>Användning av den webbaserade Windows PowerShell-konsolen

Uppdaterad: Juni 24 2013

Gäller för: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web Access kan användarna logga in på en säker webbplats; för att kunna använda Windows PowerShell-sessioner, cmdletar och skript för att hantera en fjärrdator.

Eftersom Windows PowerShell-konsolen körs i en webbläsare, kan du öppna från en mängd olika klientenheter; nästan alla enheter med en webbläsare fungerar.

Den webbaserade Windows PowerShell-konsolen är inriktad på en fjärrdator som anges av användare som en del av processen för inloggning.

Det här avsnittet beskriver hur du logga in och börja använda Windows PowerShell Web Access webbaserade konsolen.

Det här avsnittet beskriver inte hur du använder Windows PowerShell eller kör cmdletar eller skript.
Information om hur du använder Windows PowerShell och scripting resurser finns i [finns också](#see-also) avsnittet i slutet av det här avsnittet.

## <a name="supported-browsers-and-client-devices"></a>Webbläsare och klientenheter som stöds

Windows PowerShell Web Access har stöd för följande webbläsare.
Även om mobila webbläsare inte stöds officiellt, kan många kanske köra den webbaserade Windows PowerShell-konsolen.
Andra webbläsare som accepterar cookies, kör JavaScript och kör HTTPS-webbplatser förväntas fungera, men är inte testade officiellt.

### <a name="supported-desktop-computer-browsers"></a>Datorwebbläsare som stöds

- Windows Internet Explorer för Microsoft Windows 8.0, 9.0, 10.0 och 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m för Windows
- Apple Safari 5.1.2 för Windows
- Apple Safari 5.1.2 för Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Minimalt testade mobila enheter eller webbläsare

- Windows Phone 7 och 7.5
- Google Android WebKit 3.1, webbläsaren Android 2.2.1 (Kernel 2.6)
- Apple Safari för iPhones operativsystem 5.0.1
- Apple Safari för iPad 2-operativsystem 5.0.1

### <a name="browser-requirements"></a>Krav på webbläsare

Webbläsare måste göra följande för att använda Windows PowerShell Web Access webbaserade konsolen.

- Tillåt cookies från gateway-webbplatsen för Windows PowerShell Web Access.
- Kunna öppna och läsa HTTPS-sidor.
- Öppna och köra webbplatser som använder JavaScript.

## <a name="signing-in-to-windows-powershell-web-access"></a>Logga in på Windows PowerShell Web Access

Windows PowerShell Web Access-administratör ger dig en URL som är adressen till webbplatsen organisationer Windows PowerShell Web Access gateway.
Som standard är webbplatsadressen *https://\<server_name\>/pswa*.

Innan du loggar in på Windows PowerShell Web Access, bör du se till att namnet eller IP-adressen för den fjärrdator som du vill hantera.
Du måste vara en behörig användare på fjärrdatorn och den måste vara konfigurerad för att tillåta fjärrhantering.
Mer information om hur du konfigurerar din dator för att tillåta fjärrhantering finns [aktivera och använda fjärrkommandon i Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting).

Det enklaste sättet att konfigurera datorn för att tillåta fjärrhantering är att köra den **Enable-PSRemoting - force** på datorn i en Windows PowerShell-session som har öppnats med utökade användarrättigheter (**Kör som administratör**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Så här loggar du in på Windows PowerShell Web Access

1. Öppna Windows PowerShell Web Access-webbplatsen i ett webbläsarfönster eller flik.

1. Ange ditt nätverksanvändarnamn, lösenord och namnet på den dator som du vill hantera (och där du är en auktoriserad användare) på sidan Windows PowerShell Web Access-inloggning. Om Windows PowerShell Web Access-administratören har instruerat dig att använda en URI för en anpassad webbplats eller proxyserver i stället för namnet på en dator, väljer **anslutnings-URI** i den **anslutningstypen** fältet och sedan Ange URI: N.

    > ![Obs](images/Note.jpeg) **Observera**:
    >
    > - Om måldatorn är i en arbetsgrupp, Använd följande syntax för att ange ditt användarnamn och logga in på datorn: `<workgroup_name>\<user_name>`
    > - Om måldatorn är gateway-servern, kan du ange `localhost` i fältet för datornamn
    > - Om måldatorn är gateway-servern och gateway-servern finns i en arbetsgrupp, måste du använda `<workgroup name>\<user_name>` i användarnamn arkiverats. Du kan använda `localhost` i fältet för datornamn.

1. Den **valfria anslutningsinställningar** relaterar till behörighetskraven för den fjärrdator som du vill hantera. Mer information om de parametrar som motsvarar valfria anslutningsinställningar finns i [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet-hjälpen.

    De autentiseringsuppgifter du använder för att skicka via Windows PowerShell Web Access-gateway är vanligtvis samma som identifieras av den fjärrdator som du vill hantera. Om du vill använda andra autentiseringsuppgifter för att hantera fjärrdatorn som du angav i steg 2, expandera den **valfria anslutningsinställningar** och anger alternativa autentiseringsuppgifter. Annars går du till steg 6.

1. Om Windows PowerShell Web Access-administratören har skapat en anpassad sessionskonfiguration för Windows PowerShell Web Access-användare, skriver du namnet på Konfigurationsnamnet session i den **Konfigurationsnamnet** fältet. Mer information om sessionskonfigurationer finns [about_Session_Configurations](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Behåll den **autentiseringstyp** inställd på **standard** om du har fått instruktioner att göra något annat av Windows PowerShell Web Access-administratör.

1. Klicka på **logga in**.

## <a name="signing-out-and-timing-out"></a>Logga ut och uppnådd tidsgräns

Något av följande loggar du ut från webbaserade Windows PowerShell-sessionen.

- Klicka på **logga ut** i det nedre högra hörnet av konsolen. (Endast Windows Server 2012)

- Klicka på **spara** eller **avsluta** i det nedre högra hörnet av konsolen (endast Windows Server 2012 R2). Klicka på **spara** sparar och stänger Windows PowerShell Web Access sessionen; du kan återansluta till sessionen senare. När du loggar in på Windows PowerShell Web Access igen, visar Windows PowerShell Web Access en lista över dina sparade sessioner. Du kan välja och ansluta till en sparad session eller starta en ny session. Det maximala antalet öppna sessioner som användare tillåts ha, både sparade och aktiva, har konfigurerats av gateway-administratören.

    Klicka på **avsluta** loggar du ut från Windows PowerShell Web Access-sessionen utan att spara den.

- Om du försöker logga in för att hantera en annan fjärrdator i samma webbläsarsession eller i en ny flik i samma webbläsarsession. (Detta gäller inte om gateway-servern kör Windows Server 2012 R2 Windows PowerShell Web Access körs på Windows Server 2012 R2 tillåter att flera användarsessioner på nya flikar i samma webbläsarsession.) Mer information om hur du använder flera aktiva sessioner på samma dator finns i ansluta till flera måldatorer samtidigt i den [begränsningar i den webbaserade konsolen](#limitations-of-the-web-based-console) i det här avsnittet.

- 20 minuters inaktivitet i sessionen. Gateway-administratören kan anpassa tidsgränsen för inaktivitet; Mer information finns i [sessionshantering](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Om du är frånkopplad från en session i den webbaserade konsolen på grund av ett nätverksfel eller andra oplanerade avstängningar eller fel och inte eftersom du har stängt sessionen anslutna själv, Windows PowerShell Web Access sessionen fortsätter att köras, till målet dator tills tidsgränsen på klientsidan uppnås. Denna tidsgräns är som standard är 20 minuter och har konfigurerats av gateway-administratören. Sessionen kopplas från när antingen standardvärdet 20 minuter eller den tidsperiod som angetts av gateway-administratören uppnås, beroende på vilken som är kortast.

        Om gateway-servern kör Windows Server 2012 R2, Windows PowerShell Web Access kan användarna återansluta till sparade sessioner vid ett senare tillfälle, men du kan inte se eller återansluta till sparade sessioner förrän efter tidsgränsen som angetts av gateway-administratören har upphörde att gälla.

- Stänga webbläsarfönster eller flikar.

- Stäng av klientenheten där webbläsaren körs eller koppla bort den från nätverket.

- Kör den **avsluta** i webbkonsolen. Det här kommandot fungerar inte om sessionskonfigurationen som du är ansluten till är konfigurerad för att stödja [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) läge, eller är i ett begränsat körningsutrymme.

Om du vill logga in igen, öppnar du Windows PowerShell Web Access-webbsidan igen och logga in genom att följa stegen i [inloggning till Windows PowerShell Web Access](#signing-in-to-windows-powershell-web-access) i det här avsnittet.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Skillnader i den webbaserade Windows PowerShell-konsolen

När du loggar in på Windows PowerShell Web Access, öppnas en webbaserad Windows PowerShell-konsol i ditt webbläsarfönster eller flik. Eftersom konsolen är ansluten till den fjärrdator som du angav när du loggar in kan kan endast de Windows PowerShell-cmdletar eller skript som är tillgängliga på fjärrdatorn användas i konsolen. Det här avsnittet beskrivs andra begränsningar i Windows PowerShell Web Access-konsoler och skillnader mellan Windows PowerShell Web Access-konsoler och den installerade **PowerShell.exe** konsolen.

### <a name="functional-disparity-with-powershellexe"></a>Funktionella skillnader med PowerShell.exe

Flesta funktioner i Windows PowerShell-värden är tillgänglig i Windows PowerShell Web Access webbaserade konsolen, men det finns vissa funktioner som inte är tillgängliga.

- Kapslade förloppet visas.

  Windows PowerShell Web Access visar en förlopps-GUI för cmdletar för att rapportera förlopp, men endast på den översta nivån statusinformation visas.

- Ändring av indatafärg.

  Indatafärgen (både förgrund och bakgrund) går inte att ändra. Utdatastilen för varningar, utförligt läge och felmeddelanden går att ändra genom att köra ett skript.

- PSHostRawUserInterface.

  Windows PowerShell Web Access implementeras via Windows PowerShell-fjärrhantering och använder ett fjärrkörningsutrymme. Windows PowerShell Web Access implementerar inte några metoder i det här gränssnittet. exempelvis de kommandon som skriver till Windows-konsolen. Kommandon som t.ex **PowerTab** fungerar inte i Windows PowerShell Web Access.

- Funktionstangenter.

  Windows PowerShell Web Access stöder inte vissa funktionstangenter i många fall eftersom kommandon som är reserverade av webbläsaren.

### <a name="unsupported-shortcut-keys"></a>Kortkommandon som inte stöds

Funktionen nyckel | Åtgärd
-- | --
Ctrl+C | I Windows PowerShell Web Access **Ctrl + C** används av webbläsaren för att kopiera innehållet. Konsolen har en **Avbryt** knapp och användarna kan också använda **Ctrl + Q** att avbryta kommandon.
Alt-mellanslag, e, l | Bläddrar genom skärmbufferten
Alt+mellanslag, e, f | Söker efter text i skärmbufferten
Alt+mellanslag, e, k | Markerar text som ska kopieras från skärmbufferten
Alt+mellanslag, e, p | Klistra in innehållet i Urklipp i Windows PowerShell-konsolen
Alt+mellanslag, c | Stäng Windows PowerShell-konsolen
Ctrl+Break | Tvinga Windows PowerShell-fönstret stängs
Ctrl+Home | Raderar från början av den aktuella kommandoraden
Ctrl+End | Raderar till slutet av kommandoraden
F1 | Flyttar markören ett tecken till höger på kommandoraden
F2 | Skapar ett nytt kommando genom att kopiera ditt senaste kommando upp till det tecken som du skriver
F3 | Slutför kommandoraden med innehåll från din senaste kommandorad
F4 | Tar bort tecken från markörens position
F5 | Söker bakåt genom kommandohistoriken. Om du vill få åtkomst till kommandon i kommandohistoriken i Windows PowerShell Web Access, klickar du på den **historik** Rulla knappar i den webbaserade konsolen.
F7 | Väljer ett kommando interaktivt från kommandohistoriken
F8 | Skanningshistoriken visar kommandon som matchar aktuell text
F9 | Kör ett visst numrerat kommando från historiken
Page Up | Kör det första kommandot i historiken
Page Down | Kör det sista kommandot i historiken
Alt+F7 | Rensar listan med kommandohistorik

### <a name="limitations-of-the-web-based-console"></a>Begränsningar i den webbaserade konsolen

- Dubbelhopp

    Du kan stöta på i dubbelhopp (eller anslutning till en annan dator från den första anslutningen) begränsningen om du försöker skapa eller arbeta i en ny session med hjälp av Windows PowerShell Web Access. Windows PowerShell Web Access använder ett fjärrstyrt körningsutrymme och för närvarande **PowerShell.exe** stöder inte upprätta en fjärranslutning till en annan dator från ett fjärrkörningsutrymme. Om du försöker ansluta till en andra fjärrdator från en befintlig anslutning med hjälp av den **Enter-PSSession** cmdlet, till exempel kan du olika fel, såsom €modulens hämta nätverksresurser.

    För att undvika dubbelhoppfel bör administratören konfigurera CredSSP-autentisering i nätverksmiljön organisationer. Mer information om hur du konfigurerar CredSSP-autentisering finns [CredSSP för fjärrkommunikation med andra hopp](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) på Microsofts webbplats. Du kan också ange explicita autentiseringsuppgifter när du vill hantera en andra fjärrdator. Implicita autentiseringsuppgifter kommer troligen inte att tillåta ett andra hopp.

- Fjärrkommunikation

    Windows PowerShell Web Access använder och har samma begränsningar som en Windows PowerShell-fjärrsession. Kommandon som direkt anropar Windows-konsolens API:er, till exempel för konsolbaserade redigerare eller textbaserade menyprogram, fungerar inte eftersom kommandona inte kan läsas eller skrivas till standardindata, utdata och fel-pipes. Därför kommandon som startar en körbar fil, som **notepad.exe**, eller visar ett Grafiskt som `OpenGridView` eller `ogv`, fungerar inte. Din upplevelse påverkas av problemet; för dig visas det att Windows PowerShell Web Access inte svarar på kommandot.

- Flikavslutande

    Flikavslutande fungerar inte i en sessionskonfiguration med ett begränsat körningsutrymme eller någon som är i **NoLanguage** läge. Även om administratörer kan konfigurera en session att stödja flikavslutande, rekommenderas det inte av säkerhetsskäl eftersom det kan exponera följande information för obehöriga användare.

    - Interna sökvägar till systemfiler

    - Delade mappar på interna datorer

    - Variabler i körningsutrymmet

    - Inlästa typer eller .NET Framework-namnområden

    - Miljövariabler

- **NoLanguage** session eller ett begränsat körningsutrymme

    Användare som loggar in på en **NoLanguage** sessionskonfiguration eller ett begränsat körningsutrymme i Windows PowerShell Web Access kan inte köra den **avsluta** kommando för att avsluta sessionen. Om du vill logga ut användaren klicka på **logga ut** på konsolsidan.

- Ansluta till flera måldatorer samtidigt.

    Om gateway-servern kör Windows Server 2012, kan Windows PowerShell Web Access endast en fjärrdatoranslutning per webbläsarsession. Det tillåter inte användare att logga in en gång och ansluta till flera fjärrdatorer med hjälp av separata flikar i webbläsaren. När du öppnar en ny flik eller ett nytt fönster i webbläsaren, Windows PowerShell Web Access uppmanar dig att koppla från den aktuella sessionen och starta en ny session, så att du kan ansluta till den nya (eller samma) fjärrdator. Om två eller flera separata sessioner till olika fjärrdatorer önskas, men kan en funktion i Internet Explorer du skapa en ny session. Du kan börja en ny webbläsarsession i Internet Explorer **ALT**öppnar den **filen** -menyn och välj sedan **ny Session**. Sedan öppna Windows PowerShell Web Access-webbplatsen i den nya sessionen och logga in att få åtkomst till en annan fjärrdator.

    När Windows PowerShell Web Access-gateway körs på Windows Server 2012 R2 kan användarna öppna flera anslutningar till fjärrdatorer i olika webbläsarflikar. Om du vill öppna fler än en anslutning till en fjärrdator med hjälp av den webbaserade Windows PowerShell-konsolen, kontrollera med Windows PowerShell Web Access gateway-administratören att se om den här funktionen stöds av gateway-servern.

- Beständiga Windows PowerShell-sessioner (återanslutning).

    När du timeout för Windows PowerShell Web Access-gateway, är fjärranslutningen mellan gatewayen och måldatorn stängd. Detta stoppar alla cmdletar eller skript som för närvarande används. Du uppmanas att använda Windows PowerShell **-jobbet** infrastruktur när du utför tidskrävande uppgifter så att du kan starta jobb, koppla från datorn, återansluta senare och ha jobben kvar. En annan fördel med **-jobbet** cmdletar är att du kan starta dem med hjälp av Windows PowerShell Web Access, logga ut och sedan återansluta senare, genom att köra Windows PowerShell Web Access eller en annan värd (till exempel Windows PowerShell Integrerad skriptmiljö (ISE)).

- Ändra storlek på konsolen.

    Den **PowerShell.exe** konsolfönstret storlek kan ändras i följande tre sätt.

    - Dra och justera storleken på konsolfönstret med musen

    - Ändra höjd- och breddegenskaperna med ett grafiskt användargränssnitt för konsolegenskaper

    - Ändra höjden och bredden på konsolfönstren med en cmdlet

        Konsolfönstret för Windows PowerShell Web Access kan konfigureras med hjälp av cmdlets på följande sätt. I följande exempel visas en användare ändrar bredd i administratörskonsolen för Windows PowerShell Web Access att **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        Du kan ändra höjden på konsolen på ett liknande sätt.

        Ytterligare exempel för att anpassa konsolvyn finns i den [Windows PowerShell-teamets blogg](http://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Se även

- [Windows PowerShell-Cmdlet-referens](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Windows PowerShell på Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
- [Skriptcenterdatabasen](http://gallery.technet.microsoft.com/scriptcenter)
- [Skriptcenter – Se hit, skriptdoktorn!](https://technet.microsoft.com/scriptcenter)
- [Windows PowerShell-teamets blogg](http://blogs.msdn.com/b/powershell/)