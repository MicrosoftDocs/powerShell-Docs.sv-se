---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Checklista för resursskapande
ms.openlocfilehash: c0a18169b5e9f6ba0c3848b00725731453763611
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941196"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="fb4c5-103">Checklista för resursskapande</span><span class="sxs-lookup"><span data-stu-id="fb4c5-103">Resource authoring checklist</span></span>

<span data-ttu-id="fb4c5-104">Den här check listan är en lista över bästa metoder när du redigerar en ny DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="fb4c5-105">Resource module innehåller. psd1-filen och schema. MOF för varje resurs</span><span class="sxs-lookup"><span data-stu-id="fb4c5-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="fb4c5-106">Kontrol lera att resursen har rätt struktur och innehåller alla filer som krävs.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="fb4c5-107">Varje modul ska innehålla en. psd1-fil och varje icke-sammansatt resurs ska ha schema. MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="fb4c5-108">Resurser som inte innehåller schemat visas inte i `Get-DscResource`. användarna kommer inte att kunna använda IntelliSense: er när de skriver kod mot modulerna i ISE.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="fb4c5-109">Katalog strukturen för xRemoteFile-resursen, som är en del av [modulen xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="fb4c5-110">Resurs och schema är korrekta</span><span class="sxs-lookup"><span data-stu-id="fb4c5-110">Resource and schema are correct</span></span>

<span data-ttu-id="fb4c5-111">Kontrol lera resurs schema filen (\*. schema. MOF).</span><span class="sxs-lookup"><span data-stu-id="fb4c5-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="fb4c5-112">Du kan använda [DSC Resource designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) för att utveckla och testa ditt schema.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span>
<span data-ttu-id="fb4c5-113">Kontrollera att:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-113">Make sure that:</span></span>

- <span data-ttu-id="fb4c5-114">Egenskaps typerna är korrekta (t. ex. Använd inte sträng för egenskaper som accepterar numeriska värden bör du använda UInt32 eller andra numeriska typer i stället)</span><span class="sxs-lookup"><span data-stu-id="fb4c5-114">Property types are correct (e.g. don't use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="fb4c5-115">Egenskaps attribut anges korrekt som: ([key], [required], [Write], [Read])</span><span class="sxs-lookup"><span data-stu-id="fb4c5-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="fb4c5-116">Minst en parameter i schemat måste markeras som [key]</span><span class="sxs-lookup"><span data-stu-id="fb4c5-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="fb4c5-117">[Read]-egenskapen är inte tillsammans med någon av: [required], [key], [Write]</span><span class="sxs-lookup"><span data-stu-id="fb4c5-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="fb4c5-118">Om flera kvalificerare anges utom [Läs], har [key] företräde</span><span class="sxs-lookup"><span data-stu-id="fb4c5-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="fb4c5-119">Om [Write] och [required] anges prioriteras [required]</span><span class="sxs-lookup"><span data-stu-id="fb4c5-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="fb4c5-120">ValueMap anges där lämpligt exempel:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="fb4c5-121">Eget namn anges och bekräftar till namn konventioner för DSC</span><span class="sxs-lookup"><span data-stu-id="fb4c5-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="fb4c5-122">Exempel: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="fb4c5-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="fb4c5-123">Varje fält har meningsfull beskrivning.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-123">Every field has meaningful description.</span></span> <span data-ttu-id="fb4c5-124">PowerShell-GitHub-lagringsplatsen har användbara exempel, till exempel [. schema. MOF för xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="fb4c5-124">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="fb4c5-125">Dessutom bör du använda **test-xDscResource** och **test-xDscSchema-cmdlet:** ar från [DSC Resource designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) för att automatiskt verifiera resursen och schemat:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-125">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="fb4c5-126">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="fb4c5-127">Resurs inläsningar utan fel</span><span class="sxs-lookup"><span data-stu-id="fb4c5-127">Resource loads without errors</span></span>

<span data-ttu-id="fb4c5-128">Kontrol lera om modulen kan läsas in korrekt.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-128">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="fb4c5-129">Detta kan uppnås manuellt, genom att köra `Import-Module <resource_module> -force` och bekräfta att inga fel har inträffat, eller genom att skriva test automatisering.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="fb4c5-130">I det senare fallet kan du följa den här strukturen i test fallet:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="fb4c5-131">Resursen är idempotenta i det positiva fallet</span><span class="sxs-lookup"><span data-stu-id="fb4c5-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="fb4c5-132">En av de grundläggande egenskaperna hos DSC-resurser är idempotence.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="fb4c5-133">Det innebär att att tillämpa en DSC-konfiguration som innehåller resursen flera gånger kommer alltid att uppnå samma resultat.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="fb4c5-134">Om vi till exempel skapar en konfiguration som innehåller följande fil resurs:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="fb4c5-135">När du har tillämpat det för första gången ska filen test. txt visas i `C:\test` mapp.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="fb4c5-136">Efterföljande körningar av samma konfiguration bör dock inte ändra datorns tillstånd (t. ex. inga kopior av den `test.txt` filen ska skapas).</span><span class="sxs-lookup"><span data-stu-id="fb4c5-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span>
<span data-ttu-id="fb4c5-137">För att säkerställa att en resurs är idempotenta kan du upprepade gånger anropa `Set-TargetResource` när du testar resursen direkt eller anropa `Start-DscConfiguration` flera gånger när du utför testningen.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="fb4c5-138">Resultatet bör vara detsamma efter varje körning.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="fb4c5-139">Testa användar ändrings scenario</span><span class="sxs-lookup"><span data-stu-id="fb4c5-139">Test user modification scenario</span></span>

<span data-ttu-id="fb4c5-140">Genom att ändra datorns tillstånd och sedan köra DSC igen, kan du kontrol lera att `Set-TargetResource` och `Test-TargetResource` fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="fb4c5-141">Här följer några steg som du bör vidta:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="fb4c5-142">Starta med resursen inte i önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-142">Start with the resource not in the desired state.</span></span>
2. <span data-ttu-id="fb4c5-143">Kör konfiguration med din resurs</span><span class="sxs-lookup"><span data-stu-id="fb4c5-143">Run configuration with your resource</span></span>
3. <span data-ttu-id="fb4c5-144">Verifiera `Test-DscConfiguration` returnerar sant</span><span class="sxs-lookup"><span data-stu-id="fb4c5-144">Verify `Test-DscConfiguration` returns True</span></span>
4. <span data-ttu-id="fb4c5-145">Ändra det konfigurerade objektet så att det inte är i önskat tillstånd</span><span class="sxs-lookup"><span data-stu-id="fb4c5-145">Modify the configured item to be out of the desired state</span></span>
5. <span data-ttu-id="fb4c5-146">Verifiera `Test-DscConfiguration` returnerar falskt</span><span class="sxs-lookup"><span data-stu-id="fb4c5-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="fb4c5-147">Här är ett mer konkret exempel med hjälp av register resurser:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-147">Here's a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="fb4c5-148">Starta med register nyckeln har inte önskat tillstånd</span><span class="sxs-lookup"><span data-stu-id="fb4c5-148">Start with registry key not in the desired state</span></span>
2. <span data-ttu-id="fb4c5-149">Kör `Start-DscConfiguration` med en konfiguration för att spara den i önskat tillstånd och kontrol lera att den är klar.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
3. <span data-ttu-id="fb4c5-150">Kör `Test-DscConfiguration` och kontrol lera att den returnerar true</span><span class="sxs-lookup"><span data-stu-id="fb4c5-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
4. <span data-ttu-id="fb4c5-151">Ändra värdet för nyckeln så att det inte är i önskat tillstånd</span><span class="sxs-lookup"><span data-stu-id="fb4c5-151">Modify the value of the key so that it is not in the desired state</span></span>
5. <span data-ttu-id="fb4c5-152">Kör `Test-DscConfiguration` och kontrol lera att den returnerar false</span><span class="sxs-lookup"><span data-stu-id="fb4c5-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
6. <span data-ttu-id="fb4c5-153">`Get-TargetResource` funktionerna har verifierats med hjälp av `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="fb4c5-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="fb4c5-154">`Get-TargetResource` bör returnera information om resursens aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="fb4c5-155">Se till att testa den genom att anropa `Get-DscConfiguration` när du har tillämpat konfigurationen och verifiera att utdata på rätt sätt visar datorns aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="fb4c5-156">Det är viktigt att testa det separat, eftersom eventuella problem i det här avsnittet inte visas när du anropar `Start-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="fb4c5-157">Anropa **Get/Set/test-TargetResource-** funktioner direkt</span><span class="sxs-lookup"><span data-stu-id="fb4c5-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="fb4c5-158">Se till att testa funktionerna **Get/Set/test-TargetResource** som implementerats i din resurs genom att anropa dem direkt och kontrol lera att de fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="fb4c5-159">Verifiera slut punkt till slut punkt med **Start-DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="fb4c5-159">Verify End to End using **Start-DscConfiguration**</span></span>

<span data-ttu-id="fb4c5-160">Testa **Get/Set/test-TargetResource-** funktioner genom att anropa dem direkt, men alla problem kommer inte att upptäckas på det sättet.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="fb4c5-161">Du bör fokusera betydande del av testningen på att använda `Start-DscConfiguration` eller hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="fb4c5-162">Detta är i själva verket hur användarna kommer att använda resursen, så funktionen underskattar inte betydelsen av den här typen av tester.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-162">In fact, this is how users will use the resource, so don't underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="fb4c5-163">Möjliga typer av problem:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-163">Possible types of issues:</span></span>

- <span data-ttu-id="fb4c5-164">Autentiseringsuppgiften/sessionen kan fungera annorlunda eftersom DSC-agenten körs som en tjänst.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="fb4c5-165">Se till att testa alla funktioner som slutar att avslutas.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="fb4c5-166">Fel utdata från `Start-DscConfiguration` kan skilja sig från de som visas när du anropar `Set-TargetResource`-funktionen direkt.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="fb4c5-167">Testa kompatibilitet på alla plattformar som stöds av DSC</span><span class="sxs-lookup"><span data-stu-id="fb4c5-167">Test compatability on all DSC supported platforms</span></span>

<span data-ttu-id="fb4c5-168">Resursen ska fungera på alla plattformar som stöds av DSC (Windows Server 2008 R2 och senare).</span><span class="sxs-lookup"><span data-stu-id="fb4c5-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="fb4c5-169">Installera den senaste versionen av WMF (Windows Management Framework) på ditt operativ system för att få den senaste versionen av DSC.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="fb4c5-170">Om resursen inte fungerar på vissa av dessa plattformar efter design ska ett visst fel meddelande returneras.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="fb4c5-171">Kontrol lera också att din resurs kontrollerar om cmdlets som du anropar finns på en viss dator.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="fb4c5-172">Windows Server 2012 har lagt till ett stort antal nya cmdletar som inte är tillgängliga på Windows Server-2008R2, även med WMF installerat.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="fb4c5-173">Verifiera på Windows-klienten (om tillämpligt)</span><span class="sxs-lookup"><span data-stu-id="fb4c5-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="fb4c5-174">Ett mycket vanligt test glapp verifierar bara resursen på Server versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="fb4c5-175">Många resurser är också utformade för att fungera på klient-SKU: er, så om det är sant i ditt fall kan du inte glömma att testa det på dessa plattformar.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-175">Many resources are also designed to work on Client SKUs, so if that's true in your case, don't forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="fb4c5-176">Get-Dscresource Keyword Supports visar resursen</span><span class="sxs-lookup"><span data-stu-id="fb4c5-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="fb4c5-177">När du har distribuerat modulen ska du anropa `Get-DscResource` lista din resurs bland andra på grund av ett resultat.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="fb4c5-178">Om du inte hittar din resurs i listan ser du till att schema. MOF-filen för resursen finns.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-178">If you can't find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="fb4c5-179">Resurs modulen innehåller exempel</span><span class="sxs-lookup"><span data-stu-id="fb4c5-179">Resource module contains examples</span></span>

<span data-ttu-id="fb4c5-180">Skapa kvalitets exempel som hjälper andra att förstå hur de används.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="fb4c5-181">Detta är viktigt, särskilt eftersom många användare behandlar exempel kod som dokumentation.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="fb4c5-182">Först bör du bestämma de exempel som ska ingå i modulen – du bör minst omfatta de viktigaste användnings fallen för din resurs:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="fb4c5-183">Om din modul innehåller flera resurser som behöver fungera tillsammans för ett scenario från slut punkt till slut punkt skulle det första exemplet vara bäst.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="fb4c5-184">De inledande exemplen bör vara väldigt enkla – hur du kommer igång med dina resurser i små hanterbara segment (t. ex. skapa en ny virtuell hård disk)</span><span class="sxs-lookup"><span data-stu-id="fb4c5-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="fb4c5-185">Efterföljande exempel bör bygga på dessa exempel (t. ex. skapa en virtuell dator från en virtuell hård disk, ta bort virtuell dator, ändra VM) och Visa avancerade funktioner (t. ex. skapa en virtuell dator med dynamiskt minne)</span><span class="sxs-lookup"><span data-stu-id="fb4c5-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="fb4c5-186">Exempel på konfigurationer ska vara parameterstyrda (alla värden ska skickas till konfigurationen som parametrar och det får inte finnas några hårdkodad-värden):</span><span class="sxs-lookup"><span data-stu-id="fb4c5-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- <span data-ttu-id="fb4c5-187">Det är en bra idé att inkludera (kommentera ut) exempel på hur du anropar konfigurationen med de faktiska värdena i slutet av exempel skriptet.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-187">It's a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
  <span data-ttu-id="fb4c5-188">I konfigurationen ovan är det till exempel inte nödvändigt vis uppenbart att det bästa sättet att ange UserAgent är:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="fb4c5-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` i vilket fall en kommentar kan klargöra den avsedda körningen av konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- <span data-ttu-id="fb4c5-190">För varje exempel skriver du en kort beskrivning som förklarar vad det gör och syftet med parametrarna.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="fb4c5-191">Se till att exemplen tar upp de flesta viktiga scenarier för din resurs, och om inget saknas, kontrollerar du att alla kör och sätter datorn i önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-191">Make sure examples cover most the important scenarios for your resource and if there's nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="fb4c5-192">Fel meddelanden är lätta att förstå och hjälpa användare att lösa problem</span><span class="sxs-lookup"><span data-stu-id="fb4c5-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="fb4c5-193">Fel meddelanden bör vara:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-193">Good error messages should be:</span></span>

- <span data-ttu-id="fb4c5-194">Det: det största problemet med fel meddelanden är att de ofta inte finns, så se till att de finns där.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-194">There: The biggest problem with error messages is that they often don't exist, so make sure they are there.</span></span>
- <span data-ttu-id="fb4c5-195">Lätt att förstå: läslig, inga dolda felkoder</span><span class="sxs-lookup"><span data-stu-id="fb4c5-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="fb4c5-196">Exakt: beskriv vad som är exakt som problemet</span><span class="sxs-lookup"><span data-stu-id="fb4c5-196">Precise: Describe what's exactly the problem</span></span>
- <span data-ttu-id="fb4c5-197">Informell: råd om hur du kan åtgärda problemet</span><span class="sxs-lookup"><span data-stu-id="fb4c5-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="fb4c5-198">Avslutningen: klandra inte användaren eller gör så att de känner sig dåligt</span><span class="sxs-lookup"><span data-stu-id="fb4c5-198">Polite: Don't blame user or make them feel bad</span></span>

<span data-ttu-id="fb4c5-199">Se till att kontrol lera om det finns fel i end to end-scenarier (med `Start-DscConfiguration`), eftersom de kan skilja sig från de som returneras när du kör resurs funktionerna direkt.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="fb4c5-200">Logg meddelanden är lätta att förstå och informativt (inklusive – utförliga,-felsöka och ETW-loggar)</span><span class="sxs-lookup"><span data-stu-id="fb4c5-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="fb4c5-201">Se till att de loggar som returneras av resursen är lätta att förstå och ange värde för användaren.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="fb4c5-202">Resurserna bör returnera all information som kan vara till hjälp för användaren, men fler loggar är inte alltid bättre.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="fb4c5-203">Du bör undvika redundans och att mata ut data som inte ger ytterligare värde – gör inte någon att gå igenom hundratals logg poster för att hitta det du söker.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-203">You should avoid redundancy and outputting data which does not provide additional value – don't make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="fb4c5-204">Det är naturligtvis ingen acceptabel lösning för det här problemet.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="fb4c5-205">När du testar bör du även analysera utförliga loggar och fel söknings loggar (genom att köra `Start-DscConfiguration` med `–Verbose` och `–Debug` växlar på lämpligt sätt), samt ETW-loggar.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="fb4c5-206">Om du vill se DSC ETW loggar går du till Loggboken och öppnar följande mapp: program och tjänster-Microsoft-Windows-önskad tillstånds konfiguration.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="fb4c5-207">Som standard kommer det att finnas en drifts kanal, men se till att du aktiverar analys-och fel söknings kanaler innan du kör konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="fb4c5-208">Om du vill aktivera analytiska/felsöka kanaler kan du köra skriptet nedan:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="fb4c5-209">Resurs implementeringen innehåller inte hårdkodad-sökvägar</span><span class="sxs-lookup"><span data-stu-id="fb4c5-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="fb4c5-210">Se till att det inte finns några hårdkodad sökvägar i resurs implementeringen, särskilt om de antar språk (en-US) eller om det finns systemvariabler som kan användas.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="fb4c5-211">Om din resurs behöver åtkomst till vissa sökvägar använder du miljövariabler istället för att hårdkoda sökvägen, eftersom den kan vara annorlunda på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="fb4c5-212">Exempel:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-212">Example:</span></span>

<span data-ttu-id="fb4c5-213">Istället för:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="fb4c5-214">Du kan skriva:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="fb4c5-215">Resurs implementeringen innehåller ingen användar information</span><span class="sxs-lookup"><span data-stu-id="fb4c5-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="fb4c5-216">Se till att det inte finns några e-postnamn, konto information eller namn på personer i koden.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="fb4c5-217">Resursen har testats med giltiga/ogiltiga autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="fb4c5-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="fb4c5-218">Om din resurs tar emot autentiseringsuppgifter som parameter:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="fb4c5-219">Kontrol lera att resursen fungerar när det lokala systemet (eller dator kontot för fjär resurser) inte har åtkomst.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="fb4c5-220">Kontrol lera att resursen fungerar med autentiseringsuppgifter som angetts för Get-, set-och test</span><span class="sxs-lookup"><span data-stu-id="fb4c5-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="fb4c5-221">Om resursen har åtkomst till resurser testar du alla varianter som du behöver stödja, till exempel:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="fb4c5-222">Standard resurser i Windows.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-222">Standard windows shares.</span></span>
  - <span data-ttu-id="fb4c5-223">DFS-resurser.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-223">DFS shares.</span></span>
  - <span data-ttu-id="fb4c5-224">SAMBA i resurser (om du vill ha stöd för Linux.)</span><span class="sxs-lookup"><span data-stu-id="fb4c5-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="fb4c5-225">Resursen kräver inte interaktiva ingångar</span><span class="sxs-lookup"><span data-stu-id="fb4c5-225">Resource does not require interactive input</span></span>

<span data-ttu-id="fb4c5-226">**Get/Set/test-TargetResource-** funktioner ska köras automatiskt och får inte vänta på användarens indata i körnings fasen (t. ex. bör du inte använda `Get-Credential` inuti dessa funktioner).</span><span class="sxs-lookup"><span data-stu-id="fb4c5-226">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user's input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="fb4c5-227">Om du behöver ange användarens indata, bör du skicka den till konfigurationen som en parameter under kompilerings fasen.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-227">If you need to provide user's input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="fb4c5-228">Resurs funktionen har testats grundligt</span><span class="sxs-lookup"><span data-stu-id="fb4c5-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="fb4c5-229">Den här check listan innehåller objekt som är viktiga för att testas och/eller som ofta saknas.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="fb4c5-230">Det kommer att finnas flera tester, främst funktioner som är speciella för den resurs som du testar och som inte nämns här.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="fb4c5-231">Glöm inte om negativa test fall.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-231">Don't forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="fb4c5-232">Bästa praxis: modulen resurs innehåller mappen tester med skriptet ResourceDesignerTests. ps1</span><span class="sxs-lookup"><span data-stu-id="fb4c5-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="fb4c5-233">Det är en bra idé att skapa mappen "tester" i modulen resurs, skapa `ResourceDesignerTests.ps1`-fil och lägga till tester med **test-xDscResource** och **test-xDscSchema** för alla resurser i den aktuella modulen.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-233">It's a good practice to create folder "Tests" inside resource module, create `ResourceDesignerTests.ps1` file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="fb4c5-234">På så sätt kan du snabbt verifiera scheman för alla resurser från de aktuella modulerna och göra en Sanity kontroll innan du publicerar.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="fb4c5-235">För xRemoteFile kan `ResourceTests.ps1` se så enkelt som:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="fb4c5-236">Bästa praxis: resursvyn innehåller Resource designer-skript för att skapa schema</span><span class="sxs-lookup"><span data-stu-id="fb4c5-236">Best practice: Resource folder contains resource designer script for generating schema</span></span>

<span data-ttu-id="fb4c5-237">Varje resurs ska innehålla ett Resource designer-skript som genererar ett MOF-schema för resursen.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-237">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="fb4c5-238">Den här filen ska placeras i `<ResourceName>\ResourceDesignerScripts` och vara namngiven som generate `<ResourceName>Schema.ps1` för xRemoteFile-resurs den här filen kallas `GenerateXRemoteFileSchema.ps1` och innehåller:</span><span class="sxs-lookup"><span data-stu-id="fb4c5-238">This file should be placed in `<ResourceName>\ResourceDesignerScripts` and be named Generate `<ResourceName>Schema.ps1` For xRemoteFile resource this file would be called `GenerateXRemoteFileSchema.ps1` and contain:</span></span>

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="fb4c5-239">Bästa praxis: resurs stöder-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fb4c5-239">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="fb4c5-240">Om din resurs utför "farliga" åtgärder är det en bra idé att implementera `-WhatIf`-funktioner.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-240">If your resource is performing "dangerous" operations, it's a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="fb4c5-241">När du är klar kontrollerar du att `-WhatIf` utdata korrekt beskriver åtgärder som skulle inträffa om kommandot kördes utan `-WhatIf` växel.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-241">After it's done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span>
<span data-ttu-id="fb4c5-242">Kontrol lera också att åtgärderna inte körs (inga ändringar i nodens tillstånd görs) när `–WhatIf` switch finns.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-242">Also, verify that operations does not execute (no changes to the node's state are made) when `–WhatIf` switch is present.</span></span>
<span data-ttu-id="fb4c5-243">Vi antar till exempel att vi testar fil resursen.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-243">For example, let's assume we are testing File resource.</span></span> <span data-ttu-id="fb4c5-244">Nedan visas en enkel konfiguration som skapar fil `test.txt` med innehållet "test":</span><span class="sxs-lookup"><span data-stu-id="fb4c5-244">Below is simple configuration which creates file `test.txt` with contents "test":</span></span>

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

<span data-ttu-id="fb4c5-245">Om vi kompilerar och sedan kör konfigurationen med växeln `-WhatIf`, säger utdata till oss exakt vad som skulle hända när vi kör konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-245">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="fb4c5-246">Själva konfigurationen utfördes dock inte (`test.txt` filen skapades inte).</span><span class="sxs-lookup"><span data-stu-id="fb4c5-246">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="fb4c5-247">Den här listan är inte fullständig, men den täcker många viktiga problem som kan uppstå vid design, utveckling och testning av DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="fb4c5-247">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
