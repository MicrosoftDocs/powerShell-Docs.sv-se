---
title: Nyheter i PowerShell Core 6,2
description: Nya funktioner och ändringar som lanseras i PowerShell Core 6,2
ms.date: 03/28/2019
ms.openlocfilehash: 2f5f5d11ba46d53966093c5e3ed6d0c7d47308d0
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737142"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="106c4-103">Nyheter i PowerShell Core 6,2</span><span class="sxs-lookup"><span data-stu-id="106c4-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="106c4-104">PowerShell Core 6,2-versionen fokuserar på prestanda förbättringar, fel korrigeringar och mindre cmdlet-och språk förbättringar som förbättrar kvaliteten.</span><span class="sxs-lookup"><span data-stu-id="106c4-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="106c4-105">Om du vill se en fullständig lista över förbättringar kan du kolla in vår detaljerade [ChangeLogs](https://github.com/PowerShell/PowerShell/releases) på GitHub.</span><span class="sxs-lookup"><span data-stu-id="106c4-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="106c4-106">Experimentella funktioner</span><span class="sxs-lookup"><span data-stu-id="106c4-106">Experimental Features</span></span>

<span data-ttu-id="106c4-107">Tidigare aktiverade vi stöd för [experimentella funktioner][].</span><span class="sxs-lookup"><span data-stu-id="106c4-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="106c4-108">I 6,2-versionen har vi fyra experimentella funktioner för att testa. Ge feedback så att vi kan göra förbättringar och avgöra om funktionen är värd för att marknadsföra till en vanlig status.</span><span class="sxs-lookup"><span data-stu-id="106c4-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="106c4-109">Använd `Get-ExperimentalFeature` för att hämta en lista över tillgängliga experimentella funktioner.</span><span class="sxs-lookup"><span data-stu-id="106c4-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="106c4-110">Du kan aktivera eller inaktivera dessa funktioner med `Enable-ExperimentalFeature` och `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="106c4-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="106c4-111">Kommandot hittade inte förslag</span><span class="sxs-lookup"><span data-stu-id="106c4-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="106c4-112">Den här funktionen använder fuzzy-matchning för att hitta förslag på kommandon eller cmdletar som du kan ha felskrivit.</span><span class="sxs-lookup"><span data-stu-id="106c4-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="106c4-113">Exempel</span><span class="sxs-lookup"><span data-stu-id="106c4-113">Example</span></span>

<span data-ttu-id="106c4-114">I det här exemplet är det felstavade cmdlet-namnet suddigt matchat med flera förslag från de mest sannolika.</span><span class="sxs-lookup"><span data-stu-id="106c4-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a><span data-ttu-id="106c4-115">Implicit fjärran batchbearbetning</span><span class="sxs-lookup"><span data-stu-id="106c4-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="106c4-116">När du använder [implicit fjärr kommunikation](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) i en pipeline behandlar PowerShell varje kommando i pipelinen separat.</span><span class="sxs-lookup"><span data-stu-id="106c4-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="106c4-117">Objekt serialiseras upprepade gånger och `de-serialized` mellan klienten och fjärrsystemet under körningen av pipelinen.</span><span class="sxs-lookup"><span data-stu-id="106c4-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="106c4-118">Med den här funktionen analyserar PowerShell pipelinen för att avgöra om kommandot är säkert att köra och finns på mål systemet.</span><span class="sxs-lookup"><span data-stu-id="106c4-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="106c4-119">Om värdet är true, kör PowerShell hela pipelinen via en fjärr anslutning och endast serialiserar och `de-serializes` tillbaka resultatet till klienten.</span><span class="sxs-lookup"><span data-stu-id="106c4-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="106c4-120">Ett verkligt globalt test av `Get-Process | Sort-Object` över localhost minskar från 10-15 sekunder till 20-30 **millisekunder**.</span><span class="sxs-lookup"><span data-stu-id="106c4-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="106c4-121">Funktionen behöver bara aktive ras på klienten.</span><span class="sxs-lookup"><span data-stu-id="106c4-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="106c4-122">Inga ändringar krävs på servern.</span><span class="sxs-lookup"><span data-stu-id="106c4-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="106c4-123">Tillfällig enhet</span><span class="sxs-lookup"><span data-stu-id="106c4-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="106c4-124">Om du använder PowerShell Core på olika operativ system kommer du att upptäcka att miljövariabeln för att hitta den temporära katalogen är annorlunda på Windows, macOS och Linux!</span><span class="sxs-lookup"><span data-stu-id="106c4-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="106c4-125">Med den här funktionen får du en [PSDrive][] som kallas `Temp:` som automatiskt mappas till den temporära mappen för det operativ system som du använder.</span><span class="sxs-lookup"><span data-stu-id="106c4-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="106c4-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="106c4-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

<span data-ttu-id="106c4-127">Tänk på att interna fil kommandon (t. ex. `ls` på Linux) inte är medvetna om PSDrives och inte ser den här `Temp:` enheten.</span><span class="sxs-lookup"><span data-stu-id="106c4-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="106c4-128">Utökning av förkortning</span><span class="sxs-lookup"><span data-stu-id="106c4-128">Abbreviation Expansion</span></span>

<span data-ttu-id="106c4-129">PowerShell-cmdletar förväntas ha beskrivande substantiv.</span><span class="sxs-lookup"><span data-stu-id="106c4-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="106c4-130">Detta resulterar i långa namn som är svårare att skriva.</span><span class="sxs-lookup"><span data-stu-id="106c4-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="106c4-131">Med den här funktionen kan du bara skriva versaler i cmdleten och använda TABB-slutförande för att hitta en matchning.</span><span class="sxs-lookup"><span data-stu-id="106c4-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="106c4-132">Exempel</span><span class="sxs-lookup"><span data-stu-id="106c4-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="106c4-133">Om du trycker på tabbtangenten och har modulen Azure PowerShell [AZ](https://www.powershellgallery.com/packages/Az) installerad, kommer den att kompletteras med:</span><span class="sxs-lookup"><span data-stu-id="106c4-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="106c4-134">Den här funktionen är avsedd att användas interaktivt.</span><span class="sxs-lookup"><span data-stu-id="106c4-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="106c4-135">Det går inte att köra förkortade former av cmdletar.</span><span class="sxs-lookup"><span data-stu-id="106c4-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="106c4-136">Den här funktionen ersätter inte alias.</span><span class="sxs-lookup"><span data-stu-id="106c4-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="106c4-137">Icke-bakåtkompatibla ändringar</span><span class="sxs-lookup"><span data-stu-id="106c4-137">Breaking Changes</span></span>

- <span data-ttu-id="106c4-138">Korrigera `-NoEnumerate` beteende i `Write-Output` att vara konsekvent med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="106c4-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="106c4-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="106c4-139">(#9069)</span></span>
- <span data-ttu-id="106c4-140">Kontrol `Join-String -InputObject 1,2,3` resultat som motsvarar `1,2,3 | Join-String` resultat (#8611) (tack @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="106c4-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="106c4-141">Lägg till `-Stable` i `Sort-Object` och relaterade tester (#7862) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="106c4-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="106c4-142">Förbättra `Start-Sleep`-cmdlet för att acceptera bråktal (#8537) (tack @Prototyyppi!)</span><span class="sxs-lookup"><span data-stu-id="106c4-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="106c4-143">Ändra hash för att använda OrdinalIgnoreCase för att vara `case-insensitive` i alla kulturer (#8566)</span><span class="sxs-lookup"><span data-stu-id="106c4-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="106c4-144">Åtgärda **LiteralPath** i `Import-Csv` att binda till `Get-ChildItem` utdata (#8277) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="106c4-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="106c4-145">Hoppar inte längre över en kolumn utan namn om dubbel quote-avgränsare används i `Import-Csv` (#7899) (tack @Topping!)</span><span class="sxs-lookup"><span data-stu-id="106c4-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="106c4-146">`Get-ExperimentalFeature` har inte längre `-ListAvailable` växel (#8318)</span><span class="sxs-lookup"><span data-stu-id="106c4-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="106c4-147">Felsök-parametern anger nu `$DebugPreference` att **fortsätta** i stället för **fråga** (#8195) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="106c4-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="106c4-148">Använd `-OutputFormat` om det anges i icke-interaktiva, omdirigerade, kodade kommando som används med pwsh (#8115)</span><span class="sxs-lookup"><span data-stu-id="106c4-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="106c4-149">Läs in sammansättning från modulens bas Sök väg innan du försöker läsa in från GAC (#8073)</span><span class="sxs-lookup"><span data-stu-id="106c4-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="106c4-150">Ta bort Tilde från Linux Preview-paket (#8244)</span><span class="sxs-lookup"><span data-stu-id="106c4-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="106c4-151">Flytta bearbetning av `-WorkingDirectory` innan profiler bearbetas (#8079)</span><span class="sxs-lookup"><span data-stu-id="106c4-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="106c4-152">Lägg inte till `PATHEXT` Environment-variabel på UNIX (#7697) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="106c4-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="106c4-153">Kända problem</span><span class="sxs-lookup"><span data-stu-id="106c4-153">Known Issues</span></span>

- <span data-ttu-id="106c4-154">Det finns ett problem med att läsa in moduler för fjärr kommunikation på Windows IOT ARM-plattformar.</span><span class="sxs-lookup"><span data-stu-id="106c4-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="106c4-155">Se (#8053)</span><span class="sxs-lookup"><span data-stu-id="106c4-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="106c4-156">Allmänna uppdateringar och korrigeringar</span><span class="sxs-lookup"><span data-stu-id="106c4-156">General Updates and Fixes</span></span>

- <span data-ttu-id="106c4-157">Aktivera ifyllnad av Skift läges okänsligt för filer och mappar på SKIFT läges känsligt fil system (#8128)</span><span class="sxs-lookup"><span data-stu-id="106c4-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="106c4-158">Gör PSVersionInfo. PSVersion och PSVersionInfo. PSEdition Public (#8054) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="106c4-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="106c4-159">Lägg till typ-härledning för `$_` / `$PSItem` i `catch{ }` block (#8020) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="106c4-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="106c4-160">Korrigera statisk metod typ för anrops typ (#8018) (tack @SeeminglyScience!)</span><span class="sxs-lookup"><span data-stu-id="106c4-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="106c4-161">Skapa härledda typer för `Select-Object`, `Group-Object`, **PSObject** och **hash** (#7231) (tack @powercode!)</span><span class="sxs-lookup"><span data-stu-id="106c4-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="106c4-162">Stöd för anrops metod med `ByRef-like` typ parametrar (#7721)</span><span class="sxs-lookup"><span data-stu-id="106c4-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="106c4-163">Hantera det fall där sökvägen till Windows PowerShell-modulen redan finns i miljöns PSModulePath (#7727)</span><span class="sxs-lookup"><span data-stu-id="106c4-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="106c4-164">Aktivera `SecureString`-cmdletar för icke-Windows genom att lagra den oformaterade texten (#9199)</span><span class="sxs-lookup"><span data-stu-id="106c4-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="106c4-165">Förbättra fel meddelandet på icke-Windows när du importerar CliXml med SecureString (#7997)</span><span class="sxs-lookup"><span data-stu-id="106c4-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="106c4-166">Lägger till parameter ReplyTo till `Send-MailMessage` (#8727) (tack @replicaJunction!)</span><span class="sxs-lookup"><span data-stu-id="106c4-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="106c4-167">Lägg till föråldrat meddelande i `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="106c4-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="106c4-168">Åtgärda `Restart-Computer` att arbeta på `localhost` när WinRM inte finns (#9160)</span><span class="sxs-lookup"><span data-stu-id="106c4-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="106c4-169">Gör `Start-Job` Utlös fel när PowerShell håller på att nås (#9128)</span><span class="sxs-lookup"><span data-stu-id="106c4-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="106c4-170">Lägg C# till stil typs acceleratorer och suffix för ushort, uint, ulong och korta litteraler (#7813) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="106c4-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="106c4-171">Nya suffix har lagts till för numeriska literaler – se [about_Numeric_Literals][] (#7901) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="106c4-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="106c4-172">Korrekt rapport effekt nivå när SupportsShouldProcess inte är inställt på True (#8209) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="106c4-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="106c4-173">Korrigera charset-problem i webb-cmdlets (#8742) (tack @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="106c4-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="106c4-174">Fix förväntar dig `100-continue` problem med Web-cmdlets (#8679) (tack @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="106c4-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="106c4-175">Åtgärda problem med fil blockering med Web-cmdlets (#7676) (tack @Claustn!)</span><span class="sxs-lookup"><span data-stu-id="106c4-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="106c4-176">Åtgärda problem med tolkning av tecken tabell i `Invoke-RestMethod` (#8694) (tack @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="106c4-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="106c4-177">Åter`ConvertTo-Json` för att exponera JsonObject. ConvertToJson som ett offentligt API (#8682)</span><span class="sxs-lookup"><span data-stu-id="106c4-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="106c4-178">Lägg till konfigurerbart högsta djup i `ConvertFrom-Json` med-djup (#8199) (tack @louistio!)</span><span class="sxs-lookup"><span data-stu-id="106c4-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="106c4-179">Lägg till parametern EscapeHandling i `ConvertTo-Json`-cmdlet (#7775) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="106c4-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="106c4-180">Lägg till `-CustomPipeName` i pwsh och `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="106c4-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="106c4-181">Aktivera skapande av relativa symboliska länkar i Windows med `New-Item` (#8783)</span><span class="sxs-lookup"><span data-stu-id="106c4-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="106c4-182">Tillåt Windows-användare i utvecklarläge att skapa symlinks utan utökade privilegier (#8534)</span><span class="sxs-lookup"><span data-stu-id="106c4-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="106c4-183">Aktivera `Write-Information` att acceptera `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="106c4-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="106c4-184">Korrigera `Get-Help` för avancerade funktioner med hjälp innehåll för MAML (#8353)</span><span class="sxs-lookup"><span data-stu-id="106c4-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="106c4-185">Åtgärda `Get-Help` PSTypeName-problem med-parameter när endast en parameter deklareras (#8754) (tack @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="106c4-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="106c4-186">Token calculation-korrigering för `Get-Help` som körts på script block för kommentars hjälpen.</span><span class="sxs-lookup"><span data-stu-id="106c4-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="106c4-187">(#8238) (Tack @hubuk!)</span><span class="sxs-lookup"><span data-stu-id="106c4-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="106c4-188">Ändra `Get-Help` cmdlet-parameter-parameter så att den accepterar String-matriser (#8454) (tack @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="106c4-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="106c4-189">Lös PAGER om sökvägen innehåller blank steg (#8571) (tack @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="106c4-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="106c4-190">Lägg till en prompt till användningen av `less` i funktionen "hjälp" för att instruera användaren att avsluta (#7998)</span><span class="sxs-lookup"><span data-stu-id="106c4-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="106c4-191">Lägg till stöd för uppräknings-och tecken typer i `Format-Hex` cmdlet (#8191) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="106c4-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="106c4-192">Ta bort ShouldProcess från `Format-Hex` (#8178)</span><span class="sxs-lookup"><span data-stu-id="106c4-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="106c4-193">Lägg till nya förskjutnings-och Count-parametrar till `Format-Hex` och omstrukturering av cmdleten (#7877) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="106c4-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="106c4-194">Tillåt ' name ' som en aliasnamn för ' Label ' i `ConvertTo-Html`, Tillåt att ' width '-posten är ett heltal (#8426) (tack @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="106c4-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="106c4-195">Gör script block-baserade beräknade egenskaper fungerar igen i `ConvertTo-Html` (#8427) (tack @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="106c4-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="106c4-196">Lägg till cmdlet `Join-String` för att skapa text från pipeline-inmatare (#7660) (tack @powercode!)</span><span class="sxs-lookup"><span data-stu-id="106c4-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="106c4-197">Korrigera `Join-String`-cmdlet FormatString parameter Logic (#8449) (tack @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="106c4-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="106c4-198">Ändra `Clear-Host` tillbaka till att använda `$RAWUI` och rensa för att arbeta via fjärr kommunikation (#8609)</span><span class="sxs-lookup"><span data-stu-id="106c4-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="106c4-199">Ändra `Clear-Host` till att bara anropa `[console]::clear` och ta bort radera alias från UNIX (#8603)</span><span class="sxs-lookup"><span data-stu-id="106c4-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="106c4-200">Åtgärda LiteralPath i `Import-Csv` att binda till `Get-ChildItem` utdata (#8277) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="106c4-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="106c4-201">Hjälp funktionen ska inte använda pager för AliasHelpInfo (#8552)</span><span class="sxs-lookup"><span data-stu-id="106c4-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="106c4-202">Lägg till `-UseMinimalHeader` i `Start-Transcript` för att minimera avskrifts huvudet (#8402) (tack @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="106c4-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="106c4-203">Lägg till `Enable-ExperimentalFeature`-och `Disable-ExperimentalFeature`-cmdletar (#8318)</span><span class="sxs-lookup"><span data-stu-id="106c4-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="106c4-204">Visa alla cmdletar från **PSDiagnostics** om logman. exe är tillgängligt (#8366)</span><span class="sxs-lookup"><span data-stu-id="106c4-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="106c4-205">Ta bort **bevara** parameter från `New-PSDrive` på `non-Windows` plattform (#8291) (tack @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="106c4-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="106c4-206">Lägg till stöd för `cd +` (#7206) (tack @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="106c4-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="106c4-207">Aktivera `Set-Location -LiteralPath` att arbeta med mappar med namnet-och + (#8089)</span><span class="sxs-lookup"><span data-stu-id="106c4-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="106c4-208">`Test-Path` returnerar `$false` när ett tomt eller `$null` sökvägar anges (#8080) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="106c4-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="106c4-209">Tillåt att dynamisk parameter returneras även om sökvägen inte matchar någon Provider (#7957)</span><span class="sxs-lookup"><span data-stu-id="106c4-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="106c4-210">Stöd `Get-PSHostProcessInfo` och `Enter-PSHostProcess` på UNIX-plattformar (#8232)</span><span class="sxs-lookup"><span data-stu-id="106c4-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="106c4-211">Minska allokeringarna i `Get-Content`-cmdlet (#8103) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="106c4-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="106c4-212">Aktivera `Add-Content` för att dela Läs behörighet med andra verktyg när du skriver innehåll (#8091)</span><span class="sxs-lookup"><span data-stu-id="106c4-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="106c4-213">`Get/Add-Content` genererar förbättrat fel vid mål för en behållare (#7823) (tack @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="106c4-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="106c4-214">Lägg till `-Name`, `-NoUserOverrides` och `-ListAvailable` parametrar till `Get-Culture` cmdlet (#7702) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="106c4-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="106c4-215">Lägg till enhetligt attribut för att slutföra **kodnings** parametern.</span><span class="sxs-lookup"><span data-stu-id="106c4-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="106c4-216">(#7732) (Tack @ThreeFive-O!)</span><span class="sxs-lookup"><span data-stu-id="106c4-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="106c4-217">Tillåt numeriska ID: n och namnet på registrerade tecken sidor i **encoding** -parametrar (#7636) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="106c4-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="106c4-218">Korrigera `Rename-Item -Path` med jokertecken (#7398) (tack @kwkam!)</span><span class="sxs-lookup"><span data-stu-id="106c4-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="106c4-219">När du använder `Start-Transcript` och filen finns tom fil i stället för att ta bort (#8131) (tack @paalbra!)</span><span class="sxs-lookup"><span data-stu-id="106c4-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="106c4-220">Gör `Add-Type` filer med öppen källkod med **fileaccess. Read** och **fileshare. read** explicit (#7915) (tack @IISResetMe!)</span><span class="sxs-lookup"><span data-stu-id="106c4-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="106c4-221">Korrigera `Enter-PSSession -ContainerId` för de senaste Windows-versionerna (#7883)</span><span class="sxs-lookup"><span data-stu-id="106c4-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="106c4-222">Se till att egenskapen **NestedModules** har fyllts i `Test-ModuleManifest` (#7859)</span><span class="sxs-lookup"><span data-stu-id="106c4-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="106c4-223">Lägg till `%F` fall i `Get-Date`-UFormat (#7630) (tack @britishben!)</span><span class="sxs-lookup"><span data-stu-id="106c4-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="106c4-224">Korrigera `Set-Service -Status Stopped` att stoppa tjänster med beroenden (#5525) (tack @zhenggu!)</span><span class="sxs-lookup"><span data-stu-id="106c4-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentella funktioner]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
