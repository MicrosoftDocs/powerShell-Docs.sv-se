---
ms.date: 08/23/2017
keywords: PowerShell cmdlet
title: Felsökning av åtkomstproblem i windows powershell-webbåtkomst
ms.openlocfilehash: 314e4a8098988111739705d55b68ff5ed2f5eff3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688121"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Felsökning av åtkomstproblem i Windows PowerShell-webbåtkomst

Uppdaterad: Juni 24 2013 (omarbetad 23 augusti 2017)

Gäller för: Windows Server 2012 R2, Windows Server 2012

I följande avsnitt identifiera några vanliga problem vid försök att ansluta till en fjärrdator med hjälp av Windows PowerShell-webbåtkomst och innehåller förslag för att lösa problemen.

## <a name="sign-in-failure"></a>Inloggningsfel

Fel kan inträffa på grund av något av följande.

- En auktoriseringsregel som ger användaren åtkomst till datorn, eller en specifik sessionskonfiguration på fjärrdatorn, saknas.

  Windows PowerShell Web Access-säkerheten är begränsad; användare måste beviljas explicit åtkomst till fjärrdatorer med hjälp av auktoriseringsregler.

  Mer information om hur du skapar auktoriseringsregler finns i [auktoriseringsregler och säkerhet funktioner i Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- Användaren har inte auktoriserad åtkomst till måldatorn. Detta bestäms av åtkomstkontrollistor (ACL).

  Mer information finns i [inloggning till Windows PowerShell-webbåtkomst](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), eller Windows PowerShell-teamets blogg.

- Windows PowerShell fjärrhantering inte kanske är aktiverat på måldatorn.

  Kontrollera fjärrhantering är aktiverat på den dator som användaren försöker ansluta.

  Mer information finns i [hur du konfigurerar din dator för fjärrkommunikation](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>Internt serverfel

När användare försöker logga in på Windows PowerShell-webbåtkomst i Internet Explorer, visas en **internt serverfel** sidan eller *Internet Explorer* slutar svara.

Det här problemet är specifikt för Internet Explorer.

### <a name="possible-cause"></a>Möjlig orsak

Detta kan inträffa om en användare har loggat in med ett domännamn som innehåller kinesiska tecken, eller om ett eller flera kinesiska tecken ingår i namnet på gateway-servern.

#### <a name="workaround"></a>Lösning

1. [Installera och köra Internet Explorer 10](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Ändra Internet Explorer **dokumentläge** att ställa in *IE10* standarder.
   1. Tryck på **F12** att öppna konsolen utvecklingsverktyg
   1. I Internet Explorer 10 klickar du på **Webbläsarläge**, och välj sedan *Internet Explorer 10*.
   1. Klicka på **dokumentläge**, och klicka sedan på *IE10* standarder.
   1. Tryck på **F12** igen för att stänga konsolen utvecklingsverktyg.
1. Inaktivera automatisk proxykonfiguration i Internet Explorer 10.
   1. Klicka på **verktyg**, och klicka sedan på **Internetalternativ**.
   1. I den **Internetalternativ** dialogrutan den **anslutningar** fliken **LAN-inställningar**.
   1. Rensa den **automatisk identifiering av inställningar** markerar du kryssrutan. Klicka på **OK**, och klicka sedan på **OK** igen för att stänga den *Internetalternativ* dialogrutan.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Det går inte att ansluta till en fjärrdator

Om måldatorn är medlem i en arbetsgrupp, använder du följande syntax för att ange ditt användarnamn och logga in på datorn: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Det går inte att hitta hanteringsverktyg för Webbserver (IIS), trots att rollen har installerats

Om du har installerat Windows PowerShell-webbåtkomst med hjälp av den `Install-WindowsFeature` cmdlet, management är inte hanteringsverktygen installerade såvida inte den `-IncludeManagementTools` parametern har lagts till i cmdleten.

Ett exempel finns i [installera Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Du kan lägga till IIS Manager-konsolen och andra IIS-hanteringsverktygen att du behöver, genom att välja verktyg i en **guiden Lägg till roller och funktioner** session som är riktad till gateway-servern.
Lägg till roller och funktioner som guiden öppnas från i Server Manager.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Windows PowerShell Web Access-webbplatsen är inte tillgänglig

Om Förbättrad säkerhetskonfiguration är aktiverad i Internet Explorer (IE ESC), kan du lägga till Windows PowerShell Web Access-webbplatsen i listan över betrodda platser.

En mindre rekommenderade metod, på grund av säkerhetsrisker, är att inaktivera IE ESC.
Du kan inaktivera IE ESC i panelen Egenskaper på sidan lokal Server i Server Manager.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Ett autentiseringsfel inträffade. Kontrollera att du har behörighet att ansluta till måldatorn.

Ovanstående felmeddelande visas vid försök att ansluta när gateway-servern är måldatorn och finns också i en arbetsgrupp.

När gateway-servern också är målservern och det är i en arbetsgrupp, ange användarnamn, datornamn och användargruppnamn.
Använd inte en punkt (.) ensamt som representerar namnet på datorn.

### <a name="scenarios-and-proper-values"></a>Scenarier och rätt värden

#### <a name="all-cases"></a>Alla fall

Parameter | Värde
-- | --
UserName | Server\_namn\\användaren\_namn<br/>Localhost\\user\_name<br/>. \\användaren\_namn
UserGroup | Server\_name\\user\_group<br/>Localhost\\användaren\_grupp<br/>. \\användaren\_grupp
ComputerGroup | Server\_name\\computer\_group<br/>Localhost\\datorn\_grupp<br/>. \\datorn\_grupp

#### <a name="gateway-server-is-in-a-domain"></a>Gateway-servern finns i en domän

Parameter | Värde
-- | --
ComputerName | Fullständigt kvalificerat namn på gateway-server eller Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Gateway-servern finns i en arbetsgrupp

Parameter | Värde
-- | --
ComputerName | Servernamn

### <a name="gateway-credentials"></a>Gateway-autentiseringsuppgifter

Logga in på en gateway-server som måldator med hjälp av autentiseringsuppgifter som är formaterade som något av följande.

- Server\_namn\\användaren\_namn
- Localhost\\user\_name
- . \\användaren\_namn

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>En säkerhetsidentifierare (SID) visas i en auktoriseringsregel

En säkerhetsidentifierare (SID) visas i en auktoriseringsregel i stället syntaxen användaren\_namn/dator\_namn.

Antingen är regeln inte längre giltig eller så misslyckades frågan till Active Directory Domain Services.
En auktoriseringsregel är vanligtvis inte giltig i scenarier där gateway-servern har funnits en gång i en arbetsgrupp, men senare har anslutits till en domän

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Det går inte att logga in med regeln som en IPv6-adress med en domän

Det går inte att logga in på en måldator som har angetts i auktoriseringsregler som en IPv6-adress med en domän.

Auktoriseringsregler stöder inte en IPv6-adress i form av ett domännamn.

Använd en IPv6-adress (som innehåller kolon) om du vill ange en måldator med hjälp av en IPv6-adress i auktoriseringsregeln.
Både domän och numeriska (med kolon) IPv6-adresser stöds som Måldatornamn på inloggningssidan för Windows PowerShell Web Access, men inte i auktoriseringsregler.

Mer information om IPv6-adresser finns i [så här fungerar IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Se även

- [Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [Använd den webbaserade Windows PowerShell-konsolen](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)