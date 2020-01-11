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
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="4f58e-103">Felsökning av åtkomstproblem i Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="4f58e-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="4f58e-104">Uppdaterad: 24 juni 2013 (ändrad 23 augusti 2017)</span><span class="sxs-lookup"><span data-stu-id="4f58e-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="4f58e-105">Gäller för: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="4f58e-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="4f58e-106">I följande avsnitt beskrivs några vanliga problem vid försök att ansluta till en fjärrdator med hjälp av Windows PowerShell-webbåtkomst och förslag på hur du kan lösa problemen.</span><span class="sxs-lookup"><span data-stu-id="4f58e-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="4f58e-107">Inloggningsfel</span><span class="sxs-lookup"><span data-stu-id="4f58e-107">Sign-in failure</span></span>

<span data-ttu-id="4f58e-108">Fel kan inträffa på grund av något av följande.</span><span class="sxs-lookup"><span data-stu-id="4f58e-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="4f58e-109">En auktoriseringsregel som ger användaren åtkomst till datorn, eller en specifik sessionskonfiguration på fjärrdatorn, saknas.</span><span class="sxs-lookup"><span data-stu-id="4f58e-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="4f58e-110">Säkerheten i Windows PowerShell-webbåtkomsten är begränsad. användare måste beviljas explicit åtkomst till fjärrdatorer med hjälp av auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="4f58e-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="4f58e-111">Mer information om hur du skapar auktoriseringsregler finns i [auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="4f58e-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="4f58e-112">Användaren har inte auktoriserad åtkomst till måldatorn.</span><span class="sxs-lookup"><span data-stu-id="4f58e-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="4f58e-113">Detta bestäms av åtkomstkontrollistor (ACL).</span><span class="sxs-lookup"><span data-stu-id="4f58e-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="4f58e-114">Mer information finns i [Logga in på Windows PowerShell-webbåtkomst](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)eller Windows PowerShell-teamets blogg.</span><span class="sxs-lookup"><span data-stu-id="4f58e-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="4f58e-115">Windows PowerShell-fjärrhantering kanske inte är aktiverat på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="4f58e-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="4f58e-116">Kontrol lera att fjärrhantering har Aktiver ATS på den dator som användaren försöker ansluta till.</span><span class="sxs-lookup"><span data-stu-id="4f58e-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="4f58e-117">Mer information finns i [så här konfigurerar du din dator för fjärr kommunikation](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="4f58e-117">For more information, see [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="4f58e-118">Internt Server fel</span><span class="sxs-lookup"><span data-stu-id="4f58e-118">Internal Server Error</span></span>

<span data-ttu-id="4f58e-119">När användarna försöker logga in på Windows PowerShell-webbåtkomsten i ett Internet Explorer-fönster visas sidan **internt Server fel** eller *Internet Explorer* slutar svara.</span><span class="sxs-lookup"><span data-stu-id="4f58e-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="4f58e-120">Det här problemet är specifikt för Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4f58e-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="4f58e-121">Möjlig orsak</span><span class="sxs-lookup"><span data-stu-id="4f58e-121">Possible cause</span></span>

<span data-ttu-id="4f58e-122">Detta kan inträffa om en användare har loggat in med ett domännamn som innehåller kinesiska tecken, eller om ett eller flera kinesiska tecken ingår i namnet på gateway-servern.</span><span class="sxs-lookup"><span data-stu-id="4f58e-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="4f58e-123">Lösning</span><span class="sxs-lookup"><span data-stu-id="4f58e-123">Workaround</span></span>

1. <span data-ttu-id="4f58e-124">Installera och kör Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="4f58e-124">Install and run Internet Explorer 10</span></span>
1. <span data-ttu-id="4f58e-125">Ändra inställningen för **dokument läge** i Internet Explorer till *IE10* -standarder.</span><span class="sxs-lookup"><span data-stu-id="4f58e-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="4f58e-126">Öppna Utvecklarverktyg-konsolen genom att trycka på **F12**</span><span class="sxs-lookup"><span data-stu-id="4f58e-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="4f58e-127">I Internet Explorer 10 klickar du på **webb läsar läge**och väljer sedan *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="4f58e-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="4f58e-128">Klicka på **dokument läge**och klicka sedan på *IE10* -standarder.</span><span class="sxs-lookup"><span data-stu-id="4f58e-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="4f58e-129">Tryck på **F12** igen för att stänga utvecklarverktyg-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4f58e-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="4f58e-130">Inaktivera automatisk proxykonfiguration i Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="4f58e-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="4f58e-131">Klicka på **verktyg**och sedan på **Internet alternativ**.</span><span class="sxs-lookup"><span data-stu-id="4f58e-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="4f58e-132">I dialog rutan **Internet alternativ** på fliken **anslutningar** klickar du på LAN- **Inställningar**.</span><span class="sxs-lookup"><span data-stu-id="4f58e-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="4f58e-133">Avmarkera kryss rutan **Automatisk identifiering av inställningar** .</span><span class="sxs-lookup"><span data-stu-id="4f58e-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="4f58e-134">Klicka på **OK**och sedan på **OK** igen för att stänga dialog rutan *Internet alternativ* .</span><span class="sxs-lookup"><span data-stu-id="4f58e-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="4f58e-135">Det går inte att ansluta till en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="4f58e-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="4f58e-136">Om mål datorn är medlem i en arbets grupp använder du följande syntax för att ange ditt användar namn och logga in på datorn: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="4f58e-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="4f58e-137">Det går inte att hitta hanteringsverktyg för Webbserver (IIS), trots att rollen har installerats</span><span class="sxs-lookup"><span data-stu-id="4f58e-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="4f58e-138">Om du har installerat Windows PowerShell-webbåtkomst med hjälp av `Install-WindowsFeature`-cmdleten installeras inte hanterings verktygen om inte parametern **IncludeManagementTools** läggs till i cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4f58e-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the **IncludeManagementTools** parameter is added to the cmdlet.</span></span>

<span data-ttu-id="4f58e-139">Ett exempel finns i [Installera Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="4f58e-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="4f58e-140">Du kan lägga till konsolen IIS-hanteraren och andra hanterings verktyg för IIS som du behöver genom att välja verktygen i **guiden Lägg till roller och funktioner i guiden Lägg till roller och funktioner** som är mål för Gateway-servern.</span><span class="sxs-lookup"><span data-stu-id="4f58e-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span> <span data-ttu-id="4f58e-141">Guiden Lägg till roller och funktioner öppnas inifrån Serverhanteraren.</span><span class="sxs-lookup"><span data-stu-id="4f58e-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="4f58e-142">Webbplatsen för Windows PowerShell-webbåtkomst är inte tillgänglig</span><span class="sxs-lookup"><span data-stu-id="4f58e-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="4f58e-143">Om förbättrad säkerhets konfiguration är aktive rad i Internet Explorer (IE ESC) kan du lägga till webbplatsen för Windows PowerShell-webbåtkomsten i listan över betrodda platser.</span><span class="sxs-lookup"><span data-stu-id="4f58e-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="4f58e-144">En mindre rekommenderad metod, på grund av säkerhets risker, är att inaktivera IE ESC.</span><span class="sxs-lookup"><span data-stu-id="4f58e-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span> <span data-ttu-id="4f58e-145">Du kan inaktivera IE ESC i panelen egenskaper på sidan för den lokala servern i Serverhanteraren.</span><span class="sxs-lookup"><span data-stu-id="4f58e-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="4f58e-146">Ett auktoriseringsfel inträffade.</span><span class="sxs-lookup"><span data-stu-id="4f58e-146">An authorization failure occurred.</span></span> <span data-ttu-id="4f58e-147">Kontrollera att du har behörighet att ansluta till måldatorn.</span><span class="sxs-lookup"><span data-stu-id="4f58e-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="4f58e-148">Ovanstående fel meddelande visas vid försök att ansluta när Gateway-servern är mål datorn och även finns i en arbets grupp.</span><span class="sxs-lookup"><span data-stu-id="4f58e-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="4f58e-149">Om Gateway-servern också är mål servern och finns i en arbets grupp, anger du användar namn, dator namn och användar grupp namn.</span><span class="sxs-lookup"><span data-stu-id="4f58e-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span> <span data-ttu-id="4f58e-150">Använd inte en punkt (.) för att representera dator namnet.</span><span class="sxs-lookup"><span data-stu-id="4f58e-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="4f58e-151">Scenarier och lämpliga värden</span><span class="sxs-lookup"><span data-stu-id="4f58e-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="4f58e-152">Alla fall</span><span class="sxs-lookup"><span data-stu-id="4f58e-152">All cases</span></span>

  <span data-ttu-id="4f58e-153">Parameter</span><span class="sxs-lookup"><span data-stu-id="4f58e-153">Parameter</span></span>   |                                        <span data-ttu-id="4f58e-154">Värde</span><span class="sxs-lookup"><span data-stu-id="4f58e-154">Value</span></span>
------------- | -----------------------------------------------------------------------------------
<span data-ttu-id="4f58e-155">UserName</span><span class="sxs-lookup"><span data-stu-id="4f58e-155">UserName</span></span>      | `Server_name\user_name`<br/>`Localhost\user_name`<br/>`.\user_name`
<span data-ttu-id="4f58e-156">UserGroup</span><span class="sxs-lookup"><span data-stu-id="4f58e-156">UserGroup</span></span>     | `Server_name\user_group`<br/>`Localhost\user_group`<br/>`.\user_group`
<span data-ttu-id="4f58e-157">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="4f58e-157">ComputerGroup</span></span> | `Server_name\computer_group`<br/>`Localhost\computer_group`<br/>`.\computer_group`

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="4f58e-158">Gateway-servern finns i en domän</span><span class="sxs-lookup"><span data-stu-id="4f58e-158">Gateway server is in a domain</span></span>

 <span data-ttu-id="4f58e-159">Parameter</span><span class="sxs-lookup"><span data-stu-id="4f58e-159">Parameter</span></span>   |                        <span data-ttu-id="4f58e-160">Värde</span><span class="sxs-lookup"><span data-stu-id="4f58e-160">Value</span></span>
------------ | ----------------------------------------------------
<span data-ttu-id="4f58e-161">ComputerName</span><span class="sxs-lookup"><span data-stu-id="4f58e-161">ComputerName</span></span> | <span data-ttu-id="4f58e-162">Fullständigt kvalificerat namn på gateway-server eller Localhost</span><span class="sxs-lookup"><span data-stu-id="4f58e-162">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="4f58e-163">Gateway-servern finns i en arbetsgrupp</span><span class="sxs-lookup"><span data-stu-id="4f58e-163">Gateway server is in a workgroup</span></span>

 <span data-ttu-id="4f58e-164">Parameter</span><span class="sxs-lookup"><span data-stu-id="4f58e-164">Parameter</span></span>   |    <span data-ttu-id="4f58e-165">Värde</span><span class="sxs-lookup"><span data-stu-id="4f58e-165">Value</span></span>
------------ | -----------
<span data-ttu-id="4f58e-166">ComputerName</span><span class="sxs-lookup"><span data-stu-id="4f58e-166">ComputerName</span></span> | <span data-ttu-id="4f58e-167">Servernamn</span><span class="sxs-lookup"><span data-stu-id="4f58e-167">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="4f58e-168">Gateway-autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="4f58e-168">Gateway credentials</span></span>

<span data-ttu-id="4f58e-169">Logga in på en gateway-server som måldator med hjälp av autentiseringsuppgifter som är formaterade som något av följande.</span><span class="sxs-lookup"><span data-stu-id="4f58e-169">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- `Server_name\user_name`
- `Localhost\user_name`
- `.\user_name`

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="4f58e-170">En säkerhets identifierare (SID) visas i en auktoriseringsregel</span><span class="sxs-lookup"><span data-stu-id="4f58e-170">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="4f58e-171">En säkerhets identifierare (SID) visas i en auktoriseringsregel i stället för syntaxen `user_name/computer_name`.</span><span class="sxs-lookup"><span data-stu-id="4f58e-171">A security identifier (SID) is displayed in an authorization rule instead of the syntax `user_name/computer_name`.</span></span>

<span data-ttu-id="4f58e-172">Antingen är regeln inte längre giltig eller så misslyckades frågan till Active Directory Domain Services.</span><span class="sxs-lookup"><span data-stu-id="4f58e-172">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="4f58e-173">En auktoriseringsregel är vanligt vis inte giltig i scenarier där Gateway-servern har varit i en tid i en arbets grupp, men senare har anslutits till en domän</span><span class="sxs-lookup"><span data-stu-id="4f58e-173">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="4f58e-174">Det går inte att logga in med regel som en IPv6-adress med en domän</span><span class="sxs-lookup"><span data-stu-id="4f58e-174">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="4f58e-175">Det går inte att logga in på en måldator som har angetts i auktoriseringsregler som en IPv6-adress med en domän.</span><span class="sxs-lookup"><span data-stu-id="4f58e-175">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="4f58e-176">Auktoriseringsregler stöder inte en IPv6-adress i form av ett domännamn.</span><span class="sxs-lookup"><span data-stu-id="4f58e-176">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="4f58e-177">Använd en IPv6-adress (som innehåller kolon) om du vill ange en måldator med hjälp av en IPv6-adress i auktoriseringsregeln.</span><span class="sxs-lookup"><span data-stu-id="4f58e-177">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="4f58e-178">Både domän-och numeriska (med kolon) IPv6-adresser stöds som mål dator namn på inloggnings sidan för Windows PowerShell-webbåtkomst, men inte i auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="4f58e-178">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="4f58e-179">Mer information om IPv6-adresser finns i [så här fungerar IPv6](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="4f58e-179">For more information about IPv6 addresses, see [How IPv6 Works](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)).</span></span>

## <a name="see-also"></a><span data-ttu-id="4f58e-180">Se även</span><span class="sxs-lookup"><span data-stu-id="4f58e-180">See Also</span></span>

- <span data-ttu-id="4f58e-181">[Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-Webbåtkomst](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="4f58e-181">[Authorization Rules and Security Features of Windows PowerShell Web Access](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span></span>
- <span data-ttu-id="4f58e-182">[Använd den webbaserade Windows PowerShell-konsolen](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="4f58e-182">[Use the Web-based Windows PowerShell Console](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span></span>
- [<span data-ttu-id="4f58e-183">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="4f58e-183">about_Remote_Requirements</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
