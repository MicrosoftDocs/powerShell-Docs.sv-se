---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: WinRMSecurity
ms.openlocfilehash: 59717e4806857e6760de523335bbee6028da8e84
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086379"
---
# <a name="powershell-remoting-security-considerations"></a>Säkerhets överväganden för PowerShell-fjärrkommunikation

PowerShell-fjärrkommunikation är det rekommenderade sättet att hantera Windows-system. PowerShell-fjärrkommunikation är aktiverat som standard i Windows Server 2012 R2. Det här dokumentet beskriver säkerhets problem, rekommendationer och bästa praxis när du använder PowerShell-fjärrkommunikation.

## <a name="what-is-powershell-remoting"></a>Vad är PowerShell-fjärrkommunikation?

PowerShell-fjärrkommunikation använder [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), som är Microsofts implementering av protokollet [WS-Management (Web Services for Management)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) , så att användarna kan köra PowerShell-kommandon på fjärrdatorer. Du hittar mer information om hur du använder PowerShell-fjärrkommunikation vid [körning av fjärrkommandon](https://technet.microsoft.com/library/dd819505.aspx).

PowerShell-fjärrkommunikation är inte detsamma som att använda parametern **computername** för en cmdlet för att köra den på en fjärrdator, som använder RPC (Remote Procedure Call) som sitt underliggande protokoll.

## <a name="powershell-remoting-default-settings"></a>Standardinställningar för PowerShell-fjärrkommunikation

PowerShell-fjärrkommunikation (och WinRM) lyssnar på följande portar:

- HTTP: 5985
- HTTPS: 5986

Som standard tillåter PowerShell-fjärrkommunikation endast anslutningar från medlemmar i gruppen Administratörer. Sessioner startas under användarens kontext, så alla åtkomst kontroller för operativ system som tillämpas på enskilda användare och grupper fortsätter att gälla för dem när de är anslutna via PowerShell-fjärrkommunikation.

I privata nätverk godkänner standard regeln för Windows-brandväggen för PowerShell-fjärrkommunikation alla anslutningar. I offentliga nätverk tillåter Windows-Standardregeln PowerShell fjärr anslutningar endast från samma undernät. Du måste uttryckligen ändra regeln för att öppna PowerShell-fjärrkommunikationer för alla anslutningar i ett offentligt nätverk.

>**Varning:** Brand Väggs regeln för offentliga nätverk är avsedd att skydda datorn från potentiellt skadliga externa anslutnings försök. Var försiktig när du tar bort den här regeln.

## <a name="process-isolation"></a>Process isolering

PowerShell-fjärrkommunikation använder [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) för kommunikation mellan datorer.
WinRM körs som en tjänst under nätverks tjänst kontot och skapar isolerade processer som körs som användar konton som värdar för PowerShell-instanser. En instans av PowerShell som körs som en användare har ingen åtkomst till en process som kör en instans av PowerShell som en annan användare.

## <a name="event-logs-generated-by-powershell-remoting"></a>Händelse loggar som genererats av PowerShell-fjärrkommunikation

FireEye har fått en klar Sammanfattning av händelse loggarna och andra säkerhets fakta som skapats av PowerShell-fjärrsessioner, tillgängliga vid utvärdering av [PowerShell-attacker](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Krypterings-och transport protokoll

Det är bra att överväga säkerheten hos en PowerShell-fjärranslutning från två perspektiv: inledande autentisering och pågående kommunikation.

Oavsett vilket transport protokoll som används (HTTP eller HTTPS) krypterar PowerShell-fjärrkommunikation alltid all kommunikation efter den första autentiseringen med en symmetrisk AES-256-nyckel per session.

### <a name="initial-authentication"></a>Inledande autentisering

Autentiseringen bekräftar identiteten för klienten till servern – och helst-servern till klienten.

När en klient ansluter till en domän server med dess dator namn (t. ex.: Server01 eller server01.contoso.com) är standardautentiseringsprotokollet [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos garanterar både användarens identitet och Server identitet utan att skicka några sorters återanvändbara autentiseringsuppgifter.

När en klient ansluter till en domän server med dess IP-adress, eller ansluter till en arbets grupps Server, är Kerberos-autentisering inte möjlig. I så fall använder PowerShell-fjärrkommunikationer autentiseringsprotokollet [NTLM-autentisering](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). NTLM-autentiseringsprotokollet garanterar användar identiteten utan att skicka någon sorts kan delegeras-autentiseringsuppgift. För att bevisa användar identitet kräver NTLM-protokollet att både klienten och servern beräknar en sessionsnyckel från användarens lösen ord utan att behöva utväxla själva lösen ordet. Servern känner vanligt vis inte till användarens lösen ord, så den kommunicerar med domänkontrollanten, som känner till användarens lösen ord och beräknar sessionsnyckeln för servern.

NTLM-protokollet garanterar dock inte Server identiteten. Precis som med alla protokoll som använder NTLM för autentisering kan en angripare med åtkomst till en domänansluten dators dator konto anropa domänkontrollanten för att beräkna en NTLM-sessionsnyckel och därmed imitera servern.

NTLM-baserad autentisering är inaktiverat som standard, men kan tillåtas genom att antingen konfigurera SSL på mål servern eller genom att konfigurera inställningen för WinRM TrustedHosts på klienten.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Använda SSL-certifikat för att verifiera Server identitet under NTLM-baserade anslutningar

Eftersom NTLM-autentiseringsprotokollet inte kan garantera identiteten för mål servern (bara att det redan känner till ditt lösen ord) kan du konfigurera mål servrar för att använda SSL för PowerShell-fjärrkommunikation. Att tilldela ett SSL-certifikat till mål servern (om det utfärdats av en certifikat utfärdare som klienten också litar på) aktiverar NTLM-baserad autentisering som garanterar både användar identitet och Server identitet.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Ignorerar NTLM-baserade server identitets fel

Om det är omöjligt att distribuera ett SSL-certifikat till en server för NTLM-anslutningar kan du utelämna de resulterande identitets felen genom att lägga till servern i listan WinRM **TrustedHosts** . Observera att om du lägger till ett server namn i listan TrustedHosts bör du inte betraktas som någon form av en instruktion av själva Värdarnas trovärdighet, eftersom NTLM-autentiseringsprotokollet inte kan garantera att du ansluter till värden som du avser att ansluta till.
I stället bör du se till att inställningen TrustedHosts är listan över värdar för vilka du vill förhindra att det fel som genereras av inte kan verifiera serverns identitet.


### <a name="ongoing-communication"></a>Pågående kommunikation

När den inledande autentiseringen är klar krypterar [PowerShell-Fjärrprotokollet](https://msdn.microsoft.com/library/dd357801.aspx) all pågående kommunikation med en symmetrisk AES-256-nyckel per session.


## <a name="making-the-second-hop"></a>Gör det andra hoppet

Som standard använder PowerShell-fjärrkommunikation Kerberos (om det är tillgängligt) eller NTLM för autentisering. Båda protokollen autentiserar sig på fjärrdatorn utan att skicka autentiseringsuppgifter till den.
Det här är det säkraste sättet att autentisera, men eftersom fjärrdatorn inte har användarens autentiseringsuppgifter kan den inte komma åt andra datorer och tjänster för användarens räkning.
Detta kallas "andra hopp problemet".

Det finns flera sätt att undvika det här problemet. För beskrivningar av dessa metoder och för-och nack delar med varandra, se [göra det andra hoppet i PowerShell-fjärrkommunikation](PS-remoting-second-hop.md).