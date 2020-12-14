---
description: Förklarar språk lägen och deras inverkan på PowerShell-sessioner.
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 9e4b1ec2dd16d3442c553460ff217e7e0223f41f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708498"
---
# <a name="about-language-modes"></a><span data-ttu-id="ec135-103">Om språk lägen</span><span class="sxs-lookup"><span data-stu-id="ec135-103">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="ec135-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ec135-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ec135-105">Förklarar språk lägen och deras inverkan på PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="ec135-105">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="ec135-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ec135-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="ec135-107">Språk läget i en PowerShell-session bestämmer delvis vilka element i PowerShell-språket som kan användas i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ec135-107">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="ec135-108">PowerShell har stöd för följande språk lägen:</span><span class="sxs-lookup"><span data-stu-id="ec135-108">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="ec135-109">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="ec135-109">FullLanguage</span></span>
- <span data-ttu-id="ec135-110">ConstrainedLanguage (lanserades i PowerShell 3,0)</span><span class="sxs-lookup"><span data-stu-id="ec135-110">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="ec135-111">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="ec135-111">RestrictedLanguage</span></span>
- <span data-ttu-id="ec135-112">Inget språk</span><span class="sxs-lookup"><span data-stu-id="ec135-112">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="ec135-113">VAD ÄR ETT SPRÅK LÄGE?</span><span class="sxs-lookup"><span data-stu-id="ec135-113">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="ec135-114">Språk läget avgör vilka språk element som tillåts i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ec135-114">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="ec135-115">Språk läget är i själva verket en egenskap för den session konfiguration (eller "slut punkt") som används för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="ec135-115">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="ec135-116">Alla sessioner som använder en viss konfiguration av sessionen har språk läget i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="ec135-116">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="ec135-117">Alla PowerShell-sessioner har ett språk läge, inklusive PSSessions som du skapar med hjälp av `New-PSSession` cmdleten, tillfälliga sessioner som använder parametern ComputerName och de standardsessioner som visas när du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec135-117">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="ec135-118">Fjärrsessioner skapas med hjälp av sessionens konfigurationer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ec135-118">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="ec135-119">Språk läget som anges i konfigurationen bestämmer sessionens språkläge.</span><span class="sxs-lookup"><span data-stu-id="ec135-119">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="ec135-120">Om du vill ange PSSession för en använder du parametern ConfigurationName för cmdletar som skapar en session.</span><span class="sxs-lookup"><span data-stu-id="ec135-120">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="ec135-121">SPRÅK LÄGEN</span><span class="sxs-lookup"><span data-stu-id="ec135-121">LANGUAGE MODES</span></span>

<span data-ttu-id="ec135-122">I det här avsnittet beskrivs språk lägena i PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="ec135-122">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="ec135-123">FULLSTÄNDIGT språk (FullLanguage)</span><span class="sxs-lookup"><span data-stu-id="ec135-123">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="ec135-124">FullLanguage-läget tillåter alla språk element i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ec135-124">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="ec135-125">FullLanguage är standard språk läget för standardsessioner i alla versioner av Windows förutom Windows RT.</span><span class="sxs-lookup"><span data-stu-id="ec135-125">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="ec135-126">BEGRÄNSAT språk (RestrictedLanguage)</span><span class="sxs-lookup"><span data-stu-id="ec135-126">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="ec135-127">I RestrictedLanguage-läge kan användare köra kommandon (cmdlets, functions, CIM-kommandon och arbets flöden) men får inte använda skript block.</span><span class="sxs-lookup"><span data-stu-id="ec135-127">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="ec135-128">Som standard tillåts endast följande variabler i RestrictedLanguage-läge:</span><span class="sxs-lookup"><span data-stu-id="ec135-128">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="ec135-129">Modul manifest, som använder RestrictedLanguage-läge, tillåter även följande ytterligare variabler:</span><span class="sxs-lookup"><span data-stu-id="ec135-129">Module manifests, which use RestrictedLanguage mode, permit the following additional variables as well:</span></span>

- `$PSScriptRoot`
- <span data-ttu-id="ec135-130">`$PSEdition` (i PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="ec135-130">`$PSEdition` (in PowerShell Core)</span></span>
- <span data-ttu-id="ec135-131">`$EnabledExperimentalFeatures` (i PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="ec135-131">`$EnabledExperimentalFeatures` (in PowerShell Core)</span></span>

<span data-ttu-id="ec135-132">Endast följande jämförelse operatorer tillåts:</span><span class="sxs-lookup"><span data-stu-id="ec135-132">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="ec135-133">`-eq` Skeppningskvantiteten</span><span class="sxs-lookup"><span data-stu-id="ec135-133">`-eq` (equal)</span></span>
- <span data-ttu-id="ec135-134">`-gt` (större än)</span><span class="sxs-lookup"><span data-stu-id="ec135-134">`-gt` (greater-than)</span></span>
- <span data-ttu-id="ec135-135">`-lt` (mindre än)</span><span class="sxs-lookup"><span data-stu-id="ec135-135">`-lt` (less-than)</span></span>

<span data-ttu-id="ec135-136">Tilldelnings instruktioner, egenskaps referenser och metod anrop är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ec135-136">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="ec135-137">INGET språk (nolanguage)</span><span class="sxs-lookup"><span data-stu-id="ec135-137">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="ec135-138">Nospråks läge kan bara användas via API: et.</span><span class="sxs-lookup"><span data-stu-id="ec135-138">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="ec135-139">Nospråk läge innebär att ingen skript text för något formulär tillåts.</span><span class="sxs-lookup"><span data-stu-id="ec135-139">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="ec135-140">Detta utesluter användningen av metoden **AddScript ()** som skickar fragment av PowerShell-skript för att parsas och köras.</span><span class="sxs-lookup"><span data-stu-id="ec135-140">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="ec135-141">Du kan bara använda **AddCommand ()** och **AddParameter ()** som inte går igenom parsern.</span><span class="sxs-lookup"><span data-stu-id="ec135-141">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="ec135-142">BEGRÄNSAT språk (begränsat språk)</span><span class="sxs-lookup"><span data-stu-id="ec135-142">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="ec135-143">ConstrainedLanguage-läget tillåter alla cmdletar och alla PowerShell-språkelement, men det begränsar tillåtna typer.</span><span class="sxs-lookup"><span data-stu-id="ec135-143">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="ec135-144">ConstrainedLanguage-läget har utformats för att stödja kod integritet i användarläge (UMCI) på Windows RT.</span><span class="sxs-lookup"><span data-stu-id="ec135-144">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="ec135-145">Det är det enda språk läge som stöds i Windows RT, men det är tillgängligt i alla system som stöds.</span><span class="sxs-lookup"><span data-stu-id="ec135-145">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="ec135-146">UMCI skyddar ARM-enheter genom att bara tillåta att Microsoft-signerade och Microsoft-certifierade appar installeras på Windows RT-baserade enheter.</span><span class="sxs-lookup"><span data-stu-id="ec135-146">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="ec135-147">ConstrainedLanguage-läget hindrar användare från att använda PowerShell för att kringgå eller bryta mot UMCI.</span><span class="sxs-lookup"><span data-stu-id="ec135-147">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="ec135-148">Funktionerna i ConstrainedLanguage-läge är följande:</span><span class="sxs-lookup"><span data-stu-id="ec135-148">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="ec135-149">Alla cmdletar i Windows-moduler och andra UMCI-godkända cmdlets är fullt funktionella och har fullständig åtkomst till system resurser, förutom vad som anges.</span><span class="sxs-lookup"><span data-stu-id="ec135-149">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="ec135-150">Alla element i PowerShell-skript språket är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ec135-150">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="ec135-151">Alla moduler som ingår i Windows kan importeras och alla kommandon som modulerna exporterar körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ec135-151">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="ec135-152">I PowerShell-arbetsflöde kan du skriva och köra skript arbets flöden (arbets flöden skrivna i PowerShell-språket).</span><span class="sxs-lookup"><span data-stu-id="ec135-152">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="ec135-153">XAML-baserade arbets flöden stöds inte och du kan inte köra XAML i ett skript arbets flöde, till exempel med hjälp av `Invoke-Expression -Language XAML` .</span><span class="sxs-lookup"><span data-stu-id="ec135-153">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="ec135-154">Arbets flöden kan heller inte anropa andra arbets flöden, även om kapslade arbets flöden tillåts.</span><span class="sxs-lookup"><span data-stu-id="ec135-154">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="ec135-155">`Add-Type`Cmdleten kan läsa in signerade sammansättningar, men det går inte att läsa in godtycklig C#-kod eller Win32-API: er.</span><span class="sxs-lookup"><span data-stu-id="ec135-155">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="ec135-156">`New-Object`Cmdleten kan endast användas för tillåtna typer (visas nedan).</span><span class="sxs-lookup"><span data-stu-id="ec135-156">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="ec135-157">Endast tillåtna typer (listade nedan) kan användas i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec135-157">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="ec135-158">Andra typer är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ec135-158">Other types are not permitted.</span></span>

- <span data-ttu-id="ec135-159">Typ konvertering tillåts, men endast om resultatet är en tillåten typ.</span><span class="sxs-lookup"><span data-stu-id="ec135-159">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="ec135-160">Cmdlet-parametrar som konverterar inmatade strängar till typer fungerar endast när den resulterande typen är en tillåten typ.</span><span class="sxs-lookup"><span data-stu-id="ec135-160">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="ec135-161">Metoden **toString ()** och .net-metoderna för tillåtna typer (listas nedan) kan anropas.</span><span class="sxs-lookup"><span data-stu-id="ec135-161">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="ec135-162">Det går inte att anropa andra metoder.</span><span class="sxs-lookup"><span data-stu-id="ec135-162">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="ec135-163">Användare kan hämta alla egenskaper av tillåtna typer.</span><span class="sxs-lookup"><span data-stu-id="ec135-163">Users can get all properties of allowed types.</span></span> <span data-ttu-id="ec135-164">Användare kan bara ange värden för egenskaper för kärn typer.</span><span class="sxs-lookup"><span data-stu-id="ec135-164">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="ec135-165">Endast följande COM-objekt tillåts:</span><span class="sxs-lookup"><span data-stu-id="ec135-165">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="ec135-166">**Skript. ord lista**</span><span class="sxs-lookup"><span data-stu-id="ec135-166">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="ec135-167">**Scripting. FileSystemObject**</span><span class="sxs-lookup"><span data-stu-id="ec135-167">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="ec135-168">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="ec135-168">**VBScript.RegExp**</span></span>

<span data-ttu-id="ec135-169">Följande typer tillåts i ConstrainedLanguage-läge.</span><span class="sxs-lookup"><span data-stu-id="ec135-169">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="ec135-170">Användare kan få egenskaper, anropa metoder och konvertera objekt till de här typerna.</span><span class="sxs-lookup"><span data-stu-id="ec135-170">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="ec135-171">Tillåtna typer:</span><span class="sxs-lookup"><span data-stu-id="ec135-171">Allowed Types:</span></span>

- <span data-ttu-id="ec135-172">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-172">AliasAttribute</span></span>
- <span data-ttu-id="ec135-173">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-173">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="ec135-174">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-174">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="ec135-175">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-175">AllowNullAttribute</span></span>
- <span data-ttu-id="ec135-176">Matris</span><span class="sxs-lookup"><span data-stu-id="ec135-176">Array</span></span>
- <span data-ttu-id="ec135-177">Bool</span><span class="sxs-lookup"><span data-stu-id="ec135-177">Bool</span></span>
- <span data-ttu-id="ec135-178">stor</span><span class="sxs-lookup"><span data-stu-id="ec135-178">byte</span></span>
- <span data-ttu-id="ec135-179">char</span><span class="sxs-lookup"><span data-stu-id="ec135-179">char</span></span>
- <span data-ttu-id="ec135-180">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-180">CmdletBindingAttribute</span></span>
- <span data-ttu-id="ec135-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="ec135-181">DateTime</span></span>
- <span data-ttu-id="ec135-182">decimal</span><span class="sxs-lookup"><span data-stu-id="ec135-182">decimal</span></span>
- <span data-ttu-id="ec135-183">DirectoryEntry</span><span class="sxs-lookup"><span data-stu-id="ec135-183">DirectoryEntry</span></span>
- <span data-ttu-id="ec135-184">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="ec135-184">DirectorySearcher</span></span>
- <span data-ttu-id="ec135-185">double</span><span class="sxs-lookup"><span data-stu-id="ec135-185">double</span></span>
- <span data-ttu-id="ec135-186">flyt</span><span class="sxs-lookup"><span data-stu-id="ec135-186">float</span></span>
- <span data-ttu-id="ec135-187">GUID</span><span class="sxs-lookup"><span data-stu-id="ec135-187">Guid</span></span>
- <span data-ttu-id="ec135-188">Hash</span><span class="sxs-lookup"><span data-stu-id="ec135-188">Hashtable</span></span>
- <span data-ttu-id="ec135-189">int</span><span class="sxs-lookup"><span data-stu-id="ec135-189">int</span></span>
- <span data-ttu-id="ec135-190">Int16</span><span class="sxs-lookup"><span data-stu-id="ec135-190">Int16</span></span>
- <span data-ttu-id="ec135-191">long</span><span class="sxs-lookup"><span data-stu-id="ec135-191">long</span></span>
- <span data-ttu-id="ec135-192">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="ec135-192">ManagementClass</span></span>
- <span data-ttu-id="ec135-193">ManagementObject</span><span class="sxs-lookup"><span data-stu-id="ec135-193">ManagementObject</span></span>
- <span data-ttu-id="ec135-194">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="ec135-194">ManagementObjectSearcher</span></span>
- <span data-ttu-id="ec135-195">NullString</span><span class="sxs-lookup"><span data-stu-id="ec135-195">NullString</span></span>
- <span data-ttu-id="ec135-196">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-196">OutputTypeAttribute</span></span>
- <span data-ttu-id="ec135-197">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-197">ParameterAttribute</span></span>
- <span data-ttu-id="ec135-198">PSCredential</span><span class="sxs-lookup"><span data-stu-id="ec135-198">PSCredential</span></span>
- <span data-ttu-id="ec135-199">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-199">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="ec135-200">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="ec135-200">PSListModifier</span></span>
- <span data-ttu-id="ec135-201">PSObject</span><span class="sxs-lookup"><span data-stu-id="ec135-201">PSObject</span></span>
- <span data-ttu-id="ec135-202">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="ec135-202">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="ec135-203">PSReference</span><span class="sxs-lookup"><span data-stu-id="ec135-203">PSReference</span></span>
- <span data-ttu-id="ec135-204">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-204">PSTypeNameAttribute</span></span>
- <span data-ttu-id="ec135-205">Verifiering</span><span class="sxs-lookup"><span data-stu-id="ec135-205">Regex</span></span>
- <span data-ttu-id="ec135-206">SByte</span><span class="sxs-lookup"><span data-stu-id="ec135-206">SByte</span></span>
- <span data-ttu-id="ec135-207">sträng</span><span class="sxs-lookup"><span data-stu-id="ec135-207">string</span></span>
- <span data-ttu-id="ec135-208">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="ec135-208">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="ec135-209">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="ec135-209">SwitchParameter</span></span>
- <span data-ttu-id="ec135-210">System. globalisering. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="ec135-210">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="ec135-211">System .net. IPAddress</span><span class="sxs-lookup"><span data-stu-id="ec135-211">System.Net.IPAddress</span></span>
- <span data-ttu-id="ec135-212">System .net. mail. mail-adress</span><span class="sxs-lookup"><span data-stu-id="ec135-212">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="ec135-213">System. Numerics. BigInteger</span><span class="sxs-lookup"><span data-stu-id="ec135-213">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="ec135-214">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="ec135-214">System.Security.SecureString</span></span>
- <span data-ttu-id="ec135-215">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="ec135-215">TimeSpan</span></span>
- <span data-ttu-id="ec135-216">UInt16</span><span class="sxs-lookup"><span data-stu-id="ec135-216">UInt16</span></span>
- <span data-ttu-id="ec135-217">UInt32</span><span class="sxs-lookup"><span data-stu-id="ec135-217">UInt32</span></span>
- <span data-ttu-id="ec135-218">UInt64</span><span class="sxs-lookup"><span data-stu-id="ec135-218">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="ec135-219">HITTA SPRÅK LÄGET FÖR EN SESSIONS KONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="ec135-219">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="ec135-220">När en sessions konfiguration skapas med hjälp av en konfigurations fil för en session, har sessionen en LanguageMode-egenskap.</span><span class="sxs-lookup"><span data-stu-id="ec135-220">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="ec135-221">Du kan hitta språk läget genom att hämta värdet för egenskapen LanguageMode.</span><span class="sxs-lookup"><span data-stu-id="ec135-221">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="ec135-222">I andra konfigurationer av sessioner kan du hitta språk läget indirekt genom att söka efter språk läge för en session som skapats med hjälp av konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="ec135-222">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="ec135-223">HITTA SPRÅK LÄGET FÖR EN SESSION</span><span class="sxs-lookup"><span data-stu-id="ec135-223">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="ec135-224">Du kan hitta språk läget för en FullLanguage-eller ConstrainedLanguage-session genom att hämta värdet för egenskapen LanguageMode för sessionens tillstånd.</span><span class="sxs-lookup"><span data-stu-id="ec135-224">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="ec135-225">Exempel:</span><span class="sxs-lookup"><span data-stu-id="ec135-225">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="ec135-226">I sessioner med RestrictedLanguage-och nolanguage-lägen kan du dock inte använda punkt metoden för att hämta egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="ec135-226">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="ec135-227">I stället visar fel meddelandet språk läge.</span><span class="sxs-lookup"><span data-stu-id="ec135-227">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="ec135-228">När du kör `$ExecutionContext.SessionState.LanguageMode` kommandot i en RestrictedLanguage-session returnerar PowerShell fel meddelandena PropertyReferenceNotSupportedInDataSection och VariableReferenceNotSupportedInDataSection.</span><span class="sxs-lookup"><span data-stu-id="ec135-228">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="ec135-229">PropertyReferenceNotSupportedInDataSection: egenskaps referenser är inte tillåtna i begränsat språk läge eller i ett data avsnitt.</span><span class="sxs-lookup"><span data-stu-id="ec135-229">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="ec135-230">VariableReferenceNotSupportedInDataSection en variabel som inte kan refereras till i begränsat språk läge eller ett data avsnitt som refereras till.</span><span class="sxs-lookup"><span data-stu-id="ec135-230">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="ec135-231">När du kör `$ExecutionContext.SessionState.LanguageMode` kommandot i en nolanguage-session, returnerar PowerShell fel meddelandet ScriptsNotAllowed.</span><span class="sxs-lookup"><span data-stu-id="ec135-231">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="ec135-232">ScriptsNotAllowed: syntaxen stöds inte av den här körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="ec135-232">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="ec135-233">Detta kan bero på att det inte är i något språk läge.</span><span class="sxs-lookup"><span data-stu-id="ec135-233">This might be because it is in no-language mode.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec135-234">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="ec135-234">SEE ALSO</span></span>

- [<span data-ttu-id="ec135-235">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="ec135-235">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="ec135-236">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="ec135-236">about_Session_Configurations</span></span>](about_Session_Configurations.md)
