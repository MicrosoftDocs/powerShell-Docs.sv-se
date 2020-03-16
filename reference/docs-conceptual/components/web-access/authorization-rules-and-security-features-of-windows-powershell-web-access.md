---
ms.date: 06/27/2017
keywords: PowerShell, cmdlet
title: Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst
ms.openlocfilehash: c426b8cfb10829241ba244a5d840c91e1de9f66e
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79407037"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst

Uppdaterad: 24 juni 2013

Gäller för: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell-webbåtkomsten i Windows Server 2012 R2 och Windows Server 2012 har en begränsad säkerhets modell. Användare måste uttryckligen beviljas åtkomst innan de kan logga in på Windows PowerShell Web Access Gateway och använda den webbaserade Windows PowerShell-konsolen.

## <a name="configuring-authorization-rules-and-site-security"></a>Konfigurera auktoriseringsregler och säkerhet för webbplatser

När Windows PowerShell-webbåtkomsten har installerats och gatewayen har kon figurer ATS kan användarna öppna inloggnings sidan i en webbläsare, men de kan inte logga in förrän Windows PowerShell-administratören ger användare åtkomst uttryckligen. Åtkomst kontrollen för Windows PowerShell-webbåtkomst hanteras med hjälp av en uppsättning Windows PowerShell-cmdlets som beskrivs i följande tabell. Det finns ingen jämförbar GUI för att lägga till eller hantera auktoriseringsregler.
Se [cmdlets för Windows PowerShell-webbåtkomst](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Administratörer kan definiera regler för `{0-n}` autentisering för Windows PowerShell-webbåtkomst. Standardsäkerheten är begränsande i stället för tillåtande; noll autentiseringsregler innebär att ingen användare har åtkomst till något.

[Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) och [test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) i Windows Server 2012 R2 innehåller en parameter för autentiseringsuppgifter som gör att du kan lägga till och testa auktoriseringsregler för Windows PowerShell-webbåtkomsten från en fjärrdator eller från en aktiv Windows PowerShell-webbapp. Precis som med andra Windows PowerShell-cmdletar som har en parameter för autentiseringsuppgifter kan du ange ett PSCredential-objekt som värde för parametern. Om du vill skapa ett PSCredential-objekt som innehåller autentiseringsuppgifter som du vill skicka till en fjärrdator kör du cmdleten [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) .

Vitlista-regler är regler för Windows PowerShell-autentisering. Varje regel är en definition av en tillåten anslutning mellan användare, mål datorer och särskilda konfigurationer för Windows PowerShell- [sessioner](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) (kallas även slut punkter eller _körnings utrymmen_) på angivna mål datorer.
En förklaring om **körnings utrymmen** finns i [Starta användning av PowerShell-körnings utrymmen](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> En användare behöver endast att en regel är TRUE för att få åtkomst. Om en användare får åtkomst till en dator med antingen fullständig språk åtkomst eller enbart åtkomst till Windows PowerShell-cmdletar för fjärrhantering från den webbaserade konsolen, kan användaren logga in (eller hopp) till andra datorer som är anslutna till den första mål datorn. Det säkraste sättet att konfigurera Windows PowerShell-webbåtkomsten är att endast tillåta användare åtkomst till begränsade sessionsinställningar som gör att de kan utföra specifika uppgifter som de normalt behöver utföra på distans.

Cmdletarna som refereras i [Windows PowerShell-webbåtkomst-cmdlet: ar](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) gör det möjligt att skapa en uppsättning åtkomst regler som används för att auktorisera en användare på Windows PowerShell-webbåtkomst-gatewayen. Reglerna skiljer sig från åtkomstkontrollistor (ACL) på måldatorn och ger ett extra säkerhetslager för webbåtkomst. Mer information om säkerhet finns i följande avsnitt.

Om användarna inte kan skicka några av de föregående säkerhets lagren får de ett allmänt "åtkomst nekad"-meddelande i sina webbläsarfönster. Även om säkerhetsinformation är loggad på gateway-servern, visas inte information om hur många säkerhetslager som skickades för slutanvändarna, ej heller på vilket lager inloggnings- eller autentiseringsfelet uppstod.

Mer information om hur du konfigurerar auktoriseringsregler finns i [Konfigurera auktoriseringsregler](#configuring-authorization-rules-and-site-security) i det här avsnittet.

### <a name="security"></a>Säkerhet

Windows PowerShell-webbåtkomstens säkerhets modell har fyra lager mellan en slutanvändare av den webbaserade-konsolen och en mål dator. Windows PowerShell Web Access-administratörer kan lägga till säkerhets lager genom ytterligare konfiguration i konsolen för IIS-hanteraren. Mer information om hur du skyddar webbplatser i IIS Manager-konsolen finns i [Konfigurera webb Server säkerhet (IIS7)](https://technet.microsoft.com/library/cc731278).

Mer information om metod tips för IIS och förhindrar DOS-attacker (Denial-of-Service) finns i [metod tips för att förhindra dos/denial of Service-attacker](https://technet.microsoft.com/library/cc750213).
En administratör kan också köpa och installera ytterligare program vara för Retail-autentisering.

I följande tabell beskrivs de fyra säkerhetslagren mellan slutanvändare och måldatorer.

|Nivå|Lager|
|-|-|
|1|[säkerhets funktioner i IIS-webbservern](#iis-web-server-security-features)|
|2|[Windows PowerShell Web Access Forms-baserad Gateway-autentisering](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[auktoriseringsregler för Windows PowerShell-Webbåtkomst](#windows-powershell-web-access-authorization-rules)|
|4|[mål regler för autentisering och auktorisering](#target-authentication-and-authorization-rules)|

Detaljerad information om varje lager hittar du under följande rubriker:

#### <a name="iis-web-server-security-features"></a>Säkerhets funktioner i IIS-webbservern

Windows PowerShell Web Access-användare måste alltid ange ett användar namn och lösen ord för att autentisera sina konton på gatewayen. Windows PowerShell Web Access-administratörer kan också aktivera eller inaktivera valfri autentisering av klient certifikat, se [Installera och använda Windows PowerShell-webbåtkomst](install-and-use-windows-powershell-web-access.md) för att aktivera ett test certifikat och senare, så här konfigurerar du ett äkta certifikat.

Funktionen för valfria klientcertifikat kräver att slutanvändarna har ett giltigt klientcertifikat, förutom sina användarnamn och lösenord, och att de ingår i konfigurationen av Webbserver (IIS). När klient certifikat skiktet är aktiverat uppmanas användarna att ange giltiga certifikat innan inloggnings uppgifterna utvärderas i Windows PowerShell-webbåtkomsten. Autentiseringen av klientcertifikat kontrollerar automatiskt klientcertifikatet. Om ett giltigt certifikat inte hittas informerar Windows PowerShell-webbåtkomsten användare, så att de kan tillhandahålla certifikatet. Om ett giltigt klient certifikat hittas öppnar Windows PowerShell-webbåtkomsten inloggnings sidan för användarna att ange sina användar namn och lösen ord.

Detta är ett exempel på ytterligare säkerhets inställningar som erbjuds av IIS-webbservern. Mer information om andra IIS-säkerhetsfunktioner finns i [Konfigurera webb Server säkerhet (IIS 7)](https://technet.microsoft.com/library/cc731278).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows PowerShell Web Access Forms-baserad Gateway-autentisering

Inloggnings sidan för Windows PowerShell-webbåtkomst kräver en uppsättning autentiseringsuppgifter (användar namn och lösen ord) och ger användarna möjlighet att ange olika autentiseringsuppgifter för mål datorn.
Om användaren inte tillhandahåller alternativa autentiseringsuppgifter används de primära användarnamn och lösenord som ansluter till gatewayen också för att ansluta till måldatorn.

De autentiseringsuppgifter som krävs autentiseras på Windows PowerShell-webbåtkomst-gatewayen. Autentiseringsuppgifterna måste vara giltiga användar konton på den lokala Windows PowerShell-webbåtkomsten Gateway-servern eller i Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Auktoriseringsregler för Windows PowerShell-Webbåtkomst

När en användare har autentiserats på gatewayen kontrollerar Windows PowerShell-webbåtkomsten auktoriseringsregler för att kontrol lera om användaren har åtkomst till den begärda mål datorn. Efter en lyckad auktorisering skickas användarens autentiseringsuppgifter tillsammans till mål datorn.

Reglerna utvärderas bara när en användare har autentiserats av gatewayen och innan användaren kan autentiseras på en måldator.

#### <a name="target-authentication-and-authorization-rules"></a>Mål för autentisering och auktoriseringsregler

Det sista säkerhets lagret för Windows PowerShell-webbåtkomst är mål datorns egna säkerhets konfiguration. Användarna måste ha rätt åtkomst behörighet på mål datorn och även i Windows PowerShell-webbåtkomstens auktoriseringsregler för att köra en Windows PowerShell-webbaserad konsol som påverkar en måldator via Windows PowerShell-webbåtkomst.

Det här lagret erbjuder samma säkerhetsmekanismer som utvärderar anslutnings försök om användare försökte skapa en Windows PowerShell-fjärrsession till en måldator i Windows PowerShell genom att köra cmdletarna [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) eller [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession) .

Som standard använder Windows PowerShell-webbåtkomsten primärt användar namn och lösen ord för autentisering på både gatewayen och mål datorn. På den webbaserade inloggningssidan, i avsnittet **Valfria anslutningsinställningar**, får användarna möjlighet att ange olika autentiseringsuppgifter till måldatorn, om det behövs. Om användaren inte tillhandahåller alternativa autentiseringsuppgifter används de primära användarnamn och lösenord som ansluter till gatewayen också för att ansluta till måldatorn.

Auktoriseringsregler kan användas för att ge användarna åtkomst till en viss sessionskonfiguration. Du kan skapa _begränsade körnings utrymmen_ -eller sessionshantering för Windows PowerShell-webbåtkomst och tillåta att vissa användare endast ansluter till vissa konfigurationer när de loggar in på Windows PowerShell-webbåtkomst. Du kan använda åtkomstkontrollistor (ACL) för att avgöra vilka användare som har åtkomst till specifika slutpunkter och ytterligare begränsa åtkomsten till slutpunkten för en specifik uppsättning användare genom att använda de auktoriseringsregler som beskrivs i det här avsnittet. Mer information om begränsade körnings utrymmen finns i [skapa en begränsad körnings utrymme](https://msdn.microsoft.com/library/dn614668).

### <a name="configuring-authorization-rules"></a>Konfigurera auktoriseringsregler

Administratörer vill förmodligen ha samma auktoriseringsregel för Windows PowerShell Web Access-användare som redan har definierats i deras miljö för fjärrhantering i Windows PowerShell. I den första proceduren i det här avsnittet beskrivs hur du lägger till en regel för säker auktorisering. Den ger åtkomst till en användare som loggar in för att hantera en dator i en enda sessionskonfiguration. Den andra proceduren beskriver hur du tar bort en auktoriseringsregel som inte längre behövs.

Om du planerar att använda anpassade sessionsinställningar för att tillåta att vissa användare endast arbetar inom begränsade körnings utrymmen i Windows PowerShell-webbåtkomst, skapar du dina anpassade sessionsnycklar innan du lägger till auktoriseringsregler som refererar till dem. Du kan inte använda Windows PowerShell-cmdletar för webb åtkomst för att skapa anpassade sessionsnycklar. Mer information om hur du skapar anpassade diskpartitionskonfigurationer finns [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Windows PowerShell-cmdletar för webb åtkomst stöder ett jokertecken, en asterisk (\*). Jokertecken i strängar stöds inte. Använd en enda asterisk per egenskap (användare, datorer eller sessionskonfigurationer).

> [!NOTE]
> Mer information om hur du kan använda auktoriseringsregler för att ge åtkomst till användare och skydda Windows PowerShell-webbåtkomsten finns i [andra exempel på auktoriseringsbeslut](#other-authorization-rule-scenario-examples) i den här artikeln.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Så här lägger du till en regel för begränsad auktorisering

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användar rättigheter.

   - På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitets fältet och klickar sedan på **Kör som administratör**.

   - På Windows **start**skärm högerklickar du på **Windows PowerShell** och klickar sedan på **Kör som administratör**.

2. **Valfritt steg** För att begränsa användar åtkomst med hjälp av sessionsbaserade:

   Kontrol lera att de sessionsinställningar som du vill använda redan finns i reglerna.

   Om de inte har skapats än använder du instruktioner för att skapa sessionsinställningar i [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Med den här auktoriseringsregeln kan en speciell användare få åtkomst till en dator i nätverket som de normalt har åtkomst till, med åtkomst till en speciell sessionsinformation som är begränsad till användaren™ s typiska skript-och cmdlet-behov. Skriv följande och tryck sedan på **RETUR**.

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

#### <a name="to-remove-an-authorization-rule"></a>Så här tar du bort en auktoriseringsregel

1. Om en Windows PowerShell-session inte redan är öppen, se steg 1 i [för att lägga till en restriktiv auktoriseringsregel](#to-add-a-restrictive-authorization-rule) i det här avsnittet.

2. Skriv följande och tryck sedan på **Retur**, där *regel-ID* representerar det unika ID-numret för regeln som du vill ta bort.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Om du inte känner till ID-numret, men du vet det egna namnet för regeln som du vill ta bort, kan du hämta namnet på regeln och skicka det till `Remove-PswaAuthorizationRule`-cmdleten för att ta bort regeln, vilket visas i följande exempel:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> Du uppmanas inte att bekräfta om du vill ta bort den angivna regeln, utan regeln tas bort när du trycker på **Retur**. Du måste vara säker på att du vill ta bort auktoriseringsregeln innan du kör cmdleten `Remove-PswaAuthorizationRule`.

#### <a name="other-authorization-rule-scenario-examples"></a>Andra scenarioexempel på auktoriseringsregler

Varje Windows PowerShell-session använder en konfiguration av sessionen. Om ingen har angetts för en session använder Windows PowerShell standard konfigurationen för den inbyggda Windows PowerShell-sessionen, som kallas Microsoft. PowerShell. Sessionens standardkonfiguration innehåller alla cmdletar som är tillgängliga på en dator. Administratörer kan begränsa åtkomsten till alla datorer genom att definiera en sessionskonfiguration med ett begränsat körningsutrymme (ett begränsat antal cmdletar och uppgifter som slutanvändarna kan utföra). En användare som beviljas åtkomst till en dator med antingen fullständig språk åtkomst eller bara Windows PowerShell-fjärrhanterings-cmdlet: ar kan ansluta till andra datorer som är anslutna till den första datorn. Att definiera en begränsad körnings utrymme kan hindra användare från att komma åt andra datorer från sina tillåtna Windows PowerShell-körnings utrymme och förbättra säkerheten för din Windows PowerShell-webbåtkomst miljö. Konfigurationen av sessionen kan distribueras (med hjälp av grupprincip) till alla datorer som administratörer vill göra tillgängliga via Windows PowerShell-webbåtkomst. Mer information om sessionsinställningar finns [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx). Nedan följer några exempel på det här scenariot.

- En administratör skapar en slutpunkt som kallas **PswaEndpoint**, med ett begränsat körningsutrymme. Sedan skapar administratören en regel, `*,*,PswaEndpoint`och distribuerar slut punkten till andra datorer. Med regeln kan alla användare få åtkomst till alla datorer med slutpunkten **PswaEndpoint**.
  Om detta är den enda auktoriseringsregeln som definieras i regeluppsättningen, kommer datorer utan den slutpunkten inte vara åtkomliga.

- Administratören har skapat en slutpunkt med ett begränsat körningsutrymme som kallas **PswaEndpoint** och vill begränsa åtkomsten till särskilda användare. Administratören skapar en grupp av användare som kallas **Level1Support**och definierar följande regel: **Level1Support,\*, PswaEndpoint**. Den här regeln beviljar alla användare i gruppen **Level1Support** åtkomst till alla datorer med konfigurationen **PswaEndpoint**. På samma sätt kan åtkomst begränsas till en specifik uppsättning datorer.

- Vissa administratörer ger vissa användare mer åtkomst än andra. Till exempel skapar administratören två användargrupper, **Admins** och **BasicSupport**. Administratören skapar också en slut punkt med en begränsad körnings utrymme som kallas **PswaEndpoint**och definierar följande två regler: **admins,\*,\*** och **BasicSupport,\*, PswaEndpoint**. Den första regeln ger alla användare i gruppen **Admin** åtkomst till alla datorer och den andra regeln ger alla användare i gruppen **BasicSupport** åtkomst till enbart datorerna med **PswaEndpoint**.

- En administratör har konfigurerat en privat testmiljö och vill ge alla auktoriserade nätverksanvändare åtkomst till alla datorer i nätverket som de normalt har åtkomst till, samt åtkomst alla sessionskonfigurationer som de normalt har åtkomst till. Eftersom det är en privat testmiljö skapar administratören en auktoriseringsregel som inte är säker. -Administratören kör cmdleten `Add-PswaAuthorizationRule * * *`, som använder jokertecknet **\*** för att representera alla användare, alla datorer och alla konfigurationer. – Den här regeln motsvarar följande: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Den här regeln rekommenderas inte i en säker miljö och kringgår säkerhets skiktet för auktorisering i Windows PowerShell-webbåtkomsten.

- En administratör måste tillåta att användarna ansluter till måldatorerna i en miljö som innehåller både arbetsgrupper och domäner, där arbetsgruppsdatorer ibland används för att ansluta till måldatorerna i domäner och datorer i domäner ibland används för att ansluta till måldatorerna i arbetsgrupper. Administratören har en gateway-server, *PswaServer*, i en arbetsgrupp och måldatorn *srv1.contoso.com* i en domän. Användaren *Chris* är en auktoriserad lokal användare av både arbetsgruppens gateway-server och måldatorn. Sitt användar namn på arbets grupps servern är *chrisLocal*; och hans användar namn på mål datorn är *contoso\\Christer*. För att ge åtkomst till srv1.contoso.com för Chris lägger administratören till följande regel.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

I föregående regelexempel autentiseras Chris på gateway-servern och därefter åtkomsten till *srv1*. På inloggnings sidan måste Chris ange en andra uppsättning autentiseringsuppgifter i de **valfria anslutnings inställningarna** (*contoso\\Christer*). Gateway-servern använder denna ytterligare uppsättning autentiseringsuppgifter för att autentisera honom på måldatorn, *srv1.contoso.com*.

I föregående scenario upprättar Windows PowerShell-webbåtkomsten en lyckad anslutning till mål datorn förrän följande har lyckats och tillåts av minst en auktoriseringsregel.

1. Autentisering på arbets gruppens Gateway-server genom att lägga till ett användar namn i formatet *server_name*\\*user_name* till auktoriseringsregeln

2. Autentisering på måldatorn med hjälp av alternativa autentiseringsuppgifter som anges på inloggningssidan i **Valfria anslutningsinställningar**

   > [!NOTE]
   > Om gatewayen och måldatorerna finns i olika arbetsgrupper eller domäner, måste en förtroenderelation upprättas mellan de två arbetsgruppsdatorerna, de två domänerna eller mellan arbetsgruppen och domänen. Den här relationen kan inte konfigureras med hjälp av Windows PowerShell-cmdletar för Windows PowerShell-autentisering. Auktoriseringsregler definierar inte en förtroenderelation mellan datorer. De kan bara auktorisera användare till att ansluta till specifika måldatorer och sessionskonfigurationer. Mer information om hur du konfigurerar en förtroende relation mellan olika domäner finns i [skapa domän-och skogs förtroenden](https://technet.microsoft.com/library/cc794775.aspx).
   > Mer information om hur du lägger till arbets grupps datorer i en lista över betrodda värdar finns i [fjärrhantering med Serverhanteraren](https://technet.microsoft.com/library/dd759202.aspx).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Använda en enda uppsättning auktoriseringsregler för flera platser

Auktoriseringsregler lagras i en XML-fil. Som standard är Sök vägs namnet för XML-filen `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

Sökvägen till Authorization Rules-XML-filen lagras i filen **powwa. config** , som finns i `$env:windir\Web\PowershellWebAccess\data`. Administratören har möjlighet att ändra referens till standardsökvägen i **powwa.config** för att anpassa till inställningar eller krav. Genom att låta administratören ändra platsen för filen kan flera Windows PowerShell-webbåtkomst-gatewayer använda samma auktoriseringsregler, om en sådan konfiguration önskas.

## <a name="session-management"></a>Sessionshantering

Som standard begränsar Windows PowerShell-webbåtkomsten en användare till tre sessioner på en gång. Du kan redigera webb programmets **Web. config-** fil i IIS-hanteraren för att stödja ett annat antal sessioner per användare. Sökvägen till filen **Web. config** är `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

Som standard konfigureras IIS-webbservern för att starta om programpoolen om några inställningar redige ras. Programpoolen startas till exempel om om ändringar görs i **Web. config-** filen. > eftersom **Windows PowerShell-webbåtkomsten** använder InMemory-sessionstillstånd, kan > användare som är inloggade i **Windows PowerShell-webbåtkomst-** sessioner förlora sina sessioner när programpoolen startas om.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Ange standardparametrar på inloggningssidan

Om din Windows PowerShell-Gateway för webb åtkomst körs på Windows Server 2012 R2 kan du konfigurera standardvärden för de inställningar som visas på inloggnings sidan för Windows PowerShell-webbåtkomst. Du kan konfigurera värden i filen **Web. config** som beskrivs i föregående stycke. Standardvärdena för inloggningssidans inställningar finns i avsnittet **appSettings** i filen web.config. Följande är ett exempel från **appSettings**-avsnittet. Giltiga värden för många av de här inställningarna är desamma som för motsvarande parametrar för cmdleten [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) i Windows PowerShell.

Till exempel är `defaultApplicationName`-nyckeln, som visas i följande kodblock, värdet för variabeln **$PSSessionApplicationName** preferens på mål datorn.

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

### <a name="time-outs-and-unplanned-disconnections"></a>Tidsgränser och oplanerade frånkopplingar

Tids gränsen nåddes för Windows PowerShell-webbåtkomstens sessioner. I Windows PowerShell-webbåtkomsten som körs på Windows Server 2012 visas ett timeout-meddelande för inloggade användare efter 15 minuters inaktivitet i sessionen. Om användaren inte svarar inom fem minuter efter det att tids gräns meddelandet visas, avslutas sessionen och användaren loggas ut. Du kan ändra timeout-perioder för sessioner i webbplats inställningarna i IIS-hanteraren.

I Windows PowerShell-webbåtkomsten som körs på Windows Server 2012 R2 är tids gränsen för sessioner som standard efter 20 minuters inaktivitet. Om användarna är frånkopplade från sessioner i den webbaserade konsolen på grund av nätverks fel eller andra oplanerade avstängningar eller fel, och inte eftersom de har stängt sessionerna, fortsätter Windows PowerShell-webbåtkomsten sessioner att köras, ansluten till mål datorerna tills timeout-tiden på klient sidan går ut. Sessionen kopplas från när antingen standardvärdet 20 minuter eller den tidsperiod som angetts av gateway-administratören uppnås, beroende på vilken som är kortast.

Om Gateway-servern kör Windows Server 2012 R2 gör Windows PowerShell-webbåtkomsten att användarna återansluter till sparade sessioner vid ett senare tillfälle, men när nätverks fel, oplanerade avstängningar eller andra fel vid frånkopplade sessioner, kan användarna inte se eller återansluta till sparat sessioner fram till dess att tids gräns perioden som anges av Gateway-administratören har upphörde.

## <a name="see-also"></a>Se även

[Installera och använda Windows PowerShell-Webbåtkomst](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Cmdletar för Windows PowerShell-Webbåtkomst](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
