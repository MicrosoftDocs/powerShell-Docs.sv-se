---
ms.date: 06/27/2017
keywords: PowerShell cmdlet
title: Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst
ms.openlocfilehash: 07b85a3c7bced58b9ee8db401f0339ba6011bc96
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268355"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst

Uppdaterad: Juni 24 2013

Gäller för: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell-webbåtkomst i Windows Server 2012 R2 och Windows Server 2012 har en begränsande säkerhetsmodell. Användarna måste uttryckligen beviljas åtkomst innan de kan logga in på Windows PowerShell Web Access-gateway och använda den webbaserade Windows PowerShell-konsolen.

## <a name="configuring-authorization-rules-and-site-security"></a>Konfigurera auktoriseringsregler och säkerhet för webbplatser

När Windows PowerShell Web Access har installerats och gatewayen har konfigurerats, kan användarna öppna på inloggningssidan i en webbläsare, men de kan inte logga in förrän Windows PowerShell Web Access-administratören ger dem uttrycklig åtkomst. ”Windows PowerShell Web Access-åtkomstkontroll hanteras med hjälp av uppsättning Windows PowerShell cmdlets som beskrivs i följande tabell. Det finns ingen jämförbar GUI för att lägga till eller hantera auktoriseringsregler.
Se [Windows PowerShell-cmdletar för webbåtkomst](cmdlets/web-access-cmdlets.md).

Administratörer kan definiera `{0-n}` authentication-regler för Windows PowerShell Web Access. Standardsäkerheten är begränsande i stället för tillåtande; noll autentiseringsregler innebär att ingen användare har åtkomst till något.

[Add-PswaAuthorizationRule](cmdlets/add-pswaauthorizationrule.md) och [Test-PswaAuthorizationRule](cmdlets/test-pswaauthorizationrule.md) i Windows Server 2012 R2 inkluderar en parameter för autentiseringsuppgifter som gör det möjligt att lägga till och testa Windows PowerShell-webbåtkomst auktoriseringsregler från en fjärransluten datorn, eller från inom en aktiv Windows PowerShell Web Access-session. Som med andra Windows PowerShell-cmdletar som har en parameter för autentiseringsuppgifter, kan du ange ett PSCredential-objekt som värde för parametern. Om du vill skapa ett PSCredential-objekt som innehåller autentiseringsuppgifter som du vill skicka till en fjärrdator, kör den [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) cmdlet.

Windows PowerShell Web Access authentication-regler är godkända regler. Varje regel är en definition av en tillåten anslutning mellan användare, måldatorer och viss Windows PowerShellÂ [sessionskonfigurationer](/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) (kallas också slutpunkter eller _körningsutrymmen_) på måldatorerna som angetts.
Förklaringar på **körningsutrymmen** Se [början användning av PowerShell Körningsutrymmen](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> En användare behöver endast att en regel är TRUE för att få åtkomst. Om en användare får åtkomst till en dator med antingen fullständig språkåtkomst eller endast åtkomst till Windows PowerShell-cmdletar för fjärrhantering, från den webbaserade konsolen kan användaren logga in (eller hopp) till andra datorer som är anslutna till den första måldatorn. Det säkraste sättet att konfigurera Windows PowerShell-webbåtkomst är att ge användarna åtkomst endast till begränsade sessionskonfigurationer som gör att de utför olika aktiviteter som normalt sett måste utföras med fjärranslutning.

De cmdletar som refereras i [Windows PowerShell-cmdletar för webbåtkomst](cmdlets/web-access-cmdlets.md) kunna skapa en uppsättning åtkomstregler som används för att auktorisera en användare på Windows PowerShell Web Access-gateway. Reglerna skiljer sig från åtkomstkontrollistor (ACL) på måldatorn och ger ett extra säkerhetslager för webbåtkomst. Mer information om säkerhet finns i följande avsnitt.

Om användarna inte kan skicka någon av de föregående säkerhetslagren, får de ett allmänt ”åtkomst nekad”-meddelande i sina webbläsarfönster. Även om säkerhetsinformation är loggad på gateway-servern, visas inte information om hur många säkerhetslager som skickades för slutanvändarna, ej heller på vilket lager inloggnings- eller autentiseringsfelet uppstod.

Mer information om hur du konfigurerar auktoriseringsregler finns i [konfigurera auktoriseringsregler](#configuring-authorization-rules-and-site-security) i det här avsnittet.

### <a name="security"></a>Säkerhet

Windows PowerShell Web Access-säkerhetsmodellen har fyra lager mellan en slutanvändare i den webbaserade konsolen och en måldator. Windows PowerShell Web Access-administratörer kan lägga till säkerhetslager via ytterligare konfiguration i IIS Manager-konsolen. Mer information om hur du skyddar webbplatser i IIS Manager-konsolen finns i [konfigurera säkerheten för webbservern (IIS7)](https://technet.microsoft.com/library/cc731278).

Mer information om IIS-metodtips och att förhindra denial of service-attacker, se [bästa praxis för att förhindra DoS/Denial of Service-attacker](https://technet.microsoft.com/library/cc750213).
En administratör kan också köpa och installera ytterligare programvara autentisering.

I följande tabell beskrivs de fyra säkerhetslagren mellan slutanvändare och måldatorer.

|Nivå|Lager|
|-|-|
|1|[IIS web server-säkerhetsfunktioner](#iis-web-server-security-features)|
|2|[Windows powershell web access-formulärbaserad gateway-autentisering](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[auktoriseringsregler för Windows powershell web access](#windows-powershell-web-access-authorization-rules)|
|4|[mål-autentisering och auktorisering regler](#target-authentication-and-authorization-rules)|

Detaljerad information om varje lager kan hittas under följande rubriker:

#### <a name="iis-web-server-security-features"></a>Säkerhetsfunktioner för IIS-webbserver

Windows PowerShell Web Access-användare måste alltid ange ett användarnamn och lösenord för att autentisera sina konton på gatewayen. Men Windows PowerShell Web Access-administratörer kan också aktivera autentisering av valfria klientcertifikat eller inaktivera, se [installera och använda windows powershell-webbåtkomst](install-and-use-windows-powershell-web-access.md) att aktivera ett testcertifikat och senare, hur du konfigurerar en äkta certifikat).

Funktionen för valfria klientcertifikat kräver att slutanvändarna har ett giltigt klientcertifikat, förutom sina användarnamn och lösenord, och att de ingår i konfigurationen av Webbserver (IIS). När lagret för klientcertifikatet är aktiverat uppmanas användaren att ange giltiga certifikat innan sina inloggningsuppgifter i Windows PowerShell Web Access inloggningssida. Autentiseringen av klientcertifikat kontrollerar automatiskt klientcertifikatet. Om ett giltigt certifikat hittas, informerar Windows PowerShell-webbåtkomst användare, så att de kan ange certifikatet. Om ett giltigt klientcertifikat hittas, öppnar inloggningssidan där användarna anger sina användarnamn och lösenord i Windows PowerShell Web Access.

Det här är ett exempel på ytterligare säkerhetsinställningar som erbjuds av IIS-webbserver. Mer information om andra IIS-säkerhetsfunktioner finns i [konfigurera Web Server-säkerhet (IIS 7)](https://technet.microsoft.com/library/cc731278).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows PowerShell-webbåtkomst formulärbaserad gateway-autentisering

Windows PowerShell Web Access-inloggningssidan kräver en uppsättning autentiseringsuppgifter (användarnamn och lösenord) och ger användarna möjlighet att ange olika autentiseringsuppgifter för måldatorn.
Om användaren inte tillhandahåller alternativa autentiseringsuppgifter används de primära användarnamn och lösenord som ansluter till gatewayen också för att ansluta till måldatorn.

De nödvändiga autentiseringsuppgifterna som autentiseras på gatewayen för Windows PowerShell Web Access. Dessa autentiseringsuppgifter måste vara giltiga användarkonton i antingen den lokala Windows PowerShell-webbåtkomst gateway-servern eller i Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Regler för Windows PowerShell-webbåtkomst

När en användare autentiseras på gatewayen, kontrollerar Windows PowerShell-webbåtkomst auktoriseringsregler för att kontrollera om användaren har åtkomst till den begärda måldatorn. Efter auktoriseringen skickas användarens autentiseringsuppgifter vidare till måldatorn.

Reglerna utvärderas bara när en användare har autentiserats av gatewayen och innan användaren kan autentiseras på en måldator.

#### <a name="target-authentication-and-authorization-rules"></a>Mål för autentisering och auktoriseringsregler

Det sista säkerhetslagret för Windows PowerShell-webbåtkomst är den target egna säkerhetskonfigurationen. Användarna måste ha lämpliga åtkomsträttigheter som konfigurerats på måldatorn och även i auktoriseringsregler Windows PowerShell-webbåtkomst att köra en Windows PowerShell-webbaserad konsol som påverkar en måldator via Windows PowerShell Web Access.

Lagret innehåller samma säkerhetsmekanismer som utvärderar anslutningsförsök om användarna försökte skapa en fjärransluten Windows PowerShell-session till en måldator från Windows PowerShell genom att köra den [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) eller [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession) cmdletar.

Som standard använder Windows PowerShell-webbåtkomst primära användarnamn och lösenord för autentisering på både gatewayen och måldatorn. Den webbaserade inloggningssidan, i avsnittet **valfria anslutningsinställningar**, får användarna möjlighet att ange olika autentiseringsuppgifter för måldatorn, om de behövs. Om användaren inte tillhandahåller alternativa autentiseringsuppgifter används de primära användarnamn och lösenord som ansluter till gatewayen också för att ansluta till måldatorn.

Auktoriseringsregler kan användas för att ge användarna åtkomst till en viss sessionskonfiguration. Du kan skapa _begränsade körningsutrymmen_ eller sessionskonfigurationer för Windows PowerShell-webbåtkomst och ge särskilda användare att ansluta till vissa specifika sessionskonfigurationer när de loggar in på Windows PowerShell Web Access. Du kan använda åtkomstkontrollistor (ACL) för att avgöra vilka användare som har åtkomst till specifika slutpunkter och ytterligare begränsa åtkomsten till slutpunkten för en specifik uppsättning användare genom att använda de auktoriseringsregler som beskrivs i det här avsnittet. Mer information om begränsade körningsutrymmen finns i [skapar en begränsad körningsutrymme](https://msdn.microsoft.com/library/dn614668).

### <a name="configuring-authorization-rules"></a>Konfigurera auktoriseringsregler

Administratörer vill troligen ha samma auktoriseringsregel för Windows PowerShell Web Access-användare som redan har definierats i sin miljö för Windows PowerShell remote management. I den första proceduren i det här avsnittet beskrivs hur du lägger till en regel för säker auktorisering. Den ger åtkomst till en användare som loggar in för att hantera en dator i en enda sessionskonfiguration. Den andra proceduren beskriver hur du tar bort en auktoriseringsregel som inte längre behövs.

Om du tänker använda anpassade konfigurationer för att tillåta specifika användare att arbeta i begränsade körningsutrymmen i Windows PowerShell Web Access kan du skapa dina anpassade konfigurationer innan du lägger till auktoriseringsregler som refererar till dem. Du kan inte använda Windows PowerShell Web Access-cmdlets för att skapa anpassade sessionskonfigurationer. Mer information om hur du skapar anpassade sessionskonfigurationer finns i [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Windows PowerShell Web Access-cmdletarna har stöd för ett jokertecken, en asterisk ( \* ). Jokertecken i strängar stöds inte. Använd en enda asterisk per egenskap (användare, datorer eller sessionskonfigurationer).

> [!NOTE]
> Fler sätt som du kan använda regler för att bevilja åtkomst till användare och säkra Windows PowerShell Web Access-miljö finns i [andra Scenarioexempel](#other-authorization-rule-scenario-examples) i det här avsnittet.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Så här lägger du till en regel för begränsad auktorisering

1. Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter.

   - Högerklicka på Windows-skrivbordet **Windows PowerShell** Aktivitetsfältet och klickar sedan på **Kör som administratör**.

   - På Windows **starta** högerklickar **Windows PowerShell**, och klicka sedan på **kör som administratör**.

2. **Valfritt steg** för att begränsa användaråtkomst med hjälp av sessionskonfigurationer:

   Kontrollera att de sessionskonfigurationer som du vill använda redan finns i dina regler.

   Om de inte ännu har skapats följer du instruktionerna för att skapa sessionskonfigurationer i [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Denna auktoriseringsregel ger en viss användaråtkomst till en dator i nätverket som de normalt har åtkomst till med åtkomst till en viss sessionskonfiguration som är begränsad till användaren '™ s vanliga skript och cmdlet-behov. Skriv följande och tryck sedan på **Ange**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - I följande exempel en användare med namnet _JSmith_ i den _Contoso_ domän beviljas åtkomst att hantera datorn _Contoso_214_, och använda en sessionskonfiguration med namnet _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Kontrollera att regeln har skapats genom att köra den **Get-PswaAuthorizationRule** cmdlet, eller `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`.
   Till exempel `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Så här tar du bort en auktoriseringsregel

1. Om en Windows PowerShell-session inte redan är öppen, se steg 1 i [att lägga till en regel för begränsad auktorisering](#to-add-a-restrictive-authorization-rule) i det här avsnittet.

2. Skriv följande och tryck sedan på **RETUR**, där *regel ID* representerar det unika ID-nummer för regeln som du vill ta bort.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Om du inte känner till ID-numret, men du vet det egna namnet för regeln som du vill ta bort, kan du hämta namnet på regeln och skicka det till `Remove-PswaAuthorizationRule`-cmdleten för att ta bort regeln, vilket visas i följande exempel:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
  ```

> [!NOTE]
> Du uppmanas inte att bekräfta om du vill ta bort den angivna regeln; regeln tas bort när du trycker på **RETUR**. Du måste vara säker på att du vill ta bort auktoriseringsregeln innan du kör cmdleten `Remove-PswaAuthorizationRule`.

#### <a name="other-authorization-rule-scenario-examples"></a>Andra scenarioexempel på auktoriseringsregler

Alla Windows PowerShell-session använder en sessionskonfiguration. Om en inte anges för en session, använder Windows PowerShell den inbyggda Windows PowerShell sessionskonfiguration som kallas Microsoft.PowerShell, som standard. Sessionens standardkonfiguration innehåller alla cmdletar som är tillgängliga på en dator. Administratörer kan begränsa åtkomsten till alla datorer genom att definiera en sessionskonfiguration med ett begränsat körningsutrymme (ett begränsat antal cmdletar och uppgifter som slutanvändarna kan utföra). En användare som beviljas åtkomst till en dator med antingen fullständig språkåtkomst eller endast Windows PowerShell fjärrhantering cmdlets kan ansluta till andra datorer som är anslutna till den första datorn. Definiera ett begränsat körningsutrymme kan förhindra användare från att komma åt andra datorer från sina tillåtna Windows PowerShell-körningsutrymme och förbättrar säkerheten för din Windows PowerShell Web Access-miljö. Sessionskonfigurationen kan distribueras (med hjälp av en grupprincip) till alla datorer som administratörerna vill göra tillgängliga via Windows PowerShell Web Access. Mer information om sessionskonfigurationer finns i [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx). Nedan följer några exempel på det här scenariot.

- En administratör skapar en slutpunkt som kallas **PswaEndpoint**, med ett begränsat körningsutrymme. Sedan skapar administratören en regel `*,*,PswaEndpoint`, och distribuerar slutpunkten till andra datorer. Regeln tillåter alla användare åtkomst till alla datorer med slutpunkten **PswaEndpoint**.
  Om detta är den enda auktoriseringsregeln som definieras i regeluppsättningen, kommer datorer utan den slutpunkten inte vara åtkomliga.

- Administratören har skapat en slutpunkt med ett begränsat körningsutrymme som kallas **PswaEndpoint**, och vill begränsa åtkomsten till specifika användare. Administratören skapar en grupp av användare som kallas **Level1Support**, och definierar följande regel: **Level1Support,\*, PswaEndpoint**. Den här regeln beviljar alla användare i gruppen **Level1Support** åtkomst till alla datorer med den **PswaEndpoint** konfiguration. På samma sätt kan åtkomst begränsas till en specifik uppsättning datorer.

- Vissa administratörer ger vissa användare mer åtkomst än andra. Exempelvis kan en administratör skapar två användargrupper, **administratörer** och **BasicSupport**. Administratören skapar även en slutpunkt med ett begränsat körningsutrymme som kallas **PswaEndpoint**, och definierar följande två regler: **administratörer,\*,\***  och  **BasicSupport,\*, PswaEndpoint**. Den första regeln ger alla användare i den **Admin** gruppåtkomst till alla datorer och den andra regeln ger alla användare i den **BasicSupport** åtkomst till de datorerna som har enbart  **PswaEndpoint**.

- En administratör har konfigurerat en privat testmiljö och vill ge alla auktoriserade nätverksanvändare åtkomst till alla datorer i nätverket som de normalt har åtkomst till, samt åtkomst alla sessionskonfigurationer som de normalt har åtkomst till. Eftersom det är en privat testmiljö skapar administratören en auktoriseringsregel som inte är säker. -Administratören kör cmdleten `Add-PswaAuthorizationRule * * *`, som använder jokertecknet **\*** att representera alla användare, alla datorer och alla konfigurationer. – Den här regeln motsvarar följande: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Den här regeln rekommenderas inte i en säker miljö och kringgår auktorisering regeln lager av säkerhet som tillhandahålls av Windows PowerShell Web Access.

- En administratör måste tillåta att användarna ansluter till måldatorerna i en miljö som innehåller både arbetsgrupper och domäner, där arbetsgruppsdatorer ibland används för att ansluta till måldatorerna i domäner och datorer i domäner ibland används för att ansluta till måldatorerna i arbetsgrupper. Administratören har en gateway-server *PswaServer*, i en arbetsgrupp och måldatorn *srv1.contoso.com* finns i en domän. Användaren *Chris* är en auktoriserad lokal användare av både arbetsgruppens gateway-server och måldatorn. Hans användarnamn på arbetsgruppsservern är *chrisLocal*; och hans användarnamn på måldatorn är *contoso\\chris*. För att ge åtkomst till srv1.contoso.com för Chris lägger administratören till följande regel.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

I föregående regelexempel autentiseras Chris på gateway-servern och därefter sin åtkomst till *srv1*. På sidan logga in måste Chris ange en annan uppsättning autentiseringsuppgifter i den **valfria anslutningsinställningar** området (*contoso\\chris*). Gateway-servern använder denna ytterligare uppsättning autentiseringsuppgifter för att autentisera honom på måldatorn, *srv1.contoso.com*.

I föregående fall upprättar en anslutning till måldatorn av Windows PowerShell-webbåtkomst förrän följande har lyckats och tillåts av minst en auktoriseringsregel.

1. Autentisering på arbetsgruppens gateway-server genom att lägga till ett användarnamn i formatet *server_name*\\*user_name* till auktoriseringsregeln

2. Autentisering på måldatorn med hjälp av alternativa autentiseringsuppgifter som anges på sidan logga in i den **valfria anslutningsinställningar** område

   > [!NOTE]
   > Om gatewayen och måldatorerna finns i olika arbetsgrupper eller domäner, måste en förtroenderelation upprättas mellan de två arbetsgruppsdatorerna, de två domänerna eller mellan arbetsgruppen och domänen. Den här relationen kan inte konfigureras med hjälp av Windows PowerShell-webbåtkomst cmdletar för auktoriseringsregeln. Auktoriseringsregler definierar inte en förtroenderelation mellan datorer. De kan bara auktorisera användare till att ansluta till specifika måldatorer och sessionskonfigurationer. Mer information om hur du konfigurerar en förtroenderelation mellan olika domäner finns i [skapa domän- och skogsförtroenden](https://technet.microsoft.com/library/cc794775.aspx).
   > Mer information om hur du lägger till arbetsgruppsdatorer i en lista med betrodda värdar finns i [fjärrhantering med Serverhanteraren](https://technet.microsoft.com/library/dd759202.aspx).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Använda en enda uppsättning auktoriseringsregler för flera platser

Auktoriseringsregler lagras i en XML-fil. Som standard är sökvägsnamnet för XML-filen `%windir%\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

Sökvägen till auktoriseringsreglernas XML-fil är lagrad i den **powwa.config** -fil som finns i `%windir%\Web\PowershellWebAccess\data`. Administratören har möjlighet att ändra referensen till standardsökvägen i **powwa.config** till inställningar eller krav. Administratören har möjlighet att ändra platsen för filen kan flera Windows PowerShell Web Access-gateways använda samma auktoriseringsregler, om en sådan konfiguration önskas.

## <a name="session-management"></a>Sessionshantering

Som standard begränsar Windows PowerShell-webbåtkomst en användare till tre sessioner samtidigt. Du kan redigera webbprogrammets **web.config** fil i IIS-hanteraren för att stödja ett annat antal sessioner per användare. Sökvägen till den **web.config** filen är `$Env:Windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

Som standard är IIS-webbservern konfigurerad för att starta om programpoolen om några inställningar redigeras. Till exempel programpoolen startas om ifall ändringar görs i **web.config** fil. > eftersom **Windows PowerShell-webbåtkomst** använder minnesinterna sessionstillstånd > användare loggat in på **Windows PowerShell-webbåtkomst** förlorar sina sessioner när programpoolen startas.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Ange standardparametrar på inloggningssidan

Om din Windows PowerShell Web Access-gateway körs på Windows Server 2012 R2 kan konfigurera du standardvärden för de inställningar som visas på inloggningssidan för Windows PowerShell Web Access. Du kan konfigurera värden i den **web.config** fil som beskrevs i föregående stycke. Standardvärdena för inloggningssidan-inställningar finns i den **appSettings** delen av filen web.config; följande är ett exempel på den **appSettings** avsnittet. Giltiga värden för många av de här inställningarna är samma som för motsvarande parametrar för den [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet i Windows PowerShell.

Till exempel den `defaultApplicationName` nyckeln, som visas i följande kodblock, är värdet för den **$PSSessionApplicationName** inställningsvariabeln på måldatorn.

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

Timeout för Windows PowerShell Web Access-sessioner. I Windows PowerShell Web Access som körs på Windows Server 2012, visas ett meddelande om timeout för inloggade användare efter 15 minuters inaktivitet i sessionen. Om användaren inte svarar inom fem minuter efter tidsgränsmeddelandet avslutas sessionen och användaren loggas ut. Du kan ändra tidsgränsperioderna för sessioner i webbplatsinställningarna i IIS-hanteraren.

I Windows PowerShell Web Access som körs på Windows Server 2012 R2, tidsgräns för sessioner, som standard efter 20 minuter av inaktivitet. Om användarna kopplas från sessioner i den webbaserade konsolen på grund av nätverksfel eller andra oplanerade avstängningar eller fel, och inte eftersom de har stängt sessionerna själva, Windows PowerShell Web Access-sessioner som fortsätter att köras, den är ansluten till måldatorerna, innan tidsgränsen på klientsidan uppnås. Sessionen kopplas från när antingen standardvärdet 20 minuter eller den tidsperiod som angetts av gateway-administratören uppnås, beroende på vilken som är kortast.

Om gateway-servern kör Windows Server 2012 R2, Windows PowerShell Web Access kan användarna ansluta på nytt till sparade sessioner vid ett senare tillfälle, men när nätverksfel, oplanerade avstängningar eller andra fel kan du koppla från sessioner, användare kan inte se eller återansluta till sparade sessioner förrän tidsgränsen som angetts av gateway-administratören har uppnåtts.

## <a name="see-also"></a>Se även

[Installera och använda Windows PowerShell-webbåtkomst](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Windows PowerShell-cmdletar för Webbåtkomst](cmdlets/web-access-cmdlets.md)