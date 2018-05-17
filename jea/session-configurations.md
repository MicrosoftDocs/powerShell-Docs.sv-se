---
ms.date: 06/12/2017
keywords: jea powershell säkerhet
title: JEA Sessionskonfigurationer
ms.openlocfilehash: 3e5a663be8e7aba09a2592c278224cd892c89a20
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="jea-session-configurations"></a>JEA Sessionskonfigurationer

> Gäller för: Windows PowerShell 5.0

En slutpunkt för JEA är registrerad på en dator genom att skapa och registrera en konfigurationsfil för PowerShell-session på ett visst sätt.
Fastställa sessionskonfigurationer *som* kan använda JEA slutpunkt och vilka roller de har åtkomst till.
De kan också definiera globala inställningar som gäller för användare av en roll i JEA-sessionen.

Det här avsnittet beskriver hur du skapar en konfigurationsfil för PowerShell-session och registrera en JEA slutpunkt.

## <a name="create-a-session-configuration-file"></a>Skapa en konfigurationsfil för session

Du måste ange hur den slutpunkten ska konfigureras för att kunna registrera en JEA slutpunkt.
Det finns många alternativ att överväga här är det viktigaste att vilka som ska ha åtkomst till slutpunkten JEA, vilka roller kommer de tilldelas, vilken identitet JEA används under försättsbladen och vad ska vara namnet på slutpunkten JEA.
Dessa definieras i konfigurationsfilen en PowerShell-session som är en PowerShell-datafil som slutar med filnamnstillägget .pssc.

Kör följande kommando för att skapa en konfigurationsfil för stommen sessionen för JEA slutpunkter.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Endast de vanligaste konfigurationsalternativ ingår i filen stommen som standard.
> Använd den `-Full` växel om du vill inkludera alla tillämpliga inställningar i den genererade PSSC.

Du kan öppna konfigurationsfilen session i en textredigerare.
Den `-SessionType RestrictedRemoteServer` fältet som anger att sessionskonfigurationen kommer att användas av JEA för säker hantering.
Sessioner som konfigureras på det här sättet kommer att fungera i [NoLanguage läge](https://technet.microsoft.com/library/dn433292.aspx) och får bara innehålla följande 8 standardkommandon (och alias) tillgängliga:

- Rensa-värden (cls, rensa)
- Avsluta-PSSession (exsn, avsluta)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Måttobjekt (mått)
- Standard ut
- Select-Object (Välj)

Inga PowerShell-providers är tillgängliga, inte heller några externa program (körbara filer, skript osv.).

Det finns flera andra fält som du vill konfigurera för JEA-sessionen.
De beskrivs i följande avsnitt.

### <a name="choose-the-jea-identity"></a>Välj JEA identitet

JEA måste en identitet (konto) ska användas när en användare som ansluten kommandon körs i bakgrunden.
Du bestämmer vilken identitet JEA används i konfigurationsfilen för sessionen.

#### <a name="local-virtual-account"></a>Lokala virtuellt konto

Om de roller som stöds av den här slutpunkten JEA används för att hantera den lokala datorn, och ett lokalt administratörskonto är tillräckligt för att köra kommandon har, bör du konfigurera JEA om du vill använda ett virtuellt lokalt konto.
Virtuella konton är tillfälliga konton som är unik för en viss användare och endast senaste under hela sin PowerShell-session.
På en medlemsserver eller arbetsstation virtuella konton som hör till den lokala datorn **administratörer** grupp och har åtkomst till de flesta systemresurser.
På en Active Directory-domänkontrollant virtuella konton tillhör domänens **Domänadministratörer** grupp.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Om roller som stöds av sessionskonfigurationen inte kräver dessa breda behörigheter, kan du alternativt ange de säkerhetsgrupper som virtuellt konto ska tillhöra.
De angivna säkerhetsgrupperna måste vara lokala grupper, inte grupper från en domän på en medlemsserver eller en arbetsstation.

När en eller flera säkerhetsgrupper anges virtuellt konto kommer inte längre tillhör administratörsgruppen lokalt eller via domänadministratör.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Grupphanterat tjänstkonto


För scenarier som kräver JEA användare att komma åt nätverksresurser, till exempel andra datorer eller webbtjänster, är en grupp Hanterat tjänstkonto (gMSA) en lämpligare identitet ska användas.
gMSA-konton får du en domän-identitet som kan användas för att autentisera mot resurser på en dator i domänen.
Rättigheter i gMSA ger du bestäms av resurserna som du ansluter till.
Du har automatiskt inte administratörsrättigheter på alla datorer eller tjänster om inte datorn/service uttryckligen tilldelats gMSA-kontot admin-privilegier.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

gMSA konton bör endast användas när åtkomst till nätverksresurser krävs på olika orsaker:

- Det är svårare att spåra tillbaka åtgärder för att en användare när du använder ett konto för gMSA eftersom alla användare delar samma kör som-identitet. Du måste kontakta PowerShell-session betyg och loggfilerna för att korrelera användare med sina åtgärder.

- GMSA-kontot kan ha åtkomst till många nätverksresurser som anslutande användaren inte behöver åtkomst till. Alltid ett försök att begränsa gällande behörigheter i en JEA session att följa principen om minsta behörighet.

> [!NOTE]
> Gruppen hanterade tjänstkonton är bara tillgängliga i Windows PowerShell 5.1 eller nyare och på domänanslutna datorer.


#### <a name="more-information-about-run-as-users"></a>Mer information om Kör som-användare

Mer information om Kör som identiteter och hur de factor i säkerheten för en JEA session kan hittas i den [säkerhetsaspekter](security-considerations.md) artikel.

### <a name="session-transcripts"></a>Sessionen betyg

Vi rekommenderar att du konfigurerar en JEA session konfigurationsfil att registreras automatiskt betyg användarnas sessioner.
PowerShell-session betyg innehåller information om den anslutande användaren kör som-identitet som har tilldelats dem, och kommandon som körs av användaren.
De kan vara användbara för en granskning team som behöver förstå vem som utförde en viss ändring i ett system.

Ange en sökväg till en mapp där betyg ska lagras för att konfigurera automatisk skrivfel i konfigurationsfilen för sessionen.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Den angivna mappen ska konfigureras för att förhindra att användare kan ändra eller ta bort alla data i den.
Betyg skrivs till mappen som kontot Lokalt System som kräver Läs- och skrivbehörighet till katalogen.
Vanliga användare bör ha ingen åtkomst till mappen och en begränsad uppsättning säkerhetsadministratörer ska ha åtkomst till att granska betyg.

### <a name="user-drive"></a>Enheten

Om du ansluter användarna kommer att behöva kopiera filer till eller från JEA slutpunkten för att köra ett kommando, kan du aktivera enhetens användare i konfigurationsfilen för sessionen.
Användarens enhet är en [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) som är mappad till en unik mapp för varje anslutning användare.
Den här mappen fungerar som ett utrymme att kopiera filer till eller från systemet, utan att ge dem åtkomst till fullständig filsystemet eller exponera filsystem-providern.
Användarens enhet innehållet är beständiga mellan sessioner för situationer där nätverksanslutningen kan avbrytas.

```powershell
MountUserDrive = $true
```

Som standard kan enhetens användare du lagra upp till 50MB data per användare.
Du kan begränsa mängden data som en användare kan använda med den *UserDriveMaximumSize* fältet.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Om du inte vill att data på enheten för användaren ska vara beständig kan du konfigurera en schemalagd aktivitet på systemet att automatiskt Rensa mappen varje natt.

> [!NOTE]
> Enhetens användare är endast tillgänglig i Windows PowerShell 5.1 eller nyare.

### <a name="role-definitions"></a>Rolldefinitioner

Rolldefinitioner i en session konfigurationsfil definierar mappningen av *användare* till *roller*.
Alla användare eller grupp som ingår i det här fältet beviljas automatiskt behörighet till slutpunkten JEA när den är registrerad.
Varje användare eller grupp kan ingå som en nyckel i hashtabellen bara en gång, men kan tilldelas flera roller.
Namnet på rollen funktionen ska vara namnet på filen rollen kapaciteten utan .psrc filnamnstillägget.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Om en användare tillhör mer än en grupp i rolldefinitionen, kommer de att få åtkomst till roller för varje.
Om två roller ger åtkomst till samma cmdletar kan beviljas den mest Tillåtande parameteruppsättningen för användaren.

När du anger för lokala användare eller grupper i fältet roll definitioner, måste du använda datornamnet (inte *localhost* eller *.*) innan ett omvänt snedstreck.
Du kan kontrollera namnet på datorn genom att kontrollera den `$env:computername` variabeln.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Sökordning för rollen kapaciteten
I exemplet ovan visas roll funktioner refereras av enkla namnet (filnamn utan filtillägget) i filen rollen kapaciteten.
Om flera rollen funktioner är tillgängliga på datorn med samma enkla namn, använder PowerShell dess implicit Sökordning för att välja filen effektiva rollen kapaciteten.
Kommer det att **inte** ge åtkomst till alla rollen kapaciteten för filer med samma namn.

JEA använder den `$env:PSModulePath` miljövariabeln för att avgöra vilka sökvägar för att söka efter roll funktionsfiler.
I var och en av dessa sökvägar söker JEA efter giltig PowerShell-modulerna som innehåller en undermapp ”RoleCapabilities”.
Precis som med importerar moduler föredrar JEA roll-funktioner som levereras med Windows till anpassad roll funktionerna med samma namn.
För andra namnkonflikter bestäms prioritet av den ordning som räknar Windows upp filer i katalogen (inte garanterat i alfabetisk ordning).
Den första roll kapaciteten filen hittades som matchar den önskade namn kommer att användas för den anslutande användaren.

Eftersom sökordningen för roll-funktionen är inte deterministisk när två eller flera funktioner för rollen har samma namn, är det **rekommenderar** som kontrollerar funktioner för rollen har unika namn på din dator.

### <a name="conditional-access-rules"></a>Regler för villkorlig åtkomst

Alla användare och grupper som ingår i fältet RoleDefinitions beviljas automatiskt åtkomst till JEA slutpunkter.
Regler för villkorlig åtkomst kan du förfina åtkomst och användaren måste tillhöra ytterligare säkerhetsgrupper som inte påverkar de roller som de har tilldelats.
Detta kan vara användbart om du vill integrera ”bara i tiden” privilegierad åtkomst lösning, autentisering med smartkort eller andra flerfunktionsautentisering lösning med JEA.

Regler för villkorlig åtkomst har definierats i fältet RequiredGroups i en konfigurationsfil för sessionen.
Det, kan du ange en hash-tabell (du kan också kapslade) som använder 'Och' och 'Eller' för att skapa dina regler.
Här följer några exempel på hur du använder det här fältet:

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
Sessionen konfigurationsfiler kan också göra allt en roll kapaciteten fil kan göra, men utan möjlighet att ge anslutande användare åtkomst till olika kommandon.
Om du vill tillåta alla användare åtkomst till specifika cmdlet: ar, funktioner och leverantörer kan du göra det direkt i konfigurationsfilen för sessionen.
En fullständig lista över egenskaper som stöds i konfigurationsfilen session kör `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Testa en session-konfigurationsfil

Du kan testa en session konfigurationen med hjälp av den [Test PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.
Det rekommenderas starkt att du testar din session-konfigurationsfil om du har redigerat filen pssc manuellt med hjälp av en textredigerare så syntax är korrekt.
Om en session konfigurationsfil inte klarar det här testet, kan den inte registrerats på datorn.

## <a name="sample-session-configuration-file"></a>Exempelkonfigurationsfilen för session

Nedan visas en komplett exempel som visar hur du skapar och validera en sessionskonfiguration för JEA.
Observera att rolldefinitioner skapas och lagras i den `$roles` variabel för bekvämlighets skull och läsbarhet.
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

## <a name="updating-session-configuration-files"></a>Uppdatera session konfigurationsfiler

Om du behöver ändra egenskaperna för en sessionskonfiguration JEA, inklusive koppling av användare till roller, måste du [avregistrera](register-jea.md#unregistering-jea-configurations) och [Omregistrera](register-jea.md) JEA sessionskonfigurationen.
När du registrera JEA sessionskonfigurationen kan du använda en uppdaterad PowerShell-session konfigurationsfil som innehåller dina önskade ändringar.

## <a name="next-steps"></a>Nästa steg

- [Registrera en JEA-konfiguration](register-jea.md)
- [Författare JEA roller](role-capabilities.md)