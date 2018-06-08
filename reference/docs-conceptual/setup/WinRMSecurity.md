---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: WinRMSecurity
ms.openlocfilehash: 43e77067e301cdf1b792cb0d24b72ee0abb3349a
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482955"
---
# <a name="powershell-remoting-security-considerations"></a>PowerShell fjärrkommunikation säkerhetsaspekter

PowerShell-fjärrkommunikation är det rekommenderade sättet att hantera Windows-System. PowerShell-fjärrkommunikation är aktiverad som standard i Windows Server 2012 R2. Det här dokumentet beskriver säkerhetsbeaktanden, rekommendationer och metodtips när du använder PowerShell-fjärrkommunikation.

## <a name="what-is-powershell-remoting"></a>Vad är PowerShell-fjärrkommunikation?

PowerShell-fjärrkommunikation använder [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), vilket är Microsofts implementering av den [Web Services for Management (WS-Management)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) protokoll, så att användarna kan köra PowerShell kommandon på fjärrdatorer. Du hittar mer information om hur du använder PowerShell-fjärrkommunikation på [köra fjärrkommandon](https://technet.microsoft.com/library/dd819505.aspx).

PowerShell-fjärrkommunikation är inte detsamma som att använda den **ComputerName** parametern för en cmdlet ska köras på en fjärrdator som använder Remote Procedure Call (RPC) som dess underliggande protokoll.

## <a name="powershell-remoting-default-settings"></a>Standardinställningarna för PowerShell-fjärrkommunikation

PowerShell-fjärrkommunikation (och WinRM) lyssna på följande portar:

- HTTP: 5985
- HTTPS: 5986

Som standard tillåter PowerShell-fjärrkommunikation bara anslutningar från medlemmarna i gruppen Administratörer. Sessioner startas under användarkontext, så att alla åtkomstkontroller för operativsystemet som används för enskilda användare och grupper fortsätta att gälla för dem när du är ansluten via PowerShell-fjärrkommunikation.

Standardregel för Windows-brandväggen för PowerShell-fjärrkommunikation godkänner alla anslutningar i privata nätverk. I offentliga nätverk kan Windows-brandväggen Standardregeln PowerShell-fjärrkommunikation bara anslutningar från inom samma undernät. Du måste uttryckligen ändra regeln för att öppna PowerShell-fjärrkommunikation för alla anslutningar i offentliga nätverk.

>**Varning:** brandväggsregeln för offentliga nätverk är avsedd att skydda datorn mot potentiellt skadliga externa anslutningsförsök. Var försiktig när du tar bort den här regeln.

## <a name="process-isolation"></a>Processisolering av

PowerShell-fjärrkommunikation använder [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) för kommunikation mellan datorer.
WinRM körs som en tjänst under kontot Nätverkstjänst, och skapas isolerade processer som körs som användarkonton till värden PowerShell instanser. En instans av PowerShell som körs som en användare inte har åtkomst till en process som kör en instans av PowerShell som en annan användare.

## <a name="event-logs-generated-by-powershell-remoting"></a>Händelseloggar som genererats av PowerShell-fjärrkommunikation

FireEye har angett en bra översikt över händelseloggarna och andra säkerhetsbevis som genererats av PowerShell-fjärrkommunikation sessioner, finns på [undersöker PowerShell attacker](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Kryptering och transport protokoll

Är det bra att tänka på säkerheten för en PowerShell-fjärrkommunikation anslutning ur två perspektiv: första autentiseringen och en pågående kommunikation.

Oavsett transportprotokollet används (HTTP eller HTTPS) krypterar PowerShell-fjärrkommunikation alltid all kommunikation efter första autentiseringen med sessions-AES 256 symmetrisk nyckel.

### <a name="initial-authentication"></a>Första autentiseringen

Autentisering bekräftar identiteten för klient till server- och helst - servern till klienten.

När en klient ansluter till en domänserver namn (d.v.s.: server01, eller server01.contoso.com), är standardautentiseringsprotokollet [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos garanterar både användar-ID och serveridentitet utan att skicka någon form av återanvändbara autentiseringsuppgifter.

När en klient ansluter till en domänserver med dess IP-adress eller ansluter till en arbetsgruppsserver, är Kerberos-autentisering inte möjligt. I så fall PowerShell-fjärrkommunikation är beroende av [NTLM-autentiseringsprotokollet](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). NTLM-autentiseringsprotokollet garanterar användaridentiteten utan att skicka alla slags kan delegeras autentiseringsuppgifter. För att bevisa användaridentitet kräver NTLM-protokollet att både klient och server compute en sessionsnyckel från användarens lösenord utan att någonsin utbyta själva lösenordet. Servern vanligtvis vet inte lösenordet, så att den kommunicerar med domänkontrollanten som känner till användarens lösenord och beräknar sessionsnyckeln för servern.

NTLM-protokollet garanterar inte, men serveridentitet. Precis som med alla protokoll som använder NTLM för autentisering, kunde en angripare med tillgång till en domänansluten dator datorkontot anropa domänkontrollanten för att beräkna NTLM-sessionsnyckel och därmed personifiera servern.

NTLM-autentisering är inaktiverat som standard, men kan tillåtas genom antingen konfigurera SSL på målservern, eller genom att konfigurera inställningen WinRM TrustedHosts på klienten.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Använder SSL-certifikat för att verifiera serveridentitet under NTLM-baserade anslutningar

Eftersom NTLM-autentiseringsprotokollet går inte att kontrollera identiteten på målservern (endast som redan vet lösenordet), kan du konfigurera målservrar för att använda SSL för PowerShell-fjärrkommunikation. Tilldela målservern ett SSL-certifikat (om det utfärdats av en certifikatsutfärdare som klienten också) gör det möjligt för NTLM-autentisering som garanterar både användar-ID och serveridentitet.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Ignorerar NTLM-baserad server identitet fel

Om det är omöjligt att distribuera ett SSL-certifikat till en server för NTLM-anslutningar, kan du förhindra de identitet fel genom att lägga till servern WinRM **TrustedHosts** lista. Observera att lägga till ett servernamn i listan TrustedHosts inte ska betraktas som någon form av instruktionen för trovärdighet värddatorer själva – som NTLM-autentiseringsprotokollet inte kan garantera att du i själva verket ansluter till värden är Avsikten är att ansluta till.
I stället bör du inställningen TrustedHosts att listan över värdar som du vill ignorera felet genereras av att det inte går att verifiera serverns identitet.


### <a name="ongoing-communication"></a>En pågående kommunikation

När den första autentiseringen är klar, den [PowerShell fjärrkommunikation protokollet](https://msdn.microsoft.com/library/dd357801.aspx) krypterar alla pågående kommunikation med en tillfälliga AES 256 symmetrisk nyckel.


## <a name="making-the-second-hop"></a>Gör ett andra hopp

Som standard använder PowerShell-fjärrkommunikation Kerberos (om tillgängligt) eller NTLM för autentisering. Båda dessa protokoll autentisera fjärrdatorn utan att skicka autentiseringsuppgifter till den.
Detta är det säkraste sättet att autentisera, men eftersom fjärrdatorn inte har användarens autentiseringsuppgifter, den kan inte komma åt andra datorer och tjänster för användarens räkning.
Detta kallas ”andra hopp problemet”.

Det finns flera sätt att undvika problemet. Beskrivningar av dessa metoder och tekniker och nackdelar med varje finns [att göra ett andra hopp i PowerShell-fjärrkommunikation](PS-remoting-second-hop.md).