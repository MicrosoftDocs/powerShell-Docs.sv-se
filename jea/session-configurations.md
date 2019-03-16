---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: JEA Sessionskonfigurationer
ms.openlocfilehash: b98726ea7ed3aabdfd05034c3b70118e327160cd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056608"
---
# <a name="jea-session-configurations"></a>JEA Sessionskonfigurationer

> Gäller för: Windows PowerShell 5.0

En JEA-slutpunkt har registrerats i ett system genom att skapa och registrera en konfigurationsfil för PowerShell-session på ett visst sätt.
Sessionskonfigurationer fastställa *som* kan använda JEA-slutpunkt och vilka roller de har åtkomst till.
De kan också definiera globala inställningar som gäller för användare av en roll i JEA-session.

Det här avsnittet beskriver hur du skapar en konfigurationsfil för PowerShell-session och registrera en JEA-slutpunkt.

## <a name="create-a-session-configuration-file"></a>Skapa en konfigurationsfil för session

Du måste ange hur att slutpunkten ska konfigureras för att registrera en JEA-slutpunkt.
Det finns många alternativ att överväga här det viktigaste för vilka som ska ha åtkomst till JEA-slutpunkt, vilka roller kommer de tilldelas, vilken identitet JEA använder under försättsbladen och vad är namnet på JEA-slutpunkt.
Dessa definieras i en PowerShell-session konfigurationsfil, vilket är en PowerShell-datafil som slutar med filnamnstillägget .pssc.

Kör följande kommando för att skapa en konfigurationsfil för stommen session för JEA-slutpunkter.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Endast de vanligaste konfigurationsalternativ som ingår i filen stommen som standard.
> Använd den `-Full` växel för att ta med alla tillämpliga inställningar i den genererade PSSC.

Du kan öppna konfigurationsfilen session i en textredigerare.
Den `-SessionType RestrictedRemoteServer` fält anger att sessionskonfigurationen ska användas av JEA för säker hantering.
Sessioner som konfigureras på det här sättet kommer att fungera i [NoLanguage läge](https://technet.microsoft.com/library/dn433292.aspx) och får bara innehålla följande standardkommandon för 8 (och alias) tillgängliga:

- Clear-värd (cls, rensa)
- Avsluta-PSSession (exsn, avsluta)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Måttobjektet (mått)
- Out-Default
- Select-Object (Välj)

Inga PowerShell-providers är tillgängliga, och inte heller några externa program (körbara filer, skript osv.).

Det finns flera andra fält som du vill konfigurera för JEA-sessionen.
De beskrivs i följande avsnitt.

### <a name="choose-the-jea-identity"></a>Välj JEA-identitet

JEA måste en identitet (konto) du använder när du kör en anslutna användare kommandon i bakgrunden.
Du bestämmer dig för vilken identitet JEA används i konfigurationsfilen för sessionen.

#### <a name="local-virtual-account"></a>Lokala virtuellt konto

Om de roller som stöds av den här JEA-slutpunkt används för att hantera den lokala datorn och ett lokalt administratörskonto räcker för att köra kommandona har, bör du konfigurera JEA om du vill använda ett lokalt virtuellt konto.
Virtuella konton är tillfälliga konton som är unika för en viss användare och endast senaste under av sina PowerShell-session.
På en medlemsserver eller arbetsstation virtuella konton som hör till den lokala datorn **administratörer** gruppen och har åtkomst till de flesta systemresurser.
På en Active Directory-domänkontrollant, virtuella konton tillhör domänens **Domänadministratörer** grupp.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Om de roller som stöds av sessionskonfigurationen inte behöver sådan bred privilegier, kan du ange de säkerhetsgrupper som virtuellt konto ska tillhöra.
De angivna säkerhetsgrupperna måste vara lokala grupper, inte grupper från en domän på en medlemsserver eller arbetsstation.

När du anger en eller flera säkerhetsgrupper virtuellt konto kommer inte längre tillhör gruppen lokala administratörer.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Virtuella konton beviljas tillfälligt inloggningen som en tjänst direkt i den lokala server säkerhetsprincipen.  Om en av VirtualAccountGroups som angetts har redan beviljats den här behörigheten i principen, kommer inte längre individuella virtuella konto har lagts till och tas bort från principen.  Detta kan vara användbart i scenarier, till exempel domänkontrollanter där ändringar i den säkerhetsprincip för domänkontrollanter granskas noggrant.  Detta är endast tillgängligt i Windows Server 2016 med November 2018 eller senare samlad och Windows Server 2019 med januari 2019 eller senare samlad.

#### <a name="group-managed-service-account"></a>Grupphanterat tjänstkonto


För scenarier som kräver JEA-användare att komma åt nätverksresurser, till exempel andra datorer eller webbtjänster, är ett grupphanterade tjänstkonto (gMSA) en lämpligare identitet för att använda.
gMSA-konton får du en domänidentitet som kan användas för att autentisera mot resurser på en dator i domänen.
Rättigheterna i gMSA ger du bestäms av resurserna som du ansluter till.
Du har automatiskt inte administratörsrättigheter på alla datorer eller tjänster, såvida inte datorn/tjänstadministratören har uttryckligen beviljat gMSA-kontot administratörsprivilegier.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

gMSA-konton bör endast användas när åtkomst till nätverksresurser krävs olika orsaker:

- Det är svårare att spåra tillbaka åtgärder för att en användare när du använder ett konto för gMSA eftersom alla användare delar samma kör som-identitet. Behöver du PowerShell-session betyg och loggar för att korrelera användare med sina åtgärder.

- GMSA-kontot kan ha åtkomst till många nätverksresurser som anslutande användaren inte behöver åtkomst till. Försök alltid att begränsa gällande behörigheter i en JEA-session för att följa principen om lägsta behörighet.

> [!NOTE]
> Gruppen hanterade tjänstkonton är endast tillgängliga i Windows PowerShell 5.1 eller senare och på domänanslutna datorer.

#### <a name="more-information-about-run-as-users"></a>Mer information om Kör som-användare

Mer information om Kör som identiteter och hur de ta med i säkerheten i en JEA-session finns i den [säkerhetsöverväganden](security-considerations.md) artikeln.

### <a name="session-transcripts"></a>Sessionen avskrifter

Vi rekommenderar att du konfigurerar en konfigurationsfil för JEA-sessionen att registreras automatiskt avskrifter av användarnas sessioner.
PowerShell-session avskrifter innehåller information om den anslutande användaren, kör som-identiteten som tilldelats dem, och kommandona som körs av användaren.
De kan vara praktiskt att en granskning team som behöver förstå vem som utförde en viss ändring av ett system.

Ange en sökväg till en mapp där avskrifter ska sparas för att konfigurera automatisk avskrift i konfigurationsfilen för sessionen.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Den angivna mappen ska konfigureras för att hindra användare från att ändra eller ta bort alla data i den.
Avskrifter skrivs till mappen som kontot Lokalt System, vilket kräver Läs- och skrivåtkomst till katalogen.
Vanliga användare bör inte ha åtkomst till mappen och en begränsad uppsättning säkerhetsadministratörer ska ha åtkomst till att granska avskrifter.

### <a name="user-drive"></a>Enheten

Om dina anslutande användare behöver att kopiera filer till och från JEA-slutpunkt för att köra ett kommando, kan du aktivera enheten i konfigurationsfilen för sessionen.
Användare-enheten är en [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) som är mappad till en unik mapp för varje anslutande användaren.
Den här mappen fungerar som ett utrymme att kopiera filer till och från systemet, utan att ge dem åtkomst till filsystemet fullständig eller exponera filsystem-providern.
Användarens enhet innehållet är beständiga mellan sessioner för situationer där nätverksanslutningen kan avbrytas.

```powershell
MountUserDrive = $true
```

Som standard kan på enheten du lagra upp till 50MB data per användare.
Du kan begränsa mängden data som en användare kan använda med den *UserDriveMaximumSize* fält.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Om du inte vill att data i användarens enhet ska vara beständig, kan du konfigurera en schemalagd aktivitet på systemet att automatiskt Rensa mappen varje natt.

> [!NOTE]
> Användare-enheten är endast tillgängliga i Windows PowerShell 5.1 eller senare.

### <a name="role-definitions"></a>Rolldefinitioner

Rolldefinitioner i en konfigurationsfil för sessionen definierar mappningen av *användare* till *roller*.
Varje användare eller grupp som ingår i det här fältet kommer automatiskt att beviljas behörighet att JEA-slutpunkt när den är registrerad.
Varje användare eller grupp kan ingå som en nyckel i hash-tabellen bara en gång, men kan tilldelas flera roller.
Namnet på rollen funktionen ska vara namnet på rollen kapaciteten för filen, utan tillägget .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Om en användare tillhör mer än en grupp i rolldefinitionen kan får de åtkomst till roller för var och en.
Om två roller ger åtkomst till samma cmdlets kan beviljas den mest Tillåtande parameteruppsättningen för användaren.

När du anger lokala användare eller grupper i rollen definitioner fältet, måste du använda namnet på datorn (inte *localhost* eller *.*) innan den omvänt snedstrecken.
Du hittar namnet på datorn genom att kontrollera den `$env:computername` variabeln.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Sökordning för roll-funktion

I exemplet ovan visas rollfunktioner refereras av filens roll funktionen fast namn (filnamn utan filtillägget).
Om flera rollfunktioner är tillgängliga på datorn med samma fast namn, använder PowerShell dess implicita ordning för att markera filen effektiva roll funktionen.
Kommer det att **inte** ge åtkomst till alla roll funktionsfiler med samma namn.

JEA använder den `$env:PSModulePath` miljövariabeln för att avgöra vilka sökvägar kan du söka efter roll funktionsfiler.
I var och en av dessa sökvägar söker JEA efter giltiga PowerShell-moduler som innehåller en undermapp som ”RoleCapabilities”.
Precis som med importerar moduler, föredrar JEA rollfunktioner som medföljer Windows till den anpassade rollen funktionerna med samma namn.
För andra namnkonflikter bestäms prioritet av den ordning som räknar Windows upp filerna i katalogen (inte nödvändigtvis i alfabetisk ordning).
Den första roll funktionen filen hittades som matchar önskat namn ska användas för den anslutande användaren.

Eftersom sökordningen för roll-funktionen är inte deterministisk när två eller fler rollfunktioner har samma namn, är det **rekommenderar vi** du se till rollfunktioner har unika namn på din dator.

### <a name="conditional-access-rules"></a>Regler för villkorlig åtkomst

Alla användare och grupper som ingår i fältet RoleDefinitions beviljas automatiskt åtkomst till JEA-slutpunkter.
Regler för villkorlig åtkomst kan du förfina den här åtkomsten och Kräv att användare ska tillhöra ytterligare säkerhetsgrupper som inte påverkar de roller som de är tilldelade.
Detta kan vara användbart om du vill integrera ”just in-time” privilegierad åtkomst till hanteringslösningen, autentisering med smartkort eller andra Multi-Factor authentication-lösning med JEA.

Regler för villkorlig åtkomst har definierats i fältet RequiredGroups i en konfigurationsfil för sessionen.
Där kan du ange en hash-tabell (du kan också kapslade) som använder ”och” och ”eller” för att skapa dina regler.
Här följer några exempel på hur du kan använda det här fältet:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> Regler för villkorlig åtkomst är bara tillgängliga i Windows PowerShell 5.1 eller senare.

### <a name="other-properties"></a>Andra egenskaper

Sessionen konfigurationsfiler kan också göra allt en roll funktionen fil kan göra, men utan möjlighet att ge den anslutande användare åtkomst till olika kommandon.
Om du vill tillåta alla användare åtkomst till specifika cmdlet: ar, funktioner eller leverantörer kan du göra det direkt i konfigurationsfilen för sessionen.
En fullständig lista över egenskaper som stöds i konfigurationsfilen session kör `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Testa en konfigurationsfil för session

Du kan testa en session konfiguration med hjälp av den [Test PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.
Vi rekommenderar starkt att du testar din session-konfigurationsfil om du har redigerat filen pssc manuellt med hjälp av en textredigerare så syntaxen är korrekt.
Om en session konfigurationsfil inte skickar det här testet, kan den inte har registreras i systemet.

## <a name="sample-session-configuration-file"></a>Exempelkonfigurationsfil för session

Nedan visas ett komplett exempel som visar hur du skapar och validerar en sessionskonfiguration för JEA.
Observera att rolldefinitionerna skapas och lagras i den `$roles` variabeln för bekvämlighets skull och läsbarhet.
Det är inte ett krav att göra detta.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Uppdaterar sessionen konfigurationsfiler

Om du behöver ändra egenskaperna för en JEA-sessionskonfiguration, inklusive mappningen av användare till roller måste du [avregistrera](register-jea.md#unregistering-jea-configurations) och [Omregistrera](register-jea.md) JEA-sessionskonfiguration.
När du registrera JEA sessionskonfigurationen kan du använda en uppdaterad PowerShell-session configuration-fil som innehåller dina önskade ändringar.

## <a name="next-steps"></a>Nästa steg

- [Registrera en JEA-konfiguration](register-jea.md)
- [Författare JEA roller](role-capabilities.md)
