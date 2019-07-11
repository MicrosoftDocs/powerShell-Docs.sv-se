---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: JEA Sessionskonfigurationer
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726544"
---
# <a name="jea-session-configurations"></a>JEA Sessionskonfigurationer

En JEA-slutpunkt har registrerats i ett system genom att skapa och registrera en konfigurationsfil för PowerShell-session. Sessionskonfigurationer definierar vem som kan använda JEA-slutpunkt och vilka roller som de har åtkomst till. De kan också definiera globala inställningar som gäller för alla användare av den JEA-sessionen.

## <a name="create-a-session-configuration-file"></a>Skapa en konfigurationsfil för session

Du måste ange hur att slutpunkten är konfigurerad för att registrera en JEA-slutpunkt. Det finns många alternativ att överväga. De viktigaste alternativen är:

- Vem har tillgång till JEA-slutpunkt
- Vilka roller som de tilldelas
- Vilken identitet JEA använder under försättsbladen
- Namnet på JEA-slutpunkt

De här alternativen har definierats i en PowerShell-datafilen med en `.pssc` tillägg som kallas en konfigurationsfil för PowerShell-session. Konfigurationsfilen session kan redigeras med valfri textredigerare.

Kör följande kommando för att skapa en tom mall-konfigurationsfil.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Endast de vanligaste konfigurationsalternativ ingår i mallfilen som standard. Använd den `-Full` växel för att ta med alla tillämpliga inställningar i den genererade PSSC.

Den `-SessionType RestrictedRemoteServer` fält anger att sessionskonfigurationen används av JEA för säker hantering. Sessioner av den här typen fungera i **NoLanguage** läge och endast har åtkomst till följande standardkommandon för (och alias):

- Clear-värd (cls, rensa)
- Avsluta-PSSession (exsn, avsluta)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Måttobjektet (mått)
- Out-Default
- Select-Object (Välj)

Inga PowerShell-providers är tillgängliga, och inte heller några externa program (körbara filer eller skript).

Mer information om lägena för språk finns i [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Välj JEA-identitet

JEA måste en identitet (konto) du använder när du kör en anslutna användare kommandon i bakgrunden.
Du definierar vilken identitet JEA används i konfigurationsfilen för sessionen.

#### <a name="local-virtual-account"></a>Lokala virtuellt konto

Lokala virtuella konton är användbara när alla roller som definierats för JEA-slutpunkt som används för att hantera den lokala datorn och ett lokalt administratörskonto räcker för att köra kommandona har.
Virtuella konton är tillfälliga konton som är unika för en viss användare och endast senaste under av sina PowerShell-session. På en medlemsserver eller arbetsstation virtuella konton som hör till den lokala datorn **administratörer** grupp. På en Active Directory-domänkontrollant, virtuella konton tillhör domänens **Domänadministratörer** grupp.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Om de roller som definieras av sessionskonfigurationen inte kräver administratörsprivilegier, kan du ange de säkerhetsgrupper som virtuellt konto ska tillhöra. De angivna säkerhetsgrupperna måste vara lokala grupper, inte grupper från en domän på en medlemsserver eller arbetsstation.

När en eller flera säkerhetsgrupper anges, inte är virtuellt konto tilldelad till den lokala administratörsgruppen.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Virtuella konton beviljas tillfälligt inloggningen som en tjänst direkt i den lokala server säkerhetsprincipen. Om en av VirtualAccountGroups som angetts har redan beviljats den här behörigheten i principen, kommer inte längre individuella virtuella konto har lagts till och tas bort från principen. Detta kan vara användbart i scenarier, till exempel domänkontrollanter där ändringar i den säkerhetsprincip för domänkontrollanter granskas noggrant. Detta är endast tillgängligt i Windows Server 2016 med November 2018 eller senare samlad och Windows Server 2019 med januari 2019 eller senare samlad.

#### <a name="group-managed-service-account"></a>Grupphanterat tjänstkonto

Ett-grupphanterat tjänstkonto (GMSA) är rätt identitet ska användas när JEA-användare behöver åtkomst till nätverksresurser, till exempel filresurser och webbtjänster. GMSAs ger dig en domänidentitet som används för att autentisera med resurser på en dator i domänen. De rättigheter som ett GMSA ger bestäms av resurserna som du försöker komma åt. Du har inte administratörsrättigheter på alla datorer eller tjänster, såvida inte den maskin- eller administratören uttryckligen har gett dessa rättigheter till GMSA.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

GMSAs bör endast användas när det behövs:

- Det är svårt att spåra tillbaka åtgärder för att en användare när du använder ett GMSA. Varje användare delar samma kör som-identitet. Du måste granska PowerShell-session betyg och loggfiler för att korrelera enskilda användare med sina åtgärder.

- GMSA kan ha åtkomst till många nätverksresurser som anslutande användaren inte behöver åtkomst till. Försök alltid att begränsa gällande behörigheter i en JEA-session för att följa principen om lägsta behörighet.

> [!NOTE]
> Gruppen hanterade tjänstkonton är endast tillgänglig på domänanslutna datorer med hjälp av PowerShell 5.1 eller senare.

Mer information om hur du skyddar en JEA-session finns i den [säkerhetsöverväganden](security-considerations.md) artikeln.

### <a name="session-transcripts"></a>Sessionen avskrifter

Vi rekommenderar att du konfigurerar en JEA-slutpunkt för att registreras automatiskt avskrifter av användarnas sessioner. PowerShell-session avskrifter innehåller information om den anslutande användaren, kör som-identiteten som tilldelats dem, och kommandona som körs av användaren. De kan vara praktiskt att en granskning team som behöver förstå vem som har gjort en ändring av specifika till ett system.

Ange en sökväg till en mapp där avskrifter ska sparas för att konfigurera automatisk avskrift i konfigurationsfilen för sessionen.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Avskrifter skrivs till mappen som den **lokalt System** konto, vilket kräver Läs- och skrivåtkomst till katalogen. Vanliga användare bör ha någon åtkomst till mappen. Begränsa antalet administratörer av informationssäkerhet som har åtkomst till att granska avskrifter.

### <a name="user-drive"></a>Enheten

Om anslutande användarna behöver för att kopiera filer till eller från JEA-slutpunkt, kan du aktivera enheten i konfigurationsfilen för sessionen. Användare-enheten är en **PSDrive** som är mappad till en unik mapp för varje anslutande användaren. Den här mappen kan du kopiera filer till eller från systemet utan att ge dem åtkomst till filsystemet fullständig eller exponera filsystem-providern. Användarens enhet innehållet är beständiga mellan sessioner för situationer där nätverksanslutningen kan avbrytas.

```powershell
MountUserDrive = $true
```

Som standard kan på enheten du lagra upp till 50MB data per användare. Du kan begränsa mängden data som en användare kan använda med den *UserDriveMaximumSize* fält.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Om du inte vill att data i användarens enhet ska vara beständig, kan du konfigurera en schemalagd aktivitet för att automatiskt Rensa mappen varje natt.

> [!NOTE]
> Användare-enheten är endast tillgängliga i PowerShell 5.1 eller senare.

Läs mer om PSDrives [hantera PowerShell enheter](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Rolldefinitioner

Rolldefinitioner i en konfigurationsfil för sessionen definierar mappningen av **användare** till **roller**. Varje användare eller grupp som ingår i det här fältet har beviljats behörighet att JEA-slutpunkt när den är registrerad.
Varje användare eller grupp kan ingå som en nyckel i hash-tabellen bara en gång, men kan tilldelas flera roller. Namnet på funktionen roll bör vara namnet på filen roll funktionen utan den `.psrc` tillägget.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Om en användare tillhör mer än en grupp i rolldefinitionen kan få de åtkomst till rollerna för var och en. När två roller bevilja åtkomst till samma cmdlets, beviljas den mest Tillåtande parameteruppsättningen för användaren.

När du anger lokala användare eller grupper i rollen definitioner fältet, måste du använda namnet på datorn, inte **localhost** eller jokertecken. Du hittar namnet på datorn genom att kontrollera den `$env:COMPUTERNAME` variabeln.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Sökordning för roll-funktion

I exemplet ovan visas rollfunktioner refererar till det grundläggande namnet på rollen kapaciteten för filen. Det grundläggande namnet på en fil är filnamn utan filtillägget. Om flera rollfunktioner är tillgängliga på datorn med samma namn, använder PowerShell dess implicita ordning för att markera filen effektiva roll funktionen. JEA har **inte** ge åtkomst till alla roll funktionsfiler med samma namn.

JEA använder den `$env:PSModulePath` miljövariabeln för att avgöra vilka sökvägar kan du söka efter roll funktionsfiler. JEA söker efter giltiga PowerShell-moduler som innehåller en ”RoleCapabilities” undermapp i var och en av dessa sökvägar. Precis som med importerar moduler, föredrar JEA rollfunktioner som medföljer Windows till den anpassade rollen funktionerna med samma namn.

För andra namnkonflikter bestäms prioritet av den ordning som räknar Windows upp filerna i katalogen. Ordningen är inte garanterat som alfabetisk. Den första roll funktionen filen hittades som matchar det angivna namnet används för anslutande användaren. Sedan rollen funktionen search ordning är inte deterministisk, är det **rekommenderar vi** att rollfunktioner har unika filnamn.

### <a name="conditional-access-rules"></a>Regler för villkorlig åtkomst

Alla användare och grupper som ingår i den **RoleDefinitions** fältet beviljas automatiskt åtkomst till JEA-slutpunkter. Regler för villkorlig åtkomst kan du förfina den här åtkomsten och Kräv att användare ska tillhöra ytterligare säkerhetsgrupper som inte påverkar de roller som de tilldelats. Detta är användbart när du vill integrera en hanteringslösning för privilegierad just-in-time-åtkomst, autentisering med smartkort eller andra Multi-Factor authentication-lösning med JEA.

Regler för villkorlig åtkomst har definierats i fältet RequiredGroups i en konfigurationsfil för sessionen.
Där kan du ange en hash-tabell (du kan också kapslade) som använder ”och” och ”eller” för att skapa dina regler. Här följer några exempel på hur du använder det här fältet:

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
> Regler för villkorlig åtkomst är bara tillgängliga i PowerShell 5.1 eller senare.

### <a name="other-properties"></a>Andra egenskaper

Sessionen konfigurationsfiler kan också göra allt en roll funktionen fil kan göra, men utan möjlighet att ge den anslutande användare åtkomst till olika kommandon. Om du vill tillåta alla användare åtkomst till specifika cmdlet: ar, funktioner eller leverantörer kan du göra det direkt i konfigurationsfilen för sessionen.
En fullständig lista över egenskaper som stöds i konfigurationsfilen session kör `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Testa en konfigurationsfil för session

Du kan testa en session konfiguration med hjälp av den [Test PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet. Vi rekommenderar att du testar din session-konfigurationsfil om du manuellt har redigerat den `.pssc` filen. Testa säkerställer syntaxen är korrekt. Om en konfigurationsfil för sessionen inte det här testet, kan den inte registreras i systemet.

## <a name="sample-session-configuration-file"></a>Exempelkonfigurationsfil för session

I följande exempel visas hur du skapar och validera en sessionskonfiguration för JEA. Rolldefinitionerna skapas och lagras i den `$roles` variabeln för bekvämlighets skull och läsbarhet. Det är inte ett krav att göra detta.

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

Om du vill ändra egenskaperna för en JEA-sessionskonfiguration, inklusive mappningen av användare till roller måste du [avregistrera](register-jea.md#unregistering-jea-configurations). Sedan [Omregistrera](register-jea.md) JEA-sessionskonfiguration som använder en konfigurationsfil för uppdaterade session.

## <a name="next-steps"></a>Nästa steg

- [Registrera en JEA-konfiguration](register-jea.md)
- [Författare JEA roller](role-capabilities.md)
