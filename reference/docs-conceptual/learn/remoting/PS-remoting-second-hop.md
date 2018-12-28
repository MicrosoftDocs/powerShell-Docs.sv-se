---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Gör det andra hoppet i PowerShell-fjärrkommunikation
ms.openlocfilehash: 06ca43e3e0524d89ec6f66f6553c4c75072beaf3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404979"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Gör det andra hoppet i PowerShell-fjärrkommunikation

”Andra hopp problemet” avser en situation som liknar följande:

1. Du är inloggad _cypress_.
2. Från _cypress_, du startar en fjärrsession PowerShell till att ansluta till _ServerB_.
3. Ett kommando som du kör på _ServerB_ via PowerShell-fjärrkommunikation session försöker få åtkomst till en resurs på _ServerC_.
4. Åtkomst till resursen på _ServerC_ nekas, eftersom de autentiseringsuppgifter som du använde för att skapa PowerShell-fjärrkommunikation sessionen inte skickas från _ServerB_ till _ServerC_.

Det finns flera sätt att åtgärda problemet. I det här avsnittet ska vi titta på flera av de mest populära lösningarna på problemet för andra hopp.

## <a name="credssp"></a>CredSSP

Du kan använda den [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) för autentisering. CredSSP cachelagrar autentiseringsuppgifter på fjärrservern (_ServerB_), så använder det öppnar du upp till stöldattacker av autentiseringsuppgifter. Om fjärrdatorn komprometteras har angriparen tillgång till användarens autentiseringsuppgifter. CredSSP är inaktiverad som standard på både klienten och servern datorer. Endast i de mest tillförlitliga miljöerna bör du aktivera CredSSP. Till exempel en domänadministratör ansluter till en domänkontrollant, eftersom domänkontrollanten är betrodda.

Mer information om säkerhetsfrågor när du använder CredSSP för PowerShell-fjärrkommunikation finns [oavsiktlig Sabotage: Håll CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Mer information om stöldattacker av autentiseringsuppgifter finns i [Mitigating Pass-the-Hash (PtH)-attacker och annan stöld](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Ett exempel på hur du aktiverar och använder CredSSP för PowerShell-fjärrkommunikation finns i [med CredSSP för att lösa problemet andra hopp](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Fördelar

- Den fungerar för alla servrar med Windows Server 2008 eller senare.

### <a name="cons"></a>Nackdelar

- Har säkerhetsrisker.
- Kräver konfiguration av både klient och server-roller.

## <a name="kerberos-delegation-unconstrained"></a>Kerberos-delegering (obegränsad)

Du kan också använda obegränsad Kerberos-delegering för att göra det andra hoppet. Den här metoden ger dock ingen kontroll över där delegerade autentiseringsuppgifter används.

>**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättning kan inte delegeras. Mer information finns i [Security fokus: Analys ”kontot är känsligt och kan inte delegeras” för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Fördelar

- Kräver ingen särskild kodning.

### <a name="cons"></a>Nackdelar

- Stöder inte det andra hoppet för WinRM.
- Innehåller ingen kontroll över där autentiseringsuppgifter används, skapar en säkerhetsrisk.

## <a name="kerberos-constrained-delegation"></a>Kerberos-begränsad delegering

Du kan använda äldre begränsad delegering (inte Resursbaserad) för att göra det andra hoppet.

>**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättning kan inte delegeras. Mer information finns i [Security fokus: Analys ”kontot är känsligt och kan inte delegeras” för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Fördelar

- Kräver ingen särskild kodning

### <a name="cons"></a>Nackdelar

- Stöder inte det andra hoppet för WinRM.
- Måste konfigureras på Active Directory-objekt på fjärrservern (_ServerB_).
- Begränsad till en domän. Det går inte att mellan domäner eller skogar.
- Kräver behörighet att uppdatera objekt och tjänsthuvudnamn (SPN).

## <a name="resource-based-kerberos-constrained-delegation"></a>Resursbaserade Kerberos-begränsad delegering

Använder resursbaserade Kerberos-begränsad delegering (introducerades i Windows Server 2012) måste du konfigurera delegering av autentiseringsuppgifter på server-objekt där resurserna finns.
I det andra hopp scenariot som beskrivs ovan, konfigurerar du _ServerC_ ange från där du ska ta emot delegerade autentiseringsuppgifter.

>**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättning kan inte delegeras. Mer information finns i [Security fokus: Analys ”kontot är känsligt och kan inte delegeras” för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Fördelar

- Autentiseringsuppgifterna har inte sparats.
- Relativt enkelt att konfigurera med hjälp av PowerShell-cmdlets – ingen särskild kodning krävs.
- Ingen åtkomst till särskilda domänen krävs.
- Arbeta över domäner och skogar.
- PowerShell-kod.

### <a name="cons"></a>Nackdelar

- Kräver Windows Server 2012 eller senare.
- Stöder inte det andra hoppet för WinRM.
- Kräver behörighet att uppdatera objekt och tjänsthuvudnamn (SPN).

### <a name="example"></a>Exempel

Låt oss titta på ett exempel som konfigurerar resursen begränsad delegering som baseras på PowerShell _ServerC_ att tillåta delegerade autentiseringsuppgifter från en _ServerB_.
Det här exemplet förutsätts att alla servrar som kör Windows Server 2012 eller senare, och att det finns minst en domänkontrollant för Windows Server 2012 varje domän till där någon av servrarna tillhör.

Innan du kan konfigurera begränsad delegering, måste du lägga till den `RSAT-AD-PowerShell` för att installera Active Directory PowerShell-modulen och importera sedan modulen till sessionen:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Flera tillgängliga cmdlet: ar har nu en **PrincipalsAllowedToDelegateToAccount** parameter:

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

Den **PrincipalsAllowedToDelegateToAccount** parametern anger Active Directory-objektattribut **msDS-AllowedToActOnBehalfOfOtherIdentity**, som innehåller en åtkomstkontrollista (ACL) som Anger vilka konton som har behörighet att delegera autentiseringsuppgifter till det associerade kontot (i vårt exempel, kommer den att datorkontot för _Server_).

Nu ska vi konfigurera de variabler som vi använder för att representera servrar:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (och därför PowerShell-fjärrkommunikation) körs som datorkontot som standard. Du kan se detta genom att titta på den **Referensdimensionerna** egenskapen för den `winrm` service:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

För _ServerC_ att tillåta delegering från en PowerShell-fjärrkommunikation-session på _ServerB_, så vi beviljas åtkomst genom att ange den **PrincipalsAllowedToDelegateToAccount** parametern på _ServerC_ till datorobjekt _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) cacheminnen nekas åtkomstförsök (negativ cache) i 15 minuter. Om _ServerB_ har tidigare försökte komma åt _ServerC_, måste du rensa cacheminnet på _ServerB_ genom att aktivera följande kommando:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Du kan också starta om datorn eller vänta minst 15 minuter för att rensa cacheminnet.

Efter att rensa cacheminnet, kan du köra kod från _cypress_ via _ServerB_ till _ServerC_:

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

I det här exemplet på `$using` variabeln används för att göra den `$ServerC` variabeln som är synliga för _ServerB_. Mer information om den `$using` variabel, se [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Gör att flera servrar att delegera autentiseringsuppgifter för att _ServerC_, ange värdet för den **PrincipalsAllowedToDelegateToAccount** parametern på _ServerC_ till en matris:

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Om du vill göra det andra hoppet i flera domäner lägger du till fullständigt kvalificerade domännamnet (FQDN) på domänkontrollanten för domänen som _ServerB_ tillhör:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Om du vill ta bort möjligheten att delegera ServerC autentiseringsuppgifter, ange värdet för den **PrincipalsAllowedToDelegateToAccount** parametern på _ServerC_ till `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Information om resursbaserade Kerberos-begränsad delegering

- [Vad är nytt i Kerberos-autentisering](https://technet.microsoft.com/library/hh831747.aspx)
- [Hur Windows Server 2012 övergångar enkelt Kerberos-begränsad delegering, del 1](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Hur Windows Server 2012 övergångar enkelt Kerberos-begränsad delegering, del 2](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Förstå Kerberos-begränsad delegering för Azure Active Directory Application Proxy-distributioner med integrerad Windows-autentisering](https://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory-schemat attribut M2.210 attributet msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]: Tillägg för Kerberos-protokollet: Tjänst för användare och begränsad delegering protokollet 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)
- [Resursen baserat Kerberos-begränsad delegering](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Fjärradministration utan begränsad delegering med hjälp av PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration med RunAs

Du kan skapa en sessionskonfiguration på _ServerB_ och Ställ in dess **RunAsCredential** parametern.

Information om hur du använder PSSessionConfiguration och RunAs lösa andra hopp problemet finns i [en annan lösning till Multi-hop PowerShell-fjärrkommunikation](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Fördelar

- Fungerar med servrar med WMF 3.0 eller senare.

### <a name="cons"></a>Nackdelar

- Kräver konfiguration av **PSSessionConfiguration** och **RunAs** på varje mellanliggande server (_ServerB_).
- Kräver lösenord Underhåll när du använder en domän **RunAs** konto

## <a name="just-enough-administration-jea"></a>JEA (Just Enough Administration)

JEA kan du begränsa vilka kommandon som en administratör kan köras under en PowerShell-session. Det kan användas för att lösa problemet med andra hopp.

Läs om hur JEA [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).

### <a name="pros"></a>Fördelar

- Inget lösenord Underhåll när du använder ett virtuellt konto.

### <a name="cons"></a>Nackdelar

- Kräver WMF 5.0 eller senare.
- Kräver konfiguration på varje mellanliggande server (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Skicka autentiseringsuppgifter inuti en Invoke-Command-skriptblock

Du kan skicka autentiseringsuppgifter i den **ScriptBlock** parameter för ett anrop till den [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.

### <a name="pros"></a>Fördelar

- Kräver inte särskild serverkonfiguration.
- Fungerar på en server som kör WMF 2.0 eller senare.

### <a name="cons"></a>Nackdelar

- Kräver en olämpliga kod-teknik.
- Om kör WMF 2.0, kräver olika syntax för att skicka argument till en fjärrsession.

### <a name="example"></a>Exempel

I följande exempel visas hur du skickar autentiseringsuppgifter i en **Invoke-Command** skriptblock:

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>Se även

[Säkerhetsöverväganden för PowerShell-fjärrkommunikation](WinRMSecurity.md)