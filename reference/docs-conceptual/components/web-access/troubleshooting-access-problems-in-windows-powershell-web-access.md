---
ms.date: 08/23/2017
keywords: PowerShell, cmdlet
title: fel sökning av åtkomst problem i Windows PowerShell-Webbåtkomst
ms.openlocfilehash: 818beffaf7df55ae36a154b7b751f9201c5b4299
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870191"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Felsökning av åtkomstproblem i Windows PowerShell-webbåtkomst

Uppdaterad: 24 juni 2013 (ändrad 23 augusti 2017)

Gäller för: Windows Server 2012 R2, Windows Server 2012

I följande avsnitt beskrivs några vanliga problem vid försök att ansluta till en fjärrdator med hjälp av Windows PowerShell-webbåtkomst och förslag på hur du kan lösa problemen.

## <a name="sign-in-failure"></a>Inloggningsfel

Fel kan inträffa på grund av något av följande.

- En auktoriseringsregel som ger användaren åtkomst till datorn, eller en specifik sessionskonfiguration på fjärrdatorn, saknas.

  Säkerheten i Windows PowerShell-webbåtkomsten är begränsad. användare måste beviljas explicit åtkomst till fjärrdatorer med hjälp av auktoriseringsregler.

  Mer information om hur du skapar auktoriseringsregler finns i [auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- Användaren har inte auktoriserad åtkomst till måldatorn. Detta bestäms av åtkomstkontrollistor (ACL).

  Mer information finns i [Logga in på Windows PowerShell-webbåtkomst](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)eller Windows PowerShell-teamets blogg.

- Windows PowerShell-fjärrhantering kanske inte är aktiverat på mål datorn.

  Kontrol lera att fjärrhantering har Aktiver ATS på den dator som användaren försöker ansluta till.

  Mer information finns i [så här konfigurerar du din dator för fjärr kommunikation](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>Internt Server fel

När användarna försöker logga in på Windows PowerShell-webbåtkomsten i ett Internet Explorer-fönster visas sidan **internt Server fel** eller *Internet Explorer* slutar svara.

Det här problemet är specifikt för Internet Explorer.

### <a name="possible-cause"></a>Möjlig orsak

Detta kan inträffa om en användare har loggat in med ett domännamn som innehåller kinesiska tecken, eller om ett eller flera kinesiska tecken ingår i namnet på gateway-servern.

#### <a name="workaround"></a>Lösning

1. Installera och kör Internet Explorer 10
1. Ändra inställningen för **dokument läge** i Internet Explorer till *IE10* -standarder.
   1. Öppna Utvecklarverktyg-konsolen genom att trycka på **F12**
   1. I Internet Explorer 10 klickar du på **webb läsar läge**och väljer sedan *Internet Explorer 10*.
   1. Klicka på **dokument läge**och klicka sedan på *IE10* -standarder.
   1. Tryck på **F12** igen för att stänga utvecklarverktyg-konsolen.
1. Inaktivera automatisk proxykonfiguration i Internet Explorer 10.
   1. Klicka på **verktyg**och sedan på **Internet alternativ**.
   1. I dialog rutan **Internet alternativ** på fliken **anslutningar** klickar du på LAN- **Inställningar**.
   1. Avmarkera kryss rutan **Automatisk identifiering av inställningar** . Klicka på **OK**och sedan på **OK** igen för att stänga dialog rutan *Internet alternativ* .

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Det går inte att ansluta till en fjärrdator

Om mål datorn är medlem i en arbets grupp använder du följande syntax för att ange ditt användar namn och logga in på datorn: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Det går inte att hitta hanteringsverktyg för Webbserver (IIS), trots att rollen har installerats

Om du har installerat Windows PowerShell-webbåtkomst med hjälp av `Install-WindowsFeature`-cmdleten installeras inte hanterings verktygen om inte parametern **IncludeManagementTools** läggs till i cmdleten.

Ett exempel finns i [Installera Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Du kan lägga till konsolen IIS-hanteraren och andra hanterings verktyg för IIS som du behöver genom att välja verktygen i **guiden Lägg till roller och funktioner i guiden Lägg till roller och funktioner** som är mål för Gateway-servern. Guiden Lägg till roller och funktioner öppnas inifrån Serverhanteraren.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Webbplatsen för Windows PowerShell-webbåtkomst är inte tillgänglig

Om förbättrad säkerhets konfiguration är aktive rad i Internet Explorer (IE ESC) kan du lägga till webbplatsen för Windows PowerShell-webbåtkomsten i listan över betrodda platser.

En mindre rekommenderad metod, på grund av säkerhets risker, är att inaktivera IE ESC. Du kan inaktivera IE ESC i panelen egenskaper på sidan för den lokala servern i Serverhanteraren.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Ett auktoriseringsfel inträffade. Kontrollera att du har behörighet att ansluta till måldatorn.

Ovanstående fel meddelande visas vid försök att ansluta när Gateway-servern är mål datorn och även finns i en arbets grupp.

Om Gateway-servern också är mål servern och finns i en arbets grupp, anger du användar namn, dator namn och användar grupp namn. Använd inte en punkt (.) för att representera dator namnet.

### <a name="scenarios-and-proper-values"></a>Scenarier och lämpliga värden

#### <a name="all-cases"></a>Alla fall

  Parameter   |                                        Värde
------------- | -----------------------------------------------------------------------------------
UserName      | `Server_name\user_name`<br/>`Localhost\user_name`<br/>`.\user_name`
UserGroup     | `Server_name\user_group`<br/>`Localhost\user_group`<br/>`.\user_group`
ComputerGroup | `Server_name\computer_group`<br/>`Localhost\computer_group`<br/>`.\computer_group`

#### <a name="gateway-server-is-in-a-domain"></a>Gateway-servern finns i en domän

 Parameter   |                        Värde
------------ | ----------------------------------------------------
ComputerName | Fullständigt kvalificerat namn på gateway-server eller Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Gateway-servern finns i en arbetsgrupp

 Parameter   |    Värde
------------ | -----------
ComputerName | Servernamn

### <a name="gateway-credentials"></a>Gateway-autentiseringsuppgifter

Logga in på en gateway-server som måldator med hjälp av autentiseringsuppgifter som är formaterade som något av följande.

- `Server_name\user_name`
- `Localhost\user_name`
- `.\user_name`

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>En säkerhets identifierare (SID) visas i en auktoriseringsregel

En säkerhets identifierare (SID) visas i en auktoriseringsregel i stället för syntaxen `user_name/computer_name`.

Antingen är regeln inte längre giltig eller så misslyckades frågan till Active Directory Domain Services. En auktoriseringsregel är vanligt vis inte giltig i scenarier där Gateway-servern har varit i en tid i en arbets grupp, men senare har anslutits till en domän

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Det går inte att logga in med regel som en IPv6-adress med en domän

Det går inte att logga in på en måldator som har angetts i auktoriseringsregler som en IPv6-adress med en domän.

Auktoriseringsregler stöder inte en IPv6-adress i form av ett domännamn.

Använd en IPv6-adress (som innehåller kolon) om du vill ange en måldator med hjälp av en IPv6-adress i auktoriseringsregeln. Både domän-och numeriska (med kolon) IPv6-adresser stöds som mål dator namn på inloggnings sidan för Windows PowerShell-webbåtkomst, men inte i auktoriseringsregler.

Mer information om IPv6-adresser finns i [så här fungerar IPv6](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)).

## <a name="see-also"></a>Se även

- [Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-Webbåtkomst](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))
- [Använd den webbaserade Windows PowerShell-konsolen](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))
- [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
