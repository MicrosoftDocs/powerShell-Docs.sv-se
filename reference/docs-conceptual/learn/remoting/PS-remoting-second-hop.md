---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Göra det andra hoppet i PowerShell-fjärrkommunikation
ms.openlocfilehash: f4cfde39de8494050c31cfc3181271b968819695
ms.sourcegitcommit: a35450f420dc10a02379f6e6f08a28ad11fe5a6d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71692154"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Göra det andra hoppet i PowerShell-fjärrkommunikation

"Andra hopp problemet" syftar på en situation som följande:

1. Du är inloggad på _reserverad_.
2. Frånsäkerhetsstartar du en fjärran sluten PowerShell-session för att ansluta till _ServerB_.
3. Ett kommando som du kör på _ServerB_ via din PowerShell-fjärrsession försöker få åtkomst till en resurs på _ServerC_.
4. Åtkomst till resursen på _ServerC_ nekas eftersom de autentiseringsuppgifter som du använde för att skapa PowerShell-fjärrsessionen inte skickas från _ServerB_ till _ServerC_.

Det finns flera sätt att åtgärda problemet. I det här avsnittet ska vi titta på flera av de mest populära lösningarna för det andra hopp problemet.

## <a name="credssp"></a>CredSSP

Du kan använda [CredSSP (Credential Security Support Provider)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) för autentisering. CredSSP cachelagrar autentiseringsuppgifter på fjärrservern (_ServerB_) så att du kan använda den för att öppna autentiseringsuppgifter för stöld av autentiseringsuppgifter. Om fjärrdatorn komprometteras har angriparen till gång till användarens autentiseringsuppgifter. CredSSP är inaktiverat som standard på både klient-och serverdatorer. Du bör endast aktivera CredSSP i de mest betrodda miljöerna. Till exempel en domän administratör som ansluter till en domänkontrollant eftersom domänkontrollanten är hög betrodd.

Mer information om säkerhets problem när du använder CredSSP för PowerShell-fjärrkommunikation finns i [Accidental sabotage: Förvarning för CredSSP @ no__t-0.

Mer information om stöld av autentiseringsuppgifter finns i [minimera pass-The-hash-attacker (PTH) och annan stöld av autentiseringsuppgifter](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Ett exempel på hur du aktiverar och använder CredSSP för PowerShell-fjärrkommunikation finns i [använda CredSSP för att lösa det andra hopp problemet](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Experter

- Det fungerar för alla servrar med Windows Server 2008 eller senare.

### <a name="cons"></a>Nackdelar

- Säkerhets problem.
- Kräver konfiguration av både klient-och Server roller.

## <a name="kerberos-delegation-unconstrained"></a>Kerberos-delegering (obegränsad)

Du kan också använda Kerberos-obegränsad delegering för att göra det andra hoppet. Den här metoden ger dock ingen kontroll över var delegerade autentiseringsuppgifter används.

>**Obs:** Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras. Mer information finns i [Security Focus: Analys av kontot är känsligt och kan inte delegeras för privilegierade konton @ no__t-0 och [Kerberos-autentiseringsinställningar och-inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Experter

- Kräver ingen särskild kodning.

### <a name="cons"></a>Nackdelar

- Har inte stöd för det andra hoppet för WinRM.
- Ger ingen kontroll över var autentiseringsuppgifter används, vilket skapar en säkerhets risk.

## <a name="kerberos-constrained-delegation"></a>Kerberos-begränsad delegering

Du kan använda en äldre begränsad delegering (inte resurs baserad) för att göra det andra hoppet. Konfigurera Kerberos-begränsad delegering med alternativet "Använd valfria autentiseringsprotokoll" för att tillåta protokoll över gång.

> [!NOTE]
> Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras. Mer information finns i [Security Focus: Analys av kontot är känsligt och kan inte delegeras för privilegierade konton @ no__t-0 och [Kerberos-autentiseringsinställningar och-inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Experter

- Kräver ingen särskild kodning

### <a name="cons"></a>Nackdelar

- Har inte stöd för det andra hoppet för WinRM.
- Måste konfigureras på Active Directory-objektet på fjärrservern (_ServerB_).
- Begränsad till en domän. Det går inte att korsa domäner eller skogar.
- Kräver behörighet att uppdatera objekt och SPN-namn (Service Principal Names).

## <a name="resource-based-kerberos-constrained-delegation"></a>Resurs-baserad Kerberos-begränsad delegering

Med hjälp av resurs baserad Kerberos-begränsad delegering (som introducerades i Windows Server 2012) konfigurerar du delegering av autentiseringsuppgifter på det Server objekt där resurserna finns.
I det andra hopp scenariot som beskrivs ovan konfigurerar du _ServerC_ för att ange från vilken den ska acceptera delegerade autentiseringsuppgifter.

>**Obs:** Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras. Mer information finns i [Security Focus: Analys av kontot är känsligt och kan inte delegeras för privilegierade konton @ no__t-0 och [Kerberos-autentiseringsinställningar och-inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Experter

- Autentiseringsuppgifterna lagras inte.
- Relativt enkelt att konfigurera med hjälp av PowerShell-cmdletar – ingen särskild kod krävs.
- Ingen särskild domän åtkomst krävs.
- Fungerar över domäner och skogar.
- PowerShell-kod.

### <a name="cons"></a>Nackdelar

- Kräver Windows Server 2012 eller senare.
- Har inte stöd för det andra hoppet för WinRM.
- Kräver behörighet att uppdatera objekt och SPN-namn (Service Principal Names).

### <a name="example"></a>Exempel

Nu ska vi titta på ett PowerShell-exempel som konfigurerar resurs baserad begränsad delegering på _ServerC_ för att tillåta delegerade autentiseringsuppgifter från en _ServerB_.
I det här exemplet förutsätts att alla servrar kör Windows Server 2012 eller senare och att det finns minst en Windows Server 2012-domänkontrollant varje domän som någon av servrarna tillhör.

Innan du kan konfigurera begränsad delegering måste du lägga till funktionen `RSAT-AD-PowerShell` för att installera Active Directory PowerShell-modulen och sedan importera modulen till sessionen:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Flera tillgängliga cmdlets har nu en **PrincipalsAllowedToDelegateToAccount** -parameter:

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

Parametern **PrincipalsAllowedToDelegateToAccount** anger attributet **msDS-AllowedToActOnBehalfOfOtherIdentity**för Active Directory Object som innehåller en åtkomst kontrol lista (ACL) som anger vilka konton som har behörighet att delegera autentiseringsuppgifter till det associerade kontot (i vårt exempel är det dator kontot för _servern_).

Nu ska vi ställa in variablerna som ska användas för att representera servrarna:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (och därmed PowerShell-fjärrkommunikation) körs som dator kontot som standard. Du kan se detta genom att titta på egenskapen **StartName** för tjänsten `winrm`:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

För att _ServerC_ ska kunna tillåta delegering från en PowerShell-fjärrsession på _ServerB_kommer vi att bevilja åtkomst genom att ställa in **PrincipalsAllowedToDelegateToAccount** -parametern på _ServerC_ till datorobjektet för _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [-Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) nekade åtkomst försök (negativt cacheminne) i 15 minuter. Om _ServerB_ tidigare har försökt få åtkomst till _ServerC_måste du rensa cacheminnet på _ServerB_ genom att anropa följande kommando:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Du kan också starta om datorn eller vänta minst 15 minuter för att rensa cacheminnet.

När du har rensat cacheminnet kan du köra kod från _reserverad_ till _ServerB_ till _ServerC_:

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

I det här exemplet används variabeln `$using` för att göra `$ServerC`-variabeln synlig för _ServerB_. Mer information om variabeln `$using` finns i [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Om du vill tillåta att flera servrar delegerar autentiseringsuppgifter till _ServerC_anger du värdet för parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ till en matris:

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

Om du vill göra det andra hoppet över domäner lägger du till fullständigt kvalificerat domän namn (FQDN) för domän kontrol Lanterna för den domän som _ServerB_ tillhör:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Om du vill ta bort möjligheten att delegera autentiseringsuppgifter till ServerC anger du värdet för parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ till `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Information om Resource-baserad Kerberos-begränsad delegering

- [Vad är nytt i Kerberos-autentisering](https://technet.microsoft.com/library/hh831747.aspx)
- [Hur Windows Server 2012 underlättar smärta hos Kerberos-begränsad delegering, del 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Hur Windows Server 2012 underlättar smärta hos Kerberos-begränsad delegering, del 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Förstå Kerberos-begränsad delegering för Azure Active Directory-programproxy distributioner med integrerad Windows-autentisering](https://aka.ms/kcdpaper)
- [ [MS-ADA2]: Active Directory schemaattributet M 2.210 attributet msDS-AllowedToActOnBehalfOfOtherIdentity @ no__t-0
- [ [MS-SFU]: Kerberos-protokoll tillägg: Tjänst för användare och begränsad Delegerings protokoll 1.3.2 S4U2proxy @ no__t-0
- [Resurs baserad Kerberos-begränsad delegering](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Fjärr administration utan begränsad delegering med PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration med RunAs

Du kan skapa en sessionshantering på _ServerB_ och ange dess **RunAsCredential** -parameter.

Information om hur du använder PSSessionConfiguration och RunAs för att lösa det andra hopp problemet finns i [en annan lösning på multi-hop PowerShell-fjärrkommunikation](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Experter

- Fungerar med valfri server med WMF 3,0 eller senare.

### <a name="cons"></a>Nackdelar

- Kräver konfiguration av **PSSessionConfiguration** och **runas** på varje mellanliggande server (_ServerB_).
- Kräver lösen ords underhåll när du använder ett domän konto för **runas**

## <a name="just-enough-administration-jea"></a>JEA (Just Enough Administration)

Med JEA kan du begränsa vilka kommandon en administratör kan köra under en PowerShell-session. Det kan användas för att lösa det andra hopp problemet.

Mer information om JEA finns i [tillräckligt med administration](https://docs.microsoft.com/powershell/jea/overview).

### <a name="pros"></a>Experter

- Inget lösen ords underhåll när du använder ett virtuellt konto.

### <a name="cons"></a>Nackdelar

- Kräver WMF 5,0 eller senare.
- Kräver konfiguration på varje mellanliggande server (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Skicka autentiseringsuppgifter i ett Invoke-kommando skript block

Du kan skicka autentiseringsuppgifter i **script block** -parametern för ett anrop till cmdleten [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) .

### <a name="pros"></a>Experter

- Kräver ingen särskild Server konfiguration.
- Fungerar på alla servrar som kör WMF 2,0 eller senare.

### <a name="cons"></a>Nackdelar

- Kräver en olämplig kod teknik.
- Om du kör WMF 2,0 krävs en annan syntax för att skicka argument till en fjärrsession.

### <a name="example"></a>Exempel

I följande exempel visas hur du skickar autentiseringsuppgifter i ett **Invoke-kommando** skript block:

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
