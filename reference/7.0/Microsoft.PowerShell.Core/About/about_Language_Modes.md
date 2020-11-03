---
description: Förklarar språk lägen och deras inverkan på PowerShell-sessioner.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: c560101dd70c94c131e3ca9d8e9958d3a278de40
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271184"
---
# <a name="about-language-modes"></a><span data-ttu-id="83132-104">Om språk lägen</span><span class="sxs-lookup"><span data-stu-id="83132-104">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="83132-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="83132-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="83132-106">Förklarar språk lägen och deras inverkan på PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="83132-106">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="83132-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="83132-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="83132-108">Språk läget i en PowerShell-session bestämmer delvis vilka element i PowerShell-språket som kan användas i sessionen.</span><span class="sxs-lookup"><span data-stu-id="83132-108">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="83132-109">PowerShell har stöd för följande språk lägen:</span><span class="sxs-lookup"><span data-stu-id="83132-109">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="83132-110">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="83132-110">FullLanguage</span></span>
- <span data-ttu-id="83132-111">ConstrainedLanguage (lanserades i PowerShell 3,0)</span><span class="sxs-lookup"><span data-stu-id="83132-111">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="83132-112">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="83132-112">RestrictedLanguage</span></span>
- <span data-ttu-id="83132-113">Inget språk</span><span class="sxs-lookup"><span data-stu-id="83132-113">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="83132-114">VAD ÄR ETT SPRÅK LÄGE?</span><span class="sxs-lookup"><span data-stu-id="83132-114">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="83132-115">Språk läget avgör vilka språk element som tillåts i sessionen.</span><span class="sxs-lookup"><span data-stu-id="83132-115">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="83132-116">Språk läget är i själva verket en egenskap för den session konfiguration (eller "slut punkt") som används för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="83132-116">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="83132-117">Alla sessioner som använder en viss konfiguration av sessionen har språk läget i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="83132-117">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="83132-118">Alla PowerShell-sessioner har ett språk läge, inklusive PSSessions som du skapar med hjälp av `New-PSSession` cmdleten, tillfälliga sessioner som använder parametern ComputerName och de standardsessioner som visas när du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83132-118">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="83132-119">Fjärrsessioner skapas med hjälp av sessionens konfigurationer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="83132-119">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="83132-120">Språk läget som anges i konfigurationen bestämmer sessionens språkläge.</span><span class="sxs-lookup"><span data-stu-id="83132-120">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="83132-121">Om du vill ange PSSession för en använder du parametern ConfigurationName för cmdletar som skapar en session.</span><span class="sxs-lookup"><span data-stu-id="83132-121">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="83132-122">SPRÅK LÄGEN</span><span class="sxs-lookup"><span data-stu-id="83132-122">LANGUAGE MODES</span></span>

<span data-ttu-id="83132-123">I det här avsnittet beskrivs språk lägena i PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="83132-123">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="83132-124">FULLSTÄNDIGT språk (FullLanguage)</span><span class="sxs-lookup"><span data-stu-id="83132-124">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="83132-125">FullLanguage-läget tillåter alla språk element i sessionen.</span><span class="sxs-lookup"><span data-stu-id="83132-125">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="83132-126">FullLanguage är standard språk läget för standardsessioner i alla versioner av Windows förutom Windows RT.</span><span class="sxs-lookup"><span data-stu-id="83132-126">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="83132-127">BEGRÄNSAT språk (RestrictedLanguage)</span><span class="sxs-lookup"><span data-stu-id="83132-127">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="83132-128">I RestrictedLanguage-läge kan användare köra kommandon (cmdlets, functions, CIM-kommandon och arbets flöden) men får inte använda skript block.</span><span class="sxs-lookup"><span data-stu-id="83132-128">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="83132-129">Som standard tillåts endast följande variabler i RestrictedLanguage-läge:</span><span class="sxs-lookup"><span data-stu-id="83132-129">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="83132-130">Modul manifest, som använder RestrictedLanguage-läge, tillåter även följande ytterligare variabler:</span><span class="sxs-lookup"><span data-stu-id="83132-130">Module manifests, which use RestrictedLanguage mode, permit the following additional variables as well:</span></span>

- `$PSScriptRoot`
- <span data-ttu-id="83132-131">`$PSEdition` (i PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="83132-131">`$PSEdition` (in PowerShell Core)</span></span>
- <span data-ttu-id="83132-132">`$EnabledExperimentalFeatures` (i PowerShell Core)</span><span class="sxs-lookup"><span data-stu-id="83132-132">`$EnabledExperimentalFeatures` (in PowerShell Core)</span></span>

<span data-ttu-id="83132-133">Endast följande jämförelse operatorer tillåts:</span><span class="sxs-lookup"><span data-stu-id="83132-133">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="83132-134">`-eq` Skeppningskvantiteten</span><span class="sxs-lookup"><span data-stu-id="83132-134">`-eq` (equal)</span></span>
- <span data-ttu-id="83132-135">`-gt` (större än)</span><span class="sxs-lookup"><span data-stu-id="83132-135">`-gt` (greater-than)</span></span>
- <span data-ttu-id="83132-136">`-lt` (mindre än)</span><span class="sxs-lookup"><span data-stu-id="83132-136">`-lt` (less-than)</span></span>

<span data-ttu-id="83132-137">Tilldelnings instruktioner, egenskaps referenser och metod anrop är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="83132-137">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="83132-138">INGET språk (nolanguage)</span><span class="sxs-lookup"><span data-stu-id="83132-138">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="83132-139">Nospråks läge kan bara användas via API: et.</span><span class="sxs-lookup"><span data-stu-id="83132-139">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="83132-140">Nospråk läge innebär att ingen skript text för något formulär tillåts.</span><span class="sxs-lookup"><span data-stu-id="83132-140">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="83132-141">Detta utesluter användningen av metoden **AddScript ()** som skickar fragment av PowerShell-skript för att parsas och köras.</span><span class="sxs-lookup"><span data-stu-id="83132-141">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="83132-142">Du kan bara använda **AddCommand ()** och **AddParameter ()** som inte går igenom parsern.</span><span class="sxs-lookup"><span data-stu-id="83132-142">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="83132-143">BEGRÄNSAT språk (begränsat språk)</span><span class="sxs-lookup"><span data-stu-id="83132-143">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="83132-144">ConstrainedLanguage-läget tillåter alla cmdletar och alla PowerShell-språkelement, men det begränsar tillåtna typer.</span><span class="sxs-lookup"><span data-stu-id="83132-144">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="83132-145">ConstrainedLanguage-läget har utformats för att stödja kod integritet i användarläge (UMCI) på Windows RT.</span><span class="sxs-lookup"><span data-stu-id="83132-145">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="83132-146">Det är det enda språk läge som stöds i Windows RT, men det är tillgängligt i alla system som stöds.</span><span class="sxs-lookup"><span data-stu-id="83132-146">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="83132-147">UMCI skyddar ARM-enheter genom att bara tillåta att Microsoft-signerade och Microsoft-certifierade appar installeras på Windows RT-baserade enheter.</span><span class="sxs-lookup"><span data-stu-id="83132-147">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="83132-148">ConstrainedLanguage-läget hindrar användare från att använda PowerShell för att kringgå eller bryta mot UMCI.</span><span class="sxs-lookup"><span data-stu-id="83132-148">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="83132-149">Funktionerna i ConstrainedLanguage-läge är följande:</span><span class="sxs-lookup"><span data-stu-id="83132-149">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="83132-150">Alla cmdletar i Windows-moduler och andra UMCI-godkända cmdlets är fullt funktionella och har fullständig åtkomst till system resurser, förutom vad som anges.</span><span class="sxs-lookup"><span data-stu-id="83132-150">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="83132-151">Alla element i PowerShell-skript språket är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="83132-151">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="83132-152">Alla moduler som ingår i Windows kan importeras och alla kommandon som modulerna exporterar körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="83132-152">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="83132-153">I PowerShell-arbetsflöde kan du skriva och köra skript arbets flöden (arbets flöden skrivna i PowerShell-språket).</span><span class="sxs-lookup"><span data-stu-id="83132-153">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="83132-154">XAML-baserade arbets flöden stöds inte och du kan inte köra XAML i ett skript arbets flöde, till exempel med hjälp av `Invoke-Expression -Language XAML` .</span><span class="sxs-lookup"><span data-stu-id="83132-154">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="83132-155">Arbets flöden kan heller inte anropa andra arbets flöden, även om kapslade arbets flöden tillåts.</span><span class="sxs-lookup"><span data-stu-id="83132-155">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="83132-156">`Add-Type`Cmdleten kan läsa in signerade sammansättningar, men det går inte att läsa in godtycklig C#-kod eller Win32-API: er.</span><span class="sxs-lookup"><span data-stu-id="83132-156">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="83132-157">`New-Object`Cmdleten kan endast användas för tillåtna typer (visas nedan).</span><span class="sxs-lookup"><span data-stu-id="83132-157">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="83132-158">Endast tillåtna typer (listade nedan) kan användas i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83132-158">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="83132-159">Andra typer är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="83132-159">Other types are not permitted.</span></span>

- <span data-ttu-id="83132-160">Typ konvertering tillåts, men endast om resultatet är en tillåten typ.</span><span class="sxs-lookup"><span data-stu-id="83132-160">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="83132-161">Cmdlet-parametrar som konverterar inmatade strängar till typer fungerar endast när den resulterande typen är en tillåten typ.</span><span class="sxs-lookup"><span data-stu-id="83132-161">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="83132-162">Metoden **toString ()** och .net-metoderna för tillåtna typer (listas nedan) kan anropas.</span><span class="sxs-lookup"><span data-stu-id="83132-162">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="83132-163">Det går inte att anropa andra metoder.</span><span class="sxs-lookup"><span data-stu-id="83132-163">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="83132-164">Användare kan hämta alla egenskaper av tillåtna typer.</span><span class="sxs-lookup"><span data-stu-id="83132-164">Users can get all properties of allowed types.</span></span> <span data-ttu-id="83132-165">Användare kan bara ange värden för egenskaper för kärn typer.</span><span class="sxs-lookup"><span data-stu-id="83132-165">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="83132-166">Endast följande COM-objekt tillåts:</span><span class="sxs-lookup"><span data-stu-id="83132-166">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="83132-167">**Skript. ord lista**</span><span class="sxs-lookup"><span data-stu-id="83132-167">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="83132-168">**Scripting. FileSystemObject**</span><span class="sxs-lookup"><span data-stu-id="83132-168">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="83132-169">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="83132-169">**VBScript.RegExp**</span></span>

<span data-ttu-id="83132-170">Följande typer tillåts i ConstrainedLanguage-läge.</span><span class="sxs-lookup"><span data-stu-id="83132-170">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="83132-171">Användare kan få egenskaper, anropa metoder och konvertera objekt till de här typerna.</span><span class="sxs-lookup"><span data-stu-id="83132-171">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="83132-172">Tillåtna typer:</span><span class="sxs-lookup"><span data-stu-id="83132-172">Allowed Types:</span></span>

- <span data-ttu-id="83132-173">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-173">AliasAttribute</span></span>
- <span data-ttu-id="83132-174">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-174">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="83132-175">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-175">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="83132-176">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-176">AllowNullAttribute</span></span>
- <span data-ttu-id="83132-177">Matris</span><span class="sxs-lookup"><span data-stu-id="83132-177">Array</span></span>
- <span data-ttu-id="83132-178">Bool</span><span class="sxs-lookup"><span data-stu-id="83132-178">Bool</span></span>
- <span data-ttu-id="83132-179">stor</span><span class="sxs-lookup"><span data-stu-id="83132-179">byte</span></span>
- <span data-ttu-id="83132-180">char</span><span class="sxs-lookup"><span data-stu-id="83132-180">char</span></span>
- <span data-ttu-id="83132-181">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-181">CmdletBindingAttribute</span></span>
- <span data-ttu-id="83132-182">DateTime</span><span class="sxs-lookup"><span data-stu-id="83132-182">DateTime</span></span>
- <span data-ttu-id="83132-183">decimal</span><span class="sxs-lookup"><span data-stu-id="83132-183">decimal</span></span>
- <span data-ttu-id="83132-184">DirectoryEntry</span><span class="sxs-lookup"><span data-stu-id="83132-184">DirectoryEntry</span></span>
- <span data-ttu-id="83132-185">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="83132-185">DirectorySearcher</span></span>
- <span data-ttu-id="83132-186">double</span><span class="sxs-lookup"><span data-stu-id="83132-186">double</span></span>
- <span data-ttu-id="83132-187">flyt</span><span class="sxs-lookup"><span data-stu-id="83132-187">float</span></span>
- <span data-ttu-id="83132-188">GUID</span><span class="sxs-lookup"><span data-stu-id="83132-188">Guid</span></span>
- <span data-ttu-id="83132-189">Hash</span><span class="sxs-lookup"><span data-stu-id="83132-189">Hashtable</span></span>
- <span data-ttu-id="83132-190">int</span><span class="sxs-lookup"><span data-stu-id="83132-190">int</span></span>
- <span data-ttu-id="83132-191">Int16</span><span class="sxs-lookup"><span data-stu-id="83132-191">Int16</span></span>
- <span data-ttu-id="83132-192">long</span><span class="sxs-lookup"><span data-stu-id="83132-192">long</span></span>
- <span data-ttu-id="83132-193">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="83132-193">ManagementClass</span></span>
- <span data-ttu-id="83132-194">ManagementObject</span><span class="sxs-lookup"><span data-stu-id="83132-194">ManagementObject</span></span>
- <span data-ttu-id="83132-195">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="83132-195">ManagementObjectSearcher</span></span>
- <span data-ttu-id="83132-196">NullString</span><span class="sxs-lookup"><span data-stu-id="83132-196">NullString</span></span>
- <span data-ttu-id="83132-197">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-197">OutputTypeAttribute</span></span>
- <span data-ttu-id="83132-198">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-198">ParameterAttribute</span></span>
- <span data-ttu-id="83132-199">PSCredential</span><span class="sxs-lookup"><span data-stu-id="83132-199">PSCredential</span></span>
- <span data-ttu-id="83132-200">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-200">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="83132-201">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="83132-201">PSListModifier</span></span>
- <span data-ttu-id="83132-202">PSObject</span><span class="sxs-lookup"><span data-stu-id="83132-202">PSObject</span></span>
- <span data-ttu-id="83132-203">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="83132-203">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="83132-204">PSReference</span><span class="sxs-lookup"><span data-stu-id="83132-204">PSReference</span></span>
- <span data-ttu-id="83132-205">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-205">PSTypeNameAttribute</span></span>
- <span data-ttu-id="83132-206">Verifiering</span><span class="sxs-lookup"><span data-stu-id="83132-206">Regex</span></span>
- <span data-ttu-id="83132-207">SByte</span><span class="sxs-lookup"><span data-stu-id="83132-207">SByte</span></span>
- <span data-ttu-id="83132-208">sträng</span><span class="sxs-lookup"><span data-stu-id="83132-208">string</span></span>
- <span data-ttu-id="83132-209">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="83132-209">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="83132-210">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="83132-210">SwitchParameter</span></span>
- <span data-ttu-id="83132-211">System. globalisering. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="83132-211">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="83132-212">System .net. IPAddress</span><span class="sxs-lookup"><span data-stu-id="83132-212">System.Net.IPAddress</span></span>
- <span data-ttu-id="83132-213">System .net. mail. mail-adress</span><span class="sxs-lookup"><span data-stu-id="83132-213">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="83132-214">System. Numerics. BigInteger</span><span class="sxs-lookup"><span data-stu-id="83132-214">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="83132-215">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="83132-215">System.Security.SecureString</span></span>
- <span data-ttu-id="83132-216">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="83132-216">TimeSpan</span></span>
- <span data-ttu-id="83132-217">UInt16</span><span class="sxs-lookup"><span data-stu-id="83132-217">UInt16</span></span>
- <span data-ttu-id="83132-218">UInt32</span><span class="sxs-lookup"><span data-stu-id="83132-218">UInt32</span></span>
- <span data-ttu-id="83132-219">UInt64</span><span class="sxs-lookup"><span data-stu-id="83132-219">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="83132-220">HITTA SPRÅK LÄGET FÖR EN SESSIONS KONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="83132-220">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="83132-221">När en sessions konfiguration skapas med hjälp av en konfigurations fil för en session, har sessionen en LanguageMode-egenskap.</span><span class="sxs-lookup"><span data-stu-id="83132-221">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="83132-222">Du kan hitta språk läget genom att hämta värdet för egenskapen LanguageMode.</span><span class="sxs-lookup"><span data-stu-id="83132-222">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="83132-223">I andra konfigurationer av sessioner kan du hitta språk läget indirekt genom att söka efter språk läge för en session som skapats med hjälp av konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="83132-223">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="83132-224">HITTA SPRÅK LÄGET FÖR EN SESSION</span><span class="sxs-lookup"><span data-stu-id="83132-224">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="83132-225">Du kan hitta språk läget för en FullLanguage-eller ConstrainedLanguage-session genom att hämta värdet för egenskapen LanguageMode för sessionens tillstånd.</span><span class="sxs-lookup"><span data-stu-id="83132-225">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="83132-226">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="83132-226">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="83132-227">I sessioner med RestrictedLanguage-och nolanguage-lägen kan du dock inte använda punkt metoden för att hämta egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="83132-227">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="83132-228">I stället visar fel meddelandet språk läge.</span><span class="sxs-lookup"><span data-stu-id="83132-228">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="83132-229">När du kör `$ExecutionContext.SessionState.LanguageMode` kommandot i en RestrictedLanguage-session returnerar PowerShell fel meddelandena PropertyReferenceNotSupportedInDataSection och VariableReferenceNotSupportedInDataSection.</span><span class="sxs-lookup"><span data-stu-id="83132-229">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="83132-230">PropertyReferenceNotSupportedInDataSection: egenskaps referenser är inte tillåtna i begränsat språk läge eller i ett data avsnitt.</span><span class="sxs-lookup"><span data-stu-id="83132-230">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="83132-231">VariableReferenceNotSupportedInDataSection en variabel som inte kan refereras till i begränsat språk läge eller ett data avsnitt som refereras till.</span><span class="sxs-lookup"><span data-stu-id="83132-231">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="83132-232">När du kör `$ExecutionContext.SessionState.LanguageMode` kommandot i en nolanguage-session, returnerar PowerShell fel meddelandet ScriptsNotAllowed.</span><span class="sxs-lookup"><span data-stu-id="83132-232">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="83132-233">ScriptsNotAllowed: syntaxen stöds inte av den här körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="83132-233">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="83132-234">Detta kan bero på att det inte är i något språk läge.</span><span class="sxs-lookup"><span data-stu-id="83132-234">This might be because it is in no-language mode.</span></span>

## <a name="keywords"></a><span data-ttu-id="83132-235">RESERVERADE</span><span class="sxs-lookup"><span data-stu-id="83132-235">KEYWORDS</span></span>

- <span data-ttu-id="83132-236">about_ConstrainedLanguage</span><span class="sxs-lookup"><span data-stu-id="83132-236">about_ConstrainedLanguage</span></span>
- <span data-ttu-id="83132-237">about_FullLanguage</span><span class="sxs-lookup"><span data-stu-id="83132-237">about_FullLanguage</span></span>
- <span data-ttu-id="83132-238">about_NoLanguage</span><span class="sxs-lookup"><span data-stu-id="83132-238">about_NoLanguage</span></span>
- <span data-ttu-id="83132-239">about_RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="83132-239">about_RestrictedLanguage</span></span>

## <a name="see-also"></a><span data-ttu-id="83132-240">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="83132-240">SEE ALSO</span></span>

- [<span data-ttu-id="83132-241">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="83132-241">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="83132-242">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="83132-242">about_Session_Configurations</span></span>](about_Session_Configurations.md)
