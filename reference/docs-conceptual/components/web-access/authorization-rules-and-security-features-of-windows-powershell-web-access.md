---
ms.date: 06/27/2017
keywords: PowerShell, cmdlet
title: Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-Webbåtkomst
ms.openlocfilehash: ee25df052994e47e559daa87b89af813471d896b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624762"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-Webbåtkomst

Uppdaterad: 24 juni 2013

Gäller för: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell-webbåtkomsten i Windows Server 2012 R2 och Windows Server 2012 har en begränsad säkerhets modell. Användare måste uttryckligen beviljas åtkomst innan de kan logga in på Windows PowerShell Web Access Gateway och använda den webbaserade Windows PowerShell-konsolen.

## <a name="configuring-authorization-rules-and-site-security"></a>Konfigurera auktoriseringsregler och plats säkerhet

När Windows PowerShell-webbåtkomsten har installerats och gatewayen har kon figurer ATS kan användarna öppna inloggnings sidan i en webbläsare, men de kan inte logga in förrän Windows PowerShell-administratören ger användare åtkomst uttryckligen. Åtkomst kontrollen för Windows PowerShell-webbåtkomst hanteras med hjälp av en uppsättning Windows PowerShell-cmdlets som beskrivs i följande tabell. Det finns inget jämförbart användar gränssnitt för att lägga till eller hantera auktoriseringsregler.
Se [cmdlets för Windows PowerShell-webbåtkomst](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Administratörer kan definiera `{0-n}` autentiseringsprinciper för Windows PowerShell-webbåtkomst. Standard säkerheten är begränsad snarare än att tillåtas. Zero Authentication-regler innebär att inga användare har åtkomst till något.

[Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) och [test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) i Windows Server 2012 R2 innehåller en parameter för autentiseringsuppgifter som gör att du kan lägga till och testa auktoriseringsregler för Windows PowerShell-webbåtkomsten från en fjärrdator eller från en aktiv Windows PowerShell-webbapp. Precis som med andra Windows PowerShell-cmdletar som har en parameter för autentiseringsuppgifter kan du ange ett PSCredential-objekt som värde för parametern. Om du vill skapa ett PSCredential-objekt som innehåller autentiseringsuppgifter som du vill skicka till en fjärrdator kör du cmdleten [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) .

Vitlista-regler är regler för Windows PowerShell-autentisering. Varje regel är en definition av en tillåten anslutning mellan användare, mål datorer och särskilda konfigurationer för Windows PowerShell- [sessioner](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) (kallas även slut punkter eller _körnings utrymmen_) på angivna mål datorer.
En förklaring om **körnings utrymmen** finns i [Starta användning av PowerShell-körnings utrymmen](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> En användare behöver bara en regel för att få åtkomst. Om en användare får åtkomst till en dator med antingen fullständig språk åtkomst eller enbart åtkomst till Windows PowerShell-cmdletar för fjärrhantering från den webbaserade konsolen, kan användaren logga in (eller hopp) till andra datorer som är anslutna till den första mål datorn. Det säkraste sättet att konfigurera Windows PowerShell-webbåtkomsten är att endast tillåta användare åtkomst till begränsade sessionsinställningar som gör att de kan utföra specifika uppgifter som de normalt behöver utföra på distans.

Cmdletarna som refereras i [Windows PowerShell-webbåtkomst-cmdlet: ar](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) gör det möjligt att skapa en uppsättning åtkomst regler som används för att auktorisera en användare på Windows PowerShell-webbåtkomst-gatewayen. Reglerna skiljer sig från åtkomst kontrol listorna (ACL) på mål datorn och ger ett extra säkerhets lager för webb åtkomst. Mer information om säkerhet beskrivs i följande avsnitt.

Om användarna inte kan skicka några av de föregående säkerhets lagren får de ett allmänt "åtkomst nekad"-meddelande i sina webbläsarfönster. Även om säkerhets information är inloggad på Gateway-servern, visas inte slutanvändarna information om hur många säkerhets lager de skickade, eller vid vilka skikt inloggnings-eller autentiseringsfel uppstod.

Mer information om hur du konfigurerar auktoriseringsregler finns i [Konfigurera auktoriseringsregler](#configuring-authorization-rules-and-site-security) i det här avsnittet.

### <a name="security"></a>Säkerhet

Windows PowerShell-webbåtkomstens säkerhets modell har fyra lager mellan en slutanvändare av den webbaserade-konsolen och en mål dator. Windows PowerShell Web Access-administratörer kan lägga till säkerhets lager genom ytterligare konfiguration i konsolen för IIS-hanteraren. Mer information om hur du skyddar webbplatser i IIS Manager-konsolen finns i [Konfigurera webb Server säkerhet (IIS7)](https://technet.microsoft.com/library/cc731278).

Mer information om metod tips för IIS och förhindrar DOS-attacker (Denial-of-Service) finns i [metod tips för att förhindra dos/denial of Service-attacker](https://technet.microsoft.com/library/cc750213).
En administratör kan också köpa och installera ytterligare program vara för Retail-autentisering.

I följande tabell beskrivs de fyra säkerhets nivåerna mellan slutanvändare och mål datorer.

|Nivå|Lager|
|-|-|
|1|[säkerhets funktioner i IIS-webbservern](#iis-web-server-security-features)|
|2|[Windows PowerShell Web Access Forms-baserad Gateway-autentisering](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[auktoriseringsregler för Windows PowerShell-Webbåtkomst](#windows-powershell-web-access-authorization-rules)|
|4|[mål regler för autentisering och auktorisering](#target-authentication-and-authorization-rules)|

Detaljerad information om varje lager hittar du under följande rubriker:

#### <a name="iis-web-server-security-features"></a>Säkerhets funktioner i IIS-webbservern

Windows PowerShell Web Access-användare måste alltid ange ett användar namn och lösen ord för att autentisera sina konton på gatewayen. Windows PowerShell Web Access-administratörer kan också aktivera eller inaktivera valfri autentisering av klient certifikat, se [Installera och använda Windows PowerShell-webbåtkomst](install-and-use-windows-powershell-web-access.md) för att aktivera ett test certifikat och senare, så här konfigurerar du ett äkta certifikat.

Den valfria klient certifikat funktionen kräver att slutanvändarna har ett giltigt klient certifikat, förutom deras användar namn och lösen ord, och är en del av konfigurationen av webb server (IIS). När klient certifikat skiktet är aktiverat uppmanas användarna att ange giltiga certifikat innan inloggnings uppgifterna utvärderas i Windows PowerShell-webbåtkomsten. Autentisering av klient certifikat kontrollerar automatiskt klient certifikatet. Om ett giltigt certifikat inte hittas informerar Windows PowerShell-webbåtkomsten användare, så att de kan tillhandahålla certifikatet. Om ett giltigt klient certifikat hittas öppnar Windows PowerShell-webbåtkomsten inloggnings sidan för användarna att ange sina användar namn och lösen ord.

Detta är ett exempel på ytterligare säkerhets inställningar som erbjuds av IIS-webbservern. Mer information om andra IIS-säkerhetsfunktioner finns i [Konfigurera webb Server säkerhet (IIS 7)](https://technet.microsoft.com/library/cc731278).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows PowerShell Web Access Forms-baserad Gateway-autentisering

Inloggnings sidan för Windows PowerShell-webbåtkomst kräver en uppsättning autentiseringsuppgifter (användar namn och lösen ord) och ger användarna möjlighet att ange olika autentiseringsuppgifter för mål datorn.
Om användaren inte anger alternativa autentiseringsuppgifter används även det primära användar namnet och lösen ordet som används för att ansluta till gatewayen för att ansluta till mål datorn.

De autentiseringsuppgifter som krävs autentiseras på Windows PowerShell-webbåtkomst-gatewayen. Autentiseringsuppgifterna måste vara giltiga användar konton på den lokala Windows PowerShell-webbåtkomsten Gateway-servern eller i Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Auktoriseringsregler för Windows PowerShell-Webbåtkomst

När en användare har autentiserats på gatewayen kontrollerar Windows PowerShell-webbåtkomsten auktoriseringsregler för att kontrol lera om användaren har åtkomst till den begärda mål datorn. Efter en lyckad auktorisering skickas användarens autentiseringsuppgifter tillsammans till mål datorn.

Dessa regler utvärderas bara när en användare har autentiserats av gatewayen och innan en användare kan autentiseras på en måldator.

#### <a name="target-authentication-and-authorization-rules"></a>Mål regler för autentisering och auktorisering

Det sista säkerhets lagret för Windows PowerShell-webbåtkomst är mål datorns egna säkerhets konfiguration. Användarna måste ha rätt åtkomst behörighet på mål datorn och även i Windows PowerShell-webbåtkomstens auktoriseringsregler för att köra en Windows PowerShell-webbaserad konsol som påverkar en måldator via Windows PowerShell-webbåtkomst.

Det här lagret erbjuder samma säkerhetsmekanismer som utvärderar anslutnings försök om användare försökte skapa en Windows PowerShell-fjärrsession till en måldator i Windows PowerShell genom att köra cmdletarna [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) eller [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession) .

Som standard använder Windows PowerShell-webbåtkomsten primärt användar namn och lösen ord för autentisering på både gatewayen och mål datorn. Den webbaserade inloggnings sidan i ett avsnitt med rubriken **valfria anslutnings inställningar**ger användarna möjlighet att ange olika autentiseringsuppgifter för mål datorn, om de behövs. Om användaren inte anger alternativa autentiseringsuppgifter används även det primära användar namnet och lösen ordet som används för att ansluta till gatewayen för att ansluta till mål datorn.

Auktoriseringsregler kan användas för att ge användare åtkomst till en viss konfiguration av sessionen. Du kan skapa _begränsade körnings utrymmen_ -eller sessionshantering för Windows PowerShell-webbåtkomst och tillåta att vissa användare endast ansluter till vissa konfigurationer när de loggar in på Windows PowerShell-webbåtkomst. Du kan använda åtkomst kontrol listor (ACL: er) för att avgöra vilka användare som har åtkomst till vissa slut punkter och ytterligare begränsa åtkomsten till slut punkten för en speciell uppsättning användare med hjälp av auktoriseringsregler som beskrivs i det här avsnittet. Mer information om begränsade körnings utrymmen finns i [skapa en begränsad körnings utrymme](/powershell/scripting/developer/hosting/creating-a-constrained-runspace).

### <a name="configuring-authorization-rules"></a>Konfigurera auktoriseringsregler

Administratörer vill förmodligen ha samma auktoriseringsregel för Windows PowerShell Web Access-användare som redan har definierats i deras miljö för fjärrhantering i Windows PowerShell. Den första proceduren i det här avsnittet beskriver hur du lägger till en regel för säker auktorisering som beviljar åtkomst till en användare, loggar in för att hantera en dator och inom en enda session-konfiguration. I den andra proceduren beskrivs hur du tar bort en auktoriseringsregel som inte längre behövs.

Om du planerar att använda anpassade sessionsinställningar för att tillåta att vissa användare endast arbetar inom begränsade körnings utrymmen i Windows PowerShell-webbåtkomst, skapar du dina anpassade sessionsnycklar innan du lägger till auktoriseringsregler som refererar till dem. Du kan inte använda Windows PowerShell-cmdletar för webb åtkomst för att skapa anpassade sessionsnycklar. Mer information om hur du skapar anpassade diskpartitionskonfigurationer finns [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Windows PowerShell-cmdletar för webb åtkomst stöder ett jokertecken, en \* asterisk (). Jokertecken i strängar stöds inte. Använd en enda asterisk per egenskap (användare, datorer eller sessioner).

> [!NOTE]
> Mer information om hur du kan använda auktoriseringsregler för att ge åtkomst till användare och skydda Windows PowerShell-webbåtkomsten finns i [andra exempel på auktoriseringsbeslut](#other-authorization-rule-scenario-examples) i den här artikeln.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Lägga till en restriktiv auktoriseringsregel

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter.

   - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitetsfältet och klickar sedan på **Kör som administratör**.

   - På **Start** skärmen i Windows högerklickar du på **Windows PowerShell**och klickar sedan på **Kör som administratör**.

2. **Valfritt steg** För att begränsa användar åtkomst med hjälp av sessionsbaserade:

   Kontrol lera att de sessionsinställningar som du vill använda redan finns i reglerna.

   Om de inte har skapats än använder du instruktioner för att skapa sessionsinställningar i [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Med den här auktoriseringsregeln kan en speciell användare få åtkomst till en dator i nätverket som de normalt har åtkomst till, med åtkomst till en speciell sessionsinformation som är begränsad till användarens typiska skript-och cmdlet-behov. Skriv följande kommando och tryck sedan på **Retur**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - I följande exempel beviljas en användare med namnet _JSmith_ i _contoso_ -domänen åtkomst till att hantera datorn _Contoso_214_och använda en sessionsnyckel som heter _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Kontrol lera att regeln har skapats genom att köra cmdleten **Get-PswaAuthorizationRule** eller `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`.
   Till exempel `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Ta bort en auktoriseringsregel

1. Om en Windows PowerShell-session inte redan är öppen, se steg 1 i [för att lägga till en restriktiv auktoriseringsregel](#to-add-a-restrictive-authorization-rule) i det här avsnittet.

2. Skriv följande och tryck sedan på **RETUR**, där *regel-ID* representerar det unika ID-numret för den regel som du vill ta bort.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Alternativt, om du inte känner till ID-numret, men känner till det egna namnet på regeln som du vill ta bort, kan du hämta namnet på regeln och skicka den till cmdlet: en `Remove-PswaAuthorizationRule` för att ta bort regeln, som visas i följande exempel:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> Du uppmanas inte att bekräfta om du vill ta bort den angivna auktoriseringsregeln. regeln tas bort när du trycker på **RETUR**. Se till att du vill ta bort auktoriseringsregeln innan du kör `Remove-PswaAuthorizationRule` cmdleten.

#### <a name="other-authorization-rule-scenario-examples"></a>Andra scenario exempel för auktoriseringsregler

Varje Windows PowerShell-session använder en konfiguration av sessionen. Om ingen har angetts för en session använder Windows PowerShell standard konfigurationen för den inbyggda Windows PowerShell-sessionen, som kallas Microsoft. PowerShell. Standard konfigurationen för sessionen innehåller alla cmdletar som är tillgängliga på en dator. Administratörer kan begränsa åtkomsten till alla datorer genom att definiera en sessionsinformation med en begränsad körnings utrymme (ett begränsat antal cmdlets och aktiviteter som användarna kan utföra). En användare som beviljas åtkomst till en dator med antingen fullständig språk åtkomst eller bara Windows PowerShell-fjärrhanterings-cmdlet: ar kan ansluta till andra datorer som är anslutna till den första datorn. Att definiera en begränsad körnings utrymme kan hindra användare från att komma åt andra datorer från sina tillåtna Windows PowerShell-körnings utrymme och förbättra säkerheten för din Windows PowerShell-webbåtkomst miljö. Konfigurationen av sessionen kan distribueras (med hjälp av grupprincip) till alla datorer som administratörer vill göra tillgängliga via Windows PowerShell-webbåtkomst. För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](/powershell/module/Microsoft.PowerShell.Core/About/about_session_configurations).
Här följer några exempel på det här scenariot.

- En administratör skapar en slut punkt som kallas **PswaEndpoint**, med en begränsad körnings utrymme. Sedan skapar administratören en regel, `*,*,PswaEndpoint`och distribuerar slut punkten till andra datorer. Regeln ger alla användare åtkomst till alla datorer med slut punkts **PswaEndpoint**.
  Om detta är den enda auktoriseringsregeln som definierats i regel uppsättningen skulle datorer utan den slut punkten inte vara tillgängliga.

- Administratören skapade en slut punkt med en begränsad körnings utrymme som kallas **PswaEndpoint**och vill begränsa åtkomsten till vissa användare. Administratören skapar en grupp av användare som kallas **Level1Support**och definierar följande regel: **Level1Support,\*, PswaEndpoint**. Regeln beviljar alla användare i gruppen **Level1Support** åtkomst till alla datorer med **PswaEndpoint** -konfigurationen. På samma sätt kan åtkomsten begränsas till en speciell uppsättning datorer.

- Vissa administratörer ger vissa användare mer åtkomst än andra. En administratör skapar till exempel två användar grupper, **Administratörer** och **BasicSupport**. Administratören skapar också en slut punkt med en begränsad körnings utrymme som kallas **PswaEndpoint**och definierar följande två regler: **admins,\*,\* ** och **BasicSupport,\*PswaEndpoint**. Den första regeln ger alla användare i **Administratörs** gruppen åtkomst till alla datorer och den andra regeln ger alla användare i gruppen **BasicSupport** endast åtkomst till de datorer som har **PswaEndpoint**.

- En administratör har konfigurerat en privat test miljö och vill tillåta alla auktoriserade nätverks användare åtkomst till alla datorer i nätverket som de normalt har åtkomst till, med åtkomst till alla sessionsbaserade som de normalt har åtkomst till. Eftersom det här är en privat test miljö skapar administratören en auktoriseringsregel som inte är säker. -Administratören kör cmdleten `Add-PswaAuthorizationRule * * *`, som använder jokertecknet **\*** för att representera alla användare, alla datorer och alla konfigurationer. – Den här regeln motsvarar följande: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Den här regeln rekommenderas inte i en säker miljö och kringgår säkerhets skiktet för auktorisering i Windows PowerShell-webbåtkomsten.

- En administratör måste tillåta användare att ansluta till mål datorerna i en miljö som innehåller både arbets grupper och domäner, där arbets grupps datorer ibland används för att ansluta till mål datorerna i domäner, och datorer i domäner används ibland för att ansluta till mål datorerna i arbets grupper. Administratören har en gateway-server, *PswaServer*, i en arbets grupp, och mål datorn *SRV1.contoso.com* finns i en domän. Användare *Christer* är en behörig lokal användare på både arbets gruppens Gateway-server och mål datorn. Sitt användar namn på arbets grupps servern är *chrisLocal*; och hans användar namn på mål datorn är *contoso\\Christer*. För att ge åtkomst till srv1.contoso.com för Christer lägger administratören till följande regel.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Föregående regel exempel autentiserar Christer på Gateway-servern och godkänner sedan sin åtkomst till *SRV1*. På inloggnings sidan måste Chris ange en andra uppsättning autentiseringsuppgifter i de **valfria anslutnings inställningarna** (*\\contoso Christer*). Gateway-servern använder ytterligare en uppsättning autentiseringsuppgifter för att autentisera honom på mål datorn, *SRV1.contoso.com*.

I föregående scenario upprättar Windows PowerShell-webbåtkomsten en lyckad anslutning till mål datorn förrän följande har lyckats och tillåts av minst en auktoriseringsregel.

1. Autentisering på arbets gruppens Gateway-server genom att lägga till ett användar namn i formatet *server_name*\\*user_name* till auktoriseringsregeln

2. Autentisering på mål datorn med hjälp av alternativa autentiseringsuppgifter som finns på inloggnings sidan i det **valfria anslutnings inställnings** avsnittet

   > [!NOTE]
   > Om gatewayen och mål datorerna finns i olika arbets grupper eller domäner måste en förtroende relation upprättas mellan de två arbets grupps datorerna, de två domänerna eller mellan arbets gruppen och domänen. Den här relationen kan inte konfigureras med hjälp av Windows PowerShell-cmdletar för Windows PowerShell-autentisering. Auktoriseringsregler definierar inte en förtroende relation mellan datorer. de kan bara tillåta användare att ansluta till specifika mål datorer och sessionsbaserade. Mer information om hur du konfigurerar en förtroende relation mellan olika domäner finns i [skapa domän-och skogs förtroenden](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794775(v=ws.10)).
   > Mer information om hur du lägger till arbets grupps datorer i en lista över betrodda värdar finns i [fjärrhantering med Serverhanteraren](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759202(v=ws.11)).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Använda en enda uppsättning auktoriseringsregler för flera platser

Auktoriseringsregler lagras i en XML-fil. Som standard är `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`Sök vägs namnet för XML-filen.

Sökvägen till Authorization Rules-XML-filen lagras i filen **powwa. config** , som finns i `$env:windir\Web\PowershellWebAccess\data`. Administratören har möjlighet att ändra referensen till standard Sök vägen i **powwa. config** för att passa inställningar eller krav. Genom att låta administratören ändra platsen för filen kan flera Windows PowerShell-webbåtkomst-gatewayer använda samma auktoriseringsregler, om en sådan konfiguration önskas.

## <a name="session-management"></a>Sessionshantering

Som standard begränsar Windows PowerShell-webbåtkomsten en användare till tre sessioner på en gång. Du kan redigera webb programmets **Web. config-** fil i IIS-hanteraren för att stödja ett annat antal sessioner per användare. Sökvägen till filen **Web. config** är `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

Som standard konfigureras IIS-webbservern för att starta om programpoolen om några inställningar redige ras. Programpoolen startas till exempel om om ändringar görs i **Web. config-** filen. >eftersom **Windows PowerShell-webbåtkomsten** använder InMemory-sessionstillstånd, kan >användare som är inloggade i **Windows PowerShell-webbåtkomst-** sessioner förlora sina sessioner när programpoolen startas om.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Ange standard parametrar på inloggnings Sidan

Om din Windows PowerShell-Gateway för webb åtkomst körs på Windows Server 2012 R2 kan du konfigurera standardvärden för de inställningar som visas på inloggnings sidan för Windows PowerShell-webbåtkomst. Du kan konfigurera värden i filen **Web. config** som beskrivs i föregående stycke. Standardvärden för inloggnings sidans inställningar finns i avsnittet **appSettings** i filen Web. config. följande är ett exempel på avsnittet **appSettings** . Giltiga värden för många av de här inställningarna är desamma som för motsvarande parametrar för cmdleten [New-PSSession](/powershell/module/Microsoft.PowerShell.Core/New-PSSession) i Windows PowerShell.

Till exempel är `defaultApplicationName` nyckeln, som du ser i följande kodblock, värdet för **$PSSessionApplicationName** preferens-variabeln på mål datorn.

```xml
  <appSettings>
      <add key="maxSessionsAllowedPerUser" value="3"/>
      <add key="defaultPortNumber" value="5985"/>
      <add key="defaultSSLPortNumber" value="5986"/>
      <add key="defaultApplicationName" value="WSMAN"/>
      <add key="defaultUseSslSelection" value="0"/>
      <add key="defaultAuthenticationType" value="0"/>
      <add key="defaultAllowRedirection" value="0"/>
      <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
  </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>Tids gränser och oplanerade från kopplingar

Tids gränsen nåddes för Windows PowerShell-webbåtkomstens sessioner. I Windows PowerShell-webbåtkomsten som körs på Windows Server 2012 visas ett timeout-meddelande för inloggade användare efter 15 minuters inaktivitet i sessionen. Om användaren inte svarar inom fem minuter efter det att tids gräns meddelandet visas, avslutas sessionen och användaren loggas ut. Du kan ändra timeout-perioder för sessioner i webbplats inställningarna i IIS-hanteraren.

I Windows PowerShell-webbåtkomsten som körs på Windows Server 2012 R2 är tids gränsen för sessioner som standard efter 20 minuters inaktivitet. Om användarna är frånkopplade från sessioner i den webbaserade konsolen på grund av nätverks fel eller andra oplanerade avstängningar eller fel, och inte eftersom de har stängt sessionerna, fortsätter Windows PowerShell-webbåtkomsten sessioner att köras, anslutna till mål datorerna tills tids gränsen på klient sidan går ut. Sessionen kopplas från efter antingen standardvärdet 20 minuter eller efter den tids gräns som anges av Gateway-administratören, beroende på vilket som är kortare.

Om Gateway-servern kör Windows Server 2012 R2 gör Windows PowerShell-webbåtkomsten att användarna återansluter till sparade sessioner vid ett senare tillfälle, men när nätverks fel, oplanerade avstängningar eller andra fel vid frånkopplade sessioner, kan användarna inte se eller återansluta till sparade sessioner förrän tids gränsen som angetts av Gateway-administratören har upphörde.

## <a name="see-also"></a>Se även

[Installera och använda Windows PowerShell-Webbåtkomst](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831611(v=ws.11))

[about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_Session_Configurations)

[Cmdletar för Windows PowerShell-Webbåtkomst](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
