---
ms.date: 08/23/2017
keywords: PowerShell cmdlet
title: Installera och använda windows powershell-webbåtkomst
ms.openlocfilehash: d60670954d6ab6998e905382383d60ead1129d31
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893764"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Installera och använda Windows PowerShell-webbåtkomst

Uppdaterad: November 5 2013 (redigeras: 23 augusti 2017)

Gäller för: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Introduktion

Windows PowerShell Web Access som först introducerades i Windows Server 2012, som fungerar som en Windows PowerShell-gateway, att tillhandahålla en webbaserad Windows PowerShell-konsol som är inriktad på en fjärrdator. Det gör att IT-proffs att köra Windows PowerShell-kommandon och skript från en Windows PowerShell-konsol i en webbläsare, utan Windows PowerShell, fjärrhanteringsprogramvara eller webbläsare plugin-programmet installeras på klientenheten. Allt som krävs för att köra den webbaserade Windows PowerShell-konsolen är en korrekt konfigurerad Windows PowerShell Web Access-gateway och en webbläsare som stöder JavaScript och accepterar cookies.

Exempel på klientenheter är bärbara datorer, datorer i hemmet, lånade datorer, tablet-datorer, webbkiosker, datorer som inte kör ett Windows-baserat operativsystem och webbläsare i mobiltelefoner. IT-proffs kan utföra kritiska hanteringsuppgifter på Windows-baserade fjärrservrar från enheter som har tillgång till en Internetanslutning och en webbläsare.

När du har rätt gateway-konfiguration, kan användare komma åt en Windows PowerShell-konsol med hjälp av en webbläsare. När användarna öppnar den skyddade Windows PowerShell Web Access-webbplatsen, kan de köra en webbaserad Windows PowerShell-konsol efter en lyckad autentisering.

Windows PowerShell-webbåtkomst installation och konfiguration är en process i tre steg:

1. [Installera Windows PowerShell-webbåtkomst](#install-windows-powershell-web-access)
1. [Konfigurera gatewayen](#configure-the-gateway)
1. [Konfigurera en regel för begränsad auktorisering](#configure-a-restrictive-authorization-rule)

Innan du installerar och konfigurerar Windows PowerShell Web Access, rekommenderar vi att du läser handboken hela som innehåller instruktioner om hur du installerar, säkerställer och avinstallerar Windows PowerShell Web Access.
Den [använda webbaserade Windows PowerShell-konsolen](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) avsnittet beskriver hur användare loggar in på den webbaserade konsolen och omfattar begränsningar och skillnader mellan den webbaserade Windows PowerShell-konsolen och  **PowerShell.exe** konsolen. Användare av den webbaserade konsolen bör läsa [användning av webbaserade baserat Windows PowerShell-konsolen](use-the-web-based-windows-powershell-console.md), men behöver inte läsa resten av den här guiden.

Det här avsnittet ger inte djupgående vägledning för IIS-webbserver-åtgärder. endast de steg som krävs för att konfigurera Windows PowerShell Web Access-gatewayen beskrivs i det här avsnittet. Mer information om hur du konfigurerar och säkrar webbplatser i IIS finns i IIS-dokumentationsresurserna i avsnittet Se även.

Följande diagram visar hur Windows PowerShell-webbåtkomst fungerar.

![Diagram för Windows PowerShell Web Access](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Krav för att köra Windows PowerShell-webbåtkomst

Windows PowerShell-webbåtkomst kräver webbserver (IIS), .NET Framework 4.5 och Windows PowerShell 3.0 eller Windows PowerShell 4.0 körs på servern som du vill köra gatewayen. Du kan installera Windows PowerShell-webbåtkomst på en server som kör Windows Server 2012 R2 eller Windows Server 2012 med hjälp av antingen Lägg till roller och funktioner som guiden i Serverhanteraren eller Windows PowerShell-cmdletarna för distribution för Serverhanteraren. När du installerar Windows PowerShell-webbåtkomst med hjälp av Serverhanteraren eller dess distributionscmdletar, läggs nödvändiga roller och funktioner automatiskt som en del av installationen.

Windows PowerShell Web Access kan fjärranslutna användare för åtkomst till datorer i organisationen med hjälp av Windows PowerShell i en webbläsare. Även om Windows PowerShell-webbåtkomst är ett praktiskt och kraftfullt hanteringsverktyg, webbaserad åtkomst säkerhetsrisk och bör konfigureras så säkert som möjligt. Vi rekommenderar att administratörer som konfigurerar Windows PowerShell Web Access-gatewayen använder tillgängliga säkerhetsskikt, både i cmdlet-baserade auktoriseringsregler som ingår i Windows PowerShell-webbåtkomst och säkerhet lager som är tillgängliga i webbserver ( IIS) och program från tredje part. Den här dokumentationen innehåller både oskyddade exempel som rekommenderas bara för testmiljöer och exempel som rekommenderas för säker distribution.

## <a name="browser-and-client-device-support"></a>Stöd för webbläsare och klientenheter

Windows PowerShell Web Access har stöd för följande webbläsare.
Även om mobila webbläsare inte stöds officiellt, kan många kanske köra den webbaserade Windows PowerShell-konsolen. Andra webbläsare som accepterar cookies, kör JavaScript och kör HTTPS-webbplatser förväntas fungera, men är inte testade officiellt.

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

För att använda Windows PowerShell-webbåtkomst webbaserade konsolen måste kunna webbläsaren göra följande.

- Tillåt cookies från gateway-webbplatsen för Windows PowerShell Web Access.
- Kunna öppna och läsa HTTPS-sidor.
- Öppna och köra webbplatser som använder JavaScript.

## <a name="recommended-quick-deployment"></a>Rekommenderade snabb distribution

Du kan installera Windows PowerShell Web Access-gatewayen på en server som kör Windows Server 2012 R2 eller Windows Server 2012 med antingen Windows PowerShell-cmdlets eller genom att använda Lägg till roller och funktioner som guiden som öppnas från i Server Manager. Använda Windows PowerShell-cmdletar för snabb installation och konfiguration, enligt beskrivningen i det här avsnittet.

1. [Installera Windows PowerShell-webbåtkomst](#install-Windows-powershell-web-access)
1. [Konfigurera gatewayen](#configure-the-gateway)
1. [Konfigurera en regel för begränsad auktorisering](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>Installera Windows PowerShell-webbåtkomst med hjälp av PowerShell-cmdletar

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Så här installerar du Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdletar

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter.
   - Högerklicka på Windows-skrivbordet **Windows PowerShell** Aktivitetsfältet och klickar sedan på **Kör som administratör**.
   - På Windows **starta** högerklickar **Windows PowerShell**, och klicka sedan på **kör som administratör**.

   > **![Obs](images/note.jpeg) Obs** i Windows PowerShell 3.0 och 4.0 finns behöver du inte importera serverhanterar-modulen i Windows PowerShell-sessionen innan du kör cmdletar som ingår i modulen. En modul importeras automatiskt första gången du kör en cmdlet som ingår i modulen. Dessutom är Windows PowerShell-cmdletar inte skiftlägeskänsliga.

1. Skriv följande och tryck sedan på **RETUR**, där *computer_name* representerar en fjärrdator där du vill installera Windows PowerShell Web Access, om tillämpligt. Parametern `-Restart` startar om målservrarna automatiskt om det krävs.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > **![Obs](images/note.jpeg) Obs!**
   >
   > Installera Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdletar läggs inte hanteringsverktyg för webbserver (IIS) som standard. Om du vill installera hanteringsverktygen på samma server som Windows PowerShell Web Access-gatewayen, lägger du till den `-IncludeManagementTools` parameter i installationskommandot (enligt det här steget). Om du hanterar Windows PowerShell Web Access-webbplats från en fjärrdator måste du installera snapin-modulen IIS-hanteraren genom att installera [Remote Server Administration Toolsfor Windows 8.1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) eller [Remote Server Administration Verktyg för Windows 8](https://www.microsoft.com/en-us/download/details.aspx?id=28972) på den dator som du vill hantera gatewayen.

   Om du vill installera roller och funktioner på en offline-VHD, lägger du till både parametern `-ComputerName` och parametern `-VHD`. Parametern `-ComputerName` innehåller namnet på den server som du vill montera VHD:n på och parametern `-VHD` innehåller sökvägen till VHD-filen på den angivna servern.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. När installationen är klar kontrollerar du att Windows PowerShell Web Access har installerats på målservrarna genom att köra den `Get-WindowsFeature` cmdlet på en målserver i Windows PowerShell-konsolen som har öppnats med utökade användarrättigheter. Du kan också kontrollera att Windows PowerShell Web Access har installerats i Server Manager-konsolen genom att välja en målserver på den **alla servrar** sidan och sedan visa den **roller och funktioner** panel för den valda servern. Du kan också visa filen Viktigt för Windows PowerShell Web Access.

1. När du har installerat Windows PowerShell-webbåtkomst uppmanas du att granska filen Viktigt, som innehåller grundläggande obligatoriska konfigurationsanvisningar för gatewayen. Dessa anvisningar finns också i följande avsnitt [konfigurera gatewayen](#configure-the-gateway). Sökvägen till filen Viktigt är `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Konfigurera gatewayen

Den **Install-PswaWebApplication** cmdlet är ett snabbt sätt att hämta Windows PowerShell-webbåtkomst konfigurerats. Även om du kan lägga till parametern `UseTestCertificate` i cmdleten `Install-PswaWebApplication` för att installera ett självsignerat SSL-certifikat för teständamål, är det här inte säkert; för en säker produktionsmiljö bör du alltid använda ett giltigt SSL-certifikat som har signerats av en certifikatutfärdare (CA).
Administratörer kan ersätta testcertifikatet med ett eget signerat certifikat med hjälp av konsolen för IIS-hanteraren.

Du kan slutföra konfigurationen av Windows PowerShell-webbåtkomst antingen genom att köra den `Install-PswaWebApplication` cmdlet eller genom att utföra gränssnittsbaserade konfigurationssteg i IIS-hanteraren. Som standard installerar cmdleten webbprogrammet, **pswa** (och en programpool för den, **pswa_pool**) i den **Default Web Site** behållare som visas i IIS-hanteraren; om det önskade kan instruera du cmdleten ändra plats standardbehållaren för webbprogrammet. IIS-hanteraren erbjuder konfigurationsalternativ som är tillgängliga för webbprogram, till exempel för att ändra portnumret eller SSL-certifikat.

> **![Säkerhetsmeddelande](images/securitynote.jpeg) säkerhetsmeddelande**
>
> Vi rekommenderar att administratörer konfigurerar gatewayen att använda ett giltigt certifikat som har signerats av en CA.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Så här konfigurerar du gatewayen för Windows PowerShell-webbåtkomst med ett testcertifikat med hjälp av Install-PswaWebApplication

1. Gör något av följande för att öppna en Windows PowerShell-session.

   - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i Aktivitetsfältet.

   - På Windows **starta** klickar du på **Windows PowerShell**.

2. Skriv följande och tryck sedan på **Ange**.

   `Install-PswaWebApplication -UseTestCertificate`

   > **![Säkerhetsmeddelande](images/securitynote.jpeg) säkerhetsmeddelande**
   >
   > Parametern `UseTestCertificate` bör endast användas i en privat testmiljö. För en säker produktionsmiljö bör ett giltigt certifikat som har signerats av en CA användas.

   Kör cmdlet installerar Windows PowerShell Web Access-webbprogrammet i behållaren för IIS-standardwebbplatsen. Cmdleten skapar den infrastruktur som krävs för att köra Windows PowerShell-webbåtkomst på standardwebbplatsen, `https://<server_name>/pswa`. Om du vill installera webbprogrammet på en annan webbplats, anger du webbplatsnamnet genom att lägga till parametern `WebSiteName`. Du ändrar namnet på webbprogrammet (standard är `pswa`) genom att lägga till parametern `WebApplicationName`.

   Följande inställningar konfigureras genom att köra cmdleten. Du kan ändra dessa manuellt i konsolen för IIS-hanteraren.

   - Path: / pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: `%*windir*%/Web/PowerShellWebAccess/wwwroot`

     **Exempel**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

     I det här exemplet är webbplatsen för Windows PowerShell-webbåtkomst `https://<server_name>/myWebApp`.

   > **![Obs](images/note.jpeg) Obs!**
   >
   > Du kan inte logga in förrän användare har beviljats åtkomst till webbplatsen genom att lägga till auktoriseringsregler. Mer information finns i [konfigurera en regel för begränsad auktorisering](#configure-a-restrictive-authorization-rule) och [auktoriseringsregler och säkerhet funktioner i Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Så här konfigurerar du gatewayen för Windows PowerShell-webbåtkomst med ett äkta certifikat med hjälp av Install-PswaWebApplication och IIS-hanteraren

1. Gör något av följande för att öppna en Windows PowerShell-session.

   - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i Aktivitetsfältet.

   - På Windows **starta** klickar du på **Windows PowerShell**.

2. Skriv följande och tryck sedan på **Ange**.

   `Install-PswaWebApplication`

   Följande gatewayinställningar konfigureras genom att köra cmdleten.
   Du kan ändra dessa manuellt i konsolen för IIS-hanteraren.
   Du kan även ange värden för parametrarna `WebsiteName` och `WebApplicationName` i cmdleten `Install-PswaWebApplication`.

   - Path: / pswa

   - ApplicationPool: pswa_pool

   - EnabledProtocols: http

   - PhysicalPath: `%*windir*%/Web/PowerShellWebAccess/wwwroot`

3. Öppna konsolen för IIS-hanteraren genom att göra något av följande.

   - Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet. På den **verktyg** menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.

   - På Windows **starta** klickar du på **Serverhanteraren**.

4. I trädvyn för IIS-hanteraren expanderar du noden för den server där Windows PowerShell Web Access har installerats på tills den **platser** mappen är synliga. Expandera den **platser** mapp.

5. Välj den webbplats som du har installerat Windows PowerShell Web Access-webbprogram. I den **åtgärder** fönstret klickar du på **bindningar**.

6. I den **bindning för webbplats** dialogrutan klickar du på **Lägg till**.

7. I den **Lägg till bindning för webbplats** i dialogrutan den **typ** väljer **https**.

8. I den **SSL-certifikat** väljer du det signerade certifikatet från den nedrullningsbara menyn. Klicka på **OK**. Se [och konfigurera ett SSL-certifikat i IIS-hanteraren](#to-configure-an-ssl-certificate-in-iis-Manager) i det här avsnittet för mer information om hur du skaffar ett certifikat.

   Windows PowerShell-webbåtkomst webbprogrammet har nu konfigurerats för att använda det signerade SSL-certifikatet.

   Du kan komma åt Windows PowerShell-webbåtkomst genom att öppna **https://\<server_name\>/pswa** i ett webbläsarfönster.

   > **![Obs](images/note.jpeg) Obs!**
   >
   > Du kan inte logga in förrän användare har beviljats åtkomst till webbplatsen genom att lägga till auktoriseringsregler.
   > Mer information finns i [konfigurera en regel för begränsad auktorisering](#configure-a-restrictive-authorization-rule), i det här avsnittet och [auktoriseringsregler och säkerhet funktioner i Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Konfigurera en regel för begränsad auktorisering

När Windows PowerShell Web Access har installerats och gatewayen har konfigurerats, kan användarna öppna på inloggningssidan i en webbläsare, men de kan inte logga in förrän Windows PowerShell Web Access-administratören ger dem uttrycklig åtkomst. Windows PowerShell Web Access-åtkomstkontroll hanteras med hjälp av uppsättning Windows PowerShell cmdlets som beskrivs i följande tabell. Det finns ingen jämförbar GUI för att lägga till eller hantera auktoriseringsregler. Mer detaljerad information om Windows PowerShell Web Access-cmdlets finns i cmdlet-referensavsnittet [Windows PowerShell-cmdletar för webbåtkomst](cmdlets/web-access-cmdlets.md).

Mer information om Windows PowerShell-webbåtkomst auktoriseringsregler och säkerhet finns i [auktoriseringsregler och säkerhet funktioner i Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Så här lägger du till en regel för begränsad auktorisering

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter.

   - Högerklicka på Windows-skrivbordet **Windows PowerShell** Aktivitetsfältet och klickar sedan på **Kör som administratör**.

   - På Windows **starta** högerklickar **Windows PowerShell**, och klicka sedan på **kör som administratör**.

2. Valfritt steg för att begränsa användaråtkomst med hjälp av sessionskonfigurationer: Kontrollera att sessionskonfigurationer som du vill använda i dina regler redan finns. Om de inte ännu har skapats följer du instruktionerna för att skapa sessionskonfigurationer i [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Skriv följande och tryck sedan på **Ange**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Denna auktoriseringsregel ger en viss användaråtkomst till en dator i nätverket som de normalt har åtkomst till, med åtkomst till en viss sessionskonfiguration som är begränsad till användarens vanliga skript och cmdlet-behov.

   I följande exempel beviljas en användare med namnet `JSmith` i `Contoso`-domänen åtkomst för att hantera datorn `Contoso_214`, och använda en sessionskonfiguration med namnet `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Kontrollera att regeln har skapats genom att köra den `Get-PswaAuthorizationRule` cmdlet, eller `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

5. Till exempel `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

När du har konfigurerat en auktoriseringsregel är du redo för behöriga användare att logga in på den webbaserade konsolen och börja använda Windows PowerShell Web Access.

## <a name="custom-deployment"></a>Anpassad distribution

Du kan installera Windows PowerShell Web Access-gatewayen på en server som kör Windows Server 2012 R2 eller Windows Server 2012 med hjälp av Lägg till roller och funktioner som guiden i Serverhanteraren. När du har installerat Windows PowerShell Web Access kan du anpassa konfigurationen av gatewayen i IIS-hanteraren.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Installera Windows PowerShell-webbåtkomst med hjälp av Lägg till roller och funktioner som guiden

1. Gå vidare till nästa steg om Server Manager redan är öppen. Öppna genom att göra något av följande om Server Manager inte är redan öppen.

   - Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet.

   - På Windows **starta** klickar du på **Serverhanteraren**.

2. På den **hantera** -menyn klickar du på **Lägg till roller och funktioner**.

3. På den **Välj installationstyp** väljer **rollbaserad eller funktionsbaserad installation**. Klicka på **Nästa**.

4. På den **väljer målservern** sidan väljer du en server från serverpoolen, eller en offline-VHD. Du kan välja en offline-VHD som målserver genom att först välja på vilken server VHD:n ska monteras och sedan välja VHD-filen. Information om hur du lägger till servrar i serverpoolen finns i Server Manager-hjälpen. När du har valt målservern, klickar du på **nästa**.

5. På den **Välj vilka funktioner du** sidan i guiden expanderar **Windows PowerShell**, och välj sedan **Windows PowerShell-webbåtkomst**.

6. Observera att du uppmanas att lägga till nödvändiga funktioner, till exempel .NET Framework 4.5 och rolltjänster för Webbserver (IIS). Lägg till nödvändiga funktioner och fortsätt.

   > **![Obs](images/note.jpeg) Obs!**
   >
   > Installera Windows PowerShell-webbåtkomst med hjälp av Lägg till roller och funktioner som guiden installerar även webbserver (IIS), inklusive snapin-modulen IIS-hanteraren. Snapin-modulen och andra hanteringsverktyg för IIS installeras som standard om du använder guiden Lägg till roller och funktioner. Om du installerar Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdlets som beskrivs i följande procedur, läggs inte hanteringsverktyg som standard.

7. På den **Bekräfta installationsinställningarna** om funktionsfilerna för Windows PowerShell-webbåtkomst inte lagras på målservern som du valde i steg 4, klickar du på **anger en alternativ källsökväg**, och ange sökvägen till funktionsfilerna. Annars klickar du på **installera**.

8. När du klickar på **installera**, **Installationsförlopp** sidan visas installationens förlopp, resultat och meddelanden som varningar, fel eller efter installationen konfigurationssteg som är krävs för Windows PowerShell Web Access. När du har installerat Windows PowerShell-webbåtkomst uppmanas du att granska filen Viktigt, som innehåller grundläggande obligatoriska konfigurationsanvisningar för gatewayen. Instruktionerna finns också i det här avsnittet. Sökvägen till filen Viktigt är `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Konfigurera gatewayen

Anvisningarna i det här avsnittet är för att installera Windows PowerShell Web Access-webbprogram i en underkatalog och inte i rotkatalogen för din webbplats. Den här proceduren motsvarar de åtgärder som utförs av cmdleten `Install-PswaWebApplication`. Det här avsnittet innehåller också anvisningar för hur du använder IIS-hanteraren för att konfigurera Windows PowerShell Web Access-gateway som en rotwebbplats.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Så här använder du IIS-hanteraren för att konfigurera gatewayen på en befintlig webbplats

1. Öppna konsolen för IIS-hanteraren genom att göra något av följande.

   - Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet. På den **verktyg** menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.

   - På Windows **starta** skärmen, Skriv någon del av namnet **Internet Information Services (IIS) Manager**. Klicka på genvägen när den visas i den **appar** resultat.

2. Skapa en ny programpool för Windows PowerShell Web Access. Expandera noden för gateway-servern i trädfönstret IIS-hanteraren, som du väljer i **programpooler**, och klicka på **Lägg till programpool** i den **åtgärder** fönstret.

3. Lägg till en ny programpool med namnet **pswa_pool**, eller ange ett annat namn. Klicka på **OK**.

4. I trädvyn för IIS-hanteraren expanderar du noden för den server där Windows PowerShell Web Access har installerats på tills den **platser** mappen är synliga. Välj den **platser** mapp.

5. Högerklicka på webbplatsen (till exempel **standardwebbplats**) till vilken du vill lägga till Windows PowerShell Web Access-webbplats och klicka sedan på **Lägg till program**.

6. I den **Alias** fältet, anger du pswa eller ett annat alias. Aliaset blir namnet på den virtuella katalogen. Till exempel **pswa** i följande URL representerar det alias som angetts i det här steget: **https://\<servernamn\>/pswa**.

7. I den **programpoolen** , markera den programpool som du skapade i steg 3.

8. I den **fysisk sökväg** fältet, välj platsen för programmet. Du kan använda standardplatsen, %windir%/Web/PowerShellWebAccess/wwwroot. Klicka på **OK**.

9. Följ stegen i proceduren för att konfigurera ett SSL-certifikat i IIS manager](#to-configure-an-ssl-certificate-in-iis-Manager) i det här avsnittet.

10. ![](images/SecurityNote.jpeg) Valfritt säkerhetssteg:

    Med webbplatsen vald i trädvyn, dubbelklickar du på **SSL-inställningar** i innehållsfönstret.
    Välj **Kräv SSL**, och sedan i den **åtgärder** fönstret klickar du på **tillämpa**.
    Valfritt: i den **SSL-inställningar** fönstret kan du kräva att användare som ansluter till Windows PowerShell Web Access-webbplatsen har klientcertifikat. Klientcertifikat hjälper att kontrollera identiteten på användare med klientenheter.
    Läs mer om hur klientcertifikat kan öka säkerheten för Windows PowerShell-webbåtkomst [auktoriseringsregler och säkerhet funktioner i Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) i den här guiden.

11. Öppna en webbläsarsession på en klientenhet. Mer information om vilka webbläsare och enheter finns i [webbläsare och klientenheter som stöder](#browser-and-client-device-support) i det här avsnittet.

12. Öppna den nya Windows PowerShell Web Access-webbplatsen **https://\<*gateway servernamn*\>/pswa**.

    Webbläsaren bör visa Windows PowerShell Web Access-konsolen på inloggningssidan.

    > **![Obs](images/note.jpeg) Obs!**
    >
    > Du kan inte logga in förrän användare har beviljats åtkomst till webbplatsen genom att lägga till auktoriseringsregler.
    > Mer information finns i [konfigurera en regel för begränsad auktorisering](#configure-a-restrictive-authorization-rule), i det här avsnittet och [auktoriseringsregler och säkerhet funktioner i Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. I en Windows PowerShell-session som har öppnats med utökade användarrättigheter (Kör som administratör), kör du följande skript, där *application_pool_name* representerar namnet på den programpool som du skapade i steg 3, att ge programpoolen åtkomsträttigheter till auktoriseringsfilen.

    ```
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Kör följande kommando om du vill visa befintliga åtkomsträttigheter för auktoriseringsfilen:

    ```
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Så här använder du IIS-hanteraren för att konfigurera gatewayen som en rotwebbplats med ett testcertifikat

1. Öppna konsolen för IIS-hanteraren genom att göra något av följande.

   - Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet. På den **verktyg** menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.

   - På Windows **starta** skärmen, Skriv någon del av namnet **Internet Information Services (IIS) Manager**. Klicka på genvägen när den visas i den **appar** resultat.

2. I trädvyn för IIS-hanteraren expanderar du noden för den server där Windows PowerShell Web Access har installerats på tills den **platser** mappen är synliga. Välj den **platser** mapp.

3. I den **åtgärder** fönstret klickar du på **Lägg till webbplats**.

4. Skriv ett namn för webbplatsen, till exempel **Windows PowerShell-webbåtkomst**.

5. En programpool skapas automatiskt för den nya webbplatsen. Om du vill använda en annan programpool klickar du på **Välj** att välja en programpool som associeras med den nya webbplatsen. Välj den andra programpoolen i den **Välj programpool** dialogrutan och klicka sedan på **OK**.

6. I den **fysisk sökväg** text, bläddrar till %*windir*% / Web/PowerShellWebAccess/wwwroot.

7. I den **typ** i den **bindning** Välj **https**.

8. Tilldela ett portnummer till webbplatsen som inte redan används av en annan webbplats eller ett program. Om du vill hitta öppna portar som du kan köra den **netstat** i Kommandotolkens fönster. Standardportnumret är 443.

   Ändra standardporten om 443 redan används av en annan webbplats, eller om det finns andra säkerhetsskäl för att ändra portnumret. Om en annan webbplats som körs på din gateway-servern använder den valda porten, visas en varning när du klickar på **OK** i den **Lägg till webbplats** dialogrutan. Du måste använda en ledig port för att köra Windows PowerShell Web Access.

9. Alternativt, om det behövs för din organisation, ange ett värdnamn som passar din organisation och användare, till exempel **www.contoso.com**. Klicka på **OK**.

10. För en säkrare produktionsmiljö bör ett giltigt certifikat som har signerats av en CA användas. Du måste ange ett SSL-certifikat, eftersom användare kan endast ansluta till Windows PowerShell-webbåtkomst via en HTTPS-webbplats. Se [att konfigurera ett SSL-certifikat i IIS-hanteraren](#to-configure-an-ssl-certificate-in-iis-Manager) i det här avsnittet för mer information om hur du skaffar ett certifikat.

11. Klicka på **OK** att Stäng den **Lägg till webbplats** dialogrutan.

12. I en Windows PowerShell-session som har öppnats med utökade användarrättigheter (Kör som administratör), kör du följande skript, där *application_pool_name* representerar namnet på den programpool som du skapade i steg 4, att ge programpoolen åtkomsträttigheter till auktoriseringsfilen.

    ```    
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Kör följande kommando om du vill visa befintliga åtkomsträttigheter för auktoriseringsfilen:

    ```
    c:\windows\system32\icacls.exe $authorizationFile
    ```

13. Med den nya webbplatsen vald i trädvyn för IIS-hanteraren, klickar du på **starta** i den **åtgärder** fönstret för att starta webbplatsen.

14. Öppna en webbläsarsession på en klientenhet. Mer information om vilka webbläsare och enheter finns i [webbläsare och klientenheter som stöder](#browser-and-client-device-support) i det här dokumentet.

15. Öppna den nya Windows PowerShell Web Access-webbplatsen.

    Eftersom rotwebbplatsen pekar på mappen Windows PowerShell Web Access, webbläsaren bör visa inloggningssidan för Windows PowerShell-webbåtkomst när du öppnar **https://\<*gateway_server_name* \>**. Du behöver inte lägga till **/pswa** i URL: en.

    > **![Obs](images/note.jpeg) Obs!**
    >
    > Du kan inte logga in förrän användare har beviljats åtkomst till webbplatsen genom att lägga till auktoriseringsregler.
    > Mer information finns i [konfigurera en regel för begränsad auktorisering](#configure-a-restrictive-authorization-rule), i det här avsnittet och [auktoriseringsregler och säkerhet funktioner i Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configuring-a-restrictive-authorization-rule"></a>Konfigurera en regel för begränsad auktorisering

När Windows PowerShell Web Access har installerats och gatewayen har konfigurerats, kan användarna öppna på inloggningssidan i en webbläsare, men de kan inte logga in förrän Windows PowerShell Web Access-administratören ger dem uttrycklig åtkomst. Windows PowerShell Web Access-åtkomstkontroll hanteras med hjälp av uppsättning Windows PowerShell cmdlets som beskrivs i följande tabell. Det finns ingen jämförbar GUI för att lägga till eller hantera auktoriseringsregler. Mer detaljerad information om Windows PowerShell Web Access-cmdlets finns i cmdlet-referensavsnittet [Windows PowerShell-cmdletar för webbåtkomst](cmdlets/web-access-cmdlets.md).

Mer information om Windows PowerShell-webbåtkomst auktoriseringsregler och säkerhet finns i [auktoriseringsregler och säkerhet funktioner i Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="adding-a-restrictive-authorization-rule"></a>Att lägga till en regel för begränsad auktorisering

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter.

   - Högerklicka på Windows-skrivbordet **Windows PowerShell** Aktivitetsfältet och klickar sedan på **Kör som administratör**.

   - På Windows **starta** högerklickar **Windows PowerShell**, och klicka sedan på **kör som administratör**.

2. ![Säkerhetsmeddelande](images/SecurityNote.jpeg) Valfria steg för att begränsa användaråtkomsten med hjälp av sessionskonfigurationer:

   Kontrollera om de sessionskonfigurationer som du vill använda i dina regler redan finns. Om de inte ännu har skapats följer du instruktionerna för att skapa sessionskonfigurationer i [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Skriv följande och tryck sedan på **Ange**.

   Add-PswaAuthorizationRule - UserName < domain\user | computer\user > - ComputerName < computer_name > - ConfigurationName < session_configuration_name >

   Denna auktoriseringsregel ger en viss användaråtkomst till en dator i nätverket som de normalt har åtkomst till med åtkomst till en viss sessionskonfiguration som är begränsad till användaren '™ s vanliga skript och cmdlet-behov.

   I följande exempel beviljas en användare med namnet `JSmith` i `Contoso`-domänen åtkomst för att hantera datorn `Contoso_214`, och använda en sessionskonfiguration med namnet `NewAdminsOnly`.

   Add-PswaAuthorizationRule - UserName 'Contoso\JSmith' - ComputerName Contoso_214 - ConfigurationName NewAdminsOnly

4. Kontrollera att regeln har skapats genom att köra den `Get-PswaAuthorizationRule` cmdlet, eller `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

   Till exempel `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   När du har konfigurerat en auktoriseringsregel är du redo för behöriga användare att logga in på den webbaserade konsolen och börja använda Windows PowerShell Web Access.

## <a name="configure-a-genuine-certificate"></a>Konfigurera ett äkta certifikat

Använd alltid ett giltigt SSL-certifikat som har signerats av en certifikatutfärdare (CA) för en säker produktionsmiljö. I proceduren i det här avsnittet beskrivs hur du hämtar och installerar ett giltigt SSL-certifikat från en CA.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Så här konfigurerar du ett SSL-certifikat i IIS-hanteraren

1. I trädvyn på IIS-hanteraren väljer du den server där Windows PowerShell-webbåtkomst är installerad.

2. I innehållsfönstret dubbelklickar du på **servercertifikat**.

3. I den **åtgärder** fönstret, gör du något av följande. Mer information om hur du konfigurerar servercertifikat i IIS finns i [konfigurera servercertifikat i IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).

   - Klicka på **importera** att importera ett befintligt giltigt certifikat från en plats i nätverket.

   - Klicka på **skapa certifikatbegäran** att begära ett certifikat från en Certifikatutfärdare som [VeriSign](http://www.verisign.com/), [Thawte](https://www.thawte.com/), eller [GeoTrust](https://www.geotrust.com/). Certifikatets nätverksnamn måste matcha värdhuvudet i begäran.

   Exempel: om klientwebbläsaren begär http://www.contoso.com/, nätverksnamn måste också vara http://www.contoso.com/. Det här är det mest säkra och rekommenderade alternativet för att tillhandahålla gateway för Windows PowerShell-webbåtkomst med ett certifikat.

   - Klicka på **skapa ett självsignerat certifikat** att skapa ett certifikat som du kan använda direkt och få det signerat senare av en CA om du vill. Ange ett eget namn för det självsignerade certifikatet, till exempel **Windows PowerShell-webbåtkomst**. Det här alternativet anses inte vara säkert och rekommenderas endast för en privat testmiljö.

4. När du har skapat eller hämtat ett certifikat, väljer du den webbplats som certifikatet används (till exempel **standardwebbplats**) i trädfönstret i IIS-hanteraren och klicka sedan på **bindningar** i **Åtgärder** fönstret.

5. I den **Lägg till bindning för webbplats** dialogrutan lägger du till en **https** bindning för webbplatsen, om en inte sådan redan visas. Om du inte använder ett självsignerat certifikat, anger du värdnamnet från steg 3 i den här proceduren. Om du använder ett självsignerat certifikat behövs inte det här steget.

6. Välj det certifikat som du hämtat eller skapat i steg 3 i den här proceduren och klicka sedan på **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Användning av den webbaserade Windows PowerShell-konsolen

När Windows PowerShell Web Access har installerats och gateway-konfigurationen har slutförts enligt anvisningarna i det här avsnittet, är Windows PowerShell-webbaserad konsol klart att användas. Mer information om att komma igång i den webbaserade konsolen finns i [använda webbaserade Windows PowerShell-konsolen](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Se även

[Internet Information Services (IIS) 7.0 dokumentation](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[Hjälpen för IIS-hanteraren 7.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Konfigurera säkerhet för webbserver (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))

[IPsec-distributionsresurser](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))