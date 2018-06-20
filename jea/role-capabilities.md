---
ms.date: 06/12/2017
keywords: jea powershell säkerhet
title: JEA roll funktioner
ms.openlocfilehash: 0531baa284e66a42a162329ea20ecfdca6d0b526
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190544"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="d4b47-103">JEA roll funktioner</span><span class="sxs-lookup"><span data-stu-id="d4b47-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="d4b47-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d4b47-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d4b47-105">När du skapar en JEA slutpunkt, behöver du definiera minst en ”roll funktioner” som beskriver *vad* någon kan göra i en JEA-session.</span><span class="sxs-lookup"><span data-stu-id="d4b47-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="d4b47-106">En roll-funktion är en fil med filnamnstillägget .psrc med en lista över alla cmdlets, funktioner, leverantörer och externa program som ska göras tillgängliga för att ansluta användare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4b47-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="d4b47-107">Det här avsnittet beskriver hur du skapar en fil PowerShell rollen kapaciteten för användarnas JEA.</span><span class="sxs-lookup"><span data-stu-id="d4b47-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="d4b47-108">Bestämma vilka kommandon för att tillåta</span><span class="sxs-lookup"><span data-stu-id="d4b47-108">Determine which commands to allow</span></span>

<span data-ttu-id="d4b47-109">Det första steget när du skapar en roll kapaciteten fil är att tänka på vad de användare som har tilldelats rollen behöver åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="d4b47-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="d4b47-110">Detta krav Insamlingsprocessen kan ta en stund, men det är mycket viktigt att.</span><span class="sxs-lookup"><span data-stu-id="d4b47-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="d4b47-111">Ge användare åtkomst till för få cmdletar och funktioner kan hindra dem från att få sitt jobb.</span><span class="sxs-lookup"><span data-stu-id="d4b47-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="d4b47-112">Att tillåta åtkomst till för många cmdletar och funktioner kan leda till användare göra mer än du tänkt med deras implicit administratörsrättigheter minskad säkerhet-behöver.</span><span class="sxs-lookup"><span data-stu-id="d4b47-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="d4b47-113">Hur du går om den här processen beror på din organisation och mål, men följande tips kan hjälpa dig att se till att du är på rätt väg.</span><span class="sxs-lookup"><span data-stu-id="d4b47-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="d4b47-114">**Identifiera** kommandon användare använder för att jobbet.</span><span class="sxs-lookup"><span data-stu-id="d4b47-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="d4b47-115">Detta kan innebära prospektering av IT-personal, kontrollerar automatiseringsskript eller analysera loggarna eller PowerShell-session betyg.</span><span class="sxs-lookup"><span data-stu-id="d4b47-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="d4b47-116">**Uppdatera** använder kommandoradsverktyg till PowerShell-motsvarighet, där det är möjligt, för bästa gransknings- och JEA anpassning upplevelse.</span><span class="sxs-lookup"><span data-stu-id="d4b47-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="d4b47-117">Externa program kan inte begränsas som granularly som ursprunglig PowerShell-cmdletar och funktioner i JEA.</span><span class="sxs-lookup"><span data-stu-id="d4b47-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="d4b47-118">**Begränsa** omfattning cmdlets om nödvändigt att endast tillåta att specifika parametrar eller parametervärden.</span><span class="sxs-lookup"><span data-stu-id="d4b47-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="d4b47-119">Detta är särskilt viktigt om användare bara ska kunna hantera en del av ett system.</span><span class="sxs-lookup"><span data-stu-id="d4b47-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="d4b47-120">**Skapa** anpassade funktioner att ersätta komplexa kommandon eller kommandon som är svåra att begränsa i JEA.</span><span class="sxs-lookup"><span data-stu-id="d4b47-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="d4b47-121">En enkel funktion som omsluter kommandot komplexa eller tillämpar logik för ytterligare verifiering kan erbjuda ytterligare kontroll för enkelhetens skull administratörer och slutanvändare.</span><span class="sxs-lookup"><span data-stu-id="d4b47-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="d4b47-122">**Testa** begränsade listan över tillåtna kommandon med användare och/eller automation services och justera vid behov.</span><span class="sxs-lookup"><span data-stu-id="d4b47-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="d4b47-123">Det är viktigt att komma ihåg att kommandona i en session JEA är ofta kör med admin (eller på annat sätt upphöjd) behörighet.</span><span class="sxs-lookup"><span data-stu-id="d4b47-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="d4b47-124">Noggrann val av tillgängliga kommandon är viktigt att säkerställa JEA slutpunkten inte tillåter den anslutande användaren vill höja deras behörigheter.</span><span class="sxs-lookup"><span data-stu-id="d4b47-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="d4b47-125">Nedan följer några exempel på kommandon som kan användas medvetet om tillåts i en obegränsad tillstånd.</span><span class="sxs-lookup"><span data-stu-id="d4b47-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="d4b47-126">Observera att detta inte är en komplett lista och bör endast användas som utgångspunkt vara avstängda.</span><span class="sxs-lookup"><span data-stu-id="d4b47-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="d4b47-127">Exempel på potentiellt skadliga kommandon</span><span class="sxs-lookup"><span data-stu-id="d4b47-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="d4b47-128">Risk</span><span class="sxs-lookup"><span data-stu-id="d4b47-128">Risk</span></span> | <span data-ttu-id="d4b47-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="d4b47-129">Example</span></span> | <span data-ttu-id="d4b47-130">Relaterade kommandon</span><span class="sxs-lookup"><span data-stu-id="d4b47-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="d4b47-131">Bevilja den anslutande användaren admin-privilegier för att kringgå JEA</span><span class="sxs-lookup"><span data-stu-id="d4b47-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="d4b47-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="d4b47-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="d4b47-133">Köra godtycklig kod, till exempel skadlig kod, kryphål eller anpassade skript för att kringgå skydd</span><span class="sxs-lookup"><span data-stu-id="d4b47-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="d4b47-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="d4b47-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="d4b47-135">Skapa en roll kapaciteten fil</span><span class="sxs-lookup"><span data-stu-id="d4b47-135">Create a role capability file</span></span>

<span data-ttu-id="d4b47-136">Du kan skapa en ny fil med funktionen för roll av PowerShell på [ny PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d4b47-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="d4b47-137">Den resulterande roll kapaciteten filen kan öppnas i en textredigerare och ändras så att kommandona för rollen.</span><span class="sxs-lookup"><span data-stu-id="d4b47-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="d4b47-138">I PowerShell-hjälpen innehåller flera exempel på hur du kan konfigurera filen.</span><span class="sxs-lookup"><span data-stu-id="d4b47-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="d4b47-139">Gör att PowerShell-cmdletar och funktioner</span><span class="sxs-lookup"><span data-stu-id="d4b47-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="d4b47-140">Om du vill tillåta användare att köra PowerShell-cmdlets eller funktioner, lägger du till cmdlet eller funktionen namnet VisbibleCmdlets eller VisibleFunctions fält.</span><span class="sxs-lookup"><span data-stu-id="d4b47-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="d4b47-141">Om du är osäker på om ett kommando är en cmdlet eller funktionen, kan du köra `Get-Command <name>` och kontrollera egenskapen ”CommandType” i utdata.</span><span class="sxs-lookup"><span data-stu-id="d4b47-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="d4b47-142">Ibland är omfånget för en viss cmdlet eller funktion för breda för användarnas behov.</span><span class="sxs-lookup"><span data-stu-id="d4b47-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="d4b47-143">En DNS-admin exempelvis antagligen bara måste ha åtkomst för att starta om tjänsten DNS.</span><span class="sxs-lookup"><span data-stu-id="d4b47-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="d4b47-144">I en miljö med flera innehavare där klienter har åtkomst till självbetjäning hanteringsverktyg, begränsas hyresgäster till att hantera med sina egna resurser.</span><span class="sxs-lookup"><span data-stu-id="d4b47-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="d4b47-145">I dessa fall kan du begränsa vilka parametrar som är tillgängliga från den cmdlet eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="d4b47-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="d4b47-146">I mer avancerade scenarier, kan du också behöva begränsa vilka värden som någon kan ange att dessa parametrar.</span><span class="sxs-lookup"><span data-stu-id="d4b47-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="d4b47-147">Rollen funktioner kan du definiera en uppsättning tillåtna värden eller ett mönster för reguljärt uttryck som utvärderas för att avgöra om en viss inmatning är tillåten.</span><span class="sxs-lookup"><span data-stu-id="d4b47-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="d4b47-148">Den [vanliga PowerShell-parametrar](https://technet.microsoft.com/library/hh847884.aspx) tillåts alltid, även om du begränsar tillgängliga parametrar.</span><span class="sxs-lookup"><span data-stu-id="d4b47-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="d4b47-149">Du bör inte explicit lista dem i fältet parametrar.</span><span class="sxs-lookup"><span data-stu-id="d4b47-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="d4b47-150">I tabellen nedan beskrivs de olika sätt som du kan anpassa en synlig cmdlet eller funktion.</span><span class="sxs-lookup"><span data-stu-id="d4b47-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="d4b47-151">Du kan blanda och matcha någon av de nedan i VisibleCmdlets fältet.</span><span class="sxs-lookup"><span data-stu-id="d4b47-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="d4b47-152">Exempel</span><span class="sxs-lookup"><span data-stu-id="d4b47-152">Example</span></span>                                                                                      | <span data-ttu-id="d4b47-153">Användningsfall</span><span class="sxs-lookup"><span data-stu-id="d4b47-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="d4b47-154">`'My-Func'` eller `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="d4b47-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="d4b47-155">Tillåter användaren att köra `My-Func` utan begränsningar på parametrar.</span><span class="sxs-lookup"><span data-stu-id="d4b47-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="d4b47-156">Tillåter användaren att köra `My-Func` från modulen `MyModule` utan begränsningar på parametrar.</span><span class="sxs-lookup"><span data-stu-id="d4b47-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="d4b47-157">Tillåter användaren att köra en cmdlet eller funktion med verbet `My`.</span><span class="sxs-lookup"><span data-stu-id="d4b47-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="d4b47-158">Tillåter användaren att köra en cmdlet eller funktion med substantivet `Func`.</span><span class="sxs-lookup"><span data-stu-id="d4b47-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="d4b47-159">Tillåter användaren att köra `My-Func` med den `Param1` och/eller `Param2` parametrar.</span><span class="sxs-lookup"><span data-stu-id="d4b47-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="d4b47-160">Alla värden kan anges till parametrarna.</span><span class="sxs-lookup"><span data-stu-id="d4b47-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="d4b47-161">Tillåter användaren att köra `My-Func` med den `Param1` parameter.</span><span class="sxs-lookup"><span data-stu-id="d4b47-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="d4b47-162">Endast ”Value1” och ”Value2” kan anges i parametern.</span><span class="sxs-lookup"><span data-stu-id="d4b47-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="d4b47-163">Tillåter användaren att köra `My-Func` med den `Param1` parameter.</span><span class="sxs-lookup"><span data-stu-id="d4b47-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="d4b47-164">Ett värde som börjar med ”contoso” kan anges i parametern.</span><span class="sxs-lookup"><span data-stu-id="d4b47-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="d4b47-165">Metodtips för säkerhet rekommenderas det inte att använda jokertecken när du definierar synliga cmdletar eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="d4b47-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="d4b47-166">I stället en lista med varje betrodda kommando för att se till att inga andra kommandon som delar samma namngivningsschemat oavsiktligt har behörighet.</span><span class="sxs-lookup"><span data-stu-id="d4b47-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="d4b47-167">Du kan inte använda både en ValidatePattern och ValidateSet samma cmdlet eller funktion.</span><span class="sxs-lookup"><span data-stu-id="d4b47-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="d4b47-168">Om du gör åsidosätter ValidatePattern ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="d4b47-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="d4b47-169">Mer information om ValidatePattern kolla [detta *artikel från Hey, Scripting Guy!* efter](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) och [PowerShell reguljära uttryck](https://technet.microsoft.com/library/hh847880.aspx) refererar till innehåll.</span><span class="sxs-lookup"><span data-stu-id="d4b47-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="d4b47-170">Att tillåta externa kommandon och PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="d4b47-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="d4b47-171">Du måste lägga till den fullständiga sökvägen till varje program i fältet VisibleExternalCommands så att användare köra körbara filer och PowerShell-skript (.ps1) i en session JEA.</span><span class="sxs-lookup"><span data-stu-id="d4b47-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="d4b47-172">Det är bäst, där det är möjligt att använda PowerShell-cmdlet eller funktion motsvarigheter till alla externa programfiler som tillåter du eftersom du har kontroll över vilka parametrar tillåts med PowerShell-cmdlet: ar/funktioner.</span><span class="sxs-lookup"><span data-stu-id="d4b47-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="d4b47-173">Många körbara filer kan du att både läsa det aktuella tillståndet och ändra den genom att tillhandahålla olika parametrar.</span><span class="sxs-lookup"><span data-stu-id="d4b47-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="d4b47-174">Anta till exempel att rollen för fil serveradministratör som vill kontrollera vilka nätverksresurser hanteras av den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d4b47-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="d4b47-175">Ett sätt att kontrollera är att använda `net share`.</span><span class="sxs-lookup"><span data-stu-id="d4b47-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="d4b47-176">Dock tillåter net.exe är mycket farliga eftersom administratören kan lika enkelt använda kommandot för att få administratörsrättigheter med `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="d4b47-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="d4b47-177">Är det bättre att [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) som ger samma resultat, men som har mycket mer begränsad omfattning.</span><span class="sxs-lookup"><span data-stu-id="d4b47-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="d4b47-178">När du gör externa kommandon tillgängliga för användare i en JEA session kan du alltid ange den fullständiga sökvägen till den körbara filen så ett liknande namn (och potentiellt malicous) program som placeras på en annan plats i systemet inte körs i stället.</span><span class="sxs-lookup"><span data-stu-id="d4b47-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="d4b47-179">Att tillåta åtkomst till PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="d4b47-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="d4b47-180">Som standard finns inga PowerShell-leverantörer i JEA sessioner.</span><span class="sxs-lookup"><span data-stu-id="d4b47-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="d4b47-181">Detta är främst att minska risken för konfigurationsinställningar som avslöjas för den anslutande användaren och känslig information.</span><span class="sxs-lookup"><span data-stu-id="d4b47-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="d4b47-182">Vid behov, kan du tillåta åtkomst till PowerShell-leverantörer som använder den `VisibleProviders` kommando.</span><span class="sxs-lookup"><span data-stu-id="d4b47-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="d4b47-183">En fullständig lista över providers, köra `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="d4b47-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="d4b47-184">För enkla uppgifter som kräver åtkomst till filsystemet, registret, certifikatarkivet eller andra leverantörer av känsliga kan du också överväga att skriva en egen funktion som fungerar med providern för användarens räkning.</span><span class="sxs-lookup"><span data-stu-id="d4b47-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="d4b47-185">Funktioner, cmdletar och externa program som är tillgängliga i en session JEA är inte samma begränsningar som JEA – de kan använda valfri provider som standard.</span><span class="sxs-lookup"><span data-stu-id="d4b47-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="d4b47-186">Överväga att använda den [enheten](session-configurations.md#user-drive) när filer kopieras till/från en slutpunkt för JEA krävs.</span><span class="sxs-lookup"><span data-stu-id="d4b47-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="d4b47-187">Skapa anpassade funktioner</span><span class="sxs-lookup"><span data-stu-id="d4b47-187">Creating custom functions</span></span>

<span data-ttu-id="d4b47-188">Du kan skapa anpassade funktioner i en roll kapaciteten fil till att förenkla komplexa för dina slutanvändare.</span><span class="sxs-lookup"><span data-stu-id="d4b47-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="d4b47-189">Anpassade funktioner är också användbara när du behöver avancerad verifiering logik för cmdlet parametervärden.</span><span class="sxs-lookup"><span data-stu-id="d4b47-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="d4b47-190">Du kan skriva enkla funktioner den **FunctionDefinitions** fält:</span><span class="sxs-lookup"><span data-stu-id="d4b47-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="d4b47-191">Glöm inte att lägga till namnet på din anpassade funktioner till den **VisibleFunctions** så att de kan köras av JEA användare.</span><span class="sxs-lookup"><span data-stu-id="d4b47-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="d4b47-192">Texten (skriptblock) för egna funktioner körs i standardläget för språk för systemet och är inte begränsningar för JEAS språk.</span><span class="sxs-lookup"><span data-stu-id="d4b47-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="d4b47-193">Det innebär att funktioner kan komma åt filsystem och register, och köra kommandon som inte har skapats visas i filen rollen kapaciteten.</span><span class="sxs-lookup"><span data-stu-id="d4b47-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="d4b47-194">Var noga med för att undvika att tillåta att skadlig kod som ska köras när du använder parametrar och undvika rörnät användarindata direkt till cmdlets som `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="d4b47-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="d4b47-195">I exemplet ovan ska du Observera att det fullständigt kvalificerade namnet (FQMN) `Microsoft.PowerShell.Utility\Select-Object` användes i stället för shorthand `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="d4b47-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="d4b47-196">Funktioner som är definierade i rollen funktionsfiler regleras fortfarande omfattning JEA sessioner, som innehåller funktioner för proxy JEA skapar för att begränsa befintliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="d4b47-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="d4b47-197">Select-Object är en standard begränsad cmdlet i alla JEA-sessioner som inte tillåter att du kan välja valfri egenskaper för objekt.</span><span class="sxs-lookup"><span data-stu-id="d4b47-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="d4b47-198">Om du vill använda obegränsad Select-Object i funktioner, måste du uttryckligen begära fullständigt genomförande genom att ange FQMN.</span><span class="sxs-lookup"><span data-stu-id="d4b47-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="d4b47-199">Alla begränsad cmdlet i en session JEA kommer att få samma beteende när den anropades från en funktion i enlighet med PowerShells [kommandot prioritet](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="d4b47-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="d4b47-200">Om du skriver en mängd anpassade funktioner, kan det vara lättare att placera dem i en [PowerShell-skriptet modulen](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="d4b47-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="d4b47-201">Du kan göra de här funktionerna i JEA sessionen med fältet VisibleFunctions sätt som med inbyggda och tredjeparts-moduler.</span><span class="sxs-lookup"><span data-stu-id="d4b47-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="d4b47-202">Placera rollen funktioner i en modul</span><span class="sxs-lookup"><span data-stu-id="d4b47-202">Place role capabilities in a module</span></span>

<span data-ttu-id="d4b47-203">För PowerShell för att hitta en roll kapaciteten fil måste den lagras i en mapp för ”RoleCapabilities” i en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="d4b47-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="d4b47-204">Modulen kan lagras i en mapp som ingår i den `$env:PSModulePath` miljövariabeln, men du bör inte placera den i System32 (reserverad för inbyggda moduler) eller en mapp där den betrodd, ansluter användare kan ändra filerna.</span><span class="sxs-lookup"><span data-stu-id="d4b47-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="d4b47-205">Nedan visas ett exempel på att skapa en grundläggande PowerShell skriptmodul kallas *ContosoJEA* i sökvägen ”programfiler”.</span><span class="sxs-lookup"><span data-stu-id="d4b47-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="d4b47-206">Se [förstå PowerShell-modulen](https://msdn.microsoft.com/en-us/library/dd878324.aspx) mer information om PowerShell-moduler, modulmanifest och PSModulePath miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="d4b47-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="d4b47-207">Uppdatera rollen funktioner</span><span class="sxs-lookup"><span data-stu-id="d4b47-207">Updating role capabilities</span></span>


<span data-ttu-id="d4b47-208">Du kan uppdatera en roll kapaciteten fil när som helst genom att helt enkelt sparar ändringarna i filen rollen kapaciteten.</span><span class="sxs-lookup"><span data-stu-id="d4b47-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="d4b47-209">Alla nya JEA sessioner igång när kapaciteten för rollen har uppdaterats visar de nya funktionerna.</span><span class="sxs-lookup"><span data-stu-id="d4b47-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="d4b47-210">Det är därför det är så viktigt att kontrollera åtkomst till mappen rollen funktioner.</span><span class="sxs-lookup"><span data-stu-id="d4b47-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="d4b47-211">Endast betrodda administratörer ska kunna ändra roll funktionsfiler.</span><span class="sxs-lookup"><span data-stu-id="d4b47-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="d4b47-212">Om en icke betrodd användare kan ändra funktionsfiler för rollen, kan de enkelt ge sig åtkomst till cmdlets som gör det möjligt för dem att öka sina privilegier.</span><span class="sxs-lookup"><span data-stu-id="d4b47-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="d4b47-213">Kontrollera lokalt System har läsbehörighet till rollen funktionsfiler och som innehåller moduler för administratörer som behöver låsa åtkomst till funktionerna för rollen.</span><span class="sxs-lookup"><span data-stu-id="d4b47-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="d4b47-214">Hur rollen funktioner kombineras</span><span class="sxs-lookup"><span data-stu-id="d4b47-214">How role capabilities are merged</span></span>

<span data-ttu-id="d4b47-215">Användare kan få åtkomst till flera rollen funktioner när de anger en JEA session beroende på roll-avbildningar i den [session konfigurationsfilen](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="d4b47-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="d4b47-216">När detta sker JEA försök att ge användaren den *mest Tillåtande* uppsättning kommandon som tillåts av någon av rollerna.</span><span class="sxs-lookup"><span data-stu-id="d4b47-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="d4b47-217">**VisibleCmdlets och VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="d4b47-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="d4b47-218">Den mest komplexa merge logiken påverkar cmdletar och funktioner som kan ha sina parametrar och parametervärden som är begränsad i JEA.</span><span class="sxs-lookup"><span data-stu-id="d4b47-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="d4b47-219">Reglerna är följande:</span><span class="sxs-lookup"><span data-stu-id="d4b47-219">The rules are as follows:</span></span>

1. <span data-ttu-id="d4b47-220">Om en cmdlet görs endast visas i en roll, kan det vara synliga för användare med alla tillämpliga tillgodosetts.</span><span class="sxs-lookup"><span data-stu-id="d4b47-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="d4b47-221">Om en cmdlet görs visas i mer än en roll, och varje roll har samma begränsningar för cmdleten, vara cmdlet synliga för användare med dessa begränsningar.</span><span class="sxs-lookup"><span data-stu-id="d4b47-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="d4b47-222">Om en cmdlet görs visas i mer än en roll, och varje roll kan en annan uppsättning parametrar, visas cmdlet: en och alla parametrar som definierats för varje roll för användaren.</span><span class="sxs-lookup"><span data-stu-id="d4b47-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="d4b47-223">Om en roll inte har begränsningar för parametrarna, kommer alla parametrar att tillåtas.</span><span class="sxs-lookup"><span data-stu-id="d4b47-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="d4b47-224">Om en roll som definierar en verifiera uppsättning eller verifiera mönster för en cmdlet-parameter, och den andra rollen ger parametern men inte begränsa parametervärden, kommer verifiera uppsättning eller mönster att ignoreras.</span><span class="sxs-lookup"><span data-stu-id="d4b47-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="d4b47-225">Om en uppsättning verifiera har definierats för samma cmdlet-parameter i mer än en roll, får alla värden från alla verifiera uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="d4b47-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="d4b47-226">Om ett mönster för verifiera har definierats för samma cmdlet-parameter i mer än en roll, tillåts värden som matchar någon av mönster.</span><span class="sxs-lookup"><span data-stu-id="d4b47-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="d4b47-227">Om en uppsättning verifiera har definierats i en eller flera roller och ett mönster för verifiera har definierats i en annan roll för samma cmdlet-parameter, verifiera uppsättningen ignoreras och regeln (6) gäller för de återstående verifiera mönster.</span><span class="sxs-lookup"><span data-stu-id="d4b47-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="d4b47-228">Nedan visas ett exempel på hur roller kombineras enligt reglerna:</span><span class="sxs-lookup"><span data-stu-id="d4b47-228">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



<span data-ttu-id="d4b47-229">**VisibleExternalCommands VisibleAliases VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="d4b47-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="d4b47-230">Alla andra fält i filen rollen kapaciteten läggs bara till en kumulativ uppsättning med tillåtna externa kommandon, alias, leverantörer och startskript.</span><span class="sxs-lookup"><span data-stu-id="d4b47-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="d4b47-231">Alla kommandot alias, provider eller skript som är tillgängliga i en roll-funktionen kommer att kunna JEA användaren.</span><span class="sxs-lookup"><span data-stu-id="d4b47-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="d4b47-232">Var noga med att kontrollera att den kombinerade uppsättningen providers från en roll kapaciteten och kommandon/cmdlets/funktioner från en annan tillåter inte anslutning användare oavsiktlig åtkomst till systemresurser.</span><span class="sxs-lookup"><span data-stu-id="d4b47-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="d4b47-233">Om en roll kan till exempel den `Remove-Item` cmdlet och en annan tillåter den `FileSystem` provider, du riskerar att JEA användaren ta bort godtyckliga filer från datorn.</span><span class="sxs-lookup"><span data-stu-id="d4b47-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="d4b47-234">Mer information om hur du identifierar användarnas gällande behörigheter finns i den [granskning JEA avsnittet](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="d4b47-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d4b47-235">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="d4b47-235">Next steps</span></span>

- [<span data-ttu-id="d4b47-236">Skapa en konfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="d4b47-236">Create a session configuration file</span></span>](session-configurations.md)