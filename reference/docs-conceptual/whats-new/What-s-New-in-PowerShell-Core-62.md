---
title: Nyheter i PowerShell Core 6.2
description: Nya funktioner och ändringar som introducerades i PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984501"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="5c221-103">Nyheter i PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="5c221-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="5c221-104">PowerShell Core 6.2-versionen fokuserar på prestandaförbättringar, felkorrigeringar och mindre förbättringar för cmdlet och språk som förbättrar kvaliteten.</span><span class="sxs-lookup"><span data-stu-id="5c221-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="5c221-105">Om du vill se en fullständig lista över förbättringar, Kolla in vår detaljerad [changelogs](https://github.com/PowerShell/PowerShell/releases) på GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c221-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="5c221-106">Experimentella funktioner</span><span class="sxs-lookup"><span data-stu-id="5c221-106">Experimental Features</span></span>

<span data-ttu-id="5c221-107">Tidigare var vi aktiverat stöd för [experimentella funktioner][].</span><span class="sxs-lookup"><span data-stu-id="5c221-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="5c221-108">Vi har fyra experimentella funktioner för att testa i 6.2-utgåvan. Ge feedback så att vi kan göra förbättringar och bestämma om funktionen är värt att uppgradera till vanlig status.</span><span class="sxs-lookup"><span data-stu-id="5c221-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="5c221-109">Använd `Get-ExperimentalFeature` att hämta en lista över tillgängliga experimentella funktioner.</span><span class="sxs-lookup"><span data-stu-id="5c221-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="5c221-110">Du kan aktivera eller inaktivera dessa funktioner via `Enable-ExperimentalFeature` och `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="5c221-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="5c221-111">Kommandot hittades inte förslag</span><span class="sxs-lookup"><span data-stu-id="5c221-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="5c221-112">Den här funktionen använder partiell matchning för att få förslag på kommandon eller cmdlet: ar som kanske har du angett.</span><span class="sxs-lookup"><span data-stu-id="5c221-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="5c221-113">Exempel</span><span class="sxs-lookup"><span data-stu-id="5c221-113">Example</span></span>

<span data-ttu-id="5c221-114">I det här exemplet är felstavade cmdlet-namn fuzzy matchas mot flera förslag från mest sannolikt minst sannolikt.</span><span class="sxs-lookup"><span data-stu-id="5c221-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

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

### <a name="implicit-remoting-batching"></a><span data-ttu-id="5c221-115">Implicit fjärrkommunikation batchbearbetning</span><span class="sxs-lookup"><span data-stu-id="5c221-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="5c221-116">När du använder [implicit fjärrkommunikation](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) i en pipeline PowerShell behandlar varje kommando i pipelinen oberoende av varandra.</span><span class="sxs-lookup"><span data-stu-id="5c221-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="5c221-117">Objekt flera gånger serialiseras och `de-serialized` mellan klienten och fjärrdatorn under körningen av pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5c221-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="5c221-118">Med den här funktionen analyserar PowerShell pipeline för att avgöra om kommandot är säkert att köra och den finns på målsystemet.</span><span class="sxs-lookup"><span data-stu-id="5c221-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="5c221-119">Om värdet är true PowerShell körs hela pipelinen via en fjärranslutning och endast Serialiserar och `de-serializes` resultaten tillbaka till klienten.</span><span class="sxs-lookup"><span data-stu-id="5c221-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="5c221-120">Ett verkligt test av `Get-Process | Sort-Object` över localhost sjunker från 10 – 15 sekunder till 20 – 30 **millisekunder**.</span><span class="sxs-lookup"><span data-stu-id="5c221-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="5c221-121">Funktionen behöver bara vara aktiverad på klienten.</span><span class="sxs-lookup"><span data-stu-id="5c221-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="5c221-122">Det krävs inga ändringar på servern.</span><span class="sxs-lookup"><span data-stu-id="5c221-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="5c221-123">Temp Drive</span><span class="sxs-lookup"><span data-stu-id="5c221-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="5c221-124">Om du använder PowerShell Core på olika operativsystem, kommer du att upptäcka att miljövariabeln för att hitta den tillfälliga katalogen är olika i Windows, macOS och Linux!</span><span class="sxs-lookup"><span data-stu-id="5c221-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="5c221-125">Med den här funktionen kan du få en [PSDrive][] kallas `Temp:` som mappas automatiskt till den tillfälliga mappen för operativsystemet som du använder.</span><span class="sxs-lookup"><span data-stu-id="5c221-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="5c221-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="5c221-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

<span data-ttu-id="5c221-127">Tänk på de interna kommandona (som `ls` på Linux) är inte medvetna om PSDrives och ser inte detta `Temp:` enhet.</span><span class="sxs-lookup"><span data-stu-id="5c221-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="5c221-128">Förkortning Expansion</span><span class="sxs-lookup"><span data-stu-id="5c221-128">Abbreviation Expansion</span></span>

<span data-ttu-id="5c221-129">PowerShell-cmdletar som förväntas ha beskrivande substantiv.</span><span class="sxs-lookup"><span data-stu-id="5c221-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="5c221-130">Detta resulterar i långa namn som är svårare att skriva.</span><span class="sxs-lookup"><span data-stu-id="5c221-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="5c221-131">Den här funktionen kan du bara ange versaler för cmdlet: ar och Använd tabbifyllning för att hitta en matchning.</span><span class="sxs-lookup"><span data-stu-id="5c221-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="5c221-132">Exempel</span><span class="sxs-lookup"><span data-stu-id="5c221-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="5c221-133">Om du trycker på fliken och har Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) installerat modulen, kommer det att Komplettera automatiskt till:</span><span class="sxs-lookup"><span data-stu-id="5c221-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="5c221-134">Den här funktionen är avsedd att användas interaktivt.</span><span class="sxs-lookup"><span data-stu-id="5c221-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="5c221-135">Förkortade former av cmdlet: ar kan inte utföras.</span><span class="sxs-lookup"><span data-stu-id="5c221-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="5c221-136">Den här funktionen är inte en ersättning för alias.</span><span class="sxs-lookup"><span data-stu-id="5c221-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="5c221-137">Icke-bakåtkompatibla ändringar</span><span class="sxs-lookup"><span data-stu-id="5c221-137">Breaking Changes</span></span>

- <span data-ttu-id="5c221-138">Åtgärda `-NoEnumerate` beteende i `Write-Output` för att överensstämma med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c221-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="5c221-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="5c221-139">(#9069)</span></span>
- <span data-ttu-id="5c221-140">Kontrollera `Join-String -InputObject 1,2,3` resultera lika `1,2,3 | Join-String` resultera (#8611) (tack @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="5c221-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="5c221-141">Lägg till `-Stable` till `Sort-Object` och relaterade tester (#7862) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="5c221-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5c221-142">Förbättra `Start-Sleep` cmdlet för att acceptera fraktionell (#8537) (tack @Prototyyppi!)</span><span class="sxs-lookup"><span data-stu-id="5c221-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="5c221-143">Ändra hash-tabell att använda OrdinalIgnoreCase för att vara `case-insensitive` i alla kulturer (#8566)</span><span class="sxs-lookup"><span data-stu-id="5c221-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="5c221-144">Åtgärda **LiteralPath** i `Import-Csv` att binda till `Get-ChildItem` utdata (#8277) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="5c221-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5c221-145">Hoppar över en kolumn utan namn inte längre om dubbelt citattecken avgränsare används i `Import-Csv` (#7899) (tack @Topping!)</span><span class="sxs-lookup"><span data-stu-id="5c221-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="5c221-146">`Get-ExperimentalFeature` har inte längre `-ListAvailable` växla (#8318)</span><span class="sxs-lookup"><span data-stu-id="5c221-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="5c221-147">Felsöka nu parameteruppsättningar `$DebugPreference` till **Fortsätt** i stället för **Inquire** (#8195) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="5c221-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5c221-148">Kontrollera `-OutputFormat` om anges i icke-interaktivt, omdirigerade, kodade kommando som används med pwsh (#8115)</span><span class="sxs-lookup"><span data-stu-id="5c221-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="5c221-149">Läsa in sammansättningen från modulen rotsökväg innan du försöker läsa in från den globala Sammansättningscachen (#8073)</span><span class="sxs-lookup"><span data-stu-id="5c221-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="5c221-150">Ta bort tilde från Linux förhandsversion paket (#8244)</span><span class="sxs-lookup"><span data-stu-id="5c221-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="5c221-151">Flytta bearbetning av `-WorkingDirectory` innan bearbetningen av profiler (#8079)</span><span class="sxs-lookup"><span data-stu-id="5c221-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="5c221-152">Lägg inte till `PATHEXT` miljövariabeln på Unix (#7697) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="5c221-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="5c221-153">Kända problem</span><span class="sxs-lookup"><span data-stu-id="5c221-153">Known Issues</span></span>

- <span data-ttu-id="5c221-154">Fjärrkommunikation för plattformar som Windows IOT ARM har ett problem vid inläsning av moduler.</span><span class="sxs-lookup"><span data-stu-id="5c221-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="5c221-155">Se (#8053)</span><span class="sxs-lookup"><span data-stu-id="5c221-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="5c221-156">Allmänna uppdateringar och korrigeringar</span><span class="sxs-lookup"><span data-stu-id="5c221-156">General Updates and Fixes</span></span>

- <span data-ttu-id="5c221-157">Aktivera skiftlägeskänsliga tabbifyllning för filer och mappar i skiftlägeskänsliga filsystem (#8128)</span><span class="sxs-lookup"><span data-stu-id="5c221-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="5c221-158">Gör PSVersionInfo.PSVersion och PSVersionInfo.PSEdition offentlig (#8054) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="5c221-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5c221-159">Lägg till typen Inferens för `$_`  /  `$PSItem` i `catch{ }` blockerar (#8020) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="5c221-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5c221-160">Åtgärda statisk metod anrop typ inferens (#8018) (tack @SeeminglyScience!)</span><span class="sxs-lookup"><span data-stu-id="5c221-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="5c221-161">Skapa antydda för `Select-Object`, `Group-Object`, **PSObject** och **hash-tabell** (#7231) (tack @powercode!)</span><span class="sxs-lookup"><span data-stu-id="5c221-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="5c221-162">Stöd för anropa metoden med `ByRef-like` Skriv parametrar (#7721)</span><span class="sxs-lookup"><span data-stu-id="5c221-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="5c221-163">Hantera Windows PowerShell-modulens sökväg redan används i den miljön PSModulePath (#7727)</span><span class="sxs-lookup"><span data-stu-id="5c221-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="5c221-164">Aktivera `SecureString` -cmdletar för Windows genom att lagra den oformaterade texten (#9199)</span><span class="sxs-lookup"><span data-stu-id="5c221-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="5c221-165">Förbättra felmeddelande vid icke-Windows när du importerar clixml med securestring (#7997)</span><span class="sxs-lookup"><span data-stu-id="5c221-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="5c221-166">Att lägga till parametern ReplyTo till `Send-MailMessage` (#8727) (tack @replicaJunction!)</span><span class="sxs-lookup"><span data-stu-id="5c221-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="5c221-167">Lägg till föråldrat meddelande till `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="5c221-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="5c221-168">Åtgärda `Restart-Computer` att arbeta med `localhost` när WinRM är inte finns (#9160)</span><span class="sxs-lookup"><span data-stu-id="5c221-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="5c221-169">Kontrollera `Start-Job` throw avslutande fel när PowerShell värd (#9128)</span><span class="sxs-lookup"><span data-stu-id="5c221-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="5c221-170">Lägg till C# style typ acceleratorer och suffix för ushort, uint, ulong och korta litteraler (#7813) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="5c221-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5c221-171">Har lagts till nytt suffix för numeriska literaler – Se [about_Numeric_Literals][] (#7901) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="5c221-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5c221-172">Korrekt rapportering effektnivå när SupportsShouldProcess inte är inställd på 'true' (#8209) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="5c221-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5c221-173">Åtgärda teckenuppsättningen problem i Web-Cmdlets (#8742) (tack @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="5c221-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="5c221-174">Åtgärda Expect `100-continue` problem med Web-cmdletar (#8679) (tack @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="5c221-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="5c221-175">Åtgärda blockeringsproblem för filen med web-cmdletar (#7676) (tack @Claustn!)</span><span class="sxs-lookup"><span data-stu-id="5c221-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="5c221-176">Åtgärda teckentabellen parsning problem i `Invoke-RestMethod` (#8694) (tack @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="5c221-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="5c221-177">Omstrukturera `ConvertTo-Json` att exponera JsonObject.ConvertToJson som inget offentligt API (#8682)</span><span class="sxs-lookup"><span data-stu-id="5c221-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="5c221-178">Lägg till konfigurerbara maximala djupet i `ConvertFrom-Json` med - djup (#8199) (tack @louistio!)</span><span class="sxs-lookup"><span data-stu-id="5c221-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="5c221-179">Lägg till EscapeHandling parameter i `ConvertTo-Json` cmdlet (#7775) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="5c221-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5c221-180">Lägg till `-CustomPipeName` till pwsh och `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="5c221-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="5c221-181">Aktivera skapa relativa symboliska länkar på Windows med `New-Item` (#8783)</span><span class="sxs-lookup"><span data-stu-id="5c221-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="5c221-182">Tillåt Windows-användare i utvecklare för att skapa symlinks utan höjning (#8534)</span><span class="sxs-lookup"><span data-stu-id="5c221-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="5c221-183">Aktivera `Write-Information` att acceptera `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="5c221-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="5c221-184">Åtgärda `Get-Help` för avancerade funktioner med MAML hjälpinnehåll (#8353)</span><span class="sxs-lookup"><span data-stu-id="5c221-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="5c221-185">Åtgärda `Get-Help` PSTypeName problem med - parametern när bara en parametern deklareras (#8754) (tack @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="5c221-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="5c221-186">Token beräkning korrigering för `Get-Help` körs på ScriptBlock kommentar hjälp.</span><span class="sxs-lookup"><span data-stu-id="5c221-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="5c221-187">(#8238) (Tack @hubuk!)</span><span class="sxs-lookup"><span data-stu-id="5c221-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="5c221-188">Ändra `Get-Help` cmdlet-parametern-parametern så att den accepterar sträng matriser (#8454) (tack @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="5c221-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="5c221-189">Lösa PERSONSÖKARE om sökvägen innehåller blanksteg (#8571) (tack @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="5c221-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="5c221-190">Lägg till fråga i användningen av `less` i Hjälp om du till ber användaren att avsluta (#7998)-funktionen</span><span class="sxs-lookup"><span data-stu-id="5c221-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="5c221-191">Lägga till stöd för uppräkning och char typer i `Format-Hex` cmdlet (#8191) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="5c221-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5c221-192">Ta bort ShouldProcess från `Format-Hex` (#8178)</span><span class="sxs-lookup"><span data-stu-id="5c221-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="5c221-193">Lägg till nya förskjutning och antal parametrar till `Format-Hex` och omstrukturera cmdleten (#7877) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="5c221-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5c221-194">Tillåt 'name' som ett alias-nyckel för 'etiketten' i `ConvertTo-Html`, Tillåt 'bredd-posten ska vara ett heltal (#8426) (tack @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="5c221-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="5c221-195">Kontrollera scriptblock baseras beräknade egenskaper fungerar igen i `ConvertTo-Html` (#8427) (tack @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="5c221-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="5c221-196">Lägg till cmdlet `Join-String` för att skapa text från pipelinen indata (#7660) (tack @powercode!)</span><span class="sxs-lookup"><span data-stu-id="5c221-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="5c221-197">Åtgärda `Join-String` cmdlet FormatString parametern logic (#8449) (tack @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="5c221-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="5c221-198">Ändra `Clear-Host` till att använda `$RAWUI` och avmarkera om du vill arbeta med fjärrkommunikation (#8609)</span><span class="sxs-lookup"><span data-stu-id="5c221-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="5c221-199">Ändra `Clear-Host` till kallas bara `[console]::clear` och ta bort rensa alias från Unix (#8603)</span><span class="sxs-lookup"><span data-stu-id="5c221-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="5c221-200">Åtgärda LiteralPath i `Import-Csv` att binda till `Get-ChildItem` utdata (#8277) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="5c221-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5c221-201">hjälpfunktionen bör inte använda personsökare för AliasHelpInfo (#8552)</span><span class="sxs-lookup"><span data-stu-id="5c221-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="5c221-202">Lägg till `-UseMinimalHeader` till `Start-Transcript` att minimera avskrift rubrik (#8402) (tack @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="5c221-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="5c221-203">Lägg till `Enable-ExperimentalFeature` och `Disable-ExperimentalFeature` cmdletar (#8318)</span><span class="sxs-lookup"><span data-stu-id="5c221-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="5c221-204">Exponera alla cmdletar från **PSDiagnostics** om logman.exe är tillgängliga (#8366)</span><span class="sxs-lookup"><span data-stu-id="5c221-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="5c221-205">Ta bort **spara** parametern från `New-PSDrive` på `non-Windows` plattform (#8291) (tack @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="5c221-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="5c221-206">Lägg till stöd för `cd +` (#7206) (tack @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="5c221-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="5c221-207">Aktivera `Set-Location -LiteralPath` att arbeta med mappar med följande namn - och + (#8089)</span><span class="sxs-lookup"><span data-stu-id="5c221-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="5c221-208">`Test-Path` Returnerar `$false` när en tom eller `$null` sökväg värde (#8080) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="5c221-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5c221-209">Tillåt dynamisk parameter som ska returneras även om sökvägen inte matchar någon leverantör (#7957)</span><span class="sxs-lookup"><span data-stu-id="5c221-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="5c221-210">Stöd för `Get-PSHostProcessInfo` och `Enter-PSHostProcess` på Unix-plattformar (#8232)</span><span class="sxs-lookup"><span data-stu-id="5c221-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="5c221-211">Minska allokeringar i `Get-Content` cmdlet (#8103) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="5c221-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5c221-212">Aktivera `Add-Content` delar läsbehörighet med andra verktyg vid skrivning till innehåll (#8091)</span><span class="sxs-lookup"><span data-stu-id="5c221-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="5c221-213">`Get/Add-Content` genererar förbättrad fel när måldatorn är en behållare (#7823) (tack @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="5c221-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="5c221-214">Lägg till `-Name`, `-NoUserOverrides` och `-ListAvailable` parametrar för att `Get-Culture` cmdlet (#7702) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="5c221-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5c221-215">Lägg till enhetlig attribut för slutförande för **Encoding** parametern.</span><span class="sxs-lookup"><span data-stu-id="5c221-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="5c221-216">(#7732) (Tack @ThreeFive-O!)</span><span class="sxs-lookup"><span data-stu-id="5c221-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="5c221-217">Tillåt numeriska ID: N och namnet på registrerade teckentabeller i **Encoding** parametrar (#7636) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="5c221-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5c221-218">Åtgärda `Rename-Item -Path` med jokertecken char (#7398) (tack @kwkam!)</span><span class="sxs-lookup"><span data-stu-id="5c221-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="5c221-219">När du använder `Start-Transcript` och filen finns, tom fil snarare än att tas bort (#8131) (tack @paalbra!)</span><span class="sxs-lookup"><span data-stu-id="5c221-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="5c221-220">Kontrollera `Add-Type` öppna källfiler med **FileAccess.Read** och **FileShare.Read** uttryckligen (#7915) (tack @IISResetMe!)</span><span class="sxs-lookup"><span data-stu-id="5c221-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="5c221-221">Åtgärda `Enter-PSSession -ContainerId` för den senaste Windows (#7883)</span><span class="sxs-lookup"><span data-stu-id="5c221-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="5c221-222">Se till att **NestedModules** egenskapen fylls med `Test-ModuleManifest` (#7859)</span><span class="sxs-lookup"><span data-stu-id="5c221-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="5c221-223">Lägg till `%F` fallet till `Get-Date` - UFormat (#7630) (tack @britishben!)</span><span class="sxs-lookup"><span data-stu-id="5c221-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="5c221-224">Åtgärda `Set-Service -Status Stopped` stoppa tjänsterna med beroenden (#5525) (tack @zhenggu!)</span><span class="sxs-lookup"><span data-stu-id="5c221-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentella funktioner]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
