---
ms.date: 08/23/2017
keywords: PowerShell, cmdlet
title: Installera och använda Windows PowerShell-Webbåtkomst
ms.openlocfilehash: a3207c859c4b93b07d4c1b41d7df5269daa39a7d
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78405195"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Installera och använda Windows PowerShell-webbåtkomst

Uppdaterat: 5 november 2013 (redigerad: 23 augusti 2017)

Gäller för: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Introduktion

Windows PowerShell-webbåtkomst, som introducerades i Windows Server 2012, fungerar som en Windows PowerShell-Gateway, vilket ger en webbaserad Windows PowerShell-konsol som är riktad mot en fjärrdator. Det gör det möjligt för IT-proffs att köra Windows PowerShell-kommandon och-skript från en Windows PowerShell-konsol i en webbläsare, utan Windows PowerShell, program vara för fjärrhantering eller webb läsar installation som krävs på klient enheten. Allt som krävs för att köra den webbaserade Windows PowerShell-konsolen är en korrekt konfigurerad Gateway för Windows PowerShell-webbåtkomst och en webbläsare för klient enheter som stöder Java Script och accepterar cookies.

Exempel på klientenheter är bärbara datorer, datorer i hemmet, lånade datorer, tablet-datorer, webbkiosker, datorer som inte kör ett Windows-baserat operativsystem och webbläsare i mobiltelefoner. IT-proffs kan utföra kritiska hanteringsuppgifter på Windows-baserade fjärrservrar från enheter som har tillgång till en Internetanslutning och en webbläsare.

Efter en lyckad gateway-konfiguration och konfiguration kan användare komma åt en Windows PowerShell-konsol med hjälp av en webbläsare. När användarna öppnar den säkra webbplatsen för Windows PowerShell-webbåtkomst kan de köra en webbaserad Windows PowerShell-konsol efter lyckad autentisering.

Konfiguration och konfiguration av Windows PowerShell-webbåtkomst är en process i tre steg:

1. [Installera Windows PowerShell-Webbåtkomst](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Konfigurera gatewayen](#configure-the-gateway)
1. [Konfigurera en begränsnings regel för auktorisering](#configure-a-restrictive-authorization-rule)

Innan du installerar och konfigurerar Windows PowerShell-webbåtkomsten rekommenderar vi att du läser hela den här guiden, som innehåller instruktioner om hur du installerar, skyddar och avinstallerar Windows PowerShell-webbåtkomst. Avsnittet [Använd den webbaserade Windows PowerShell-konsolen](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) beskriver hur användare loggar in i den webbaserade konsolen och täcker begränsningar och skillnader mellan den webbaserade Windows PowerShell-konsolen och **PowerShell. exe** -konsolen. Slutanvändare av den webbaserade-konsolen bör läsa [Använd den webbaserade Windows PowerShell-konsolen](use-the-web-based-windows-powershell-console.md), men behöver inte läsa resten av den här guiden.

Det här avsnittet innehåller inte detaljerad vägledning för IIS-webbserverns åtgärder. endast de steg som krävs för att konfigurera Windows PowerShell-webbåtkomst-gatewayen beskrivs i det här avsnittet. Mer information om hur du konfigurerar och säkrar webbplatser i IIS finns i IIS-dokumentationsresurserna i avsnittet Se även.

Följande diagram visar hur Windows PowerShell-webbåtkomst fungerar.

![Diagram för Windows PowerShell Web Access](media/install-and-use-windows-powershell-web-access/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Krav för att köra Windows PowerShell-webbåtkomst

Windows PowerShell-webbåtkomsten kräver webb server (IIS), .NET Framework 4,5 och Windows PowerShell 3,0 eller Windows PowerShell 4,0 för att köras på den server där du vill köra gatewayen. Du kan installera Windows PowerShell-webbåtkomst på en server som kör Windows Server 2012 R2 eller Windows Server 2012 genom att antingen använda guiden Lägg till roller och funktioner i Serverhanteraren eller Windows PowerShell-distributions-cmdletar för Serverhanteraren. När du installerar Windows PowerShell-webbåtkomst med hjälp av Serverhanteraren eller dess distributions-cmdletar läggs nödvändiga roller och funktioner automatiskt till som en del av installations processen.

Med Windows PowerShell-webbåtkomsten kan fjärran vändare få åtkomst till datorer i din organisation med hjälp av Windows PowerShell i en webbläsare. Även om Windows PowerShell-webbåtkomsten är ett bekvämt och kraftfullt hanterings verktyg utgör den webbaserade åtkomsten säkerhets risker och bör konfigureras så säkert som möjligt. Vi rekommenderar att administratörer som konfigurerar Windows PowerShell-webbåtkomst-gatewayen använder tillgängliga säkerhets lager, både cmdlet-baserade auktoriseringsregler som ingår i Windows PowerShell-webbåtkomsten och säkerhets lager som är tillgängliga på webb server ( IIS) och program från tredje part. Den här dokumentationen innehåller både oskyddade exempel som rekommenderas bara för testmiljöer och exempel som rekommenderas för säker distribution.

## <a name="browser-and-client-device-support"></a>Stöd för webbläsare och klientenheter

Windows PowerShell-webbåtkomsten stöder följande webbläsare i Internet. Även om mobila webbläsare inte stöds officiellt, kan många kunna köra den webbaserade Windows PowerShell-konsolen.
Andra webbläsare som accepterar cookies, kör JavaScript och kör HTTPS-webbplatser förväntas fungera, men är inte testade officiellt.

### <a name="supported-desktop-computer-browsers"></a>Datorwebbläsare som stöds

- Windows Internet Explorer för Microsoft Windows 8,0, 9,0, 10,0 och 11,0
- Mozilla Firefox-10.0.2
- Google Chrome 17.0.963.56 m för Windows
- Apple Safari 5.1.2 för Windows
- Apple Safari 5.1.2 för Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Minimalt testade mobila enheter eller webbläsare

- Windows Phone 7 och 7.5
- Google Android WebKit 3.1, webbläsaren Android 2.2.1 (Kernel 2.6)
- Apple Safari för iPhones operativsystem 5.0.1
- Apple Safari för iPad 2-operativsystem 5.0.1

### <a name="browser-requirements"></a>Krav för webbläsare

Om du vill använda webb åtkomst till Windows PowerShell-webbbaserad konsol måste webbläsare göra följande.

- Tillåt cookies från webbplatsen för gateway för Windows PowerShell-webbåtkomst.
- Kunna öppna och läsa HTTPS-sidor.
- Öppna och köra webbplatser som använder JavaScript.

## <a name="recommended-quick-deployment"></a>Rekommenderad snabb distribution

Du kan installera Windows PowerShell-webbåtkomst-gatewayen på en server som kör Windows Server 2012 R2 eller Windows Server 2012 med hjälp av Windows PowerShell-cmdlets eller med hjälp av guiden Lägg till roller och funktioner som öppnas från Serverhanteraren. Använd Windows PowerShell-cmdlets för snabb installation och konfiguration, enligt beskrivningen i det här avsnittet.

1. [Installera Windows PowerShell-Webbåtkomst](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Konfigurera gatewayen](#configure-the-gateway)
1. [Konfigurera en begränsnings regel för auktorisering](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>Installera Windows PowerShell-webbåtkomst med PowerShell-cmdletar

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Så här installerar du Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdletar

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användar rättigheter.

   - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitets fältet och klickar sedan på **Kör som administratör**.
   - På Windows **start**skärm högerklickar du på **Windows PowerShell** och klickar sedan på **Kör som administratör**.

   > [!NOTE]
   > I Windows PowerShell 3,0 och 4,0 behöver du inte importera modulen Serverhanteraren cmdlet till Windows PowerShell-sessionen innan du kör cmdletar som ingår i modulen. En modul importeras automatiskt första gången du kör en cmdlet som ingår i modulen.
   > Dessutom är Windows PowerShell-cmdletar inte Skift läges känsliga.

1. Skriv följande och tryck sedan på **RETUR**, där *computer_name* representerar en fjärrdator där du vill installera Windows PowerShell-webbåtkomst, om tillämpligt. Parametern `-Restart` startar om målservrarna automatiskt om det krävs.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > [!NOTE]
   > Om du installerar Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdlets läggs inte hanterings verktyg för webb server (IIS) som standard till. Om du vill installera hanterings verktygen på samma server som Windows PowerShell Web Access Gateway, lägger du till `-IncludeManagementTools`-parametern i installations kommandot (enligt vad som anges i det här steget). Om du hanterar webbplatsen för Windows PowerShell-webbåtkomsten från en fjärrdator, installerar du snapin-modulen IIS-hanteraren genom att installera [verktyg för fjärrserveradministration för windows 8,1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) eller [verktyg för fjärrserveradministration för Windows 8](https://www.microsoft.com/en-us/download/details.aspx?id=28972) på den dator som du vill hantera gatewayen från.

   Om du vill installera roller och funktioner på en offline-VHD, lägger du till både parametern `-ComputerName` och parametern `-VHD`. Parametern `-ComputerName` innehåller namnet på den server som den virtuella hård disken ska monteras på och parametern `-VHD` innehåller sökvägen till VHD-filen på den angivna servern.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. När installationen är klar kontrollerar du att Windows PowerShell-webbåtkomsten har installerats på mål servrarna genom att köra cmdleten `Get-WindowsFeature` på en mål server i en Windows PowerShell-konsol som har öppnats med utökade användar rättigheter. Du kan också kontrol lera att Windows PowerShell-webbåtkomsten har installerats i Serverhanteraren-konsolen genom att välja en mål server på sidan **alla servrar** och sedan Visa panelen **roller och funktioner** för den valda servern. Du kan också Visa Readme-filen för Windows PowerShell-webbåtkomst.

1. När Windows PowerShell-webbåtkomsten har installerats uppmanas du att gå igenom Readme-filen, som innehåller grundläggande, nödvändiga installations anvisningar för gatewayen. Dessa installations anvisningar finns också i följande avsnitt: [Konfigurera gatewayen](#configure-the-gateway). Sökvägen till Readme-filen är `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Konfigurera gatewayen

Cmdleten **install-PswaWebApplication** är ett snabbt sätt att få Windows PowerShell-webbåtkomsten konfigurerad. Även om du kan lägga till parametern `UseTestCertificate` i cmdleten `Install-PswaWebApplication` för att installera ett självsignerat SSL-certifikat för teständamål, är det här inte säkert; för en säker produktionsmiljö bör du alltid använda ett giltigt SSL-certifikat som har signerats av en certifikatutfärdare (CA). Administratörer kan ersätta testcertifikatet med ett eget signerat certifikat med hjälp av konsolen för IIS-hanteraren.

Du kan slutföra konfigurationen av webb program för Windows PowerShell Web Access antingen genom att köra cmdleten `Install-PswaWebApplication` eller genom att utföra GUI-baserade konfigurations steg i IIS-hanteraren.
Som standard installerar cmdleten webb programmet, **pswa** (och en programpool för den **pswa_pool**), i **standard** behållaren för webbplatser, som visas i IIS-hanteraren. Om du vill kan du instruera cmdleten att ändra standard webbplats behållaren för webb programmet. IIS-hanteraren erbjuder konfigurationsalternativ som är tillgängliga för webbprogram, till exempel för att ändra portnumret eller SSL-certifikat.

> [!IMPORTANT]
> Vi rekommenderar att administratörer konfigurerar gatewayen att använda ett giltigt certifikat som har signerats av en CA.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Så här konfigurerar du gatewayen för Windows PowerShell-webbåtkomst med ett testcertifikat med hjälp av Install-PswaWebApplication

1. Gör något av följande för att öppna en Windows PowerShell-session.

   - På Windows-skrivbordet, högerklickar du på **Windows PowerShell** i aktivitetsfältet.
   - På **Start**skärmen i Windows klickar du på **Windows PowerShell**.

2. Skriv följande och tryck sedan på **RETUR**.

   `Install-PswaWebApplication -UseTestCertificate`

   > [!IMPORTANT]
   > Parametern `UseTestCertificate` bör endast användas i en privat testmiljö. För en säker produktionsmiljö bör ett giltigt certifikat som har signerats av en CA användas.

   Om du kör cmdleten installeras webb programmet för Windows PowerShell-webbåtkomsten i standard webbplats behållaren för IIS. Cmdleten skapar den infrastruktur som krävs för att köra Windows PowerShell-webbåtkomst på standard webbplatsen `https://<server_name>/pswa`. Om du vill installera webbprogrammet på en annan webbplats, anger du webbplatsnamnet genom att lägga till parametern `WebSiteName`. Du ändrar namnet på webbprogrammet (standard är `pswa`) genom att lägga till parametern `WebApplicationName`.

   Följande inställningar konfigureras genom att köra cmdleten. Du kan ändra dessa manuellt i konsolen för IIS-hanteraren.

   - Sökväg:/pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath:% windir%/Web/PowerShellWebAccess/wwwroot

   **Exempel**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

   I det här exemplet är den resulterande webbplatsen för Windows PowerShell-webbåtkomsten `https://<server_name>/myWebApp`.

   > [!NOTE]
   > Du kan inte logga in förrän användare har beviljats åtkomst till webbplatsen genom att lägga till auktoriseringsregler. Mer information finns i [Konfigurera en begränsad auktoriseringsregel](#configure-a-restrictive-authorization-rule) och [auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Så här konfigurerar du gatewayen för Windows PowerShell-webbåtkomst med ett äkta certifikat med hjälp av Install-PswaWebApplication och IIS-hanteraren

1. Gör något av följande för att öppna en Windows PowerShell-session.

   - På Windows-skrivbordet, högerklickar du på **Windows PowerShell** i aktivitetsfältet.
   - På **Start**skärmen i Windows klickar du på **Windows PowerShell**.

2. Skriv följande och tryck sedan på **RETUR**.

   `Install-PswaWebApplication`

   Följande gatewayinställningar konfigureras genom att köra cmdleten. Du kan ändra dessa manuellt i konsolen för IIS-hanteraren. Du kan även ange värden för parametrarna `WebsiteName` och `WebApplicationName` i cmdleten `Install-PswaWebApplication`.

   - Sökväg:/pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath:% windir%/Web/PowerShellWebAccess/wwwroot

3. Öppna IIS-hanteringskonsolen genom att göra något av följande.

   - På Windows-skrivbordet startar du Serverhanteraren genom att klicka på **Serverhanteraren** i aktivitets fältet i Windows. I **verktyg** -menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.
   - På **Start**skärmen i Windows klickar du på **Serverhanteraren**.

4. I träd fönstret i IIS-hanteraren expanderar du noden för den server där Windows PowerShell-webbåtkomsten är installerad tills mappen **platser** visas. Expandera mappen **Platser**.

5. Välj den webbplats där du har installerat webb programmet för Windows PowerShell-webbåtkomst.
   I fönstret **Åtgärder** klickar du på **Bindningar**.

6. I dialogrutan **Bindning för webbplats** klickar du på **Lägg till**.

7. I dialogrutan **Lägg till bindning för webbplats** väljer du **https** i fältet **Typ**.

8. I fältet **SSL-certifikat** väljer du det signerade certifikatet på menyn.
   Klicka på **OK** Mer information om hur du skaffar ett certifikat finns i [Konfigurera ett SSL-certifikat i IIS-hanteraren](#to-configure-an-ssl-certificate-in-iis-manager) i det här avsnittet.

   Webb programmet för Windows PowerShell-webbåtkomst har nu kon figurer ATS för att använda ditt signerade SSL-certifikat.

   Du kan komma åt Windows PowerShell-webbåtkomsten genom att öppna `https://<server_name>/pswa` i ett webbläsarfönster.

   > [!NOTE]
   > Du kan inte logga in förrän användare har beviljats åtkomst till webbplatsen genom att lägga till auktoriseringsregler. Mer information finns i [Konfigurera en restriktiv auktoriseringsregel](#configure-a-restrictive-authorization-rule), i det här avsnittet och [auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Konfigurera en begränsnings regel för auktorisering

När Windows PowerShell-webbåtkomsten har installerats och gatewayen har kon figurer ATS kan användarna öppna inloggnings sidan i en webbläsare, men de kan inte logga in förrän Windows PowerShell-administratören ger användare åtkomst uttryckligen. Åtkomst kontrollen för Windows PowerShell-webbåtkomsten hanteras med hjälp av de Windows PowerShell-cmdlets som beskrivs i följande tabell. Det finns ingen jämförbar GUI för att lägga till eller hantera auktoriseringsregler. Mer detaljerad information om Windows PowerShell-cmdlets finns i avsnittet om cmdlet-referenser, [Windows PowerShell-webbåtkomst-cmdletar](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Mer information om Windows PowerShell-auktoriseringsregler och säkerhet finns i [auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Så här lägger du till en regel för begränsad auktorisering

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användar rättigheter.

   - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitets fältet och klickar sedan på **Kör som administratör**.
   - På Windows **start**skärm högerklickar du på **Windows PowerShell** och klickar sedan på **Kör som administratör**.

2. Valfritt steg för att begränsa användaråtkomst med hjälp av sessionskonfigurationer: Kontrollera att de sessionskonfigurationer som du vill använda i dina regler redan finns. Om de inte har skapats än använder du instruktioner för att skapa sessionsinställningar i [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Skriv följande och tryck sedan på **RETUR**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Med den här auktoriseringsregeln kan en speciell användare få åtkomst till en dator i nätverket som de normalt har åtkomst till, med åtkomst till en speciell sessionsinformation som är begränsad till användarens typiska skript-och cmdlet-behov.

   I följande exempel beviljas en användare med namnet `JSmith` i `Contoso`-domänen åtkomst för att hantera datorn `Contoso_214`, och använda en sessionskonfiguration med namnet `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Kontrol lera att regeln har skapats genom att köra antingen `Get-PswaAuthorizationRule` cmdlet eller `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

   Till exempel `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

När du har konfigurerat en auktoriseringsregel är du redo för behöriga användare att logga in i den webbaserade konsolen och börja använda Windows PowerShell-webbåtkomst.

## <a name="custom-deployment"></a>Anpassad distribution

Du kan installera gatewayen för Windows PowerShell-webbåtkomsten på en server som kör Windows Server 2012 R2 eller Windows Server 2012 med hjälp av guiden Lägg till roller och funktioner i Serverhanteraren.
När du har installerat Windows PowerShell-webbåtkomst kan du anpassa konfigurationen av gatewayen i IIS-hanteraren.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Installera Windows PowerShell-webbåtkomst med hjälp av guiden Lägg till roller och funktioner

1. Om Serverhanteraren redan är öppet går du vidare till nästa steg. Om Serverhanteraren inte redan är öppet öppnar du det genom att göra något av följande.

   - På Windows-skrivbordet startar du Serverhanteraren genom att klicka på **Serverhanteraren** i aktivitets fältet i Windows.
   - På **Start**skärmen i Windows klickar du på **Serverhanteraren**.

2. I menyn **Hantera** klickar du på **Lägg till roller och funktioner**.

3. Klicka på **Rollbaserad eller funktionsbaserad installation** på sidan **Välj installationstyp**.
   Klicka på **Next**.

4. På sidan **Välj målserver** väljer du en server från serverpoolen eller en offline-VHD. Välj en offline-VHD som mål server genom att först välja den server som du vill montera den virtuella hård disken på och sedan välja VHD-filen. Information om hur du lägger till servrar i serverpoolen finns i hjälpen för Serverhanteraren. När du har valt målservern klickar du på **Nästa**.

5. På sidan **Välj funktioner** i guiden expanderar du **Windows PowerShell** och väljer sedan **Windows PowerShell-webbåtkomst**.

6. Observera att du uppmanas att lägga till nödvändiga funktioner, till exempel .NET Framework 4.5 och rolltjänster för Webbserver (IIS). Lägg till nödvändiga funktioner och fortsätt.

   > [!NOTE]
   > När du installerar Windows PowerShell-webbåtkomst med hjälp av guiden Lägg till roller och funktioner installeras även webb server (IIS), inklusive snapin-modulen IIS-hanteraren. Snapin-modulen och andra hanterings verktyg för IIS installeras som standard om du använder guiden Lägg till roller och funktioner. Om du installerar Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdlets som beskrivs i följande procedur, läggs inte hanterings verktyg till som standard.

7. På sidan **Bekräfta installations inställningarna** , om Feature-filerna för Windows PowerShell-webbåtkomsten inte är lagrade på mål servern som du valde i steg 4, klickar du på **Ange en alternativ käll Sök väg**och anger sökvägen till-installationsfilerna. Annars klickar du på **Installera**.

8. När du har klickat på **Installera**visar sidan **installations förlopp** installations förlopp, resultat och meddelanden, till exempel varningar, fel eller konfigurations steg efter installation som krävs för Windows PowerShell-webbåtkomst. När Windows PowerShell-webbåtkomsten har installerats uppmanas du att gå igenom Readme-filen, som innehåller grundläggande, nödvändiga installations anvisningar för gatewayen. Instruktionerna finns också i det här avsnittet. Sökvägen till Readme-filen är `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Konfigurera gatewayen

Anvisningarna i det här avsnittet är för att installera Windows PowerShell Web Access-webbprogrammet i en under katalog och inte i rot katalogen på din webbplats. Den här proceduren motsvarar de åtgärder som utförs av cmdleten `Install-PswaWebApplication`. Det här avsnittet innehåller också anvisningar för hur du använder IIS-hanteraren för att konfigurera Windows PowerShell-webbåtkomst-gatewayen som en rot webbplats.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Så här använder du IIS-hanteraren för att konfigurera gatewayen på en befintlig webbplats

1. Öppna IIS-hanteringskonsolen genom att göra något av följande.

   - På Windows-skrivbordet startar du Serverhanteraren genom att klicka på **Serverhanteraren** i aktivitets fältet i Windows. I **verktyg** -menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.
   - På Windows **Start**-skärmen, fyller du i valfri del av namnet **IIS (Internet Information Services)-hanteraren**. Klicka på genvägen när den visas i **Appar**-resultaten.

2. Skapa en ny programpool för Windows PowerShell-webbåtkomst. Expandera noden för gateway-servern i trädfönstret i IIS-hanteraren, välj **Programpooler** och klicka på **Lägg till programpool** i rutan **Åtgärder**.

3. Lägg till en ny programpool med namnet **pswa_pool**, eller ange ett annat namn. Klicka på **OK**

4. I träd fönstret i IIS-hanteraren expanderar du noden för den server där Windows PowerShell-webbåtkomsten är installerad tills mappen **platser** visas. Välj mappen **Platser**.

5. Högerklicka på webbplatsen (till exempel **standard webbplats**) till vilken du vill lägga till webbplatsen för Windows PowerShell-webbåtkomsten och klicka sedan på **Lägg till program**.

6. I fältet **Alias** anger du pswa eller ett annat alias. Aliaset blir namnet på den virtuella katalogen. Till exempel representerar **pswa** i följande URL det alias som anges i det här steget: `https://<server-name>/pswa`.

7. I fältet **Programpool** väljer du programpoolen som du skapade i steg 3.

8. I fältet **Fysisk sökväg** bläddrar du efter mappen där programmet finns. Du kan använda standard platsen `$env:windir/Web/PowerShellWebAccess/wwwroot`. Klicka på **OK**

9. Följ stegen i proceduren [för att konfigurera ett SSL-certifikat i IIS-hanteraren](#to-configure-an-ssl-certificate-in-iis-manager) i det här avsnittet.

10. Valfritt säkerhets steg:

    När du har valt webbplatsen i träd fönstret dubbelklickar du på **SSL-inställningar** i innehålls rutan.
    Välj **Kräv SSL** och klicka sedan på **Verkställ** i rutan **Åtgärder**. I rutan **SSL-inställningar** kan du även kräva att användare som ansluter till webbplatsen för Windows PowerShell-webbåtkomsten har klient certifikat. Klientcertifikat hjälper att kontrollera identiteten på användare med klientenheter. Mer information om hur krav på klient certifikat kan öka säkerheten för Windows PowerShell-webbåtkomsten finns i [auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](authorization-rules-and-security-features-of-windows-powershell-web-access.md) i den här hand boken.

11. Öppna en webbläsarsession på en klientenhet. Mer information om vilka webbläsare och enheter som stöds finns i [stöd för webbläsare och klient enheter](#browser-and-client-device-support) i det här avsnittet.

12. Öppna den nya webbplatsen för Windows PowerShell-webbåtkomst, **https://\<*Gateway-Server-Name*\>/pswa**.

    Webbläsaren ska Visa inloggnings sidan för Windows PowerShell Web Access-konsolen.

    > [!NOTE]
    > Du kan inte logga in förrän användare har beviljats åtkomst till webbplatsen genom att lägga till auktoriseringsregler. Mer information finns i [Konfigurera en restriktiv auktoriseringsregel](#configure-a-restrictive-authorization-rule), i det här avsnittet och [auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. I en Windows PowerShell-session som har öppnats med utökade användar rättigheter (kör som administratör), kör du följande skript, där *application_pool_name* representerar namnet på den programpool som du skapade i steg 3 för att ge programpoolen åtkomst rättigheter till verifierings filen.

    ```powershell
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Kör följande kommando om du vill visa befintliga åtkomsträttigheter för auktoriseringsfilen:

    ```powershell
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Så här använder du IIS-hanteraren för att konfigurera gatewayen som en rotwebbplats med ett testcertifikat

1. Öppna IIS-hanteringskonsolen genom att göra något av följande.

   - På Windows-skrivbordet startar du Serverhanteraren genom att klicka på **Serverhanteraren** i aktivitets fältet i Windows. I **verktyg** -menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.
   - På Windows **Start**-skärmen, fyller du i valfri del av namnet **IIS (Internet Information Services)-hanteraren**. Klicka på genvägen när den visas i **Appar**-resultaten.

1. I träd fönstret i IIS-hanteraren expanderar du noden för den server där Windows PowerShell-webbåtkomsten är installerad tills mappen **platser** visas. Välj mappen **Platser**.

1. I fönstret **Åtgärder** klickar du på **Lägg till webbplats**.

1. Ange ett namn för webbplatsen, till exempel **Windows PowerShell-webbåtkomst**.

1. En programpool skapas automatiskt för den nya webbplatsen. Om du vill använda en annan programpool klickar du på **Välj** för att välja en programpool som associeras med den nya webbplatsen. I dialogrutan **Välj programpool**  väljer du den andra programpoolen och klickar sedan på **OK**.

1. I text rutan **fysisk sökväg** navigerar du till% windir%/Web/PowerShellWebAccess/wwwroot.

1. I fältet **Typ** i området **Bindning** väljer du **https**.

1. Tilldela ett portnummer till webbplatsen som inte redan används av en annan webbplats eller ett program.
   Om du vill hitta öppna portar kör du kommandot **netstat** i Kommandotolken. Standardportnumret är 443.

   Ändra standardporten om 443 redan används av en annan webbplats, eller om det finns andra säkerhetsskäl för att ändra portnumret. Om en annan webbplats som körs på din gateway-server använder den valda porten, visas en varning när du klickar på **OK** i dialogrutan **Lägg till webbplats**. Du måste använda en oanvänd port för att köra Windows PowerShell-webbåtkomst.

1. Om det behövs för din organisation kan du, om det behövs, ange ett värdnamn som passar din organisation och dina användare, t. ex. **`www.contoso.com`** . Klicka på **OK**

1. För en säkrare produktionsmiljö bör ett giltigt certifikat som har signerats av en CA användas. Du måste ange ett SSL-certifikat, eftersom användarna bara kan ansluta till Windows PowerShell-webbåtkomst via en HTTPS-webbplats. Mer information om hur du skaffar ett certifikat finns i [Konfigurera ett SSL-certifikat i IIS-hanteraren](#to-configure-an-ssl-certificate-in-iis-manager) i det här avsnittet.

1. Klicka på **OK** för att stänga dialogrutan **Lägg till webbplats**.

1. I en Windows PowerShell-session som har öppnats med utökade användar rättigheter (kör som administratör), kör du följande skript, där _application_pool_name_ representerar namnet på den programpool som du skapade i steg 4, för att ge programpoolen åtkomst rättigheter till verifierings filen.

   ```powershell
   $applicationPoolName = "<application_pool_name>"
   $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
   c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
   ```

   Kör följande kommando om du vill visa befintliga åtkomsträttigheter för auktoriseringsfilen:

   ```powershell
   c:\windows\system32\icacls.exe $authorizationFile
   ```

1. Med den nya webbplatsen vald i trädfönstret i IIS-hanteraren klickar du på **Starta** i fönstret **Åtgärder** för att starta webbplatsen.

1. Öppna en webbläsarsession på en klientenhet. Mer information om vilka webbläsare och enheter som stöds finns i [stöd för webbläsare och klient enheter](#browser-and-client-device-support) i det här dokumentet.

1. Öppna den nya webbplatsen för Windows PowerShell-webbåtkomst.

   Eftersom rot webbplatsen pekar på Windows PowerShell-webbåtkomst-mappen, ska webbläsaren Visa inloggnings sidan för Windows PowerShell-webbåtkomsten när du öppnar `https://<gateway_server_name>`. Du behöver inte lägga till **/pswa** till URL:en.

   > [!NOTE]
   > Du kan inte logga in förrän användare har beviljats åtkomst till webbplatsen genom att lägga till auktoriseringsregler. Mer information finns i [Konfigurera en restriktiv auktoriseringsregel](#configure-a-restrictive-authorization-rule), i det här avsnittet och [auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configuring-a-restrictive-authorization-rule"></a>Konfigurera en begränsnings regel för auktorisering

När Windows PowerShell-webbåtkomsten har installerats och gatewayen har kon figurer ATS kan användarna öppna inloggnings sidan i en webbläsare, men de kan inte logga in förrän Windows PowerShell-administratören ger användare åtkomst uttryckligen. Åtkomst kontrollen för Windows PowerShell-webbåtkomsten hanteras med hjälp av de Windows PowerShell-cmdlets som beskrivs i följande tabell. Det finns ingen jämförbar GUI för att lägga till eller hantera auktoriseringsregler. Mer detaljerad information om Windows PowerShell-cmdlets finns i avsnittet om cmdlet-referenser, [Windows PowerShell-webbåtkomst-cmdletar](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Mer information om Windows PowerShell-auktoriseringsregler och säkerhet finns i [auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="adding-a-restrictive-authorization-rule"></a>Lägga till en begränsnings regel för auktorisering

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användar rättigheter.

   - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitets fältet och klickar sedan på **Kör som administratör**.
   - På Windows **start**skärm högerklickar du på **Windows PowerShell** och klickar sedan på **Kör som administratör**.

1. Valfria steg för att begränsa användaråtkomsten med hjälp av sessionskonfigurationer:

   Kontrollera om de sessionskonfigurationer som du vill använda i dina regler redan finns. Om de inte har skapats än använder du instruktioner för att skapa sessionsinställningar i [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Skriv följande och tryck sedan på **RETUR**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Med den här auktoriseringsregeln kan en speciell användare få åtkomst till en dator i nätverket som de normalt har åtkomst till, med åtkomst till en speciell sessionsinformation som är begränsad till användaren&trade;s typiska skript-och cmdlet-behov.

   I följande exempel beviljas en användare med namnet `JSmith` i `Contoso`-domänen åtkomst för att hantera datorn `Contoso_214`, och använda en sessionskonfiguration med namnet `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

1. Kontrol lera att regeln har skapats genom att köra antingen `Get-PswaAuthorizationRule` cmdlet eller `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

   Till exempel `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   När du har konfigurerat en auktoriseringsregel är du redo för behöriga användare att logga in i den webbaserade konsolen och börja använda Windows PowerShell-webbåtkomst.

## <a name="configure-a-genuine-certificate"></a>Konfigurera ett äkta certifikat

Använd alltid ett giltigt SSL-certifikat som har signerats av en certifikatutfärdare (CA) för en säker produktionsmiljö. I proceduren i det här avsnittet beskrivs hur du hämtar och installerar ett giltigt SSL-certifikat från en CA.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Så här konfigurerar du ett SSL-certifikat i IIS-hanteraren

1. I träd fönstret i IIS-hanteraren väljer du den server där Windows PowerShell-webbåtkomsten är installerad.

1. Dubbelklicka på **Servercertifikat** i innehållsfönstret.

1. Gör något av följande i rutan **Åtgärder**. Mer information om hur du konfigurerar Server certifikat i IIS finns i [Konfigurera Server certifikat i IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).

   - Klicka på **Importera** om du vill importera ett befintligt giltigt certifikat från en plats i nätverket.
   - Klicka på **Skapa certifikatbegäran** för att begära ett certifikat från en certifikat utfärdare, till exempel [VeriSign](https://www.verisign.com/), [Thawte](https://www.thawte.com/)eller ett [förtroende](https://www.geotrust.com/). Certifikatets nätverksnamn måste matcha värdhuvudet i begäran.

     Om till exempel klient webbläsaren begär `http://www.contoso.com/`, måste även det egna namnet `http://www.contoso.com/`. Detta är det säkraste och rekommenderade alternativet för att tillhandahålla gatewayen för Windows PowerShell-webbåtkomsten med ett certifikat.

   - Klicka på **Skapa ett självsignerat certifikat** om du vill skapa ett certifikat som du kan använda direkt, och få det signerat senare av en CA om du vill. Ange ett eget namn för det självsignerade certifikatet, till exempel **Windows PowerShell-webbåtkomst**. Det här alternativet anses inte vara säkert och rekommenderas endast för en privat testmiljö.

1. När du har skapat eller hämtat ett certifikat väljer du den webbplats som certifikatet används på (till exempel **Standardwebbplats**) i trädfönstret i IIS-hanteraren och klickar sedan på **Bindningar** i fönstret **Åtgärder**.

1. I dialogrutan **Lägg till bindning för webbplats** lägger du till en **https**-bindning för webbplatsen, om en sådan inte redan visas. Om du inte använder ett självsignerat certifikat, anger du värdnamnet från steg 3 i den här proceduren. Om du använder ett självsignerat certifikat behövs inte det här steget.

1. Välj det certifikat som du hämtat eller skapat i steg 3 i den här proceduren och klicka sedan på **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Användning av den webbaserade Windows PowerShell-konsolen

När Windows PowerShell-webbåtkomst har installerats och gateway-konfigurationen har slutförts enligt beskrivningen i det här avsnittet är den webbaserade Windows PowerShell-konsolen redo att användas. Mer information om att komma igång i den webbaserade konsolen finns i [använda den webbaserade Windows PowerShell-konsolen](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Se även

[Internet Information Services (IIS) 7,0-dokumentation](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[Hjälp om IIS-hanteraren 7,0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Konfigurera webb Server säkerhet (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))

[IPsec-distributions resurser](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))
