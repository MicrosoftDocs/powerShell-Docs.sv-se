---
description: Förklarar språk lägen och deras inverkan på PowerShell-sessioner.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: a75afd5149f3d290a8ec377417d4920b0ad6b526
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271544"
---
# <a name="about-language-modes"></a><span data-ttu-id="33251-104">Om språk lägen</span><span class="sxs-lookup"><span data-stu-id="33251-104">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="33251-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="33251-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="33251-106">Förklarar språk lägen och deras inverkan på PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="33251-106">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="33251-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="33251-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="33251-108">Språk läget i en PowerShell-session bestämmer delvis vilka element i PowerShell-språket som kan användas i sessionen.</span><span class="sxs-lookup"><span data-stu-id="33251-108">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="33251-109">PowerShell har stöd för följande språk lägen:</span><span class="sxs-lookup"><span data-stu-id="33251-109">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="33251-110">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="33251-110">FullLanguage</span></span>
- <span data-ttu-id="33251-111">ConstrainedLanguage (lanserades i PowerShell 3,0)</span><span class="sxs-lookup"><span data-stu-id="33251-111">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="33251-112">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="33251-112">RestrictedLanguage</span></span>
- <span data-ttu-id="33251-113">Inget språk</span><span class="sxs-lookup"><span data-stu-id="33251-113">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="33251-114">VAD ÄR ETT SPRÅK LÄGE?</span><span class="sxs-lookup"><span data-stu-id="33251-114">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="33251-115">Språk läget avgör vilka språk element som tillåts i sessionen.</span><span class="sxs-lookup"><span data-stu-id="33251-115">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="33251-116">Språk läget är i själva verket en egenskap för den session konfiguration (eller "slut punkt") som används för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="33251-116">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="33251-117">Alla sessioner som använder en viss konfiguration av sessionen har språk läget i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="33251-117">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="33251-118">Alla PowerShell-sessioner har ett språk läge, inklusive PSSessions som du skapar med hjälp av `New-PSSession` cmdleten, tillfälliga sessioner som använder parametern ComputerName och de standardsessioner som visas när du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33251-118">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="33251-119">Fjärrsessioner skapas med hjälp av sessionens konfigurationer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="33251-119">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="33251-120">Språk läget som anges i konfigurationen bestämmer sessionens språkläge.</span><span class="sxs-lookup"><span data-stu-id="33251-120">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="33251-121">Om du vill ange PSSession för en använder du parametern ConfigurationName för cmdletar som skapar en session.</span><span class="sxs-lookup"><span data-stu-id="33251-121">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="33251-122">SPRÅK LÄGEN</span><span class="sxs-lookup"><span data-stu-id="33251-122">LANGUAGE MODES</span></span>

<span data-ttu-id="33251-123">I det här avsnittet beskrivs språk lägena i PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="33251-123">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="33251-124">FULLSTÄNDIGT språk (FullLanguage)</span><span class="sxs-lookup"><span data-stu-id="33251-124">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="33251-125">FullLanguage-läget tillåter alla språk element i sessionen.</span><span class="sxs-lookup"><span data-stu-id="33251-125">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="33251-126">FullLanguage är standard språk läget för standardsessioner i alla versioner av Windows förutom Windows RT.</span><span class="sxs-lookup"><span data-stu-id="33251-126">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="33251-127">BEGRÄNSAT språk (RestrictedLanguage)</span><span class="sxs-lookup"><span data-stu-id="33251-127">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="33251-128">I RestrictedLanguage-läge kan användare köra kommandon (cmdlets, functions, CIM-kommandon och arbets flöden) men får inte använda skript block.</span><span class="sxs-lookup"><span data-stu-id="33251-128">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="33251-129">Som standard tillåts endast följande variabler i RestrictedLanguage-läge:</span><span class="sxs-lookup"><span data-stu-id="33251-129">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="33251-130">Endast följande jämförelse operatorer tillåts:</span><span class="sxs-lookup"><span data-stu-id="33251-130">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="33251-131">`-eq` Skeppningskvantiteten</span><span class="sxs-lookup"><span data-stu-id="33251-131">`-eq` (equal)</span></span>
- <span data-ttu-id="33251-132">`-gt` (större än)</span><span class="sxs-lookup"><span data-stu-id="33251-132">`-gt` (greater-than)</span></span>
- <span data-ttu-id="33251-133">`-lt` (mindre än)</span><span class="sxs-lookup"><span data-stu-id="33251-133">`-lt` (less-than)</span></span>

<span data-ttu-id="33251-134">Tilldelnings instruktioner, egenskaps referenser och metod anrop är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="33251-134">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="33251-135">INGET språk (nolanguage)</span><span class="sxs-lookup"><span data-stu-id="33251-135">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="33251-136">Nospråks läge kan bara användas via API: et.</span><span class="sxs-lookup"><span data-stu-id="33251-136">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="33251-137">Nospråk läge innebär att ingen skript text för något formulär tillåts.</span><span class="sxs-lookup"><span data-stu-id="33251-137">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="33251-138">Detta utesluter användningen av metoden **AddScript ()** som skickar fragment av PowerShell-skript för att parsas och köras.</span><span class="sxs-lookup"><span data-stu-id="33251-138">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="33251-139">Du kan bara använda **AddCommand ()** och **AddParameter ()** som inte går igenom parsern.</span><span class="sxs-lookup"><span data-stu-id="33251-139">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="33251-140">BEGRÄNSAT språk (begränsat språk)</span><span class="sxs-lookup"><span data-stu-id="33251-140">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="33251-141">ConstrainedLanguage-läget tillåter alla cmdletar och alla PowerShell-språkelement, men det begränsar tillåtna typer.</span><span class="sxs-lookup"><span data-stu-id="33251-141">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="33251-142">ConstrainedLanguage-läget har utformats för att stödja kod integritet i användarläge (UMCI) på Windows RT.</span><span class="sxs-lookup"><span data-stu-id="33251-142">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="33251-143">Det är det enda språk läge som stöds i Windows RT, men det är tillgängligt i alla system som stöds.</span><span class="sxs-lookup"><span data-stu-id="33251-143">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="33251-144">UMCI skyddar ARM-enheter genom att bara tillåta att Microsoft-signerade och Microsoft-certifierade appar installeras på Windows RT-baserade enheter.</span><span class="sxs-lookup"><span data-stu-id="33251-144">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="33251-145">ConstrainedLanguage-läget hindrar användare från att använda PowerShell för att kringgå eller bryta mot UMCI.</span><span class="sxs-lookup"><span data-stu-id="33251-145">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="33251-146">Funktionerna i ConstrainedLanguage-läge är följande:</span><span class="sxs-lookup"><span data-stu-id="33251-146">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="33251-147">Alla cmdletar i Windows-moduler och andra UMCI-godkända cmdlets är fullt funktionella och har fullständig åtkomst till system resurser, förutom vad som anges.</span><span class="sxs-lookup"><span data-stu-id="33251-147">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="33251-148">Alla element i PowerShell-skript språket är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="33251-148">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="33251-149">Alla moduler som ingår i Windows kan importeras och alla kommandon som modulerna exporterar körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="33251-149">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="33251-150">I PowerShell-arbetsflöde kan du skriva och köra skript arbets flöden (arbets flöden skrivna i PowerShell-språket).</span><span class="sxs-lookup"><span data-stu-id="33251-150">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="33251-151">XAML-baserade arbets flöden stöds inte och du kan inte köra XAML i ett skript arbets flöde, till exempel med hjälp av `Invoke-Expression -Language XAML` .</span><span class="sxs-lookup"><span data-stu-id="33251-151">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="33251-152">Arbets flöden kan heller inte anropa andra arbets flöden, även om kapslade arbets flöden tillåts.</span><span class="sxs-lookup"><span data-stu-id="33251-152">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="33251-153">`Add-Type`Cmdleten kan läsa in signerade sammansättningar, men det går inte att läsa in godtycklig C#-kod eller Win32-API: er.</span><span class="sxs-lookup"><span data-stu-id="33251-153">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="33251-154">`New-Object`Cmdleten kan endast användas för tillåtna typer (visas nedan).</span><span class="sxs-lookup"><span data-stu-id="33251-154">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="33251-155">Endast tillåtna typer (listade nedan) kan användas i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33251-155">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="33251-156">Andra typer är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="33251-156">Other types are not permitted.</span></span>

- <span data-ttu-id="33251-157">Typ konvertering tillåts, men endast om resultatet är en tillåten typ.</span><span class="sxs-lookup"><span data-stu-id="33251-157">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="33251-158">Cmdlet-parametrar som konverterar inmatade strängar till typer fungerar endast när den resulterande typen är en tillåten typ.</span><span class="sxs-lookup"><span data-stu-id="33251-158">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="33251-159">Metoden **toString ()** och .net-metoderna för tillåtna typer (listas nedan) kan anropas.</span><span class="sxs-lookup"><span data-stu-id="33251-159">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="33251-160">Det går inte att anropa andra metoder.</span><span class="sxs-lookup"><span data-stu-id="33251-160">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="33251-161">Användare kan hämta alla egenskaper av tillåtna typer.</span><span class="sxs-lookup"><span data-stu-id="33251-161">Users can get all properties of allowed types.</span></span> <span data-ttu-id="33251-162">Användare kan bara ange värden för egenskaper för kärn typer.</span><span class="sxs-lookup"><span data-stu-id="33251-162">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="33251-163">Endast följande COM-objekt tillåts:</span><span class="sxs-lookup"><span data-stu-id="33251-163">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="33251-164">**Skript. ord lista**</span><span class="sxs-lookup"><span data-stu-id="33251-164">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="33251-165">**Scripting. FileSystemObject**</span><span class="sxs-lookup"><span data-stu-id="33251-165">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="33251-166">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="33251-166">**VBScript.RegExp**</span></span>

<span data-ttu-id="33251-167">Följande typer tillåts i ConstrainedLanguage-läge.</span><span class="sxs-lookup"><span data-stu-id="33251-167">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="33251-168">Användare kan få egenskaper, anropa metoder och konvertera objekt till de här typerna.</span><span class="sxs-lookup"><span data-stu-id="33251-168">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="33251-169">Tillåtna typer:</span><span class="sxs-lookup"><span data-stu-id="33251-169">Allowed Types:</span></span>

- <span data-ttu-id="33251-170">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-170">AliasAttribute</span></span>
- <span data-ttu-id="33251-171">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-171">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="33251-172">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-172">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="33251-173">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-173">AllowNullAttribute</span></span>
- <span data-ttu-id="33251-174">Matris</span><span class="sxs-lookup"><span data-stu-id="33251-174">Array</span></span>
- <span data-ttu-id="33251-175">Bool</span><span class="sxs-lookup"><span data-stu-id="33251-175">Bool</span></span>
- <span data-ttu-id="33251-176">stor</span><span class="sxs-lookup"><span data-stu-id="33251-176">byte</span></span>
- <span data-ttu-id="33251-177">char</span><span class="sxs-lookup"><span data-stu-id="33251-177">char</span></span>
- <span data-ttu-id="33251-178">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-178">CmdletBindingAttribute</span></span>
- <span data-ttu-id="33251-179">DateTime</span><span class="sxs-lookup"><span data-stu-id="33251-179">DateTime</span></span>
- <span data-ttu-id="33251-180">decimal</span><span class="sxs-lookup"><span data-stu-id="33251-180">decimal</span></span>
- <span data-ttu-id="33251-181">DirectoryEntry</span><span class="sxs-lookup"><span data-stu-id="33251-181">DirectoryEntry</span></span>
- <span data-ttu-id="33251-182">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="33251-182">DirectorySearcher</span></span>
- <span data-ttu-id="33251-183">double</span><span class="sxs-lookup"><span data-stu-id="33251-183">double</span></span>
- <span data-ttu-id="33251-184">flyt</span><span class="sxs-lookup"><span data-stu-id="33251-184">float</span></span>
- <span data-ttu-id="33251-185">GUID</span><span class="sxs-lookup"><span data-stu-id="33251-185">Guid</span></span>
- <span data-ttu-id="33251-186">Hash</span><span class="sxs-lookup"><span data-stu-id="33251-186">Hashtable</span></span>
- <span data-ttu-id="33251-187">int</span><span class="sxs-lookup"><span data-stu-id="33251-187">int</span></span>
- <span data-ttu-id="33251-188">Int16</span><span class="sxs-lookup"><span data-stu-id="33251-188">Int16</span></span>
- <span data-ttu-id="33251-189">long</span><span class="sxs-lookup"><span data-stu-id="33251-189">long</span></span>
- <span data-ttu-id="33251-190">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="33251-190">ManagementClass</span></span>
- <span data-ttu-id="33251-191">ManagementObject</span><span class="sxs-lookup"><span data-stu-id="33251-191">ManagementObject</span></span>
- <span data-ttu-id="33251-192">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="33251-192">ManagementObjectSearcher</span></span>
- <span data-ttu-id="33251-193">NullString</span><span class="sxs-lookup"><span data-stu-id="33251-193">NullString</span></span>
- <span data-ttu-id="33251-194">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-194">OutputTypeAttribute</span></span>
- <span data-ttu-id="33251-195">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-195">ParameterAttribute</span></span>
- <span data-ttu-id="33251-196">PSCredential</span><span class="sxs-lookup"><span data-stu-id="33251-196">PSCredential</span></span>
- <span data-ttu-id="33251-197">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-197">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="33251-198">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="33251-198">PSListModifier</span></span>
- <span data-ttu-id="33251-199">PSObject</span><span class="sxs-lookup"><span data-stu-id="33251-199">PSObject</span></span>
- <span data-ttu-id="33251-200">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="33251-200">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="33251-201">PSReference</span><span class="sxs-lookup"><span data-stu-id="33251-201">PSReference</span></span>
- <span data-ttu-id="33251-202">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-202">PSTypeNameAttribute</span></span>
- <span data-ttu-id="33251-203">Verifiering</span><span class="sxs-lookup"><span data-stu-id="33251-203">Regex</span></span>
- <span data-ttu-id="33251-204">SByte</span><span class="sxs-lookup"><span data-stu-id="33251-204">SByte</span></span>
- <span data-ttu-id="33251-205">sträng</span><span class="sxs-lookup"><span data-stu-id="33251-205">string</span></span>
- <span data-ttu-id="33251-206">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="33251-206">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="33251-207">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="33251-207">SwitchParameter</span></span>
- <span data-ttu-id="33251-208">System. globalisering. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="33251-208">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="33251-209">System .net. IPAddress</span><span class="sxs-lookup"><span data-stu-id="33251-209">System.Net.IPAddress</span></span>
- <span data-ttu-id="33251-210">System .net. mail. mail-adress</span><span class="sxs-lookup"><span data-stu-id="33251-210">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="33251-211">System. Numerics. BigInteger</span><span class="sxs-lookup"><span data-stu-id="33251-211">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="33251-212">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="33251-212">System.Security.SecureString</span></span>
- <span data-ttu-id="33251-213">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="33251-213">TimeSpan</span></span>
- <span data-ttu-id="33251-214">UInt16</span><span class="sxs-lookup"><span data-stu-id="33251-214">UInt16</span></span>
- <span data-ttu-id="33251-215">UInt32</span><span class="sxs-lookup"><span data-stu-id="33251-215">UInt32</span></span>
- <span data-ttu-id="33251-216">UInt64</span><span class="sxs-lookup"><span data-stu-id="33251-216">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="33251-217">HITTA SPRÅK LÄGET FÖR EN SESSIONS KONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="33251-217">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="33251-218">När en sessions konfiguration skapas med hjälp av en konfigurations fil för en session, har sessionen en LanguageMode-egenskap.</span><span class="sxs-lookup"><span data-stu-id="33251-218">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="33251-219">Du kan hitta språk läget genom att hämta värdet för egenskapen LanguageMode.</span><span class="sxs-lookup"><span data-stu-id="33251-219">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="33251-220">I andra konfigurationer av sessioner kan du hitta språk läget indirekt genom att söka efter språk läge för en session som skapats med hjälp av konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="33251-220">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="33251-221">HITTA SPRÅK LÄGET FÖR EN SESSION</span><span class="sxs-lookup"><span data-stu-id="33251-221">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="33251-222">Du kan hitta språk läget för en FullLanguage-eller ConstrainedLanguage-session genom att hämta värdet för egenskapen LanguageMode för sessionens tillstånd.</span><span class="sxs-lookup"><span data-stu-id="33251-222">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="33251-223">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="33251-223">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="33251-224">I sessioner med RestrictedLanguage-och nolanguage-lägen kan du dock inte använda punkt metoden för att hämta egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="33251-224">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="33251-225">I stället visar fel meddelandet språk läge.</span><span class="sxs-lookup"><span data-stu-id="33251-225">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="33251-226">När du kör `$ExecutionContext.SessionState.LanguageMode` kommandot i en RestrictedLanguage-session returnerar PowerShell fel meddelandena PropertyReferenceNotSupportedInDataSection och VariableReferenceNotSupportedInDataSection.</span><span class="sxs-lookup"><span data-stu-id="33251-226">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="33251-227">PropertyReferenceNotSupportedInDataSection: egenskaps referenser är inte tillåtna i begränsat språk läge eller i ett data avsnitt.</span><span class="sxs-lookup"><span data-stu-id="33251-227">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="33251-228">VariableReferenceNotSupportedInDataSection en variabel som inte kan refereras till i begränsat språk läge eller ett data avsnitt som refereras till.</span><span class="sxs-lookup"><span data-stu-id="33251-228">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="33251-229">När du kör `$ExecutionContext.SessionState.LanguageMode` kommandot i en nolanguage-session, returnerar PowerShell fel meddelandet ScriptsNotAllowed.</span><span class="sxs-lookup"><span data-stu-id="33251-229">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="33251-230">ScriptsNotAllowed: syntaxen stöds inte av den här körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="33251-230">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="33251-231">Detta kan bero på att det inte är i något språk läge.</span><span class="sxs-lookup"><span data-stu-id="33251-231">This might be because it is in no-language mode.</span></span>

## <a name="keywords"></a><span data-ttu-id="33251-232">RESERVERADE</span><span class="sxs-lookup"><span data-stu-id="33251-232">KEYWORDS</span></span>

- <span data-ttu-id="33251-233">about_ConstrainedLanguage</span><span class="sxs-lookup"><span data-stu-id="33251-233">about_ConstrainedLanguage</span></span>
- <span data-ttu-id="33251-234">about_FullLanguage</span><span class="sxs-lookup"><span data-stu-id="33251-234">about_FullLanguage</span></span>
- <span data-ttu-id="33251-235">about_NoLanguage</span><span class="sxs-lookup"><span data-stu-id="33251-235">about_NoLanguage</span></span>
- <span data-ttu-id="33251-236">about_RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="33251-236">about_RestrictedLanguage</span></span>

## <a name="see-also"></a><span data-ttu-id="33251-237">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="33251-237">SEE ALSO</span></span>

- [<span data-ttu-id="33251-238">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="33251-238">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="33251-239">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="33251-239">about_Session_Configurations</span></span>](about_Session_Configurations.md)
