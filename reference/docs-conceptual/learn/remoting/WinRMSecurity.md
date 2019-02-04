---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: WinRMSecurity
ms.openlocfilehash: 59717e4806857e6760de523335bbee6028da8e84
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688310"
---
# <a name="powershell-remoting-security-considerations"></a>Säkerhetsöverväganden för PowerShell-fjärrkommunikation

PowerShell-fjärrkommunikation är det rekommenderade sättet att hantera Windows-System. PowerShell-fjärrkommunikation är aktiverat som standard i Windows Server 2012 R2. Det här dokumentet Beskriver säkerhetsproblem, rekommendationer och bästa praxis när du använder PowerShell-fjärrkommunikation.

## <a name="what-is-powershell-remoting"></a>Vad är PowerShell-fjärrkommunikation?

PowerShell-fjärrkommunikation använder [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), vilket är Microsofts implementering av den [Web Services for Management (WS-Management)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) -protokollet, så att användarna kan köra PowerShell kommandon på fjärrdatorer. Du hittar mer information om hur du använder PowerShell-fjärrkommunikation på [köra fjärrkommandon](https://technet.microsoft.com/library/dd819505.aspx).

PowerShell-fjärrkommunikation är inte detsamma som att använda den **ComputerName** -parametern för en cmdlet för att köra den på en fjärrdator som använder Remote Procedure Call (RPC) som dess underliggande protokoll.

## <a name="powershell-remoting-default-settings"></a>Standardinställningarna för PowerShell-fjärrkommunikation

PowerShell-fjärrkommunikation (och WinRM) lyssna på följande portar:

- HTTP: 5985
- HTTPS: 5986

Som standard tillåter PowerShell-fjärrkommunikation bara anslutningar från medlemmarna i gruppen Administratörer. Sessioner startas under användarkontext, så att alla operativsystem åtkomstkontroller som tillämpas på enskilda användare och grupper fortsätta att tillämpas på dem när du är ansluten via PowerShell-fjärrkommunikation.

Standardregeln för Windows-brandväggen för PowerShell-fjärrkommunikation godkänner alla anslutningar i privata nätverk. I offentliga nätverk Standardregeln för Windows-brandväggen PowerShell-fjärrkommunikation endast tillåter anslutningar från inom samma undernät. Du måste uttryckligen ändra regeln för att öppna PowerShell-fjärrkommunikation för alla anslutningar i offentliga nätverk.

>**Varning:** Brandväggsregel för offentliga nätverk är avsedd att skydda datorn från potentiellt skadliga externa anslutningsförsök. Var försiktig när du tar bort den här regeln.

## <a name="process-isolation"></a>Processisolering

PowerShell-fjärrkommunikation använder [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) för kommunikation mellan datorer.
WinRM körs som en tjänst under kontot Nätverkstjänst och tio isolerade processer som körs som användarkonton till ha PowerShell instanser. En instans av PowerShell som körs som en användare har ingen åtkomst till en process som kör en instans av PowerShell som en annan användare.

## <a name="event-logs-generated-by-powershell-remoting"></a>Händelseloggar som genererats av PowerShell-fjärrkommunikation

FireEye erbjudit en bra översikt över händelseloggarna och andra säkerhetsbevis som genererats av PowerShell-fjärrkommunikation sessioner, tillgängliga på [undersöker attacker PowerShell](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Kryptering och transport-protokoll

Det kan vara bra att tänka på säkerheten i en PowerShell-fjärrkommunikation anslutning ur två perspektiv: den inledande autentiseringen och pågående kommunikation.

Oavsett transportprotokollet används (HTTP eller HTTPS) krypterar PowerShell-fjärrkommunikation alltid all kommunikation efter den inledande autentiseringen med en sessions-AES-256 symmetrisk nyckel.

### <a name="initial-authentication"></a>Den inledande autentiseringen

Autentisering bekräftar identiteten för klienten att server- och vi rekommenderar - servern till klienten.

När en klient ansluter till en domänserver namn (t.ex.: server01, eller server01.contoso.com), är standardautentiseringsprotokollet [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos garanterar både användar-ID och Serveridentiteten utan att skicka alla slags återanvändbara autentiseringsuppgifter.

När en klient ansluter till en domänserver med hjälp av dess IP-adress eller ansluter till en arbetsgruppsserver, går inte Kerberos-autentisering. I så fall PowerShell-fjärrkommunikation är beroende av den [NTLM-autentiseringsprotokollet](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). NTLM-autentiseringsprotokollet garanterar användarnas identiteter utan att skicka alla slags kan delegeras autentiseringsuppgifter. För att bevisa användaridentitet, kräver NTLM-protokollet att både klienten och servern compute en sessionsnyckel från användarens lösenord utan att någonsin utväxla själva lösenordet. Servern normalt vet inte lösenordet, så att den kommunicerar med domänkontrollanten som känner till användarens lösenord och beräknar sessionsnyckel för servern.

NTLM-protokollet garanterar inte, men serveridentitet. Precis som med alla protokoll som använder NTLM för autentisering, kan en angripare med tillgång till datorkontot för en domänansluten dator anropa domänkontrollanten för att beräkna NTLM-sessionsnyckel och därmed personifiera servern.

NTLM-baserad autentisering är inaktiverat som standard, men kan beviljas genom att antingen konfigurera SSL på målservern, eller genom att konfigurera inställningen WinRM TrustedHosts på klienten.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Använder SSL-certifikat för att verifiera serveridentitet under NTLM-baserade anslutningar

Eftersom NTLM-autentiseringsprotokollet inte kan garantera identiteten för målservern (endast som den redan vet ditt lösenord), kan du konfigurera målservrar för att använda SSL för PowerShell-fjärrkommunikation. Tilldela ett SSL-certifikat till målservern (om det har utfärdats av en certifikatutfärdare som klienten litar också) gör det möjligt för NTLM-baserad autentisering som garanterar både användar-ID och Serveridentiteten.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Ignorerar NTLM-baserad server identity-fel

Om det är omöjligt att distribuera ett SSL-certifikat till en server för NTLM-anslutningar, kan du ignorera de resulterande identity fel genom att lägga till servern WinRM **TrustedHosts** lista. Observera att lägga till ett namn i listan TrustedHosts inte ska betraktas som någon form av sammanställning av trovärdigheten för värdarna själva – eftersom NTLM-autentiseringsprotokollet inte kan garantera att du i själva verket ansluter till värden som du är Avsikten är att ansluta till.
I stället bör du överväga att TrustedHosts inställningen ska vara listan över värdar som du vill ignorera fel som genereras av att det inte går att verifiera serverns identitet.


### <a name="ongoing-communication"></a>Pågående kommunikation

När den inledande autentiseringen är klar, den [PowerShell-fjärrkommunikation protokollet](https://msdn.microsoft.com/library/dd357801.aspx) krypterar all pågående kommunikation med en sessions-AES-256 symmetrisk nyckel.


## <a name="making-the-second-hop"></a>Gör det andra hoppet

Som standard använder PowerShell-fjärrkommunikation Kerberos (om tillgängligt) eller NTLM för autentisering. Båda dessa protokoll autentisera till fjärrdatorn utan att skicka autentiseringsuppgifter till den.
Detta är det säkraste sättet att autentisera, men eftersom fjärrdatorn inte har användarens autentiseringsuppgifter, det kan inte komma åt andra datorer och tjänster för användarens räkning.
Detta kallas ”andra hopp problemet”.

Det finns flera sätt att undvika det här problemet. Beskrivningar av dessa metoder och -tekniker och nackdelar med varje finns i [gör det andra hoppet i PowerShell-fjärrkommunikation](PS-remoting-second-hop.md).