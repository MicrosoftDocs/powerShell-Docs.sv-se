---
ms.date: 2017-08-23
keywords: PowerShell-cmdlet
title: "Felsökning av åtkomstproblem i windows powershell-webbåtkomst"
ms.openlocfilehash: 08a9fd286ed8a40e9423deb7d29dc0a8ecf8e5b1
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2017
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="afaec-103">Felsökning av åtkomstproblem i Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="afaec-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="afaec-104">Uppdaterad: Juni 24 2013 (omarbetad 23 augusti 2017)</span><span class="sxs-lookup"><span data-stu-id="afaec-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="afaec-105">Gäller för: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="afaec-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="afaec-106">I följande avsnitt identifiera vanliga problem när du försöker ansluta till en fjärrdator med hjälp av Windows PowerShell Web Access och innehåller förslag för att lösa problemen.</span><span class="sxs-lookup"><span data-stu-id="afaec-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="afaec-107">Inloggningsfel</span><span class="sxs-lookup"><span data-stu-id="afaec-107">Sign-in failure</span></span>

<span data-ttu-id="afaec-108">Fel kan inträffa på grund av något av följande.</span><span class="sxs-lookup"><span data-stu-id="afaec-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="afaec-109">En auktoriseringsregel som ger användaren åtkomst till datorn, eller en specifik sessionskonfiguration på fjärrdatorn, saknas.</span><span class="sxs-lookup"><span data-stu-id="afaec-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="afaec-110">Windows PowerShell Web Access-säkerheten är begränsad; användare måste beviljas explicit åtkomst till fjärrdatorer genom att använda regler för auktorisering.</span><span class="sxs-lookup"><span data-stu-id="afaec-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="afaec-111">Mer information om hur du skapar auktoriseringsregler finns [auktoriseringsregler och säkerhet funktioner i Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="afaec-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="afaec-112">Användaren har inte auktoriserad åtkomst till måldatorn.</span><span class="sxs-lookup"><span data-stu-id="afaec-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="afaec-113">Detta bestäms av åtkomstkontrollistor (ACL).</span><span class="sxs-lookup"><span data-stu-id="afaec-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="afaec-114">Mer information finns i [inloggning till Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), eller Windows PowerShell-teamets blogg.</span><span class="sxs-lookup"><span data-stu-id="afaec-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="afaec-115">Windows PowerShell-fjärrhantering kanske inte är aktiverat på måldatorn.</span><span class="sxs-lookup"><span data-stu-id="afaec-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="afaec-116">Kontrollera fjärrhantering är aktiverat på den dator som användaren försöker ansluta.</span><span class="sxs-lookup"><span data-stu-id="afaec-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="afaec-117">Mer information finns i [hur du konfigurerar din dator för fjärrkommunikation](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="afaec-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="afaec-118">Internt serverfel</span><span class="sxs-lookup"><span data-stu-id="afaec-118">Internal Server Error</span></span>

<span data-ttu-id="afaec-119">När användarna försöker logga in på Windows PowerShell Web Access i Internet Explorer, visas en **internt serverfel** sidan eller *Internet Explorer* slutar svara.</span><span class="sxs-lookup"><span data-stu-id="afaec-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="afaec-120">Det här problemet är specifikt för Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="afaec-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="afaec-121">Möjlig orsak</span><span class="sxs-lookup"><span data-stu-id="afaec-121">Possible cause</span></span>

<span data-ttu-id="afaec-122">Detta kan inträffa om en användare har loggat in med ett domännamn som innehåller kinesiska tecken, eller om ett eller flera kinesiska tecken ingår i namnet på gateway-servern.</span><span class="sxs-lookup"><span data-stu-id="afaec-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="afaec-123">Lösning</span><span class="sxs-lookup"><span data-stu-id="afaec-123">Workaround</span></span>

1. [<span data-ttu-id="afaec-124">Installera och köra Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="afaec-124">Install and run Internet Explorer 10</span></span>](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="afaec-125">Ändra Internet Explorer **dokumentläge** till *IE10* standarder.</span><span class="sxs-lookup"><span data-stu-id="afaec-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="afaec-126">Tryck på **F12** att öppna konsolen utvecklingsverktyg</span><span class="sxs-lookup"><span data-stu-id="afaec-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="afaec-127">I Internet Explorer 10 klickar du på **Webbläsarläge**, och välj sedan *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="afaec-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="afaec-128">Klicka på **dokumentläge**, och klicka sedan på *IE10* standarder.</span><span class="sxs-lookup"><span data-stu-id="afaec-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="afaec-129">Tryck på **F12** igen för att stänga konsolen utvecklingsverktyg.</span><span class="sxs-lookup"><span data-stu-id="afaec-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="afaec-130">Inaktivera automatisk proxykonfiguration i Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="afaec-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="afaec-131">Klicka på **verktyg**, och klicka sedan på **Internetalternativ**.</span><span class="sxs-lookup"><span data-stu-id="afaec-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="afaec-132">I den **Internetalternativ** dialogrutan den **anslutningar** klickar du på **LAN-inställningar**.</span><span class="sxs-lookup"><span data-stu-id="afaec-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="afaec-133">Avmarkera den **automatisk identifiering av inställningar** kryssrutan.</span><span class="sxs-lookup"><span data-stu-id="afaec-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="afaec-134">Klicka på **OK**, och klicka sedan på **OK** igen för att stänga den *Internetalternativ* dialogrutan.</span><span class="sxs-lookup"><span data-stu-id="afaec-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="afaec-135">Det går inte att ansluta till en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="afaec-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="afaec-136">Om måldatorn är medlem i en arbetsgrupp, Använd följande syntax för att ange ditt användarnamn och logga in på datorn:`<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="afaec-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="afaec-137">Det går inte att hitta hanteringsverktyg för Webbserver (IIS), trots att rollen har installerats</span><span class="sxs-lookup"><span data-stu-id="afaec-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="afaec-138">Om du har installerat Windows PowerShell-webbåtkomst med hjälp av den `Install-WindowsFeature` cmdlet, är inte hanteringsverktygen installerade såvida inte den `-IncludeManagementTools` parameter läggs till i cmdleten.</span><span class="sxs-lookup"><span data-stu-id="afaec-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="afaec-139">Ett exempel finns [installera Windows PowerShell-webbåtkomst med hjälp av Windows PowerShell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="afaec-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="afaec-140">Du kan lägga till IIS Manager-konsolen och andra IIS-hanteringsverktygen som du behöver, genom att välja verktyg i en **guiden Lägg till roller och funktioner** session som är riktad till gateway-servern.</span><span class="sxs-lookup"><span data-stu-id="afaec-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="afaec-141">Guiden Lägg till roller och funktioner öppnas från i Serverhanteraren.</span><span class="sxs-lookup"><span data-stu-id="afaec-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="afaec-142">Windows PowerShell Web Access-webbplatsen är inte tillgänglig</span><span class="sxs-lookup"><span data-stu-id="afaec-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="afaec-143">Förbättrad säkerhetskonfiguration är aktiverad i Internet Explorer (IE ESC), kan du lägga till Windows PowerShell Web Access-webbplats i listan över betrodda platser.</span><span class="sxs-lookup"><span data-stu-id="afaec-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="afaec-144">En mindre rekommendation, på grund av säkerhetsrisker, är att inaktivera IE ESC.</span><span class="sxs-lookup"><span data-stu-id="afaec-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="afaec-145">Du kan inaktivera IE ESC i panelen Egenskaper på lokal Server-sida i Serverhanteraren.</span><span class="sxs-lookup"><span data-stu-id="afaec-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="afaec-146">Ett auktoriseringsfel inträffade.</span><span class="sxs-lookup"><span data-stu-id="afaec-146">An authorization failure occurred.</span></span> <span data-ttu-id="afaec-147">Kontrollera att du har behörighet att ansluta till måldatorn.</span><span class="sxs-lookup"><span data-stu-id="afaec-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="afaec-148">Ovanstående felmeddelande visas vid försök att ansluta när gateway-servern är måldatorn och finns också i en arbetsgrupp.</span><span class="sxs-lookup"><span data-stu-id="afaec-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="afaec-149">Om gateway-servern också är målservern och finns i en arbetsgrupp, anger du användarnamn, datornamn och användargruppnamn.</span><span class="sxs-lookup"><span data-stu-id="afaec-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="afaec-150">Använd inte en punkt (.) ensamt som representerar namnet på datorn.</span><span class="sxs-lookup"><span data-stu-id="afaec-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="afaec-151">Scenarier och rätt värden</span><span class="sxs-lookup"><span data-stu-id="afaec-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="afaec-152">Alla fall</span><span class="sxs-lookup"><span data-stu-id="afaec-152">All cases</span></span>

<span data-ttu-id="afaec-153">Parameter</span><span class="sxs-lookup"><span data-stu-id="afaec-153">Parameter</span></span> | <span data-ttu-id="afaec-154">Värde</span><span class="sxs-lookup"><span data-stu-id="afaec-154">Value</span></span>
-- | --
<span data-ttu-id="afaec-155">UserName</span><span class="sxs-lookup"><span data-stu-id="afaec-155">UserName</span></span> | <span data-ttu-id="afaec-156">Server\_namn\\användaren\_namn</span><span class="sxs-lookup"><span data-stu-id="afaec-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="afaec-157">Localhost\\användaren\_namn</span><span class="sxs-lookup"><span data-stu-id="afaec-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="afaec-158">. \\användaren\_namn</span><span class="sxs-lookup"><span data-stu-id="afaec-158">.\\user\_name</span></span>
<span data-ttu-id="afaec-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="afaec-159">UserGroup</span></span> | <span data-ttu-id="afaec-160">Server\_namn\\användaren\_grupp</span><span class="sxs-lookup"><span data-stu-id="afaec-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="afaec-161">Localhost\\användaren\_grupp</span><span class="sxs-lookup"><span data-stu-id="afaec-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="afaec-162">. \\användaren\_grupp</span><span class="sxs-lookup"><span data-stu-id="afaec-162">.\\user\_group</span></span>
<span data-ttu-id="afaec-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="afaec-163">ComputerGroup</span></span> | <span data-ttu-id="afaec-164">Server\_namn\\datorn\_grupp</span><span class="sxs-lookup"><span data-stu-id="afaec-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="afaec-165">Localhost\\datorn\_grupp</span><span class="sxs-lookup"><span data-stu-id="afaec-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="afaec-166">. \\datorn\_grupp</span><span class="sxs-lookup"><span data-stu-id="afaec-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="afaec-167">Gateway-servern finns i en domän</span><span class="sxs-lookup"><span data-stu-id="afaec-167">Gateway server is in a domain</span></span>

<span data-ttu-id="afaec-168">Parameter</span><span class="sxs-lookup"><span data-stu-id="afaec-168">Parameter</span></span> | <span data-ttu-id="afaec-169">Värde</span><span class="sxs-lookup"><span data-stu-id="afaec-169">Value</span></span>
-- | --
<span data-ttu-id="afaec-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="afaec-170">ComputerName</span></span> | <span data-ttu-id="afaec-171">Fullständigt kvalificerat namn på gateway-server eller Localhost</span><span class="sxs-lookup"><span data-stu-id="afaec-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="afaec-172">Gateway-servern finns i en arbetsgrupp</span><span class="sxs-lookup"><span data-stu-id="afaec-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="afaec-173">Parameter</span><span class="sxs-lookup"><span data-stu-id="afaec-173">Parameter</span></span> | <span data-ttu-id="afaec-174">Värde</span><span class="sxs-lookup"><span data-stu-id="afaec-174">Value</span></span>
-- | --
<span data-ttu-id="afaec-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="afaec-175">ComputerName</span></span> | <span data-ttu-id="afaec-176">Servernamn</span><span class="sxs-lookup"><span data-stu-id="afaec-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="afaec-177">Gateway-autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="afaec-177">Gateway credentials</span></span>

<span data-ttu-id="afaec-178">Logga in på en gateway-server som måldator med hjälp av autentiseringsuppgifter som är formaterade som något av följande.</span><span class="sxs-lookup"><span data-stu-id="afaec-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="afaec-179">Server\_namn\\användaren\_namn</span><span class="sxs-lookup"><span data-stu-id="afaec-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="afaec-180">Localhost\\användaren\_namn</span><span class="sxs-lookup"><span data-stu-id="afaec-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="afaec-181">. \\användaren\_namn</span><span class="sxs-lookup"><span data-stu-id="afaec-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="afaec-182">En säkerhetsidentifierare (SID) visas i en auktoriseringsregel</span><span class="sxs-lookup"><span data-stu-id="afaec-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="afaec-183">En säkerhetsidentifierare (SID) visas i en auktoriseringsregel i stället syntaxen användaren\_namn eller datorn\_namn.</span><span class="sxs-lookup"><span data-stu-id="afaec-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="afaec-184">Antingen är regeln inte längre giltig eller så misslyckades frågan till Active Directory Domain Services.</span><span class="sxs-lookup"><span data-stu-id="afaec-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="afaec-185">En auktoriseringsregel är vanligtvis inte giltig i scenarier där gateway-servern har funnits en gång i en arbetsgrupp, men senare har anslutits till en domän</span><span class="sxs-lookup"><span data-stu-id="afaec-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="afaec-186">Det går inte att logga in med regeln som en IPv6-adress med en domän</span><span class="sxs-lookup"><span data-stu-id="afaec-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="afaec-187">Det går inte att logga in på en måldator som har angetts i auktoriseringsregler som en IPv6-adress med en domän.</span><span class="sxs-lookup"><span data-stu-id="afaec-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="afaec-188">Auktoriseringsregler stöder inte en IPv6-adress i form av ett domännamn.</span><span class="sxs-lookup"><span data-stu-id="afaec-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="afaec-189">Använd en IPv6-adress (som innehåller kolon) om du vill ange en måldator med hjälp av en IPv6-adress i auktoriseringsregeln.</span><span class="sxs-lookup"><span data-stu-id="afaec-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="afaec-190">Både domänbaserade och numeriska (med kolon) IPv6-adresser stöds som Måldatornamn på sidan för Windows PowerShell Web Access, men inte i auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="afaec-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> 

<span data-ttu-id="afaec-191">Mer information om IPv6-adresser finns [så här fungerar IPv6](https://technet.microsoft.com/en-us/library/cc781672(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="afaec-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/en-us/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="afaec-192">Se även</span><span class="sxs-lookup"><span data-stu-id="afaec-192">See Also</span></span>

- <span data-ttu-id="afaec-193">[Auktoriseringsregler och säkerhetsfunktioner i Windows PowerShell-webbåtkomst](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="afaec-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="afaec-194">[Använd den webbaserade Windows PowerShell-konsolen](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="afaec-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="afaec-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="afaec-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
