---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: JEA-säkerhetsaspekter
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726578"
---
# <a name="jea-security-considerations"></a>JEA-säkerhetsaspekter

JEA hjälper dig att förbättra din säkerhetsposition genom att minska antalet permanenta administratörer på dina datorer. JEA använder en sessionskonfiguration med PowerShell för att skapa en ny startpunkt för användare att hantera systemet. Användare som behöver upphöjd, men inte obegränsad åtkomst till datorn för att utföra administrativa uppgifter kan beviljas åtkomst till JEA-slutpunkt. Eftersom JEA kan dessa användare till admin-kommandon utan fullständig administratörsåtkomst, kan du sedan ta bort användare från säkerhetsgrupper med hög behörighetsnivå.

## <a name="run-as-account"></a>Kör som-konto

Varje JEA-slutpunkt har en avsedda **kör som-** konto. Detta är det konto som den anslutande användaren åtgärder utförs. Det här kontot kan konfigureras i den [session konfigurationsfilen](session-configurations.md), och det konto som du väljer har betydelse på säkerheten för din slutpunkt.

**Virtuella konton** är det rekommenderade sättet att konfigurera den **kör som-** konto. Virtuella konton är enstaka, tillfälligt lokala konton som har skapats för den anslutande användaren ska användas under hela sin JEA-session. Så snart som sin session avslutas virtuellt konto förstörs och kan inte längre användas. Den anslutande användaren känner inte till autentiseringsuppgifterna för kontot virtuella. Virtuellt konto kan inte användas för att komma åt systemet via ett annat sätt, t.ex Fjärrskrivbord eller en obegränsad PowerShell-slutpunkt.

Som standard virtuella konton som hör till lokalt **administratörer** på datorn. Detta ger dem fullständiga rättigheter att hantera allt i systemet, men inga rättigheter att hantera resurser i nätverket.
När du autentiserar med andra datorer är som det lokala datorkontot inte virtuellt konto användarkontexten.

Domänkontrollanter är ett specialfall, eftersom det inte finns en lokal **administratörer** grupp. I stället virtuella konton tillhör **Domänadministratörer** och kan hantera katalogtjänster på domänkontrollanten. Domän-identiteten är fortfarande begränsad till användning på domänkontrollanten där JEA-sessionen har initierats. Alla nätverksåtkomst verkar komma från domänkontrollantens datorobjekt i stället.

I båda fallen kan du uttryckligen definiera vilka säkerhetsgrupper virtuella kontot tillhör. Detta är en bra idé när uppgiften kan göras utan lokala administratörsprivilegier. Om du redan har en säkerhetsgrupp som definierats för dina administratörer kan bevilja virtuellt konto medlemskap i gruppen. Virtuellt konto gruppmedlemskap är begränsad till lokala säkerhetsgrupper på arbetsstationer och medlemsservrar. Virtuella konton måste vara medlemmar i domänsäkerhetsgrupper på domänkontrollanter.
När virtuella kontot har lagts till en eller flera säkerhetsgrupper, tillhör det inte längre standardgrupper (lokal eller domänåtkomst administratörer).

I följande tabell sammanfattas de möjliga konfigurationsalternativ och resulterande behörigheter för virtuella konton:

|        Typ av dator         | Virtuell grupp kontokonfigurationen |                   Lokala användarkontext                    | Nätverket användarkontext |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Domänkontrollant            | Standard                             | Domänanvändare, medlem i ”*domän*\Domain'         | Datorkonto     |
| Domänkontrollant            | Domängrupper A och B               | Domänanvändare, medlem i ”*domän*\A ','*domän*\B'       | Datorkonto     |
| Medlemsserver eller arbetsstation | Standard                             | Lokal användare, medlem i ”*BUILTIN*\Administrators'        | Datorkonto     |
| Medlemsserver eller arbetsstation | Lokala grupper C och D                | Lokal användare, medlem i ”*datorn*\C' och '*datorn*\D” | Datorkonto     |

När du tittar på säkerhetsgranskningshändelser och händelseloggarna för programmet, ser du att varje användarsession i JEA har ett unikt virtuellt konto. Det här unika kontot kan du spåra användaråtgärder i en JEA-slutpunkt tillbaka till den ursprungliga användaren som körde kommandot. Virtuellt konto namnen följer formatet `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` till exempel om användaren **Alice** i domänen **Contoso** startar om en tjänst i en JEA-slutpunkt, användarnamnet som är associerade med alla tjänsthanteraren händelser blir `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

**Gruppen hanterade tjänstkonton (gMSAs)** är användbara när en medlemsserver måste ha åtkomst till nätverksresurser i JEA-session. Till exempel när en JEA-slutpunkt används för att styra åtkomsten till en REST API-tjänst som finns på en annan dator. Det är enkelt att skriva funktioner för att anropa REST-API: er, men du behöver en nätverksidentitet för att autentisera med API: et. Ett-grupphanterat tjänstkonto gör det andra hoppet möjligt samtidigt som de behåller kontroll över vilka datorer kan använda kontot. GMSA gällande behörigheter definieras av säkerhetsgrupper (lokalt eller via domänadministratör) som gMSA-kontot tillhör.

När en JEA-slutpunkt har konfigurerats för att använda ett gMSA åtgärderna för alla JEA-användare ser ut att komma från samma gMSA. Det enda sättet att spåra åtgärder tillbaka till en specifik användare är att identifiera uppsättningen kommandon som körs i en PowerShell-session avskrift.

**Pass till autentiseringsuppgifter** används när du inte anger en **kör som-** konto. PowerShell använder anslutande användarens autentiseringsuppgifter för att köra kommandon på fjärrservern. Detta måste du ge den anslutande användare direkt åtkomsten till Privilegierade hanteringsgrupper. Den här konfigurationen är **inte** rekommenderas för JEA. Om den anslutande användaren redan har administratörsrättigheter, kan de undvika JEA och hantera systemet via andra, obegränsad innebär. Mer information finns i avsnittet nedan om hur [JEA inte skydda mot administratörer](#jea-doesnt-protect-against-admins).

**Kör som-standardkonton** kan du ange ett användarkonto som hela PowerShell-sessionen körs under. Sessionskonfigurationer med fast **kör som-** konton (med den `-RunAsCredential` parametern) är inte medvetna om JEA. Rolldefinitioner fungerar inte som förväntat. Varje användare som har behörighet att komma åt slutpunkten tilldelas samma roll.

Du bör inte använda en **RunAsCredential** på en JEA-slutpunkt eftersom det är svårt att spåra åtgärder till specifika användare och saknar stöd för att mappa användare till roller.

## <a name="winrm-endpoint-acl"></a>WinRM slutpunkts-ACL

Som med vanlig PowerShell-fjärrkommunikation slutpunkter varje JEA-slutpunkt har en separat åtkomstkontrollista (ACL) som styr vem som kan autentisera med JEA-slutpunkt. Om felaktigt konfigurerad, betrodda användare kanske inte kan komma åt JEA-slutpunkt och ej betrodda användare kan ha åtkomst. WinRM-ACL påverkar inte mappningen av användare till JEA-roller. Mappningen styrs av den **RoleDefinitions** fält i konfigurationsfilen session används för att registrera slutpunkten.

Som standard när en JEA-slutpunkt har flera rollfunktioner är WinRM ACL konfigurerad för att tillåta åtkomst till alla mappade användare. Till exempel en JEA-session som har konfigurerats med hjälp av följande kommandon ger fullständig åtkomst till `CONTOSO\JEA_Lev1` och `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Du kan granska användarbehörigheter med den [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Om du vill ändra vilka användare som har åtkomst, kör du antingen `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` för en interaktiv prompt eller `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` att uppdatera behörigheterna. Användare behöver minst *Invoke* behörighet att komma åt JEA-slutpunkt.

Det är möjligt att skapa en JEA-slutpunkt som inte mappar en definierad roll till alla användare som har åtkomst. Dessa användare kan starta en JEA-session, men bara har åtkomst till cmdletarna som standard. Du kan granska användarbehörigheter i en JEA-slutpunkt genom att köra `Get-PSSessionCapability`. Mer information finns i [gransknings- och rapportering i JEA](audit-and-report.md).

## <a name="least-privilege-roles"></a>Minsta privilegium roller

När du designar JEA roller, är det viktigt att komma ihåg att de virtuella och grupp-hanterade tjänstkonton som körs i bakgrunden kan har obegränsad åtkomst till den lokala datorn. JEA rollfunktioner hjälper att begränsa kommandon och program som kan köras i den privilegierade kontexten.
Felaktigt roller kan farliga kommandon som kan tillåta en användare att dela ut från JEA-gränser eller få åtkomst till känslig information.

Anta exempelvis att följande roll funktionen post:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Den här rollen-funktionen kan användare köra alla PowerShell-cmdlet med substantivet **processen** från den **Microsoft.PowerShell.Management** modulen. Användare kan behöva använda cmdletar som `Get-Process` att se vilka program som körs på systemet och `Stop-Process` att avsluta program som inte svarar. Den här posten också kan dock `Start-Process`, som kan användas för att starta en godtycklig program med fullständig administratörsbehörighet. Programmet behöver inte installeras lokalt på systemet. En anslutna användare kan starta ett program från en filresurs som ger användaren privilegier som lokal administratör, kör skadlig kod och mycket mer.

En säkrare version av den här samma roll funktionen ser ut som:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Undvik att använda jokertecken i rollfunktioner. Var noga med att regelbundet [granska effektiva användarbehörigheter](audit-and-report.md#check-effective-rights-for-a-specific-user) att förstå vilka kommandon som är tillgängliga för användaren.

## <a name="jea-doesnt-protect-against-admins"></a>JEA skydda inte mot administratörer

En av huvudprinciperna för JEA är icke-administratörer att utföra vissa administratör tillåter. JEA skydda inte mot användare som redan har administratörsbehörighet. Användare som tillhör **Domänadministratörer**lokal **administratörer**, eller andra mycket Privilegierade grupper kan kringgå JEAS skydd via ett annat sätt. De kan till exempel logga in med RDP, använda fjärranslutna MMC-konsoler eller ansluta till obegränsad PowerShell-slutpunkter. Lokala administratörer på ett system kan också ändra JEA-konfigurationer för att tillåta ytterligare användare eller ändra en roll-funktion för att utöka omfånget för en användare kan göra i sina JEA-session. Det är viktigt att utvärdera JEA användarnas utökade behörigheter för att se om det finns andra sätt att få privilegierad åtkomst till systemet.

En vanlig metod är att använda JEA för vanliga dagliga underhåll och har en just-in-time, en hanteringslösning för privilegierad åtkomst som tillåter användare att tillfälligt blir lokala administratörer i nödsituationer. Detta hjälper till att säkerställa användare inte permanenta administratörer i systemet, men kan hämta dessa rättigheter om och när de utföra ett arbetsflöde som dokument deras användning av dessa behörigheter.
