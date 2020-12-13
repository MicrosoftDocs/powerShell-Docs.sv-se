---
ms.date: 06/11/2020
keywords: powershell,cmdlet
title: Säkerhets aspekter för PowerShell-fjärrkommunikation med WinRM
description: Det här dokumentet beskriver säkerhets problem, rekommendationer och bästa praxis när du använder PowerShell-fjärrkommunikation.
ms.openlocfilehash: 48167bd297905883b3d75caf9a07d06e6a9fc467
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501481"
---
# <a name="security-considerations-for-powershell-remoting-using-winrm"></a>Säkerhets aspekter för PowerShell-fjärrkommunikation med WinRM

PowerShell-fjärrkommunikation är det rekommenderade sättet att hantera Windows-system. PowerShell-fjärrkommunikation är aktiverat som standard i Windows Server 2012 R2. Det här dokumentet beskriver säkerhets problem, rekommendationer och bästa praxis när du använder PowerShell-fjärrkommunikation.

## <a name="what-is-powershell-remoting"></a>Vad är PowerShell-fjärrkommunikation?

PowerShell-fjärrkommunikation använder [Windows Remote Management (WinRM)](/windows/win32/winrm/portal), som är Microsofts implementering av protokollet [WS-Management (Web Services for Management)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) , så att användarna kan köra PowerShell-kommandon på fjärrdatorer. Du hittar mer information om hur du använder PowerShell-fjärrkommunikation vid [körning av fjärrkommandon](running-remote-commands.md).

PowerShell-fjärrkommunikation är inte detsamma som att använda parametern **computername** för en cmdlet för att köra den på en fjärrdator, som använder RPC (Remote Procedure Call) som sitt underliggande protokoll.

## <a name="powershell-remoting-default-settings"></a>Standardinställningar för PowerShell-fjärrkommunikation

PowerShell-fjärrkommunikation (och WinRM) lyssnar på följande portar:

- HTTP: 5985
- HTTPS: 5986

Som standard tillåter PowerShell-fjärrkommunikation endast anslutningar från medlemmar i gruppen Administratörer.
Sessioner startas under användarens kontext, så alla åtkomst kontroller för operativ system som tillämpas på enskilda användare och grupper fortsätter att gälla för dem när de är anslutna via PowerShell-fjärrkommunikation.

I privata nätverk godkänner standard regeln för Windows-brandväggen för PowerShell-fjärrkommunikation alla anslutningar. I offentliga nätverk tillåter Windows-Standardregeln PowerShell fjärr anslutningar endast från samma undernät. Du måste uttryckligen ändra regeln för att öppna PowerShell-fjärrkommunikationer för alla anslutningar i ett offentligt nätverk.

> [!Warning]
> Brand Väggs regeln för offentliga nätverk är avsedd att skydda datorn från potentiellt skadliga externa anslutnings försök. Var försiktig när du tar bort den här regeln.

## <a name="process-isolation"></a>Process isolering

PowerShell-fjärrkommunikation använder WinRM för kommunikation mellan datorer. WinRM körs som en tjänst under nätverks tjänst kontot och skapar isolerade processer som körs som användar konton som värdar för PowerShell-instanser. En instans av PowerShell som körs som en användare har ingen åtkomst till en process som kör en instans av PowerShell som en annan användare.

## <a name="event-logs-generated-by-powershell-remoting"></a>Händelse loggar som genererats av PowerShell-fjärrkommunikation

FireEye har fått en klar Sammanfattning av händelse loggarna och andra säkerhets fakta som skapats av PowerShell-fjärrsessioner, tillgängliga vid utvärdering av [PowerShell-attacker](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Krypterings-och transport protokoll

Det är bra att överväga säkerheten hos en PowerShell-fjärranslutning från två perspektiv: inledande autentisering och pågående kommunikation.

Oavsett vilket transport protokoll som används (HTTP eller HTTPS) krypterar WinRM alltid all PowerShell Remoting-kommunikation efter den första autentiseringen.

### <a name="initial-authentication"></a>Inledande autentisering

Autentiseringen bekräftar identiteten för klienten till servern – och helst-servern till klienten.

När en klient ansluter till en domän server med hjälp av dator namnet är standardautentiseringsprotokollet [Kerberos](/windows/win32/secauthn/microsoft-kerberos). Kerberos garanterar både användarens identitet och Server identitet utan att skicka några sorters återanvändbara autentiseringsuppgifter.

När en klient ansluter till en domän server med dess IP-adress, eller ansluter till en arbets grupps Server, är Kerberos-autentisering inte möjlig. I så fall använder PowerShell-fjärrkommunikationer autentiseringsprotokollet [NTLM-autentisering](/windows/win32/secauthn/microsoft-ntlm). NTLM-autentiseringsprotokollet garanterar användar identiteten utan att skicka någon sorts kan delegeras-autentiseringsuppgift. För att bevisa användar identitet kräver NTLM-protokollet att både klienten och servern beräknar en sessionsnyckel från användarens lösen ord utan att behöva utväxla själva lösen ordet. Servern känner vanligt vis inte till användarens lösen ord, så den kommunicerar med domänkontrollanten, som känner till användarens lösen ord och beräknar sessionsnyckeln för servern.

NTLM-protokollet garanterar dock inte Server identiteten. Precis som med alla protokoll som använder NTLM för autentisering kan en angripare med åtkomst till en domänansluten dators dator konto anropa domänkontrollanten för att beräkna en NTLM-sessionsnyckel och därmed imitera servern.

NTLM-baserad autentisering är inaktiverat som standard, men kan tillåtas genom att antingen konfigurera SSL på mål servern eller genom att konfigurera inställningen för WinRM TrustedHosts på klienten.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Använda SSL-certifikat för att verifiera Server identitet under NTLM-baserade anslutningar

Eftersom NTLM-autentiseringsprotokollet inte kan garantera identiteten för mål servern (bara att det redan känner till ditt lösen ord) kan du konfigurera mål servrar för att använda SSL för PowerShell-fjärrkommunikation.
Att tilldela ett SSL-certifikat till mål servern (om det utfärdats av en certifikat utfärdare som klienten också litar på) aktiverar NTLM-baserad autentisering som garanterar både användar identitet och Server identitet.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Ignorerar NTLM-baserade server identitets fel

Om det är omöjligt att distribuera ett SSL-certifikat till en server för NTLM-anslutningar kan du utelämna de resulterande identitets felen genom att lägga till servern i listan WinRM **TrustedHosts** . Observera att om du lägger till ett server namn i listan **TrustedHosts** bör du inte anses som någon form av en instruktion av själva Värdarnas trovärdighet, eftersom NTLM-autentiseringsprotokollet inte kan garantera att du ansluter till den värd som du vill ansluta till. I stället bör du se till att inställningen TrustedHosts är listan över värdar för vilka du vill förhindra att det fel som genereras av inte kan verifiera serverns identitet.

### <a name="ongoing-communication"></a>Pågående kommunikation

När den inledande autentiseringen är klar krypterar WinRM den pågående kommunikationen. När du ansluter via HTTPS används TLS-protokollet för att förhandla den kryptering som används för att transportera data.
När du ansluter via HTTP avgörs kryptering på meddelande nivå av det första autentiseringsprotokoll som används.

- Grundläggande autentisering ger ingen kryptering.
- NTLM-autentisering använder en RC4-chiffer med en 128-bitars nyckel.
- Kryptering av Kerberos-autentisering bestäms av `etype` i TGS-biljetten. Detta är AES-256 på moderna system.
- CredSSP-kryptering använder TLS-chiffrering som förhandlats i hand skakningen.

## <a name="making-the-second-hop"></a>Gör det andra hoppet

Som standard använder PowerShell-fjärrkommunikation Kerberos (om det är tillgängligt) eller NTLM för autentisering. Båda protokollen autentiserar sig på fjärrdatorn utan att skicka autentiseringsuppgifter till den. Det här är det säkraste sättet att autentisera, men eftersom fjärrdatorn inte har användarens autentiseringsuppgifter kan den inte komma åt andra datorer och tjänster för användarens räkning. Detta kallas "andra hopp problemet".

Det finns flera sätt att undvika det här problemet. För beskrivningar av dessa metoder och för-och nack delar med varandra, se [göra det andra hoppet i PowerShell-fjärrkommunikation](PS-remoting-second-hop.md).

## <a name="references"></a>Referenser

- [Windows Remote Management (WinRM)](/windows/win32/winrm/portal)
- [WS-Management (Web Services for Management)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf)
- [2.2.9.1 krypterade meddelande typer](/openspecs/windows_protocols/ms-wsmv/58421aa4-861a-4410-831a-c999f094cdb7)
- [Kerberos](/windows/win32/secauthn/microsoft-kerberos)
- [NTLM-autentiseringsprotokoll](/windows/win32/secauthn/microsoft-ntlm)
- [Undersöka PowerShell-attacker](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf)
