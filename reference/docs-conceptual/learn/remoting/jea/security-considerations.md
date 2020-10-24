---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: JEA säkerhets aspekter
description: Eftersom JEA tillåter dessa användare att köra administrations kommandon utan att ha fullständig administratörs behörighet kan du ta bort dessa användare från privilegierade säkerhets grupper.
ms.openlocfilehash: f65f9d6c6620261de0a9c8de7812637565ca1806
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501583"
---
# <a name="jea-security-considerations"></a>JEA säkerhets aspekter

JEA hjälper dig att förbättra din säkerhets-position genom att minska antalet permanenta administratörer på dina datorer. JEA använder en PowerShell-session konfiguration för att skapa en ny start punkt som användare kan använda för att hantera systemet. Användare som behöver förhöjd, men inte obegränsad, åtkomst till datorn för att utföra administrativa uppgifter kan beviljas åtkomst till JEA-slutpunkten. Eftersom JEA tillåter dessa användare att köra administrations kommandon utan att ha fullständig administratörs behörighet kan du ta bort dessa användare från privilegierade säkerhets grupper.

## <a name="run-as-account"></a>Run-As konto

Varje JEA-slutpunkt har ett angivet **Kör som-** konto. Detta är det konto under vilket den anslutande användarens åtgärder utförs. Det här kontot kan konfigureras i [konfigurations filen för sessionen](session-configurations.md)och det konto du väljer har stor betydelse för slut punktens säkerhet.

**Virtuella konton** är det rekommenderade sättet att konfigurera **Kör som-** kontot. Virtuella konton är temporära, temporära lokala konton som skapas för den anslutande användare som ska användas under hela JEA-sessionen. Så snart sessionen avslutas, förstörs det virtuella kontot och kan inte användas längre. Den anslutande användaren känner inte till autentiseringsuppgifterna för det virtuella kontot. Det virtuella kontot kan inte användas för att komma åt systemet via andra sätt som t. ex. fjärr skrivbord eller en obegränsad PowerShell-slutpunkt.

Som standard tillhör de virtuella kontona den lokala gruppen **Administratörer** på datorn. Detta ger dem fullständig behörighet att hantera vad som helst i systemet, men inga rättigheter att hantera resurser i nätverket.
När du autentiserar med andra datorer är användar kontexten för det lokala dator kontot, inte det virtuella kontot.

Domänkontrollanter är särskilda fall eftersom det inte finns någon lokal **Administratörs** grupp. I stället tillhör de virtuella kontona **domän administratörer** och kan hantera katalog tjänsterna på domänkontrollanten. Domän identiteten är fortfarande begränsad för användning på domänkontrollanten där JEA-sessionen instansierades. Nätverks åtkomsten visas i stället från domänkontrollantens dator objekt.

I båda fallen kan du uttryckligen definiera vilka säkerhets grupper som det virtuella kontot tillhör. Det här är en bra metod när du kan utföra en uppgift utan administratörs behörighet för lokala eller domän administratörer. Om du redan har definierat en säkerhets grupp för dina administratörer tilldelar du det virtuella kontots medlemskap i gruppen. Medlemskap i virtuella konto grupper är begränsat till lokala säkerhets grupper på arbets stationer och medlems servrar. På domänkontrollanter måste virtuella konton vara medlemmar i domän säkerhets grupper.
När det virtuella kontot har lagts till i en eller flera säkerhets grupper tillhör det inte längre standard grupperna (lokala administratörer eller domän administratörer).

I följande tabell sammanfattas möjliga konfigurations alternativ och resulterande behörigheter för virtuella konton:

|        Datortyp         | Konfiguration av virtuellt konto grupp |                   Lokal användar kontext                    | Nätverks användar kontext |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Domänkontrollant            | Standard                             | Domän användare, medlem i "*Domain*\Domain admins"         | Dator konto     |
| Domänkontrollant            | Domän grupper A och B               | Domän användare, medlem i*domän*\A,*domän*\b       | Dator konto     |
| Medlems Server eller arbets Station | Standard                             | Lokal användare, medlem i "*Builtin*\Administrators"        | Dator konto     |
| Medlems Server eller arbets Station | Lokala grupper C och D                | Lokal användare, medlem i "*Computer*\c" och "*Computer*\d" | Dator konto     |

När du tittar på säkerhets gransknings händelser och program händelse loggar ser du att varje JEA-användarsession har ett unikt virtuellt konto. Det här unika kontot hjälper dig att spåra användar åtgärder i en JEA-slutpunkt tillbaka till den ursprungliga användare som körde kommandot. Virtuella konto namn följer formatet `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` . om användaren till exempel går **Alice** in i domän **contoso** och startar om en tjänst i en Jea-slutpunkt, är det användar namn som är associerat med alla Service Control Manager-händelser `WinRM Virtual Users\WinRM_VA_1_contoso_alice` .

**Grupphanterade tjänst konton (gMSAs)** är användbara när en medlems Server måste ha åtkomst till nätverks resurser i Jea-sessionen. Till exempel när en JEA-slutpunkt används för att styra åtkomsten till en REST API tjänst som finns på en annan dator. Det är enkelt att skriva funktioner för att anropa REST-API: er, men du behöver en nätverks identitet för att autentisera med API: et. Genom att använda ett grupphanterat tjänst konto gör du det andra hoppet möjligt samtidigt som du behåller kontrollen över vilka datorer som kan använda kontot. De gällande behörigheterna för gMSA definieras av de säkerhets grupper (lokala eller domän) som gMSA-kontot tillhör.

När en JEA-slutpunkt har kon figurer ATS för att använda en gMSA, verkar åtgärderna för alla JEA-användare komma från samma gMSA. Det enda sättet att spåra åtgärder tillbaka till en bestämd användare är att identifiera de kommandon som körs i en avskrift för en PowerShell-session.

**Direkt inloggnings uppgifter** används när du inte anger ett **Kör som-** konto. PowerShell använder den anslutande användarens autentiseringsuppgift för att köra kommandon på fjärrservern. Detta kräver att du ger den anslutande användaren direkt åtkomst till privilegierade hanterings grupper. Den här konfigurationen rekommenderas **inte** för Jea. Om den anslutna användaren redan har administratörs behörighet kan de undvika JEA och hantera systemet via andra, obegränsade medel. Mer information finns i avsnittet nedan om hur [Jea inte skyddar mot administratörer](#jea-doesnt-protect-against-admins).

Med **standard kör som-konton** kan du ange vilket användar konto som hela PowerShell-sessionen ska köras under. Sessionshantering som använder fasta **Kör som** -konton (med `-RunAsCredential` parametern) är inte Jea-medvetna. Roll definitionerna fungerar inte längre som förväntat. Alla användare som har behörighet att komma åt slut punkten tilldelas samma roll.

Du bör inte använda en **RunAsCredential** på en Jea-slutpunkt eftersom det är svårt att spåra åtgärder tillbaka till vissa användare och saknar stöd för mappning av användare till roller.

## <a name="winrm-endpoint-acl"></a>Åtkomst kontrol lista för WinRM-slutpunkt

Precis som med vanliga PowerShell-slutpunkter för fjärrkommunikation har varje JEA-slutpunkt en separat åtkomst kontrol lista (ACL) som styr vem som kan autentisera med JEA-slutpunkten. Om det är felaktigt konfigurerat kanske betrodda användare inte kan komma åt JEA-slutpunkten och ej betrodda användare kan ha åtkomst. WinRM ACL påverkar inte mappningen av användare till JEA-roller. Mappningen styrs av fältet **RoleDefinitions** i den session konfigurations fil som används för att registrera slut punkten.

Som standard konfigureras WinRM ACL som standard för att tillåta åtkomst till alla mappade användare när en JEA-slutpunkt har flera roll funktioner. En JEA-session som kon figurer ATS med hjälp av följande kommandon ger till exempel fullständig åtkomst till `CONTOSO\JEA_Lev1` och `CONTOSO\JEA_Lev2` .

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Du kan granska användar behörigheter med cmdleten [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) .

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Om du vill ändra vilka användare som har åtkomst kör du antingen `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` för en interaktiv prompt eller `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` uppdaterar behörigheterna. Användare behöver minst *Invoke* -rättigheter för att få åtkomst till Jea-slutpunkten.

Det är möjligt att skapa en JEA-slutpunkt som inte mappar en definierad roll till alla användare som har åtkomst. Dessa användare kan starta en JEA-session, men har bara åtkomst till standard-cmdletarna. Du kan granska användar behörigheter i en JEA-slutpunkt genom att köra `Get-PSSessionCapability` . Mer information finns i [granskning och rapportering på Jea](audit-and-report.md).

## <a name="least-privilege-roles"></a>Roller för minsta behörighet

När du skapar JEA-roller är det viktigt att komma ihåg att de virtuella och grupphanterade tjänst konton som körs i bakgrunden kan ha obegränsad åtkomst till den lokala datorn. JEA-rollens funktioner begränsar de kommandon och program som kan köras i den privilegierade kontexten.
Felaktigt utformade roller kan tillåta farliga kommandon som kan ge en användare möjlighet att ta del av JEA-gränser eller få åtkomst till känslig information.

Anta till exempel följande roll kapacitets post:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Med den här rollen kan användarna köra alla PowerShell-cmdletar i Substantiv- **processen** från modulen **Microsoft. PowerShell. Management** . Användare kan behöva åtkomst till cmdletar som `Get-Process` för att se vilka program som körs i systemet och `Stop-Process` för att stoppa program som inte svarar. Posten tillåter dock också `Start-Process` , som kan användas för att starta ett godtyckligt program med fullständiga administratörs behörigheter. Programmet behöver inte installeras lokalt på systemet. En ansluten användare kan starta ett program från en fil resurs som ger användaren lokal administratörs behörighet, kör skadlig kod och mer.

En säkrare version av samma roll kapacitet skulle se ut så här:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Undvik att använda jokertecken i roll funktionerna. Se till att regelbundet [Granska gällande användar behörigheter](audit-and-report.md#check-effective-rights-for-a-specific-user) för att förstå vilka kommandon som är tillgängliga för användaren.

## <a name="jea-doesnt-protect-against-admins"></a>JEA skyddar inte mot administratörer

En av grund principerna för JEA är att den tillåter icke-administratörer att utföra vissa administrativa uppgifter. JEA skyddar inte mot användare som redan har administratörs behörighet. Användare som tillhör **domän administratörer**, lokala **Administratörer**eller andra privilegierade grupper kan kringgå Jea skydd på ett annat sätt. De kan till exempel Logga in med RDP, använda fjärranslutna MMC-konsoler eller ansluta till obegränsade PowerShell-slutpunkter. Lokala administratörer på ett system kan också ändra JEA-konfigurationer för att tillåta ytterligare användare eller ändra en roll kapacitet för att utöka omfattningen av vad en användare kan göra i sin JEA-session. Det är viktigt att utvärdera dina JEA-användares utökade behörigheter för att se om det finns andra sätt att få privilegie rad åtkomst till systemet.

En vanlig metod är att använda JEA för vanlig daglig underhåll och har en just-in-Time-, Privileged Access Management-lösning som gör det möjligt för användare att tillfälligt bli lokala administratörer i nödfalls situationer. På så sätt ser du till att användarna inte är permanenta administratörer i systemet, men kan hämta dessa rättigheter om och bara när de slutför ett arbets flöde som dokumenterar deras användning av dessa behörigheter.
