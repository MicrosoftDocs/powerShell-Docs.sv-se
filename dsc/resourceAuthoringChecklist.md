---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Checklista för redigering av resursen"
ms.openlocfilehash: 9e9855f4ad4ee6db4d9e3b90d3c9a03d81429805
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="781d4-103">Checklista för redigering av resursen</span><span class="sxs-lookup"><span data-stu-id="781d4-103">Resource authoring checklist</span></span>
<span data-ttu-id="781d4-104">Den här checklistan är en lista över rekommenderade metoder när du skapar en ny DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="781d4-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="781d4-105">Resursmodul innehåller .psd1 fil- och schema.mof för alla resurser</span><span class="sxs-lookup"><span data-stu-id="781d4-105">Resource module contains .psd1 file and schema.mof for every resource</span></span> 
<span data-ttu-id="781d4-106">Kontrollera att resursen har rätt struktur och innehåller alla nödvändiga filer.</span><span class="sxs-lookup"><span data-stu-id="781d4-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="781d4-107">Resursmodul för varje ska innehålla en .psd1-fil och alla icke sammansatta resurser ska ha schema.mof fil.</span><span class="sxs-lookup"><span data-stu-id="781d4-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="781d4-108">Resurser som inte innehåller schemat visas inte av **Get-DscResource** och användare kommer inte att kunna använda intellisense när skriva kod mot dessa moduler i ISE.</span><span class="sxs-lookup"><span data-stu-id="781d4-108">Resources that do not contain schema will not be listed by **Get-DscResource** and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span> <span data-ttu-id="781d4-109">Katalogstruktur för xRemoteFile resurs, som är en del av den [xPSDesiredStateConfiguration Resursmodul](https://github.com/PowerShell/xPSDesiredStateConfiguration), ser ut som följer:</span><span class="sxs-lookup"><span data-stu-id="781d4-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>


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

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="781d4-110">Resurs- och schema är korrekta ##</span><span class="sxs-lookup"><span data-stu-id="781d4-110">Resource and schema are correct##</span></span>
<span data-ttu-id="781d4-111">Verifiera resursschemat (*. schema.mof) fil.</span><span class="sxs-lookup"><span data-stu-id="781d4-111">Verify the resource schema (*.schema.mof) file.</span></span> <span data-ttu-id="781d4-112">Du kan använda den [DSC resurs Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) för att utveckla och testa ditt schema.</span><span class="sxs-lookup"><span data-stu-id="781d4-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to help develop and test your schema.</span></span> <span data-ttu-id="781d4-113">Kontrollera att:</span><span class="sxs-lookup"><span data-stu-id="781d4-113">Make sure that:</span></span>
- <span data-ttu-id="781d4-114">Egenskapstyperna är rätt (t.ex. Använd inte sträng för egenskaper som accepterar numeriska värden, bör du använda UInt32 eller andra numeriska typer i stället)</span><span class="sxs-lookup"><span data-stu-id="781d4-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="781d4-115">Egenskapsattribut är angivna korrekt som: ([nyckel], [krävs], [skriva] [läsa])</span><span class="sxs-lookup"><span data-stu-id="781d4-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="781d4-116">Minst en parameter i schemat har markerats som [nyckel]</span><span class="sxs-lookup"><span data-stu-id="781d4-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="781d4-117">[läsa] egenskapen inte användas samtidigt tillsammans med någon av: [krävs], [key], [skriva]</span><span class="sxs-lookup"><span data-stu-id="781d4-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="781d4-118">Om flera kvalificerare anges förutom [Läs], prioriteras [key]</span><span class="sxs-lookup"><span data-stu-id="781d4-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="781d4-119">Om [skriva] och [krävs] har angetts och sedan [krävs] har prioritet</span><span class="sxs-lookup"><span data-stu-id="781d4-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="781d4-120">ValueMap anges i förekommande fall</span><span class="sxs-lookup"><span data-stu-id="781d4-120">ValueMap is specified where appropriate</span></span>

<span data-ttu-id="781d4-121">Exempel:</span><span class="sxs-lookup"><span data-stu-id="781d4-121">Example:</span></span>
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- <span data-ttu-id="781d4-122">Eget namn har angetts och bekräftar att DSC namngivningskonventioner</span><span class="sxs-lookup"><span data-stu-id="781d4-122">Friendly name is specified and confirms to DSC naming conventions</span></span>

<span data-ttu-id="781d4-123">Exempel: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span><span class="sxs-lookup"><span data-stu-id="781d4-123">Example: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span></span>

- <span data-ttu-id="781d4-124">Varje fält har beskrivning.</span><span class="sxs-lookup"><span data-stu-id="781d4-124">Every field has meaningful description.</span></span> <span data-ttu-id="781d4-125">PowerShell GitHub-lagringsplatsen har bra exempel som [det. schema.mof för xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="781d4-125">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="781d4-126">Dessutom bör du använda **Test xDscResource** och **Test xDscSchema** cmdlets från [DSC resurs Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) att automatiskt kontrollera resurs- och schema:</span><span class="sxs-lookup"><span data-stu-id="781d4-126">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to automatically verify the resource and schema:</span></span>
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
<span data-ttu-id="781d4-127">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="781d4-127">For example:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="781d4-128">Resursen har lästs in utan fel</span><span class="sxs-lookup"><span data-stu-id="781d4-128">Resource loads without errors</span></span> ##
<span data-ttu-id="781d4-129">Kontrollera om modulen resurs kan läsas.</span><span class="sxs-lookup"><span data-stu-id="781d4-129">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="781d4-130">Detta kan ske manuellt, genom att köra `Import-Module <resource_module> -force ` och bekräftar att inga fel uppstått eller skrivning av test automation.</span><span class="sxs-lookup"><span data-stu-id="781d4-130">This can be achieved manually, by running `Import-Module <resource_module> -force ` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="781d4-131">Du kan följa den här strukturen i din testfall vid denna:</span><span class="sxs-lookup"><span data-stu-id="781d4-131">In case of the latter, you can follow this structure in your test case:</span></span>
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="781d4-132">Resursen är idempotent positivt om</span><span class="sxs-lookup"><span data-stu-id="781d4-132">Resource is idempotent in the positive case</span></span> 
<span data-ttu-id="781d4-133">En av de grundläggande egenskaperna för DSC-resurser är vara idempotence.</span><span class="sxs-lookup"><span data-stu-id="781d4-133">One of the fundamental characteristics of DSC resources is be idempotence.</span></span> <span data-ttu-id="781d4-134">Det innebär att tillämpa en DSC-konfiguration som innehåller den här resursen flera gånger kommer alltid att uppnå samma resultat.</span><span class="sxs-lookup"><span data-stu-id="781d4-134">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="781d4-135">Om till exempel skapar vi en konfiguration som innehåller följande filresurs:</span><span class="sxs-lookup"><span data-stu-id="781d4-135">For example, if we create a configuration which contains the following File resource:</span></span>
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
} 
```
<span data-ttu-id="781d4-136">Efter att den första gången, ska filen test.txt visas i mappen C:\test.</span><span class="sxs-lookup"><span data-stu-id="781d4-136">After applying it for the first time, file test.txt should appear in C:\test folder.</span></span> <span data-ttu-id="781d4-137">Efterföljande körningar av samma konfiguration bör inte ändra tillståndet för den datorn (t.ex. inga kopior av filen test.txt ska skapas).</span><span class="sxs-lookup"><span data-stu-id="781d4-137">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the test.txt file should be created).</span></span>
<span data-ttu-id="781d4-138">En resurs är idempotent upprepade gånger kan du anropa **Set TargetResource** vid testning av resursen direkt eller anropa **Start DscConfiguration** flera gånger vid testning av slutpunkt till slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="781d4-138">To ensure a resource is idempotent you can repeatedly call **Set-TargetResource** when testing the resource directly, or call **Start-DscConfiguration** multiple times when doing end to end testing.</span></span> <span data-ttu-id="781d4-139">Resultatet bör vara samma efter varje kör.</span><span class="sxs-lookup"><span data-stu-id="781d4-139">The result should be the same after every run.</span></span> 


## <a name="test-user-modification-scenario"></a><span data-ttu-id="781d4-140">Testa Användarscenario ändring</span><span class="sxs-lookup"><span data-stu-id="781d4-140">Test user modification scenario</span></span> ##
<span data-ttu-id="781d4-141">Genom att ändra tillståndet för datorn och sedan köra DSC, kan du kontrollera att **Set TargetResource** och **Test TargetResource** fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="781d4-141">By changing the state of the machine and then rerunning DSC, you can verify that **Set-TargetResource** and **Test-TargetResource** function properly.</span></span> <span data-ttu-id="781d4-142">Här är vad du bör göra:</span><span class="sxs-lookup"><span data-stu-id="781d4-142">Here are steps you should take:</span></span>
1.  <span data-ttu-id="781d4-143">Börja med resursen inte finns i tillståndet.</span><span class="sxs-lookup"><span data-stu-id="781d4-143">Start with the resource not in the desired state.</span></span>
2.  <span data-ttu-id="781d4-144">Kör konfiguration med din resurs</span><span class="sxs-lookup"><span data-stu-id="781d4-144">Run configuration with your resource</span></span>
3.  <span data-ttu-id="781d4-145">Kontrollera **Test DscConfiguration** returnerar True</span><span class="sxs-lookup"><span data-stu-id="781d4-145">Verify **Test-DscConfiguration** returns True</span></span>
4.  <span data-ttu-id="781d4-146">Ändra den konfigurerade artikeln för att vara utanför tillståndet</span><span class="sxs-lookup"><span data-stu-id="781d4-146">Modify the configured item to be out of the desired state</span></span>
5.  <span data-ttu-id="781d4-147">Kontrollera **Test DscConfiguration** returnerar false här är en mer konkreta exempel med hjälp av registret resursen:</span><span class="sxs-lookup"><span data-stu-id="781d4-147">Verify **Test-DscConfiguration** returns false Here’s a more concrete example using Registry resource:</span></span>
1.  <span data-ttu-id="781d4-148">Börja med registernyckeln inte i tillståndet</span><span class="sxs-lookup"><span data-stu-id="781d4-148">Start with registry key not in the desired state</span></span>
2.  <span data-ttu-id="781d4-149">Kör **Start DscConfiguration** till en konfiguration för att placera den i tillståndet och kontrollera att den skickar.</span><span class="sxs-lookup"><span data-stu-id="781d4-149">Run **Start-DscConfiguration** with a configuration to put it in the desired state and verify it passes.</span></span>
3.  <span data-ttu-id="781d4-150">Kör **Test DscConfiguration** och kontrollera att den returnerar SANT</span><span class="sxs-lookup"><span data-stu-id="781d4-150">Run **Test-DscConfiguration** and verify it returns true</span></span>
4.  <span data-ttu-id="781d4-151">Ändra värdet för nyckeln så att den inte är i tillståndet önskade</span><span class="sxs-lookup"><span data-stu-id="781d4-151">Modify the value of the key so that it is not in the desired state</span></span>
5.  <span data-ttu-id="781d4-152">Kör **Test DscConfiguration** och kontrollera att den returnerar värdet false</span><span class="sxs-lookup"><span data-stu-id="781d4-152">Run **Test-DscConfiguration** and verify it returns false</span></span>
6.  <span data-ttu-id="781d4-153">Get-TargetResource funktioner har verifierats med hjälp av Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="781d4-153">Get-TargetResource functionality was verified using Get-DscConfiguration</span></span>

<span data-ttu-id="781d4-154">Get-TargetResource ska returnera information om det aktuella tillståndet för resursen.</span><span class="sxs-lookup"><span data-stu-id="781d4-154">Get-TargetResource should return details of the current state of the resource.</span></span> <span data-ttu-id="781d4-155">Se till att testa genom att anropa Get-DscConfiguration när du använder konfigurationen och verifiera att utdata korrekt visar det aktuella tillståndet för datorn.</span><span class="sxs-lookup"><span data-stu-id="781d4-155">Make sure to test it by calling Get-DscConfiguration after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="781d4-156">Det är viktigt att testa den separat, eftersom eventuella problem i det här området inte visas när du anropar Start DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="781d4-156">It's important to test it separately, since any issues in this area won't appear when calling Start-DscConfiguration.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="781d4-157">Anropa **Get/Set/Test-TargetResource** fungerar direkt</span><span class="sxs-lookup"><span data-stu-id="781d4-157">Call **Get/Set/Test-TargetResource** functions directly</span></span> ##

<span data-ttu-id="781d4-158">Kontrollera att du testar den **Get/Set/Test-TargetResource** funktioner som implementeras i din resurs genom att anropa dem direkt och verifiera att de fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="781d4-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="781d4-159">Kontrollera slutpunkt till slutpunkt med **Start DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="781d4-159">Verify End to End using **Start-DscConfiguration**</span></span> ##

<span data-ttu-id="781d4-160">Testa **Get/Set/Test-TargetResource** funktioner genom att anropa dem direkt är viktigt, men inte alla problem identifieras det här sättet.</span><span class="sxs-lookup"><span data-stu-id="781d4-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="781d4-161">Löningen bör beakta betydande del av din testning med hjälp av **Start DscConfiguration** eller pull-servern.</span><span class="sxs-lookup"><span data-stu-id="781d4-161">You should focus significant part of your testing on using **Start-DscConfiguration** or the pull server.</span></span> <span data-ttu-id="781d4-162">Detta är hur användare kommer att använda resursen, så att inte underskattar betydelsen av den här typen av testerna.</span><span class="sxs-lookup"><span data-stu-id="781d4-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span> <span data-ttu-id="781d4-163">Möjliga typer av problem:</span><span class="sxs-lookup"><span data-stu-id="781d4-163">Possible types of issues:</span></span>
- <span data-ttu-id="781d4-164">Autentiseringsuppgifter/Session fungera annorlunda eftersom DSC-agent körs som en tjänst.</span><span class="sxs-lookup"><span data-stu-id="781d4-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="781d4-165">Se till att testa alla funktioner här slutpunkt till slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="781d4-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="781d4-166">Utdata genom att fel **Start DscConfiguration** skiljer sig från de som visas när du anropar den **Set TargetResource** fungera direkt.</span><span class="sxs-lookup"><span data-stu-id="781d4-166">Errors output by **Start-DscConfiguration** may be different than those displayed when calling the **Set-TargetResource** function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="781d4-167">Testa kompatibilitet alla DSC plattformar som stöds</span><span class="sxs-lookup"><span data-stu-id="781d4-167">Test compatability on all DSC supported platforms</span></span> ##
<span data-ttu-id="781d4-168">Resursen ska fungera för alla plattformar som stöds DSC (Windows Server 2008 R2 och senare).</span><span class="sxs-lookup"><span data-stu-id="781d4-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="781d4-169">Installera den senaste WMF (Windows Management Framework) på ditt operativsystem för att hämta den senaste versionen av DSC.</span><span class="sxs-lookup"><span data-stu-id="781d4-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="781d4-170">Om din resurs inte fungerar på några av dessa plattformar avsiktligt, ska ett visst felmeddelande returneras.</span><span class="sxs-lookup"><span data-stu-id="781d4-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="781d4-171">Kontrollera också att din resurs kontrollerar om cmdlets som du ringer finns på en viss dator.</span><span class="sxs-lookup"><span data-stu-id="781d4-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="781d4-172">Windows Server 2012 läggas till ett stort antal nya cmdlet: ar som inte är tillgängliga på Windows Server 2008R2 även med WMF installerats.</span><span class="sxs-lookup"><span data-stu-id="781d4-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span> 

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="781d4-173">Kontrollera på Windows-klient (om tillämpligt)</span><span class="sxs-lookup"><span data-stu-id="781d4-173">Verify on Windows Client (if applicable)</span></span> ##
<span data-ttu-id="781d4-174">Ett mycket vanligt test lucka verifierar resursen endast på Windows serverversioner.</span><span class="sxs-lookup"><span data-stu-id="781d4-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="781d4-175">Många resurser är också utformade att fungera på klienten SKU: er, så om detta är true i ditt fall Glöm inte att testa på dessa plattformar samt.</span><span class="sxs-lookup"><span data-stu-id="781d4-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span> 
## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="781d4-176">Get-DSCResource visar resursen</span><span class="sxs-lookup"><span data-stu-id="781d4-176">Get-DSCResource lists the resource</span></span> ##
<span data-ttu-id="781d4-177">När du har distribuerat modulen bör anropar Get-DscResource innehålla resurs bland annat som ett resultat.</span><span class="sxs-lookup"><span data-stu-id="781d4-177">After deploying the module, calling Get-DscResource should list your resource among others as a result.</span></span> <span data-ttu-id="781d4-178">Om du inte hittar din resurs i listan, kontrollera att filen schema.mof för den här resursen finns.</span><span class="sxs-lookup"><span data-stu-id="781d4-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span> 
## <a name="resource-module-contains-examples"></a><span data-ttu-id="781d4-179">Resursmodul innehåller exempel</span><span class="sxs-lookup"><span data-stu-id="781d4-179">Resource module contains examples</span></span> ##
<span data-ttu-id="781d4-180">Skapa goda exempel som hjälper andra att förstå hur du använder den.</span><span class="sxs-lookup"><span data-stu-id="781d4-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="781d4-181">Det är viktigt, särskilt eftersom många användare hantera exempelkod som dokumentation.</span><span class="sxs-lookup"><span data-stu-id="781d4-181">This is crucial, especially since many users treat sample code as documentation.</span></span> 
- <span data-ttu-id="781d4-182">Först bör du fastställa exemplen som inkluderas med modulen – åtminstone, du bör omfatta viktigaste användningsområden för din resurs:</span><span class="sxs-lookup"><span data-stu-id="781d4-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="781d4-183">Om din modulen innehåller flera resurser som arbetar tillsammans för en slutpunkt till slutpunkt-scenario, skulle grundläggande slutpunkt till slutpunkt-exempel helst vara den första.</span><span class="sxs-lookup"><span data-stu-id="781d4-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="781d4-184">Inledande exemplen ska vara enkelt – hur du kommer igång med dina resurser i små hanterbara bitar (t.ex. Skapa en ny virtuell Hårddisk)</span><span class="sxs-lookup"><span data-stu-id="781d4-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="781d4-185">Efterföljande exempel bör bygger på dessa exempel (t.ex. Skapa en virtuell dator från en virtuell Hårddisk, ta bort VM, ändra VM) och visa avancerade funktioner (t.ex. Skapa en virtuell dator med dynamiskt minne)</span><span class="sxs-lookup"><span data-stu-id="781d4-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="781d4-186">Exempelkonfigurationer bör parameteriseras (alla värden ska skickas till konfigurationen som parametrar och det inte finnas några hårdkodad värden):</span><span class="sxs-lookup"><span data-stu-id="781d4-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>
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
- <span data-ttu-id="781d4-187">Det är en bra idé att inkludera (kommenterad ut) exempel på hur du anropar konfigurationen med de faktiska värdena i slutet av exempelskriptet.</span><span class="sxs-lookup"><span data-stu-id="781d4-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span> <span data-ttu-id="781d4-188">Till exempel i konfigurationen ovan den inte nödvändigtvis visar att det är det bästa sättet att ange UserAgent:</span><span class="sxs-lookup"><span data-stu-id="781d4-188">For example, in the configuration above it isn't neccessarily obvious that the best way to specify UserAgent is:</span></span>

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`  
<span data-ttu-id="781d4-189">I så fall kan en kommentar tydliggöra avsedda körningen av konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="781d4-189">In which case a comment can clarify the intended execution of the configuration:</span></span>
```
<# 
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>  
```
- <span data-ttu-id="781d4-190">För varje exempel skriver du en kort beskrivning som förklarar vad det gör och innebörden av parametrarna.</span><span class="sxs-lookup"><span data-stu-id="781d4-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span> 
- <span data-ttu-id="781d4-191">Se till exempel täcker de flesta viktiga scenarier för din resurs och om det inte finns något saknas, kontrollera att de alla köra och placera datorn status som önskas.</span><span class="sxs-lookup"><span data-stu-id="781d4-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>  

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="781d4-192">Felmeddelanden är lätta att förstå och hjälper användarna att lösa problem</span><span class="sxs-lookup"><span data-stu-id="781d4-192">Error messages are easy to understand and help users solve problems</span></span> ##
<span data-ttu-id="781d4-193">Bra felmeddelanden bör vara:</span><span class="sxs-lookup"><span data-stu-id="781d4-193">Good error messages should be:</span></span>
- <span data-ttu-id="781d4-194">: Största problemet med felmeddelanden finns de ofta inte finns, så se till att de förekommer.</span><span class="sxs-lookup"><span data-stu-id="781d4-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span> 
- <span data-ttu-id="781d4-195">Lätt att förstå: mänsklig läsbar, inte otydligt felkoder</span><span class="sxs-lookup"><span data-stu-id="781d4-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="781d4-196">Exakt: Beskriv vad är exakt problemet</span><span class="sxs-lookup"><span data-stu-id="781d4-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="781d4-197">Informell: Råd hur du löser problemet</span><span class="sxs-lookup"><span data-stu-id="781d4-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="781d4-198">Fler: Inte skuld användaren eller se dem anser felaktiga se till att du verifiera fel i slutpunkt till slutpunkt-scenarier (med hjälp av **Start DscConfiguration**), eftersom de kan skilja sig från dem som returneras när du kör resursfunktioner direkt.</span><span class="sxs-lookup"><span data-stu-id="781d4-198">Polite: Don’t blame user or make them feel bad Make sure you verify errors in End to End scenarios (using **Start-DscConfiguration**), because they may differ from those returned when running resource functions directly.</span></span> 

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="781d4-199">Loggmeddelanden är lätta att förstå och informativ (inklusive – verbose,-ETW-loggar och felsökningsloggar)</span><span class="sxs-lookup"><span data-stu-id="781d4-199">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span> ##
<span data-ttu-id="781d4-200">Kontrollera att loggarna för utdata av resursen är enkelt att förstå och ange ett värde för användaren.</span><span class="sxs-lookup"><span data-stu-id="781d4-200">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="781d4-201">Resurser bör utdata all information som kan vara användbar för användaren, men fler loggar är inte alltid bättre.</span><span class="sxs-lookup"><span data-stu-id="781d4-201">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="781d4-202">Du bör undvika redundans och skickar data som inte ger ytterligare värde – inte göra någon Gå igenom hundratals loggposter för att hitta vad de letar efter.</span><span class="sxs-lookup"><span data-stu-id="781d4-202">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="781d4-203">Naturligtvis inga loggar är inte en godtagbar lösning på problemet antingen.</span><span class="sxs-lookup"><span data-stu-id="781d4-203">Of course, no logs is not an acceptable solution for this problem either.</span></span> 

<span data-ttu-id="781d4-204">När du testar, bör du också analysera utförlig och debug-loggar (genom att köra **Start DscConfiguration** med – utförlig och – felsöka växlar på lämpligt sätt), samt som ETW-loggar.</span><span class="sxs-lookup"><span data-stu-id="781d4-204">When testing, you should also analyze verbose and debug logs (by running **Start-DscConfiguration** with –verbose and –debug switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="781d4-205">Om du vill se DSC ETW loggar, gå till Loggboken och öppna följande mapp: program och tjänster från Microsoft - Windows - Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="781d4-205">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="781d4-206">Som standard det ska vara operativa kanalen, men se till att du aktiverar analys och felsökning kanaler innan du kör konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="781d4-206">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span> <span data-ttu-id="781d4-207">Om du vill aktivera analytiska/Debug kanaler, kan du köra skriptet nedan:</span><span class="sxs-lookup"><span data-stu-id="781d4-207">To enable Analytic/Debug channels, you can execute script below:</span></span>
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
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="781d4-208">Resurs-implementeringen innehåller inte hårdkodad sökvägar</span><span class="sxs-lookup"><span data-stu-id="781d4-208">Resource implementation does not contain hardcoded paths</span></span> ##
<span data-ttu-id="781d4-209">Kontrollera att det finns inga hårdkodad sökvägar i resurs-implementeringen särskilt om de tar språk (en-us), eller när systemvariabler som kan användas.</span><span class="sxs-lookup"><span data-stu-id="781d4-209">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="781d4-210">Om din resurs behöver åtkomst till specifika sökvägar, använda miljövariabler i stället hardcoding sökväg, eftersom den kan variera på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="781d4-210">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="781d4-211">Exempel:</span><span class="sxs-lookup"><span data-stu-id="781d4-211">Example:</span></span>

<span data-ttu-id="781d4-212">Istället för:</span><span class="sxs-lookup"><span data-stu-id="781d4-212">Instead of:</span></span>
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
<span data-ttu-id="781d4-213">Du kan skriva:</span><span class="sxs-lookup"><span data-stu-id="781d4-213">You can write:</span></span>
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)} 
```
## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="781d4-214">Resurs-implementeringen innehåller inte användarinformation</span><span class="sxs-lookup"><span data-stu-id="781d4-214">Resource implementation does not contain user information</span></span> ##
<span data-ttu-id="781d4-215">Kontrollera att det finns ingen e-namn, kontoinformation eller namnen på personer i koden.</span><span class="sxs-lookup"><span data-stu-id="781d4-215">Make sure there are no email names, account information, or names of people in the code.</span></span>
## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="781d4-216">Resursen har testats med giltig/ogiltiga autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="781d4-216">Resource was tested with valid/invalid credentials</span></span> ##
<span data-ttu-id="781d4-217">Om din resurs tar en autentiseringsuppgift som parameter:</span><span class="sxs-lookup"><span data-stu-id="781d4-217">If your resource takes a credential as parameter:</span></span>
- <span data-ttu-id="781d4-218">Kontrollera resurs fungerar när lokalt System (eller datorkontot för fjärresurser) inte har åtkomst.</span><span class="sxs-lookup"><span data-stu-id="781d4-218">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="781d4-219">Kontrollera resurs fungerar med en autentiseringsuppgift som angetts för få, ange och testa</span><span class="sxs-lookup"><span data-stu-id="781d4-219">Verify the resource works with a credential specified for Get, Set and Test</span></span> 
- <span data-ttu-id="781d4-220">Om din resurs har åtkomst till resurser, testa alla varianter som du behöver stöd som:</span><span class="sxs-lookup"><span data-stu-id="781d4-220">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="781d4-221">Standard windows-resurser.</span><span class="sxs-lookup"><span data-stu-id="781d4-221">Standard windows shares.</span></span>
  - <span data-ttu-id="781d4-222">DFS-resurser.</span><span class="sxs-lookup"><span data-stu-id="781d4-222">DFS shares.</span></span>
  - <span data-ttu-id="781d4-223">SAMBA resurser (om du vill stödja Linux.)</span><span class="sxs-lookup"><span data-stu-id="781d4-223">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="781d4-224">Resursen kräver ingen interaktiva indata</span><span class="sxs-lookup"><span data-stu-id="781d4-224">Resource does not require interactive input</span></span> ##
<span data-ttu-id="781d4-225">**Get/Set/Test-TargetResource** funktioner ska köras automatiskt och måste vänta inte för användaren input någon gång körning (t.ex. Du bör inte använda **Get-Credential** i dessa funktioner).</span><span class="sxs-lookup"><span data-stu-id="781d4-225">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use **Get-Credential** inside these functions).</span></span> <span data-ttu-id="781d4-226">Om du behöver ange användarens indata ska du skickar till konfigurationen som parameter under fasen kompilering.</span><span class="sxs-lookup"><span data-stu-id="781d4-226">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span> 
## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="781d4-227">Resursen funktioner testat noggrant</span><span class="sxs-lookup"><span data-stu-id="781d4-227">Resource functionality was thoroughly tested</span></span> ##
<span data-ttu-id="781d4-228">Den här checklistan innehåller objekt som är viktiga för att testa och/eller missas ofta.</span><span class="sxs-lookup"><span data-stu-id="781d4-228">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="781d4-229">Det blir bunch tester, främst fungerar de som är specifika för resursen du vill testa och anges inte här.</span><span class="sxs-lookup"><span data-stu-id="781d4-229">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="781d4-230">Glöm inte negativt testfall.</span><span class="sxs-lookup"><span data-stu-id="781d4-230">Don’t forget about negative test cases.</span></span> 
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="781d4-231">Bästa praxis: Resursmodul innehåller testerna mapp med ResourceDesignerTests.ps1 skript</span><span class="sxs-lookup"><span data-stu-id="781d4-231">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span> ##
<span data-ttu-id="781d4-232">Det är en bra idé att skapa mappen ”test” i Resursmodul, skapa ResourceDesignerTests.ps1 filen och Lägg till testerna via **Test xDscResource** och **Test xDscSchema** för alla resurser i de angivna modul.</span><span class="sxs-lookup"><span data-stu-id="781d4-232">It’s a good practice to create folder “Tests” inside resource module, create ResourceDesignerTests.ps1 file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span> <span data-ttu-id="781d4-233">Det här sättet kan du snabbt Validera scheman för alla resurser från den angivna moduler och gör en förstånd kontrollera innan du publicerar.</span><span class="sxs-lookup"><span data-stu-id="781d4-233">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="781d4-234">För xRemoteFile, ResourceTests.ps1 kan se ut så enkelt som:</span><span class="sxs-lookup"><span data-stu-id="781d4-234">For xRemoteFile, ResourceTests.ps1 could look as simple as:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof 
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="781d4-235">Bästa praxis: resursmapp innehåller resurs designer skript för att skapa schemat ##</span><span class="sxs-lookup"><span data-stu-id="781d4-235">Best practice: Resource folder contains resource designer script for generating schema##</span></span>
<span data-ttu-id="781d4-236">Varje resurs ska innehålla ett resurs designer skript som genererar en mof-schemat för resursen.</span><span class="sxs-lookup"><span data-stu-id="781d4-236">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="781d4-237">Den här filen ska placeras i <ResourceName>\ResourceDesignerScripts och namnges generera<ResourceName>Schema.ps1 för xRemoteFile resurs för den här filen skulle anropas GenerateXRemoteFileSchema.ps1 och innehåller:</span><span class="sxs-lookup"><span data-stu-id="781d4-237">This file should be placed in <ResourceName>\ResourceDesignerScripts and be named Generate<ResourceName>Schema.ps1 For xRemoteFile resource this file would be called GenerateXRemoteFileSchema.ps1 and contain:</span></span>
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
## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="781d4-238">Bästa praxis: resursen stöder - whatif</span><span class="sxs-lookup"><span data-stu-id="781d4-238">Best practice: Resource supports -whatif</span></span> ##
<span data-ttu-id="781d4-239">Om din resurs utför ”farliga” åtgärder, är det en bra idé att implementera - whatif funktionalitet.</span><span class="sxs-lookup"><span data-stu-id="781d4-239">If your resource is performing “dangerous” operations, it’s a good practice to implement -whatif functionality.</span></span> <span data-ttu-id="781d4-240">Kontrollera att whatif utdata korrekt beskriver åtgärder som skulle hända om kommandot kördes utan whatif växeln när det är klart.</span><span class="sxs-lookup"><span data-stu-id="781d4-240">After it’s done, make sure that whatif output correctly describes operations which would happen if command was executed without whatif switch.</span></span>
<span data-ttu-id="781d4-241">Kontrollera också att åtgärder inte körs (det görs inga ändringar till nodens tillstånd) när-whatif växeln finns.</span><span class="sxs-lookup"><span data-stu-id="781d4-241">Also, verify that operations does not execute (no changes to the node’s state are made) when –whatif switch is present.</span></span> <span data-ttu-id="781d4-242">Anta exempelvis att vi testar filresurs.</span><span class="sxs-lookup"><span data-stu-id="781d4-242">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="781d4-243">Nedan visas enkel konfiguration skapas filen ”test.txt” med innehållet ”test”:</span><span class="sxs-lookup"><span data-stu-id="781d4-243">Below is simple configuration which creates file “test.txt” with contents “test”:</span></span>
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
<span data-ttu-id="781d4-244">Om vi kompilera och köra konfigurationen med växeln-whatif utdata tala om för oss exakt vad som händer när vi kör konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="781d4-244">If we compile and then execute the configuration with the –whatif switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="781d4-245">Konfigurationen själva men har inte utförts (test.txt filen skapades inte).</span><span class="sxs-lookup"><span data-stu-id="781d4-245">The configuration itself however was not executed (test.txt file was not created).</span></span>
```powershell 
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
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

<span data-ttu-id="781d4-246">Den här listan är inte komplett, men det täcker många viktiga problem som kan uppstå vid design, utveckling och testning DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="781d4-246">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>

