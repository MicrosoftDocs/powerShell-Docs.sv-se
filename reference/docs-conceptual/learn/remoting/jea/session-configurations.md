---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017883"
---
# <a name="jea-session-configurations"></a>JEA

En JEA-slutpunkt är registrerad på ett system genom att skapa och registrera en PowerShell-sessions konfigurations fil. Sessionsbaserade definierar vem som kan använda JEA-slutpunkten och vilka roller de har åtkomst till. De definierar också globala inställningar som gäller för alla användare av JEA-sessionen.

## <a name="create-a-session-configuration-file"></a>Skapa en konfigurations fil för sessionen

För att registrera en JEA-slutpunkt måste du ange hur slut punkten ska konfigureras. Det finns många alternativ att tänka på. De viktigaste alternativen är:

- Som har åtkomst till JEA-slutpunkten
- Vilka roller de tilldelas
- Vilken identitet JEA använder under försättsblad
- Namnet på JEA-slutpunkten

De här alternativen definieras i en PowerShell-datafil med ett `.pssc`-tillägg som kallas för en PowerShell-sessions konfigurations fil. Konfigurations filen för sessionen kan redige ras med valfri text redigerare.

Kör följande kommando för att skapa en tom mall konfigurations fil.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Endast de vanligaste konfigurations alternativen ingår i mallfilen som standard. Använd `-Full` växeln för att inkludera alla tillämpliga inställningar i den genererade PSSC.

I fältet `-SessionType RestrictedRemoteServer` anges att konfigurationen används av JEA för säker hantering. Sessioner av den här typen körs i **Nolanguage** -läge och har bara åtkomst till följande standard kommandon (och alias):

- Clear-Host (CLS, Clear)
- Exit-PSSession (exsn, exit)
- Get-Command (GCM)
- Get-FormatData
- Get-Help
- Mått – objekt (mått)
- Ut-standard
- Select-Object (Välj)

Det finns inga tillgängliga PowerShell-providrar eller externa program (körbara filer eller skript).

Mer information om språk lägen finns [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Välj identiteten JEA

JEA behöver en identitet (konto) som ska användas för att köra en ansluten användares kommandon i bakgrunden.
Du definierar vilka identiteter JEA som används i sessionens konfigurations fil.

#### <a name="local-virtual-account"></a>Lokalt virtuellt konto

Lokala virtuella konton är användbara när alla roller som definierats för JEA-slutpunkten används för att hantera den lokala datorn och ett lokalt administratörs konto räcker för att köra kommandona.
Virtuella konton är tillfälliga konton som är unika för en speciell användare och som endast är under den tid som PowerShell-sessionen varar. På en medlems Server eller arbets Station tillhör virtuella konton den lokala datorns **Administratörs** grupp. På en Active Directory-domän kontroll hör virtuella konton till domänens **domän administratörs** grupp.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Om rollerna som definieras av konfigurationen av sessionen inte kräver fullständig administratörs behörighet kan du ange de säkerhets grupper som det virtuella kontot ska tillhöra. På en medlems Server eller arbets Station måste de angivna säkerhets grupperna vara lokala grupper, inte grupper från en domän.

När en eller flera säkerhets grupper har angetts är det virtuella kontot inte tilldelat till den lokala gruppen eller domän administratörs gruppen.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Virtuella konton beviljas tillfälligt inloggningen som en tjänst direkt i säkerhets principen för den lokala servern. Om ett av de VirtualAccountGroups som har angetts redan har beviljats rätt i principen, läggs det enskilda virtuella kontot inte längre till och tas bort från principen. Detta kan vara användbart i scenarier som domänkontrollanter där ändringar av säkerhets principen för domänkontrollanten granskas noga. Detta är endast tillgängligt i Windows Server 2016 med Samlad uppdatering för 2018 eller senare och Windows Server 2019 med den samlade uppdateringen från januari 2019 eller senare.

#### <a name="group-managed-service-account"></a>Grupphanterat tjänst konto

Ett grupphanterat tjänst konto (GMSA) är en lämplig identitet som används när JEA-användare behöver åtkomst till nätverks resurser, till exempel fil resurser och webb tjänster. GMSAs ger dig en domän identitet som används för att autentisera med resurser på valfri dator i domänen. De rättigheter som en GMSA tillhandahåller bestäms av de resurser som du har åtkomst till. Du har inte administratörs behörighet på alla datorer eller tjänster om inte datorn eller tjänst administratören uttryckligen har beviljat dessa rättigheter till GMSA.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

GMSAs bör endast användas när det behövs:

- Det är svårt att spåra åtgärder till en användare när du använder en GMSA. Varje användare delar samma kör som-identitet. Du måste granska avskrifter och loggar för PowerShell-sessionen för att korrelera enskilda användare med sina åtgärder.

- GMSA kan ha åtkomst till många nätverks resurser som den anslutande användaren inte behöver åtkomst till. Försök alltid att begränsa gällande behörigheter i en JEA-session så att de följer principen om minsta behörighet.

> [!NOTE]
> Grupphanterade tjänst konton är bara tillgängliga på domänanslutna datorer med PowerShell 5,1 eller senare.

Mer information om hur du skyddar en JEA-session finns i artikeln [säkerhets överväganden](security-considerations.md) .

### <a name="session-transcripts"></a>Avskrifter för session

Vi rekommenderar att du konfigurerar en JEA-slutpunkt för att automatiskt registrera avskrifter av användarnas sessioner. Avskrifter i PowerShell-sessionen innehåller information om den anslutande användaren, kör som-identiteten som tilldelats dem och kommandona som körs av användaren. De kan vara användbara för ett gransknings team som behöver förstå vem som har gjort en speciell ändring i ett system.

Om du vill konfigurera automatisk avskrift i sessionens konfigurations fil anger du en sökväg till en mapp där avskrifterna ska lagras.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Avskrifter skrivs till mappen av det **lokala system** kontot, som kräver Läs-och Skriv behörighet till katalogen. Standard användare får inte ha åtkomst till mappen. Begränsa antalet säkerhets administratörer som har åtkomst till granskning av avskrifter.

### <a name="user-drive"></a>Användar enhet

Om dina anslutna användare behöver kopiera filer till eller från JEA-slutpunkten kan du aktivera användar enheten i sessionens konfigurations fil. Användar enheten är en **PSDrive** som är mappad till en unik mapp för varje anslutning användare. Med den här mappen kan användare kopiera filer till eller från systemet utan att ge dem till gång till det fullständiga fil systemet eller exponera fil Systems leverantören. Innehållet i användar enheten är beständigt i sessioner för att hantera situationer där nätverks anslutningen kan avbrytas.

```powershell
MountUserDrive = $true
```

Som standard tillåter användar enheten att du lagrar maximalt 50 MB data per användare. Du kan begränsa mängden data som en användare kan använda med fältet *UserDriveMaximumSize* .

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Om du inte vill att data i användar enheten ska vara beständiga kan du konfigurera en schemalagd aktivitet på systemet så att den automatiskt rensar mappen varje natt.

> [!NOTE]
> Användar enheten är bara tillgänglig i PowerShell 5,1 eller senare.

Mer information om PSDrives finns i [Hantera PowerShell-enheter](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Rolldefinitioner

Roll definitioner i en sessions konfigurations fil definierar mappningen av **användare** till **roller**. Varje användare eller grupp som ingår i det här fältet beviljas behörighet till JEA-slutpunkten när den har registrerats.
Varje användare eller grupp kan endast inkluderas som en nyckel i hash-tabellen en gång, men de kan tilldelas flera roller. Namnet på roll kapaciteten bör vara namnet på roll funktions filen, utan `.psrc` tillägget.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Om en användare tillhör fler än en grupp i roll definitionen får de åtkomst till rollerna för var och en. När två roller beviljar åtkomst till samma cmdletar beviljas användaren den mest tillåtna parameter uppsättningen.

När du anger lokala användare eller grupper i fältet roll definitioner, se till att använda dator namnet, inte **localhost** eller jokertecken. Du kan kontrol lera dator namnet genom att granska `$env:COMPUTERNAME` variabeln.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Sök ordning för roll kapacitet

Som du ser i exemplet ovan refereras roll funktioner av bas namnet för roll funktions filen. Bas namnet för en fil är fil namnet utan fil namns tillägget. Om flera roll funktioner är tillgängliga i systemet med samma namn, använder PowerShell den implicita Sök ordningen för att välja den effektiva roll kapacitets filen. JEA ger **inte** åtkomst till alla roll kapacitets filer med samma namn.

JEA använder miljövariabeln `$env:PSModulePath` för att avgöra vilka sökvägar som ska genomsökas efter roll kapacitets filer. I var och en av dessa sökvägar söker JEA efter giltiga PowerShell-moduler som innehåller undermappen "RoleCapabilities". Precis som med importera moduler föredrar JEA roll funktioner som medföljer Windows till anpassade roll funktioner med samma namn.

För alla andra namn konflikter bestäms prioriteten i den ordning som Windows räknar upp filerna i katalogen. Ordningen är inte garanterat alfabetisk. Den första roll funktions filen som matchar det angivna namnet används för den anslutande användaren. Eftersom Sök ordningen för roll funktioner inte är deterministisk, rekommenderar vi **starkt** att roll funktionerna har unika fil namn.

### <a name="conditional-access-rules"></a>Regler för villkorlig åtkomst

Alla användare och grupper som ingår i fältet **RoleDefinitions** beviljas automatiskt åtkomst till Jea-slutpunkter. Med regler för villkorlig åtkomst kan du förfina den här åtkomsten och kräva att användare tillhöra ytterligare säkerhets grupper som inte påverkar de roller som de är tilldelade till. Detta är användbart när du vill integrera en just-in-Time-hanterings lösning för privilegie rad åtkomst, autentisering av smartkort eller någon annan lösning för multifaktorautentisering med JEA.

Regler för villkorlig åtkomst definieras i fältet RequiredGroups i en sessions konfigurations fil.
Där kan du ange en hash (eventuellt kapslad) som använder "och" och "eller" nycklar för att skapa regler. Här följer några exempel på hur du använder det här fältet:

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
> Regler för villkorlig åtkomst är bara tillgängliga i PowerShell 5,1 eller senare.

### <a name="other-properties"></a>Andra egenskaper

Konfigurationsfiler för sessioner kan också göra allt en roll funktions fil kan göra, precis utan möjligheten att ge användarna åtkomst till olika kommandon. Om du vill ge alla användare åtkomst till vissa cmdletar, funktioner eller providrar kan du göra det direkt i konfigurations filen för sessionen.
En fullständig lista över vilka egenskaper som stöds i konfigurations filen för sessionen får du genom att köra `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Testa en konfigurations fil för sessionen

Du kan testa en sessions konfiguration med cmdleten [test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) . Vi rekommenderar att du testar din konfigurations fil för sessionen om du har redigerat `.pssc`-filen manuellt. Testet ser till att syntaxen är korrekt. Om en sessions konfigurations fil Miss lyckas med det här testet kan den inte registreras i systemet.

## <a name="sample-session-configuration-file"></a>Exempel på konfigurations fil för sessionen

I följande exempel visas hur du skapar och validerar en sessionshantering för JEA. Roll definitionerna skapas och lagras i `$roles`-variabeln för bekvämlighet och läsbarhet. Det är inte nödvändigt att göra det.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Uppdaterar sessionens konfigurationsfiler

Om du vill ändra egenskaperna för en JEA, inklusive mappningen av användare till roller, måste du [avregistrera](register-jea.md#unregistering-jea-configurations)dig. Registrera sedan JEA [-](register-jea.md) sessionen med en uppdaterad sessions konfigurations fil.

## <a name="next-steps"></a>Nästa steg

- [Registrera en JEA-konfiguration](register-jea.md)
- [Redigera JEA-roller](role-capabilities.md)
