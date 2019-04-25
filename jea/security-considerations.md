---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: JEA-säkerhetsaspekter
ms.openlocfilehash: 9526e141517601ae3b6d6932cd3536fdf49aa9a6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084784"
---
# <a name="jea-security-considerations"></a>JEA-säkerhetsaspekter

> Gäller för: Windows PowerShell 5.0

JEA hjälper dig att förbättra din säkerhetsposition genom att minska antalet permanenta administratörer på dina datorer.
Detta sker genom att skapa en ny startpunkt för användare att hantera system (en PowerShell-session-konfiguration) som är nära låsta som standard för att förhindra missbruk.
Användare som behöver vissa, men inte obegränsad åtkomst till datorn för att utföra administrativa uppgifter kan beviljas åtkomst till JEA-slutpunkt.
Eftersom JEA tillåter dem att köra admin-kommandon utan direkt administratörsåtkomst, kan du sedan ta bort dessa användare från säkerhetsgrupper med med hög behörighetsnivå (blir vanliga användare).

Det här avsnittet beskriver JEA-säkerhetsmodellen och bästa praxis i detalj.

## <a name="run-as-account"></a>Kör som-konto

Varje JEA-slutpunkt har ett konto med avsedda ”kör som”, vilket är det konto som den anslutande användaren åtgärder utförs.
Det här kontot kan konfigureras i den [session konfigurationsfilen](session-configurations.md), och det konto som du väljer har betydelse på säkerheten för din slutpunkt.

**Virtuella konton** är det rekommenderade sättet att konfigurera kör som-konto.
Virtuella konton är enstaka, tillfälligt lokala konton som har skapats för den anslutande användaren ska användas under hela sin JEA-session.
Så snart som sin session avslutas virtuellt konto kommer att raderas och kan inte längre användas.
Den anslutande användaren vet inte autentiseringsuppgifterna för virtuellt konto och kan inte använda virtuella konto för att komma åt systemet via andra sätt, till exempel Remote Desktop eller en obegränsad PowerShell-slutpunkt.

Som standard tillhör virtuella konton gruppen lokala administratörer på datorn.
Detta ger dem fullständiga rättigheter att hantera allt i systemet, men inga rättigheter att hantera resurser i nätverket.
När du autentiserar med andra datorer blir användarkontexten som lokalt datorkonto, inte virtuellt konto.

Domänkontrollanter är ett specialfall, eftersom det inte finns något begrepp om lokala administratörsgruppen.
I stället virtuella konton tillhör Domänadministratörer i stället och kan hantera katalogtjänster på domänkontrollanten.
Domän-identiteten är fortfarande begränsad till att använda på den domänkontrollant där JEA-sessionen har initierats, och eventuella nätverksåtkomst visas komma från domänkontrollantens datorobjekt i stället.

I båda fallen kan du också explicit definiera vilka säkerhetsgrupper som virtuellt konto ska tillhöra.
Detta är en bra idé när den uppgift du utför kan göras utan lokal/domänadministratörsprivilegier.
Om du redan har en säkerhetsgrupp som definierats för dina administratörer kan ge du helt enkelt virtuellt konto medlemskap i gruppen att ge det de behörigheter som krävs.
Virtuellt konto gruppmedlemskap är begränsad till lokala säkerhetsgrupper på arbetsstation och medlemmen servrar, men på en domänkontrollant kan de bara vara medlemmar i domänsäkerhetsgrupper.
När du anger en eller flera säkerhetsgrupper för virtuellt konto om du vill tillhör, kommer den inte längre tillhör standardgrupper (lokal administratör eller domänadministratör).

I tabellen nedan sammanfattas de möjliga konfigurationsalternativ och resulterande behörigheter för virtuella konton

Typ av dator                | Virtuell grupp kontokonfigurationen | Lokala användarkontext                                      | Nätverket användarkontext
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Domänkontrollant            | Standard                             | Domänanvändare, medlem i ”*domän*\Domain'         | Datorkonto
Domänkontrollant            | Domängrupper A och B               | Domänanvändare, medlem i ”*domän*\A ','*domän*\B'       | Datorkonto
Medlemsserver eller arbetsstation | Standard                             | Lokal användare, medlem i ”*BUILTIN*\Administrators'        | Datorkonto
Medlemsserver eller arbetsstation | Lokala grupper C och D                | Lokal användare, medlem i ”*datorn*\C' och '*datorn*\D” | Datorkonto

När du tittar på säkerhetsgranskningshändelser och händelseloggarna för programmet, ser du att varje användarsession i JEA har ett unikt virtuellt konto.
På så sätt kan du spåra användaråtgärder i en JEA-slutpunkt tillbaka till den ursprungliga användaren som körde kommandot.
Virtuellt konto namnen följer formatet ”WinRM virtuella användare\\WinRM\_VA\_*ACCOUNTNUMBER*\_*domän* \_ *sAMAccountName*”till exempel om användaren” Alice ”i domänen” Contoso ”startar om en tjänst i en JEA-slutpunkt, användarnamnet som är associerade med alla service control manager-händelser blir” WinRM virtuella användare\\WinRM\_ VA\_1\_contoso\_alice ”.


**Gruppen hanterade tjänstkonton (gMSAs)** är användbara när en medlemsserver måste ha åtkomst till nätverksresurser i JEA-session.
Ett exempel för det här är en JEA-slutpunkt som används för att styra åtkomsten till en REST-API som finns på en annan dator.
Det är enkelt att skriva funktioner till att göra de önskade anrop för REST API, men för att kunna autentisera med API: et som du behöver en nätverksidentitet.
Med hjälp av en grupphanterade tjänstkontot gör ”andra hopp” möjligt medan du fortfarande har kontroll över vilka datorer kan använda kontot.
GMSA gällande behörigheter definieras av säkerhetsgrupper (lokalt eller via domänadministratör) som gMSA-kontot tillhör.

När en JEA-slutpunkt har konfigurerats för att använda ett gMSA-konto visas åtgärderna för alla JEA-användare komma från samma grupp Hanterat tjänstkonto.
Det enda sättet som du kan spåra åtgärder tillbaka till en specifik användare är att identifiera uppsättningen kommandon som körs i en PowerShell-session avskrift.

**Pass till autentiseringsuppgifter** används när du inte ange ett kör som-konto och vill använda PowerShell för att använda den anslutande användarens autentiseringsuppgifter för att köra kommandon på fjärrservern.
Den här konfigurationen är *inte* rekommenderas för JEA eftersom det kräver att bevilja den anslutande användare direkt åtkomsten till Privilegierade hanteringsgrupper.
Om den anslutande användaren redan har administratörsrättigheter, kan de undvika JEA helt och hållet och hantera systemet via andra, obegränsad innebär.
Se avsnittet nedan om hur [JEA skyddar inte mot administratörer](#jea-does-not-protect-against-admins) för mer information.

**Standard kör som-konton** kan du ange ett användarkonto som ska köras på hela PowerShell-sessionen.
Detta är en viktig skillnad eftersom en sessionskonfiguration inställd på att använda ett fast kör som-konto (med den `-RunAsCredential` parametern) inte är JEA-medveten.
Det innebär att att rolldefinitioner inte längre fungerar som förväntat och att varje användare som har behörighet att komma åt slutpunkten kommer att tilldelas samma roll.

Du bör inte använda en RunAsCredential på en JEA-slutpunkt på grund av problem i spårning av åtgärder till specifika användare och avsaknaden av stöd för att mappa användare till roller.

## <a name="winrm-endpoint-acl"></a>WinRM slutpunkts-ACL

Som med vanlig PowerShell-fjärrkommunikation slutpunkter varje JEA-slutpunkt har en separat åtkomstkontrollista (ACL) i WinRM-konfigurationen som styr vem som kan autentisera med JEA-slutpunkt.
Om felaktigt konfigurerad, betrodda användare kanske inte kan komma åt JEA-slutpunkt och/eller ej betrodda användare kan komma åt den.
WinRM-ACL påverkar inte, men mappningen av användare till JEA-roller.
Som styrs av den *RoleDefinitions* i konfigurationsfilen session som har registrerats i systemet.

Som standard när du registrerar en JEA-slutpunkt med hjälp av en konfigurationsfil för sessionen och en eller flera rollfunktioner konfigureras WinRM ACL för att tillåta alla användare som mappar till en eller flera roller tillgång till slutpunkten.
Till exempel en JEA-session som har konfigurerats med hjälp av följande kommandon för att ge fullständig åtkomst till *CONTOSO\JEA\_Lev1* och *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Du kan granska användarbehörigheter med den [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Om du vill ändra vilka användare som har åtkomst, kör du antingen `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` för en interaktiv prompt eller `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` att uppdatera behörigheterna.
Användare behöver minst *Invoke* behörighet att komma åt JEA-slutpunkt.

Om ytterligare användare beviljas åtkomst till JEA-slutpunkt, men inte tillhör någon av de roller som definierats i konfigurationsfilen för sessionen, kommer de att kunna starta en JEA-session men bara har åtkomst till cmdletarna som standard.
Du kan granska användarbehörigheter i en JEA-slutpunkt genom att köra `Get-PSSessionCapability`.
Kolla in den [gransknings- och rapportering i JEA](audit-and-report.md) artikeln för mer information om granskning vilka kommandon en användare har åtkomst till i en JEA-slutpunkt.

## <a name="least-privilege-roles"></a>Minsta privilegium roller

När du designar JEA roller, är det viktigt att komma ihåg att den virtuella eller gruppen hanterad tjänst-konto som kör i bakgrunden ofta har obegränsad åtkomst för att hantera den lokala datorn.
JEA rollfunktioner i syfte att begränsa vad det kontot kan användas för genom att begränsa de kommandon och program som kan köras med den privilegierade kontexten.
Felaktigt roller kan farliga kommandon som ska köras som kan tillåta en användare att dela ut från JEA-gränser eller få åtkomst till känslig information.

Anta exempelvis att följande roll funktionen post:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Den här rollen-funktionen kan användare köra alla PowerShell-cmdlet med substantiv ”Process” från modulen Microsoft.PowerShell.Management.
Användare kan behöva använda cmdletar som `Get-Process` att förstå vilka program som körs på systemet och `Stop-Process` att avsluta alla program som inte svarar.
Den här posten också kan dock `Start-Process`, som kan användas för att starta en godtycklig program med fullständig administratörsbehörighet.
Programmet inte behöver installeras lokalt på datorn, så att en angripare kan bara starta ett program på en filresurs som ger de anslutande användarbehörigheter för lokal administratör och kör skadlig kod ”.

En säkrare version av den här samma roll funktionen ser ut som:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Undvik att använda jokertecken i rollfunktioner och se till att [granska effektiva användarbehörigheter](audit-and-report.md#check-effective-rights-for-a-specific-user) regelbundet att förstå vilka kommandon som en användare har åtkomst till.

## <a name="jea-does-not-protect-against-admins"></a>JEA skyddar inte mot administratörer

En av huvudprinciperna för JEA är möjligheten för icke-administratörer att utföra *vissa* administrativa uppgifter.
JEA skyddar inte mot de som redan har administratörsbehörighet.
Användare som tillhör ”Domänadministratörer”, ”lokala administratörer”, eller andra mycket Privilegierade grupper i din miljö kommer fortfarande att kunna komma runt JEAS skydd genom att logga in på datorn via ett annat sätt.
De kan till exempel logga in med RDP, använda fjärranslutna MMC-konsoler eller ansluta till obegränsad PowerShell-slutpunkter.
Lokala administratörer på systemet kan också ändra JEA-konfigurationer för att tillåta ytterligare användare att hantera systemet eller ändra en roll-funktion för att utöka omfånget för en användare kan göra i sina JEA-session.
Det är därför viktigt att utvärdera JEA användarnas utökade behörigheter för att se om det finns andra sätt som de kan få privilegierad åtkomst till systemet.

En vanlig metod är att använda JEA för vanliga dagliga underhåll och har ”just in-time” privilegierad åtkomsthanteringslösning kan du tillfälligt blir lokala administratörer i nödsituationer.
Detta hjälper till att säkerställa användare inte är permanenta administratörer på systemet, men kan hämta dessa rättigheter om och när de utföra ett arbetsflöde som dokument deras användning av dessa behörigheter.