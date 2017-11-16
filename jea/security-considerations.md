---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea powershell säkerhet"
title: "JEA säkerhetsaspekter"
ms.openlocfilehash: 2dcce34113998a1c31709b6afe6d0a21c991e79d
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2017
---
# <a name="jea-security-considerations"></a>JEA säkerhetsaspekter

> Gäller för: Windows PowerShell 5.0

JEA hjälper dig att förbättra din säkerhetstillståndet genom att minska antalet permanenta administratörer på dina datorer.
Den gör detta genom att skapa en ny startpunkt för användare att hantera systemet (en PowerShell-session-konfiguration) som är nära låst som standard för att förhindra missbruk.
Användare som behöver vissa, men inte obegränsad åtkomst till datorn för att utföra administrativa uppgifter kan beviljas åtkomst till JEA slutpunkten.
Eftersom JEA tillåter dem att köra kommandon admin direkt utan administratörsåtkomst, du kan sedan ta bort dem från mycket Privilegierade säkerhetsgrupper (se dem standardanvändare).

Det här avsnittet beskriver JEA säkerhetsmodell och bästa praxis i detalj.

## <a name="run-as-account"></a>Kör som-konto

Varje JEA slutpunkt har ett konto med avsedda ”kör som”, som är det konto som den anslutande användaren åtgärder utförs.
Det här kontot kan konfigureras i den [session konfigurationsfilen](session-configurations.md), och det konto som du väljer har betydelse säkerheten för din slutpunkt.

**Virtuella konton** är det rekommenderade sättet att konfigurera kör som-konto.
Virtuella konton är gång, tillfälligt lokala konton som skapas för den anslutande användaren ska användas under sin JEA-session.
Så snart som sin session avslutas virtuellt konto kommer att raderas och kan inte användas längre.
Den anslutande användaren känner inte till autentiseringsuppgifterna för virtuellt konto och virtuella konton kan inte användas för att komma åt systemet via andra sätt, till exempel Remote Desktop eller en obegränsad PowerShell-slutpunkt.

Som standard tillhör virtuella konton gruppen lokala administratörer på datorn.
Detta ger dem fullständig behörighet att hantera allt på systemet, men inga rättigheter att hantera resurser i nätverket.
Vid autentisering med andra datorer blir användarkontexten som lokalt datorkonto, inte virtuellt konto.

Domänkontrollanter är ett specialfall, eftersom det inte finns något begrepp om den lokala administratörsgruppen.
I stället virtuella konton tillhör gruppen Domänadministratörer i stället och kan hantera katalogtjänsterna på domänkontrollanten.
Domän-identitet begränsas fortfarande att använda på den domänkontrollant där JEA sessionen har initierats och eventuella nätverksåtkomst verkar komma från domänkontrollantens datorobjekt i stället.

I båda fallen kan du också explicit definiera vilka säkerhetsgrupper virtuellt konto ska tillhöra.
Detta är en bra idé när den uppgift du utför kan göras utan lokal/domain admin-privilegier.
Om du redan har en säkerhetsgrupp som definierats för dina administratörer beviljar du helt enkelt virtuellt konto medlemskap i gruppen att ge det de behörigheter som krävs.
Virtuella gruppmedlemskap är begränsad till lokala säkerhetsgrupper på arbetsstationer och medlemsservrar, men på en domänkontrollant kan endast vara medlemmar i domänsäkerhetsgrupper.
När du anger en eller flera säkerhetsgrupper för virtuellt konto om du vill tillhör, kommer den inte längre tillhör standardgrupper (lokal administratör eller domänadministratör).

I tabellen nedan sammanfattas de möjliga konfigurationsalternativ och resulterande behörigheter för virtuella konton

Typ av dator                | Konfiguration av virtuellt konto | Lokala användare                                      | Nätverket användarkontext
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Domänkontrollant            | Standard                             | Domänanvändare, medlem '*domän*\Domain'         | Datorkonto
Domänkontrollant            | Domängrupper A och B               | Domänanvändare, medlem '*domän*\A ','*domän*\B'       | Datorkonto
Medlemsserver eller arbetsstation | Standard                             | Lokala användare, medlem '*BUILTIN*\Administrators'        | Datorkonto
Medlemsserver eller arbetsstation | Lokala grupper C och D                | Lokala användare, medlem '*datorn*\C' och '*datorn*\D' | Datorkonto

När du tittar på säkerhetsgranskningshändelser och Loggboken program ser du att varje JEA användarsession har ett unikt virtuellt konto.
Detta hjälper dig att spåra användaråtgärder i en slutpunkt för JEA tillbaka till den ursprungliga användaren som har kört kommandot.
Virtuellt konto namn följa formatet ”WinRM virtuella användare\\WinRM\_VA\_*ACCOUNTNUMBER*\_*domän* \_ *sAMAccountName*”om användaren” Alice ”i domänen” Contoso ”startar om en tjänst i en JEA slutpunkt, användarnamnet som är associerade med alla service control manager-händelser skulle exempelvis” WinRM virtuella användare\\WinRM\_ VA\_1\_contoso\_alice ”.


**Gruppera hanterade tjänstkonton (Gmsa)** är användbara när en medlemsserver måste ha tillgång till nätverksresurser i JEA-sessionen.
Ett exempel användningsfall för det här är en JEA-slutpunkt som används för att styra åtkomsten till en REST-API som finns på en annan dator.
Det är enkelt att skriva funktioner så att de önskade anrop på REST API, men för att kunna autentisera med API du behöver en nätverksidentitet.
Med hjälp av en grupphanterade tjänstkontot möjliggör ”andra hopp” medan du fortfarande har kontroll över vilka datorer som kan använda kontot.
GMSA gällande behörigheter har definierats av säkerhetsgrupper (lokalt eller via domänadministratör) som gMSA-kontot tillhör.

När en JEA slutpunkt har konfigurerats för att använda ett gMSA-konto visas åtgärder för alla JEA användare att komma från samma grupp Hanterat tjänstkonto.
Det enda sättet du kan spåra åtgärder tillbaka till en specifik användare är att identifiera en uppsättning kommandon som körs i ett PowerShell-session betyg.

**Skicka via autentiseringsuppgifter** används när du inte ange ett kör som-konto och vill använda PowerShell för att använda den anslutande användaren autentiseringsuppgifter för att köra kommandon på fjärrservern.
Den här konfigurationen är *inte* rekommenderas för JEA som kräver den du bevilja den anslutande användare direkt åtkomsten till Privilegierade hanteringsgrupper.
Om den anslutande användaren redan har administratörsrättigheter, kan de helt undvika JEA och hantera systemet via andra, obegränsad innebär.
Gå till avsnittet nedan om hur [JEA skyddar inte mot administratörer](#jea-does-not-protect-against-admins) för mer information.

**Standard kör som-konton** kan du ange ett användarkonto som hela PowerShell-session ska köras under.
Detta är en viktig skillnad eftersom en sessionskonfiguration inställd på att använda en fast kör som-konto (med den `-RunAsCredential` parametern) är inte medveten om JEA.
Som innebär att rolldefinitioner inte längre att fungera som förväntat och alla användare som har behörighet att komma åt slutpunkten ska tilldelas samma roll.

Du bör inte använda en RunAsCredential på en slutpunkt för JEA på grund av svårigheterna med att spåra åtgärder tillbaka till specifika användare och saknas stöd för att mappa användare till roller.

## <a name="winrm-endpoint-acl"></a>WinRM slutpunkts-ACL

Som med vanlig PowerShell fjärrkommunikation slutpunkter varje JEA slutpunkt har en separat åtkomstkontrollistan (ACL) i WinRM-konfigurationen som styr som kan autentisera med JEA-slutpunkten.
Om felaktigt konfigurerad betrodda användare kan inte komma åt slutpunkten JEA och/eller ej betrodda användare kan komma åt.
WinRM ACL påverkar inte, men mappningen av användare i JEA roller.
Som styrs av den *RoleDefinitions* i konfigurationsfilen session som har registrerats i systemet.

Som standard när du registrerar en JEA-slutpunkten med hjälp av en session-konfigurationsfil och en eller flera funktioner för rollen, konfigureras WinRM ACL så att alla användare som mappar till en eller flera roller åtkomst till slutpunkten.
Till exempel en JEA-session som har konfigurerats för att använda följande kommandon kommer att ge fullständig åtkomst till *CONTOSO\JEA\_Lev1* och *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Du kan granska användarbehörigheter med den [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Om du vill ändra vilka användare som har åtkomst, genom att köra något `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` för en interaktiv prompt eller `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` att uppdatera behörigheter.
Användare behöver de minst *Invoke* behörighet att komma åt JEA slutpunkten.

Om ytterligare användare beviljas åtkomst till slutpunkten JEA men inte tillhör någon av de roller som definierats i konfigurationsfilen session, kommer de att kunna starta en session JEA, men bara åtkomst till cmdletarna som standard.
Du kan granska användarbehörigheter i en slutpunkt för JEA genom att köra `Get-PSSessionCapability`.
Kolla in den [granskning och rapportering av JEA](audit-and-report.md) artikel för mer information om granskning som kommandon en användare har åtkomst till i en JEA slutpunkt.

## <a name="least-privilege-roles"></a>Minsta privilegium roller

När du designar JEA roller, är det viktigt att komma ihåg att den virtuella eller gruppen hanterad tjänst konto körs i bakgrunden ofta har obegränsad åtkomst för att hantera den lokala datorn.
JEA roll funktioner att begränsa vad det kontot som kan användas för genom att begränsa de kommandon och program som kan köras med den privilegierade kontexten.
Felaktigt roller kan farliga kommandon som ska köras som kan tillåta en användare att dela upp utanför gränserna för JEA eller få åtkomst till känslig information.

Tänk dig följande roll kapaciteten post:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Den här rollen funktionen tillåter användare att köra PowerShell-cmdlet med substantiv ”Process” från modulen Microsoft.PowerShell.Management.
Användare kan behöva använda cmdlets som `Get-Process` att förstå vilka program som körs på systemet och `Stop-Process` avstannat att avsluta några program.
Men den här posten kan också `Start-Process`, som kan användas för att starta en godtycklig program med fullständiga administratörsrättigheter.
Programmet behöver installeras lokalt på datorn, så en angriparen kan bara starta ett program på en filresurs som ger de anslutande användarbehörigheter för lokal administratör och skadlig kod körs ”.

En säkrare version av den här funktionen för samma roll ser ut som:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Undvik att använda jokertecken i rollen funktioner och se till att [granska gällande behörigheter](audit-and-report.md#check-effective-rights-for-a-specific-user) regelbundet förstå vilka kommandon som en användare har åtkomst till.

## <a name="jea-does-not-protect-against-admins"></a>JEA skyddar inte mot administratörer

En av de grundläggande principerna för JEA är icke-administratörer att utföra tillåter *vissa* administrativa uppgifter.
JEA skyddar inte mot de som redan har administratörsbehörighet.
Användare som tillhör ”Domänadministratörer”, ”lokala administratörer” eller andra mycket Privilegierade grupper i din miljö kommer fortfarande att kunna hämta runt JEAS skydd genom att logga in på datorn via ett annat sätt.
De kan till exempel logga in med RDP, använda remote MMC-konsoler, eller Anslut till obegränsad PowerShell-slutpunkter.
Lokala administratörer på datorn kan också ändra JEA konfigurationer för att tillåta ytterligare användare att hantera systemet eller ändra roll möjligheter att utöka omfånget för en användare kan göra i deras JEA-session.
Det är därför viktigt att utvärdera JEA användarnas utökad behörighet för att se om det finns andra sätt som de kan få privilegierad åtkomst till systemet.

Vanligt är att använda JEA för dagliga regelbundet underhåll och har ”bara i tiden” privileged access management lösningen att användarna blir tillfälligt lokala administratörer i nödfall.
På så sätt försäkrar du dig användare inte är permanenta administratörer på datorn, men kan få dessa behörigheter om och när de utför ett arbetsflöde som dokument deras användning av dessa behörigheter.

