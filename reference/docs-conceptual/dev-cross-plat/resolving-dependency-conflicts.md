---
title: Lösa beroende konflikter i PowerShell-modulens sammansättning
description: När du skriver en binär PowerShell-modul i C#, är det naturligt att ta beroenden på andra paket eller bibliotek för att tillhandahålla funktioner.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 93bb39bdd440c7f97c27aa81e68f68331569b69e
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810410"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a><span data-ttu-id="86278-103">Lösa beroende konflikter i PowerShell-modulens sammansättning</span><span class="sxs-lookup"><span data-stu-id="86278-103">Resolving PowerShell module assembly dependency conflicts</span></span>

<span data-ttu-id="86278-104">När du skriver en binär PowerShell-modul i C#, är det naturligt att ta beroenden på andra paket eller bibliotek för att tillhandahålla funktioner.</span><span class="sxs-lookup"><span data-stu-id="86278-104">When writing a binary PowerShell module in C#, it's natural to take dependencies on other packages or libraries to provide functionality.</span></span> <span data-ttu-id="86278-105">Att ta beroenden i andra bibliotek är önskvärt för åter användning av kod.</span><span class="sxs-lookup"><span data-stu-id="86278-105">Taking dependencies on other libraries is desirable for code reuse.</span></span> <span data-ttu-id="86278-106">PowerShell läser alltid in sammansättningar i samma kontext.</span><span class="sxs-lookup"><span data-stu-id="86278-106">PowerShell always loads assemblies into the same context.</span></span> <span data-ttu-id="86278-107">Detta visar problem när en moduls beroenden står i konflikt med redan inlästa DLL-filer och kan förhindra att två i övrigt orelaterade moduler används i samma PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="86278-107">This presents issues when a module's dependencies conflict with already-loaded DLLs and may prevent using two otherwise unrelated modules in the same PowerShell session.</span></span>

<span data-ttu-id="86278-108">Om du har fått det här problemet har du ett fel meddelande som liknar detta:</span><span class="sxs-lookup"><span data-stu-id="86278-108">If you've had this problem, you've seen an error message like this:</span></span>

![Fel meddelande om sammansättnings läsnings konflikt](./media/resolving-dependency-conflicts/moduleconflict.png)

<span data-ttu-id="86278-110">Den här artikeln beskriver några av de olika sätten att beroenden inträffar i PowerShell och metoder för att undvika problem som beror på beroende konflikter.</span><span class="sxs-lookup"><span data-stu-id="86278-110">This article looks at some of the ways dependency conflicts occur in PowerShell and ways to mitigate dependency conflict issues.</span></span> <span data-ttu-id="86278-111">Även om du inte är en moduls författare finns det några knep i här som kan hjälpa dig med beroende konflikter som inträffar i moduler som du använder.</span><span class="sxs-lookup"><span data-stu-id="86278-111">Even if you're not a module author, there are some tricks in here that might help you with dependency conflicts occurring in modules that you use.</span></span>

## <a name="why-do-dependency-conflicts-occur"></a><span data-ttu-id="86278-112">Varför inträffar beroende konflikter?</span><span class="sxs-lookup"><span data-stu-id="86278-112">Why do dependency conflicts occur?</span></span>

<span data-ttu-id="86278-113">I .NET uppstår beroende konflikter när två versioner av samma sammansättning läses in i samma _sammansättning för sammansättnings belastning_.</span><span class="sxs-lookup"><span data-stu-id="86278-113">In .NET, dependency conflicts occur when two versions of the same assembly are loaded into the same _Assembly Load Context_.</span></span> <span data-ttu-id="86278-114">Den här termen innebär något annorlunda på olika .NET-plattformar, vilket beskrivs [senare](#powershell-and-net).</span><span class="sxs-lookup"><span data-stu-id="86278-114">This term means slightly different things on different .NET platforms, which is covered [later](#powershell-and-net).</span></span> <span data-ttu-id="86278-115">Den här konflikten är ett vanligt problem som inträffar i program vara där versions beroenden används.</span><span class="sxs-lookup"><span data-stu-id="86278-115">This conflict is a common problem that occurs in any software where versioned dependencies are used.</span></span> <span data-ttu-id="86278-116">Eftersom det inte finns några enkla lösningar, och eftersom många ramverk för beroende lösningar försöker lösa problemet på olika sätt, kallas den här situationen ofta "beroende Hell".</span><span class="sxs-lookup"><span data-stu-id="86278-116">Because there are no simple solutions, and because many dependency-resolution frameworks try to solve the problem in different ways, this situation is often called "dependency hell".</span></span>

<span data-ttu-id="86278-117">Konflikt problem sammanställs av det faktum att ett projekt nästan aldrig avsiktligt eller direkt är beroende av två versioner av samma beroende.</span><span class="sxs-lookup"><span data-stu-id="86278-117">Conflict issues are compounded by the fact that a project almost never deliberately or directly depends on two versions of the same dependency.</span></span> <span data-ttu-id="86278-118">I stället har projektet två eller flera beroenden som varje kräver en annan version av samma beroende.</span><span class="sxs-lookup"><span data-stu-id="86278-118">Instead, the project has two or more dependencies that each require a different version of the same dependency.</span></span>

<span data-ttu-id="86278-119">Anta till exempel att ditt .NET-program, `DuckBuilder` , finns i två beroenden för att utföra delar av dess funktioner och ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-119">For example, say your .NET application, `DuckBuilder`, brings in two dependencies, to perform parts of its functionality and looks like this:</span></span>

![Två beroenden för DuckBuilder förlitar sig på olika versioner av Newtonsoft.Jspå](./media/resolving-dependency-conflicts/dep-conflict.jpg)

<span data-ttu-id="86278-121">Eftersom `Contoso.ZipTools` `Fabrikam.FileHelpers` båda är beroende av olika versioner av `Newtonsoft.Json` , kan det finnas en beroende konflikt beroende på hur varje beroende har lästs in.</span><span class="sxs-lookup"><span data-stu-id="86278-121">Because `Contoso.ZipTools` and `Fabrikam.FileHelpers` both depend on different versions of `Newtonsoft.Json`, there may be a dependency conflict depending on how each dependency is loaded.</span></span>

### <a name="conflicting-with-powershells-dependencies"></a><span data-ttu-id="86278-122">Konflikt med PowerShell-beroenden</span><span class="sxs-lookup"><span data-stu-id="86278-122">Conflicting with PowerShell's dependencies</span></span>

<span data-ttu-id="86278-123">I PowerShell förstoras det beroende konflikt problemet eftersom PowerShell-moduler och PowerShell: s egna beroenden läses in i samma delade kontext.</span><span class="sxs-lookup"><span data-stu-id="86278-123">In PowerShell, the dependency conflict issue is magnified because PowerShell modules and PowerShell's own dependencies are loaded into the same shared context.</span></span> <span data-ttu-id="86278-124">Det innebär att PowerShell-motorn och alla inlästa PowerShell-moduler får inte ha motstridiga beroenden.</span><span class="sxs-lookup"><span data-stu-id="86278-124">This means the PowerShell engine and all loaded PowerShell modules must not have conflicting dependencies.</span></span> <span data-ttu-id="86278-125">Ett klassiskt exempel på detta är `Newtonsoft.Json` :</span><span class="sxs-lookup"><span data-stu-id="86278-125">A classic example of this is `Newtonsoft.Json`:</span></span>

![FictionalTools-modulen är beroende av en nyare version av Newtonsoft.Jspå än PowerShell](./media/resolving-dependency-conflicts/engine-conflict.jpg)

<span data-ttu-id="86278-127">I det här exemplet är modulen `FictionalTools` beroende av `Newtonsoft.Json` version `12.0.3` , som är en nyare version av `Newtonsoft.Json` än `11.0.2` de som levereras i PowerShell-exemplet.</span><span class="sxs-lookup"><span data-stu-id="86278-127">In this example, the module `FictionalTools` depends on `Newtonsoft.Json` version `12.0.3`, which is a newer version of `Newtonsoft.Json` than `11.0.2` that ships in the example PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="86278-128">Detta är ett exempel och PowerShell 7 levereras för närvarande med `Newtonsoft.Json 12.0.3` .</span><span class="sxs-lookup"><span data-stu-id="86278-128">This is an example and PowerShell 7 currently ships with `Newtonsoft.Json 12.0.3`.</span></span>

<span data-ttu-id="86278-129">Eftersom modulen är beroende av en nyare version av sammansättningen, accepterar den inte versionen som redan har lästs in av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86278-129">Because the module depends on a newer version of the assembly, it won't accept the version that PowerShell already has loaded.</span></span> <span data-ttu-id="86278-130">Men eftersom PowerShell redan har läst in en version av sammansättningen kan modulen inte läsa in sin egen version med hjälp av den konventionella belastnings mekanismen.</span><span class="sxs-lookup"><span data-stu-id="86278-130">But because PowerShell has already loaded a version of the assembly, the module can't load its own version using the conventional load mechanism.</span></span>

### <a name="conflicting-with-another-modules-dependencies"></a><span data-ttu-id="86278-131">Konflikt med en annan moduls beroenden</span><span class="sxs-lookup"><span data-stu-id="86278-131">Conflicting with another module's dependencies</span></span>

<span data-ttu-id="86278-132">Ett annat vanligt scenario i PowerShell är att en modul läses in som är beroende av en version av en sammansättning, och sedan läses en annan modul in senare som är beroende av en annan version av den sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="86278-132">Another common scenario in PowerShell is that a module is loaded that depends on one version of an assembly, and then another module is loaded later that depends on a different version of that assembly.</span></span>

<span data-ttu-id="86278-133">Detta ser ofta ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-133">This often looks like the following:</span></span>

![Två PowerShell-moduler kräver olika versioner av Microsoft. Extensions. logging-beroendet](./media/resolving-dependency-conflicts/mod-conflict.jpg)

<span data-ttu-id="86278-135">I det här fallet `FictionalTools` kräver modulen en nyare version av `Microsoft.Extensions.Logging` än- `FilesystemManager` modulen.</span><span class="sxs-lookup"><span data-stu-id="86278-135">In this case, the `FictionalTools` module requires a newer version of `Microsoft.Extensions.Logging` than the `FilesystemManager` module.</span></span>

<span data-ttu-id="86278-136">Tänk dig att de här modulerna läser in sina beroenden genom att placera beroende sammansättningarna i samma katalog som rot modulens sammansättning.</span><span class="sxs-lookup"><span data-stu-id="86278-136">Imagine these modules load their dependencies by placing the dependency assemblies in the same directory as the root module assembly.</span></span> <span data-ttu-id="86278-137">Detta gör att .NET kan läsa in dem implicit efter namn.</span><span class="sxs-lookup"><span data-stu-id="86278-137">This allows .NET to implicitly load them by name.</span></span> <span data-ttu-id="86278-138">Om vi kör PowerShell 7 (ovanpå .NET Core 3,1) kan vi läsa in och köra och `FictionalTools` sedan läsa in och köra `FilesystemManager` utan problem.</span><span class="sxs-lookup"><span data-stu-id="86278-138">If we're running PowerShell 7 (on top of .NET Core 3.1), we can load and run `FictionalTools`, then load and run `FilesystemManager` without issue.</span></span> <span data-ttu-id="86278-139">Men om vi läser in och kör i en ny session, `FilesystemManager` `FictionalTools` hämtas vi `FileLoadException` från `FictionalTools` kommandot eftersom det kräver en nyare version av `Microsoft.Extensions.Logging` än den som lästs in.</span><span class="sxs-lookup"><span data-stu-id="86278-139">However, in a new session, if we load and run `FilesystemManager`, then load `FictionalTools`, we get a `FileLoadException` from the `FictionalTools` command because it requires a newer version of `Microsoft.Extensions.Logging` than the one loaded.</span></span>
<span data-ttu-id="86278-140">`FictionalTools` Det går inte att läsa in den nödvändiga versionen eftersom en sammansättning med samma namn redan har lästs in.</span><span class="sxs-lookup"><span data-stu-id="86278-140">`FictionalTools` can't load the version needed because an assembly of the same name has already been loaded.</span></span>

## <a name="powershell-and-net"></a><span data-ttu-id="86278-141">PowerShell och .NET</span><span class="sxs-lookup"><span data-stu-id="86278-141">PowerShell and .NET</span></span>

<span data-ttu-id="86278-142">PowerShell körs på .NET-plattformen.</span><span class="sxs-lookup"><span data-stu-id="86278-142">PowerShell runs on the .NET platform.</span></span> <span data-ttu-id="86278-143">NET ansvarar för att lösa och läsa in sammansättnings beroenden, så vi måste förstå hur .NET fungerar här för att förstå beroende konflikter.</span><span class="sxs-lookup"><span data-stu-id="86278-143">NET is ultimately responsible for resolving and loading assembly dependencies, so we must understand how .NET operates here to understand dependency conflicts.</span></span>

<span data-ttu-id="86278-144">Vi måste också confront det faktum att olika versioner av PowerShell körs på olika .NET-implementeringar.</span><span class="sxs-lookup"><span data-stu-id="86278-144">We must also confront the fact that different versions of PowerShell run on different .NET implementations.</span></span> <span data-ttu-id="86278-145">I allmänhet körs PowerShell 5,1 och senare på .NET Framework, medan PowerShell 6 och senare körs på .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86278-145">In general, PowerShell 5.1 and below run on .NET Framework, while PowerShell 6 and above run on .NET Core.</span></span> <span data-ttu-id="86278-146">Dessa två implementeringar av .NET läser in och hanterar sammansättningar på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="86278-146">These two implementations of .NET load and handle assemblies differently.</span></span>
<span data-ttu-id="86278-147">Det innebär att matchning av beroende konflikter kan variera beroende på den underliggande .NET-plattformen.</span><span class="sxs-lookup"><span data-stu-id="86278-147">This means that resolving dependency conflicts can vary depending on the underlying .NET platform.</span></span>

### <a name="assembly-load-contexts"></a><span data-ttu-id="86278-148">Sammansättnings inläsnings kontexter</span><span class="sxs-lookup"><span data-stu-id="86278-148">Assembly Load Contexts</span></span>

<span data-ttu-id="86278-149">I .NET är en _sammansättnings inläsnings kontext_ (ALC) som är ett körnings namn område där sammansättningar läses in.</span><span class="sxs-lookup"><span data-stu-id="86278-149">In .NET, an _Assembly Load Context_ (ALC) that is a runtime namespace into which assemblies are loaded.</span></span> <span data-ttu-id="86278-150">Sammansättningens namn måste vara unika.</span><span class="sxs-lookup"><span data-stu-id="86278-150">The assemblies' names must be unique.</span></span> <span data-ttu-id="86278-151">Det här konceptet gör att sammansättningar kan matchas unikt efter namn i varje ALC.</span><span class="sxs-lookup"><span data-stu-id="86278-151">This concept allows assemblies to be uniquely resolved by name in each ALC.</span></span>

### <a name="assembly-reference-loading-in-net"></a><span data-ttu-id="86278-152">Sammansättnings referens inläsning i .NET</span><span class="sxs-lookup"><span data-stu-id="86278-152">Assembly reference loading in .NET</span></span>

<span data-ttu-id="86278-153">Semantiken vid sammansättnings inläsning är beroende av både .NET-implementeringen (.NET Core vs .NET Framework) och .NET-API: et som används för att läsa in en viss sammansättning.</span><span class="sxs-lookup"><span data-stu-id="86278-153">The semantics of assembly loading depend on both the .NET implementation (.NET Core vs .NET Framework) and the .NET API used to load a particular assembly.</span></span> <span data-ttu-id="86278-154">I stället för att gå in i detalj här finns det länkar i avsnittet [Ytterligare läsning](#further-reading) som går till detaljerad information om hur .net-sammansättnings inläsning fungerar i varje .net-implementering.</span><span class="sxs-lookup"><span data-stu-id="86278-154">Rather than go into detail here, there are links in the [Further reading](#further-reading) section that go into great detail on how .NET assembly loading works in each .NET implementation.</span></span>

<span data-ttu-id="86278-155">I den här artikeln kommer vi att se följande metoder:</span><span class="sxs-lookup"><span data-stu-id="86278-155">In this article we'll refer to the following mechanisms:</span></span>

- <span data-ttu-id="86278-156">Implicit sammansättnings inläsning (effektivt `Assembly.Load(AssemblyName)` ) när .net försöker läsa in en sammansättning efter namn från en statisk sammansättnings referens i .NET-kod.</span><span class="sxs-lookup"><span data-stu-id="86278-156">Implicit assembly loading (effectively `Assembly.Load(AssemblyName)`), when .NET implicitly tries to load an assembly by name from a static assembly reference in .NET code.</span></span>
- <span data-ttu-id="86278-157">`Assembly.LoadFrom()`, ett plugin-orienterat inläsnings-API som lägger till hanterare för att lösa beroenden för den inlästa DLL-filen.</span><span class="sxs-lookup"><span data-stu-id="86278-157">`Assembly.LoadFrom()`, a plugin-oriented loading API that adds handlers to resolve dependencies of the loaded DLL.</span></span> <span data-ttu-id="86278-158">Den här metoden kan inte matcha beroenden på det sätt vi vill.</span><span class="sxs-lookup"><span data-stu-id="86278-158">This method may not resolve dependencies the way we want.</span></span>
- <span data-ttu-id="86278-159">`Assembly.LoadFile()`är ett grundläggande inläsnings-API avsett för att endast läsa in den sammansättning som är tillfrågad och hanterar inte några beroenden.</span><span class="sxs-lookup"><span data-stu-id="86278-159">`Assembly.LoadFile()`, a basic loading API intended to load only the assembly asked for and does not handle any dependencies.</span></span>

### <a name="differences-in-net-framework-vs-net-core"></a><span data-ttu-id="86278-160">Skillnader i .NET Framework vs .NET Core</span><span class="sxs-lookup"><span data-stu-id="86278-160">Differences in .NET Framework vs .NET Core</span></span>

<span data-ttu-id="86278-161">Hur dessa API: er fungerar har ändrats på ett diskret sätt mellan .NET Core och .NET Framework, så det är värt att läsa igenom [länkarna](#further-reading)som ingår.</span><span class="sxs-lookup"><span data-stu-id="86278-161">The way these APIs work has changed in subtle ways between .NET Core and .NET Framework, so it's worth reading through the included [links](#further-reading).</span></span> <span data-ttu-id="86278-162">Ett viktigt sätt är att sammansättnings inläsnings kontexter och andra metoder för sammansättnings upplösning har ändrats mellan .NET Framework och .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86278-162">Importantly, Assembly Load Contexts and other assembly resolution mechanisms have changed between .NET Framework and .NET Core.</span></span>

<span data-ttu-id="86278-163">I synnerhet har .NET Framework följande funktioner:</span><span class="sxs-lookup"><span data-stu-id="86278-163">In particular, .NET Framework has the following features:</span></span>

- <span data-ttu-id="86278-164">Global Assembly Cache, för hela datorns sammansättnings upplösning</span><span class="sxs-lookup"><span data-stu-id="86278-164">The Global Assembly Cache, for machine-wide assembly resolution</span></span>
- <span data-ttu-id="86278-165">Program domäner, som fungerar som aktiva sand boxar för sammansättnings isolering, men som även presenterar ett tävla med</span><span class="sxs-lookup"><span data-stu-id="86278-165">Application Domains, which work like in-process sandboxes for assembly isolation, but also present a serialization layer to contend with</span></span>
- <span data-ttu-id="86278-166">En begränsad sammansättnings modell för sammansättnings belastning, som beskrivs i djup [här](/dotnet/framework/deployment/best-practices-for-assembly-loading), som har en fast uppsättning sammansättnings inläsnings kontexter, var och en med sina egna beteenden:</span><span class="sxs-lookup"><span data-stu-id="86278-166">A limited assembly load context model, explained in depth [here](/dotnet/framework/deployment/best-practices-for-assembly-loading), that has a fixed set of assembly load contexts, each with their own behavior:</span></span>
  - <span data-ttu-id="86278-167">Standard inläsnings kontexten, där sammansättningar läses in som standard</span><span class="sxs-lookup"><span data-stu-id="86278-167">The default load context, where assemblies are loaded by default</span></span>
  - <span data-ttu-id="86278-168">Inläsnings kontexten för inläsning av sammansättningar manuellt vid körning</span><span class="sxs-lookup"><span data-stu-id="86278-168">The load-from context, for loading assemblies manually at runtime</span></span>
  - <span data-ttu-id="86278-169">Reflektions kontexten, för att på ett säkert sätt läsa in sammansättningar för att läsa deras metadata utan att köra dem</span><span class="sxs-lookup"><span data-stu-id="86278-169">The reflection-only context, for safely loading assemblies to read their metadata without running them</span></span>
  - <span data-ttu-id="86278-170">Mystiska annullerade att sammansättningar läses in med `Assembly.LoadFile(string path)` och `Assembly.Load(byte[] asmBytes)` bor i</span><span class="sxs-lookup"><span data-stu-id="86278-170">The mysterious void that assemblies loaded with `Assembly.LoadFile(string path)` and `Assembly.Load(byte[] asmBytes)` live in</span></span>

<span data-ttu-id="86278-171">.NET Core (och .NET 5 +) har ersatt denna komplexitet med en enklare modell:</span><span class="sxs-lookup"><span data-stu-id="86278-171">.NET Core (and .NET 5+) has replaced this complexity with a simpler model:</span></span>

- <span data-ttu-id="86278-172">Ingen Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="86278-172">No Global Assembly Cache.</span></span> <span data-ttu-id="86278-173">Programmen tar alla sina egna beroenden.</span><span class="sxs-lookup"><span data-stu-id="86278-173">Applications bring all their own dependencies.</span></span> <span data-ttu-id="86278-174">Detta tar bort en extern faktor för beroende matchning i program, vilket gör att beroende matchning är mer skalbar.</span><span class="sxs-lookup"><span data-stu-id="86278-174">This removes an external factor for dependency resolution in applications, making dependency resolution more reproducible.</span></span>
  <span data-ttu-id="86278-175">PowerShell, som plugin-värden, kan komplicera detta något för moduler.</span><span class="sxs-lookup"><span data-stu-id="86278-175">PowerShell, as the plugin host, complicates this slightly for modules.</span></span> <span data-ttu-id="86278-176">Dess beroenden i `$PSHOME` delas med alla moduler.</span><span class="sxs-lookup"><span data-stu-id="86278-176">Its dependencies in `$PSHOME` are shared with all modules.</span></span>
- <span data-ttu-id="86278-177">Endast en program domän och ingen möjlighet att skapa nya.</span><span class="sxs-lookup"><span data-stu-id="86278-177">Only one Application Domain, and no ability to create new ones.</span></span> <span data-ttu-id="86278-178">Tillämpnings programmets domän koncept underhålls i .NET Core rent för att vara det globala läget för .NET-processen.</span><span class="sxs-lookup"><span data-stu-id="86278-178">The Application Domain concept is maintained in .NET Core purely to be the global state of the .NET process.</span></span>
- <span data-ttu-id="86278-179">En ny, utöknings bar sammansättnings modell för sammansättning.</span><span class="sxs-lookup"><span data-stu-id="86278-179">A new, extensible Assembly Load Context model.</span></span> <span data-ttu-id="86278-180">Du kan få ett namn på sammansättnings matchning genom att placera den i en ny ALC.</span><span class="sxs-lookup"><span data-stu-id="86278-180">Assembly resolution can be namespaced by putting it in a new ALC.</span></span> <span data-ttu-id="86278-181">.NET Core-processer börjar med en enda standard-ALC där alla sammansättningar läses in.</span><span class="sxs-lookup"><span data-stu-id="86278-181">.NET Core processes begin with a single default ALC into which all assemblies are loaded.</span></span> <span data-ttu-id="86278-182">(förutom de som läses in med `Assembly.LoadFile(string)` och `Assembly.Load(byte[])` ), men processen kan skapa och definiera egna anpassade ALCs med en egen inläsnings logik.</span><span class="sxs-lookup"><span data-stu-id="86278-182">(except for those loaded with `Assembly.LoadFile(string)` and `Assembly.Load(byte[])`) But the process can create and define its own custom ALCs with its own loading logic.</span></span> <span data-ttu-id="86278-183">När en sammansättning läses in, läses den första ALC in i som ansvarar för att matcha dess beroenden.</span><span class="sxs-lookup"><span data-stu-id="86278-183">When an assembly is loaded, the first ALC it is loaded into is responsible for resolving its dependencies.</span></span> <span data-ttu-id="86278-184">Detta skapar möjligheter att implementera kraftfulla .NET plugin-mekanismer.</span><span class="sxs-lookup"><span data-stu-id="86278-184">This creates opportunities to implement powerful .NET plugin loading mechanisms.</span></span>

<span data-ttu-id="86278-185">I båda implementeringarna läses sammansättningar in Lazy.</span><span class="sxs-lookup"><span data-stu-id="86278-185">In both implementations, assemblies are loaded lazily.</span></span> <span data-ttu-id="86278-186">Det innebär att de läses in när en metod som kräver typen körs för första gången.</span><span class="sxs-lookup"><span data-stu-id="86278-186">This means that they are loaded when a method requiring their type is run for the first time.</span></span>

<span data-ttu-id="86278-187">Här är till exempel två versioner av samma kod som läser in ett beroende vid olika tidpunkter.</span><span class="sxs-lookup"><span data-stu-id="86278-187">For example, here are two versions of the same code that load a dependency at different times.</span></span>

<span data-ttu-id="86278-188">Det första läser alltid in sitt beroende när `Program.GetRange()` anropas, eftersom beroende referensen finns i den här metoden:</span><span class="sxs-lookup"><span data-stu-id="86278-188">The first always loads its dependency when `Program.GetRange()` is called, because the dependency reference is lexically present within the method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

<span data-ttu-id="86278-189">Den andra kommer att ladda sitt beroende endast om `limit` parametern är 20 eller mer, på grund av intern indirigering via en metod:</span><span class="sxs-lookup"><span data-stu-id="86278-189">The second will load its dependency only if the `limit` parameter is 20 or more, because of the internal indirection through a method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

<span data-ttu-id="86278-190">Det här är en bra metod eftersom den minimerar minnet och fil systemet I/O och använder resurserna mer effektivt.</span><span class="sxs-lookup"><span data-stu-id="86278-190">This is a good practice since it minimizes the memory and filesystem I/O and uses the resources more efficiently.</span></span> <span data-ttu-id="86278-191">Olycklig en sido effekt av detta är att vi inte vet att det inte går att läsa in sammansättningen förrän vi når kod Sök vägen som försöker läsa in sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="86278-191">The unfortunate a side effect of this is that we won't know that the assembly fails to load until we reach the code path that tries to load the assembly.</span></span>

<span data-ttu-id="86278-192">Det kan också skapa ett tids villkor för inläsnings konflikter.</span><span class="sxs-lookup"><span data-stu-id="86278-192">It can also create a timing condition for assembly load conflicts.</span></span> <span data-ttu-id="86278-193">Om två delar av samma program försöker läsa in olika versioner av samma sammansättning, beror den inlästa versionen på vilken kod Sök väg som körs först.</span><span class="sxs-lookup"><span data-stu-id="86278-193">If two parts of the same program try to load different versions of the same assembly, the version loaded depends on which code path is run first.</span></span>

<span data-ttu-id="86278-194">För PowerShell innebär detta att följande faktorer kan påverka en konflikt vid en sammansättnings belastning:</span><span class="sxs-lookup"><span data-stu-id="86278-194">For PowerShell, this means that the following factors can affect an assembly load conflict:</span></span>

- <span data-ttu-id="86278-195">Vilken modul lästes in först?</span><span class="sxs-lookup"><span data-stu-id="86278-195">Which module was loaded first?</span></span>
- <span data-ttu-id="86278-196">Har kod Sök vägen som använder beroende biblioteket körts?</span><span class="sxs-lookup"><span data-stu-id="86278-196">Was the code path that uses the dependency library run?</span></span>
- <span data-ttu-id="86278-197">Laddar PowerShell ett motstridigt beroende vid start eller bara under vissa kod Sök vägar?</span><span class="sxs-lookup"><span data-stu-id="86278-197">Does PowerShell load a conflicting dependency at startup or only under certain code paths?</span></span>

## <a name="quick-fixes-and-their-limitations"></a><span data-ttu-id="86278-198">Snabb korrigeringar och deras begränsningar</span><span class="sxs-lookup"><span data-stu-id="86278-198">Quick fixes and their limitations</span></span>

<span data-ttu-id="86278-199">I vissa fall är det möjligt att göra små justeringar i modulen och åtgärda saker med minimal ansträngning.</span><span class="sxs-lookup"><span data-stu-id="86278-199">In some cases, it's possible to make small adjustments to your module and fix things with minimal effort.</span></span> <span data-ttu-id="86278-200">Men dessa lösningar tenderar att komma med varningar.</span><span class="sxs-lookup"><span data-stu-id="86278-200">But these solutions tend to come with caveats.</span></span> <span data-ttu-id="86278-201">De kan användas för modulen, men de fungerar inte för alla moduler.</span><span class="sxs-lookup"><span data-stu-id="86278-201">While they may apply to your module, they won't work for every module.</span></span>

### <a name="change-your-dependency-version"></a><span data-ttu-id="86278-202">Ändra beroende version</span><span class="sxs-lookup"><span data-stu-id="86278-202">Change your dependency version</span></span>

<span data-ttu-id="86278-203">Det enklaste sättet att undvika beroende konflikter är att samtycka till ett beroende.</span><span class="sxs-lookup"><span data-stu-id="86278-203">The simplest way to avoid dependency conflicts is to agree on a dependency.</span></span> <span data-ttu-id="86278-204">Detta kan vara möjligt när:</span><span class="sxs-lookup"><span data-stu-id="86278-204">This may be possible when:</span></span>

- <span data-ttu-id="86278-205">Konflikten är ett direkt beroende av modulen och du styr versionen.</span><span class="sxs-lookup"><span data-stu-id="86278-205">Your conflict is with a direct dependency of your module and you control the version.</span></span>
- <span data-ttu-id="86278-206">Konflikten är med ett indirekt beroende, men du kan konfigurera dina direkta beroenden för att använda en fungerande indirekt beroende version.</span><span class="sxs-lookup"><span data-stu-id="86278-206">Your conflict is with an indirect dependency, but you can configure your direct dependencies to use a workable indirect dependency version.</span></span>
- <span data-ttu-id="86278-207">Du vet vilken version som är i konflikt och kan vara beroende av att den inte ändras.</span><span class="sxs-lookup"><span data-stu-id="86278-207">You know the conflicting version and can rely on it not changing.</span></span>

<span data-ttu-id="86278-208">`Newtonsoft.Json`Paketet är ett användbart exempel på det här förra scenariot.</span><span class="sxs-lookup"><span data-stu-id="86278-208">The `Newtonsoft.Json` package is a good example of this last scenario.</span></span> <span data-ttu-id="86278-209">Detta är ett beroende av PowerShell 6 och senare och används inte i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86278-209">This is a dependency of PowerShell 6 and above, and isn't used in Windows PowerShell.</span></span> <span data-ttu-id="86278-210">Ett enkelt sätt att lösa versions konflikter är att ange den lägsta versionen av i `Newtonsoft.Json` de PowerShell-versioner som du vill använda som mål.</span><span class="sxs-lookup"><span data-stu-id="86278-210">Meaning a simple way to resolve versioning conflicts is to target the lowest version of `Newtonsoft.Json` across the PowerShell versions you wish to target.</span></span>

<span data-ttu-id="86278-211">Till exempel PowerShell-6.2.6 och PowerShell 7.0.2 använder båda versioner för närvarande `Newtonsoft.Json` 12.0.3.</span><span class="sxs-lookup"><span data-stu-id="86278-211">For example, PowerShell 6.2.6 and PowerShell 7.0.2 both currently use `Newtonsoft.Json` version 12.0.3.</span></span> <span data-ttu-id="86278-212">För att skapa en modul som riktar in sig på Windows PowerShell, PowerShell 6 och PowerShell 7, riktar du till detta `Newtonsoft.Json 12.0.3` som ett beroende och inkluderar det i den inbyggda modulen.</span><span class="sxs-lookup"><span data-stu-id="86278-212">So, to create a module targeting Windows PowerShell, PowerShell 6, and PowerShell 7, you would target `Newtonsoft.Json 12.0.3` as a dependency and include it in your built module.</span></span> <span data-ttu-id="86278-213">När modulen läses in i PowerShell 6 eller 7 har PowerShell- `Newtonsoft.Json` sammansättningen redan lästs in.</span><span class="sxs-lookup"><span data-stu-id="86278-213">When the module is loaded in PowerShell 6 or 7, PowerShell's own `Newtonsoft.Json` assembly is already loaded.</span></span> <span data-ttu-id="86278-214">Dessutom är det minst den version som krävs för din modul, så upplösningen lyckas.</span><span class="sxs-lookup"><span data-stu-id="86278-214">Also, it is at least the version required for your module, so resolution succeeds.</span></span> <span data-ttu-id="86278-215">I Windows PowerShell finns inte sammansättningen redan i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86278-215">In Windows PowerShell, the assembly isn't already present in PowerShell.</span></span> <span data-ttu-id="86278-216">Därför läses den in från mappen module i stället.</span><span class="sxs-lookup"><span data-stu-id="86278-216">So, it's loaded from your module folder instead.</span></span>

<span data-ttu-id="86278-217">När du riktar in ett konkret PowerShell-paket, till exempel `Microsoft.PowerShell.Sdk` eller `System.Management.Automation` , ska NuGet kunna lösa rätt beroende versioner som krävs.</span><span class="sxs-lookup"><span data-stu-id="86278-217">Generally, when targeting a concrete PowerShell package, like `Microsoft.PowerShell.Sdk` or `System.Management.Automation`, NuGet should be able to resolve the right dependency versions required.</span></span> <span data-ttu-id="86278-218">Det blir svårare att nå både Windows PowerShell och PowerShell 6 + eftersom du måste välja mellan att använda flera ramverk eller `PowerShellStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="86278-218">Targeting both Windows PowerShell and PowerShell 6+ becomes more difficult because you must choose between targeting multiple frameworks or `PowerShellStandard.Library`.</span></span>

<span data-ttu-id="86278-219">Situationer där det inte går att fästa till en gemensam beroende version är:</span><span class="sxs-lookup"><span data-stu-id="86278-219">Circumstances where pinning to a common dependency version won't work include:</span></span>

- <span data-ttu-id="86278-220">Konflikten är med ett indirekt beroende, och ingen av dina beroenden kan konfigureras för att använda en gemensam version.</span><span class="sxs-lookup"><span data-stu-id="86278-220">The conflict is with an indirect dependency, and none of your dependencies can be configured to use a common version.</span></span>
- <span data-ttu-id="86278-221">Den andra beroende versionen kommer förmodligen att ändras ofta, så det är bara en kortsiktig korrigering att lösa en gemensam version.</span><span class="sxs-lookup"><span data-stu-id="86278-221">The other dependency version is likely to change often, so settling on a common version is only a short-term fix.</span></span>

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a><span data-ttu-id="86278-222">Lägga till en händelse hanterare för AssemblyResolve för att skapa en dynamisk bindning för omdirigering</span><span class="sxs-lookup"><span data-stu-id="86278-222">Add an AssemblyResolve event handler to create a dynamic binding redirect</span></span>

<span data-ttu-id="86278-223">Ibland går det inte att ändra din egen beroende version eller så är den för svår.</span><span class="sxs-lookup"><span data-stu-id="86278-223">Sometimes changing your own dependency version isn't possible or is too difficult.</span></span> <span data-ttu-id="86278-224">Ett annat alternativ är att konfigurera en dynamisk bindning för omdirigering genom att registrera en händelse hanterare för `AssemblyResolve` händelsen.</span><span class="sxs-lookup"><span data-stu-id="86278-224">Another option is to set up a dynamic binding redirect by registering an event handler for the `AssemblyResolve` event.</span></span>

<span data-ttu-id="86278-225">Som med en statisk omdirigering är punkten att tvinga alla konsumenter av ett beroende att använda samma faktiska sammansättning.</span><span class="sxs-lookup"><span data-stu-id="86278-225">As with a static binding redirect, the point is to force all consumers of a dependency to use the same actual assembly.</span></span> <span data-ttu-id="86278-226">Du kan avlyssna anrop för att läsa in beroendet och alltid omdirigera dem till den version som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="86278-226">You intercept calls to load the dependency and always redirect them to the version you want.</span></span>

<span data-ttu-id="86278-227">Detta ser ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="86278-227">This looks something like this:</span></span>

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

<span data-ttu-id="86278-228">Du kan tekniskt registrera en script block i PowerShell för att hantera en `AssemblyResolve` händelse, men:</span><span class="sxs-lookup"><span data-stu-id="86278-228">You can technically register a scriptblock within PowerShell to handle an `AssemblyResolve` event, but:</span></span>

- <span data-ttu-id="86278-229">En `AssemblyResolve` händelse kan utlösas i en tråd, något som PowerShell inte kan hantera.</span><span class="sxs-lookup"><span data-stu-id="86278-229">An `AssemblyResolve` event may be triggered on any thread, something that PowerShell will be unable to handle.</span></span>
- <span data-ttu-id="86278-230">Även om händelser hanteras i rätt tråd innebär PowerShell-koncepten att händelse hanterarens script block måste skrivas försiktigt för att inte vara beroende av variabler som definierats utanför den.</span><span class="sxs-lookup"><span data-stu-id="86278-230">Even when events are handled on the right thread, PowerShell's scoping concepts mean that the event handler scriptblock must be written carefully to not depend on variables defined outside it.</span></span>

<span data-ttu-id="86278-231">Det finns situationer där omdirigering till en gemensam version inte fungerar:</span><span class="sxs-lookup"><span data-stu-id="86278-231">There are situations where redirecting to a common version won't work:</span></span>

- <span data-ttu-id="86278-232">När beroendet har gjort ändringar mellan versioner, eller när beroende kod är beroende av en funktion som annars inte är tillgänglig i den version som du omdirigerar till.</span><span class="sxs-lookup"><span data-stu-id="86278-232">When the dependency has made breaking changes between versions, or when dependent code relies on a functionality otherwise not available in the version you redirect to.</span></span>
- <span data-ttu-id="86278-233">När modulen inte har lästs in före det motstridiga beroendet.</span><span class="sxs-lookup"><span data-stu-id="86278-233">When your module isn't loaded before the conflicting dependency.</span></span> <span data-ttu-id="86278-234">Om du registrerar en `AssemblyResolve` händelse hanterare efter att beroendet har lästs in utlöses den aldrig.</span><span class="sxs-lookup"><span data-stu-id="86278-234">If you register an `AssemblyResolve` event handler after the dependency has been loaded, it will never be fired.</span></span> <span data-ttu-id="86278-235">Om du försöker förhindra beroende konflikter med en annan modul kan detta vara ett problem, eftersom den andra modulen kan läsas in först.</span><span class="sxs-lookup"><span data-stu-id="86278-235">If you're trying to prevent dependency conflicts with another module, this may be an issue, since the other module may be loaded first.</span></span>

### <a name="use-the-dependency-out-of-process"></a><span data-ttu-id="86278-236">Använd beroendet av processen</span><span class="sxs-lookup"><span data-stu-id="86278-236">Use the dependency out of process</span></span>

<span data-ttu-id="86278-237">Den här lösningen är mer för modul användare än för modulens författare.</span><span class="sxs-lookup"><span data-stu-id="86278-237">This solution is more for module users than module authors.</span></span> <span data-ttu-id="86278-238">Detta är en lösning som ska användas när den är framgångs intensiv med en modul som inte fungerar på grund av en befintlig beroende konflikt.</span><span class="sxs-lookup"><span data-stu-id="86278-238">This is a solution to use when confronted with a module that won't work due to an existing dependency conflict.</span></span>

<span data-ttu-id="86278-239">Beroende konflikter inträffar eftersom två versioner av samma sammansättning läses in i samma .NET-process.</span><span class="sxs-lookup"><span data-stu-id="86278-239">Dependency conflicts occur because two versions of the same assembly are loaded into the same .NET process.</span></span> <span data-ttu-id="86278-240">En enkel lösning är att läsa in dem i olika processer, så länge du fortfarande kan använda funktionerna från båda.</span><span class="sxs-lookup"><span data-stu-id="86278-240">A simple solution is to load them into different processes, as long as you can still use the functionality from both together.</span></span>

<span data-ttu-id="86278-241">I PowerShell finns det flera sätt att åstadkomma detta:</span><span class="sxs-lookup"><span data-stu-id="86278-241">In PowerShell, there are several ways to achieve this:</span></span>

- <span data-ttu-id="86278-242">Anropa PowerShell som under process</span><span class="sxs-lookup"><span data-stu-id="86278-242">Invoke PowerShell as a subprocess</span></span>

  <span data-ttu-id="86278-243">Ett enkelt sätt att köra ett PowerShell-kommando från den aktuella processen är att bara starta en ny PowerShell-process direkt med kommando anropet:</span><span class="sxs-lookup"><span data-stu-id="86278-243">A simple way to run a PowerShell command out of the current process is to just start a new PowerShell process directly with the command call:</span></span>

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  <span data-ttu-id="86278-244">Den huvudsakliga begränsningen här är att omstrukturering av resultatet kan vara ett trickier eller fler fel som är mer känsliga än andra alternativ.</span><span class="sxs-lookup"><span data-stu-id="86278-244">The main limitation here is that restructuring the result can be trickier or more error prone than other options.</span></span>

- <span data-ttu-id="86278-245">PowerShell-jobbet</span><span class="sxs-lookup"><span data-stu-id="86278-245">The PowerShell job system</span></span>

  <span data-ttu-id="86278-246">PowerShell-jobbet kör även kommandon som är utanför processen, genom att skicka kommandon till en ny PowerShell-process och returnera resultaten:</span><span class="sxs-lookup"><span data-stu-id="86278-246">The PowerShell job system also runs commands out of process, by sending commands to a new PowerShell process and returning the results:</span></span>

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  <span data-ttu-id="86278-247">I det här fallet behöver du bara vara säker på att alla variabler och tillstånd skickas korrekt.</span><span class="sxs-lookup"><span data-stu-id="86278-247">In this case, you just need to be sure that any variables and state are passed in correctly.</span></span>

  <span data-ttu-id="86278-248">Jobb systemet kan också vara något besvärligt när du kör små kommandon.</span><span class="sxs-lookup"><span data-stu-id="86278-248">The job system can also be slightly cumbersome when running small commands.</span></span>

- <span data-ttu-id="86278-249">PowerShell-fjärranvändning</span><span class="sxs-lookup"><span data-stu-id="86278-249">PowerShell remoting</span></span>

  <span data-ttu-id="86278-250">När det är tillgängligt kan PowerShell-fjärrkommunikation vara ett användbart sätt att köra kommandon från processen.</span><span class="sxs-lookup"><span data-stu-id="86278-250">When it's available, PowerShell remoting can be a useful way to run commands out of process.</span></span> <span data-ttu-id="86278-251">Med fjärr kommunikation kan du skapa en ny **PSSession** i en ny process, anropa dess kommandon via PowerShell-fjärrkommunikation och sedan använda resultaten lokalt med de andra modulerna som innehåller de motstridiga beroendena.</span><span class="sxs-lookup"><span data-stu-id="86278-251">With remoting, you can create a fresh **PSSession** in a new process, call its commands over PowerShell remoting, then use the results locally with the other modules containing the conflicting dependencies.</span></span>

  <span data-ttu-id="86278-252">Ett exempel kan se ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-252">An example might look like this:</span></span>

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- <span data-ttu-id="86278-253">Implicit fjärr kommunikation till Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="86278-253">Implicit remoting to Windows PowerShell</span></span>

  <span data-ttu-id="86278-254">Ett annat alternativ i PowerShell 7 är att använda `-UseWindowsPowerShell` flaggan på `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="86278-254">Another option in PowerShell 7 is to use the `-UseWindowsPowerShell` flag on `Import-Module`.</span></span> <span data-ttu-id="86278-255">Detta kommer att importera modulen via en lokal Remoting-session till Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="86278-255">This will import the module through a local remoting session into Windows PowerShell:</span></span>

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  <span data-ttu-id="86278-256">Tänk på att moduler kanske inte fungerar med eller fungerar annorlunda med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86278-256">Be aware that modules may not work with, or work differently with Windows PowerShell.</span></span>

#### <a name="when-out-of-process-invocation-should-not-be-used"></a><span data-ttu-id="86278-257">När en out-of-process-anrop inte ska användas</span><span class="sxs-lookup"><span data-stu-id="86278-257">When out-of-process invocation should not be used</span></span>

<span data-ttu-id="86278-258">Som en modul skapar är kommando anrop utanför processen svårt att ta sig in i en modul och kan ha Edge-fall som orsakar problem.</span><span class="sxs-lookup"><span data-stu-id="86278-258">As a module author, out-of-process command invocation is difficult to bake into a module and may have edge cases that cause issues.</span></span> <span data-ttu-id="86278-259">I synnerhet kanske fjärr kommunikation och jobb inte är tillgängliga i alla miljöer där modulen behöver fungera.</span><span class="sxs-lookup"><span data-stu-id="86278-259">In particular, remoting and jobs may not be available in all environments where your module needs to work.</span></span> <span data-ttu-id="86278-260">Den allmänna principen för att flytta implementeringen utanför processen och tillåta PowerShell-modulen att vara en tunnare klient kan dock fortfarande användas.</span><span class="sxs-lookup"><span data-stu-id="86278-260">However, the general principle of moving the implementation out of process and allowing the PowerShell module to be a thinner client, may still be applicable.</span></span>

<span data-ttu-id="86278-261">Som en module-användare finns det fall där inaktiva anrop inte fungerar:</span><span class="sxs-lookup"><span data-stu-id="86278-261">As a module user, there are cases where out-of-process invocation won't work:</span></span>

- <span data-ttu-id="86278-262">När PowerShell-fjärrkommunikation inte är tillgängligt eftersom du inte har behörighet att använda den eller inte är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="86278-262">When PowerShell remoting is unavailable because you don't have privileges to use it or it is not enabled.</span></span>
- <span data-ttu-id="86278-263">När en viss .NET-typ krävs från utdata som indata till en metod eller ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="86278-263">When a particular .NET type is needed from output as input to a method or another command.</span></span>
  <span data-ttu-id="86278-264">Kommandon som körs via PowerShell-fjärrkommunikation genererar avserialiserade objekt i stället för .NET-objekt med starkt skriven.</span><span class="sxs-lookup"><span data-stu-id="86278-264">Commands running over PowerShell remoting emit deserialized objects rather than strongly-typed .NET objects.</span></span> <span data-ttu-id="86278-265">Det innebär att metod anrop och starkt skrivna API: er inte fungerar med utdata från kommandon som importer ATS via fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="86278-265">This means that method calls and strongly typed APIs do not work with the output of commands imported over remoting.</span></span>

## <a name="more-robust-solutions"></a><span data-ttu-id="86278-266">Robusta lösningar</span><span class="sxs-lookup"><span data-stu-id="86278-266">More robust solutions</span></span>

<span data-ttu-id="86278-267">De tidigare lösningarna hade alla scenarier och moduler som inte fungerar.</span><span class="sxs-lookup"><span data-stu-id="86278-267">The previous solutions all had scenarios and modules that don't work.</span></span> <span data-ttu-id="86278-268">De har dock också en relativt enkel att implementera på rätt sätt.</span><span class="sxs-lookup"><span data-stu-id="86278-268">However, they also have the virtue of being relatively simple to implement correctly.</span></span> <span data-ttu-id="86278-269">Följande lösningar är mer robusta, men kräver mer ansträngning att implementera korrekt och kan införa diskreta buggar om de inte skrivs försiktigt.</span><span class="sxs-lookup"><span data-stu-id="86278-269">The following solutions are more robust, but require more effort to implement correctly and can introduce subtle bugs if not written carefully.</span></span>

### <a name="loading-through-net-core-assembly-load-contexts"></a><span data-ttu-id="86278-270">Inläsning via .NET Core Assembly load-kontexter</span><span class="sxs-lookup"><span data-stu-id="86278-270">Loading through .NET Core Assembly Load Contexts</span></span>

<span data-ttu-id="86278-271">[Sammansättnings inläsnings kontexter](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALCs) som ett implementerat API introducerades i .net core 1,0 för att specifikt åtgärda behovet av att läsa in flera versioner av samma sammansättning i samma körnings miljö.</span><span class="sxs-lookup"><span data-stu-id="86278-271">[Assembly Load Contexts](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALCs) as an implementable API were introduced in .NET Core 1.0 to specifically address the need to load multiple versions of the same assembly into the same runtime.</span></span>

<span data-ttu-id="86278-272">I .NET Core och .NET 5 erbjuder de den mest robusta lösningen till problem med att läsa in versioner av en sammansättning i konflikt.</span><span class="sxs-lookup"><span data-stu-id="86278-272">Within .NET Core and .NET 5, they offer the most robust solution to the problem of loading conflicting versions of an assembly.</span></span> <span data-ttu-id="86278-273">Anpassade ALCs är dock inte tillgängliga i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86278-273">However, custom ALCs are not available in .NET Framework.</span></span> <span data-ttu-id="86278-274">Det innebär att den här lösningen endast fungerar i PowerShell 6 och senare.</span><span class="sxs-lookup"><span data-stu-id="86278-274">This means that this solution only works in PowerShell 6 and above.</span></span>

<span data-ttu-id="86278-275">För närvarande är det bästa exemplet på att använda en ALC för beroende isolering i PowerShell i PowerShell-redigeraren, språk servern för PowerShell-tillägget för Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="86278-275">Currently, the best example of using an ALC for dependency isolation in PowerShell is in PowerShell Editor Services, the language server for the PowerShell extension for Visual Studio Code.</span></span> <span data-ttu-id="86278-276">En [ALC används](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) för att förhindra att PowerShell Editor-tjänsternas egna beroenden kolliderar med dem i PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="86278-276">An [ALC is used](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) to prevent PowerShell Editor Services' own dependencies from clashing with those in PowerShell modules.</span></span>

<span data-ttu-id="86278-277">Implementering av underavsnitts beroende isolering med en ALC är konceptuellt svårt, men vi kommer att arbeta med ett minimalt exempel.</span><span class="sxs-lookup"><span data-stu-id="86278-277">Implementing module dependency isolation with an ALC is conceptually difficult, but we will work through a minimal example.</span></span> <span data-ttu-id="86278-278">Föreställ dig att vi har en enkel modul som endast är avsedd att fungera i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="86278-278">Imagine we have a simple module that is only intended to work in PowerShell 7.</span></span>
<span data-ttu-id="86278-279">Käll koden organiseras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="86278-279">The source code is organized as follows:</span></span>

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

<span data-ttu-id="86278-280">Cmdlet-implementeringen ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-280">The cmdlet implementation looks like this:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="86278-281">(Kraftigt förenklat) manifestet ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-281">The (heavily simplified) manifest, looks like this:</span></span>

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

<span data-ttu-id="86278-282">Och `csproj` ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-282">And the `csproj` looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="86278-283">När vi skapar den här modulen har genererade utdata följande layout:</span><span class="sxs-lookup"><span data-stu-id="86278-283">When we build this module, the generated output has the following layout:</span></span>

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

<span data-ttu-id="86278-284">I det här exemplet finns vårt problem i `Shared.Dependency.dll` sammansättningen, som är vår imaginära konflikt beroende.</span><span class="sxs-lookup"><span data-stu-id="86278-284">In this example, our problem is in the `Shared.Dependency.dll` assembly, which is our imaginary conflicting dependency.</span></span> <span data-ttu-id="86278-285">Detta är det beroende som vi behöver för att kunna placeras bakom en ALC så att vi kan använda den moduler-/regionsspecifika versionen.</span><span class="sxs-lookup"><span data-stu-id="86278-285">This is the dependency that we need to put behind an ALC so that we can use the module-specific version.</span></span>

<span data-ttu-id="86278-286">Vi måste skapa en ny tekniker för modulen så att:</span><span class="sxs-lookup"><span data-stu-id="86278-286">We need to re-engineer the module so that:</span></span>

- <span data-ttu-id="86278-287">Modulens beroenden läses bara in i vår anpassade ALC och inte till PowerShell: s ALC, så det kan finnas ingen konflikt.</span><span class="sxs-lookup"><span data-stu-id="86278-287">Module dependencies are only loaded into our custom ALC, and not into PowerShell's ALC, so there can be no conflict.</span></span> <span data-ttu-id="86278-288">När vi lägger till fler beroenden i vårt projekt behöver vi dessutom inte lägga till mer kod kontinuerligt för att hålla inläsningen igång.</span><span class="sxs-lookup"><span data-stu-id="86278-288">Moreover, as we add more dependencies to our project, we don't want to continuously add more code to keep loading working.</span></span> <span data-ttu-id="86278-289">I stället vill vi ha en återanvändbar, generisk lösning för matchning av beroenden.</span><span class="sxs-lookup"><span data-stu-id="86278-289">Instead, we want reusable, generic dependency resolution logic.</span></span>
- <span data-ttu-id="86278-290">Inläsning av modulen fungerar fortfarande som normalt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86278-290">Loading the module still works as normal in PowerShell.</span></span> <span data-ttu-id="86278-291">-Cmdletar och andra typer som PowerShell-modulens system behöver definieras i PowerShell: s egna ALC.</span><span class="sxs-lookup"><span data-stu-id="86278-291">Cmdlets and other types that the PowerShell module system needs are defined within PowerShell's own ALC.</span></span>

<span data-ttu-id="86278-292">För att tjänstassisterad de här två kraven måste vi dela upp vår modul i två sammansättningar:</span><span class="sxs-lookup"><span data-stu-id="86278-292">To mediate these two requirements, we must break up our module into two assemblies:</span></span>

- <span data-ttu-id="86278-293">En cmdlets-sammansättning, `AlcModule.Cmdlets.dll` som innehåller definitioner av alla typer som PowerShell-Modulsystemet behöver för att läsa in vår modul korrekt.</span><span class="sxs-lookup"><span data-stu-id="86278-293">A cmdlets assembly, `AlcModule.Cmdlets.dll`, that contains definitions of all the types that PowerShell's module system needs to load our module correctly.</span></span> <span data-ttu-id="86278-294">Nämligen alla implementeringar av `Cmdlet` Bask-klassen och den klass som implementerar `IModuleAssemblyInitializer` , som konfigurerar händelse hanteraren för `AssemblyLoadContext.Default.Resolving` att läsas in korrekt `AlcModule.Engine.dll` via vår anpassade ALC.</span><span class="sxs-lookup"><span data-stu-id="86278-294">Namely, any implementations of the `Cmdlet` base class and the class that implements `IModuleAssemblyInitializer`, which sets up the event handler for `AssemblyLoadContext.Default.Resolving` to properly load `AlcModule.Engine.dll` through our custom ALC.</span></span> <span data-ttu-id="86278-295">Eftersom PowerShell 7 avsiktligt döljer typer som definierats i sammansättningar som lästs in i andra ALCs, måste alla typer som är avsedda att vara allmänt exponerade för PowerShell definieras här.</span><span class="sxs-lookup"><span data-stu-id="86278-295">Since PowerShell 7 deliberately hides types defined in assemblies loaded in other ALCs, any types that are meant to be publicly exposed to PowerShell must also be defined here.</span></span> <span data-ttu-id="86278-296">Slutligen måste vår anpassade ALC-definition definieras i den här sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="86278-296">Finally, our custom ALC definition needs to be defined in this assembly.</span></span> <span data-ttu-id="86278-297">Utöver det, så så liten kod som möjligt bör finnas i denna sammansättning.</span><span class="sxs-lookup"><span data-stu-id="86278-297">Beyond that, as little code as possible should live in this assembly.</span></span>
- <span data-ttu-id="86278-298">En motor sammansättning, `AlcModule.Engine.dll` som hanterar den faktiska implementeringen av modulen.</span><span class="sxs-lookup"><span data-stu-id="86278-298">An engine assembly, `AlcModule.Engine.dll`, that handles the actual implementation of the module.</span></span>
  <span data-ttu-id="86278-299">Typer från detta är tillgängliga i PowerShell-ALC, men den läses in från början via vår anpassade ALC.</span><span class="sxs-lookup"><span data-stu-id="86278-299">Types from this are available in the PowerShell ALC, but it will initially be loaded through our custom ALC.</span></span> <span data-ttu-id="86278-300">Dess beroenden läses bara in i den anpassade ALC.</span><span class="sxs-lookup"><span data-stu-id="86278-300">Its dependencies are only loaded into the custom ALC.</span></span> <span data-ttu-id="86278-301">Detta blir effektivt en _bro_ mellan de två ALCs.</span><span class="sxs-lookup"><span data-stu-id="86278-301">Effectively, this becomes a _bridge_ between the two ALCs.</span></span>

<span data-ttu-id="86278-302">Med det här bro fallet ser vårt nya sammansättnings scenario ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-302">Using this bridge concept, our new assembly situation looks like this:</span></span>

![Diagram som representerar AlcModule.Engine.dll bryggning av de två ALCs](./media/resolving-dependency-conflicts/alc-diagram.jpg)

<span data-ttu-id="86278-304">För att se till att standard ALC för beroendet avsöknings logik inte löser beroenden som ska läsas in i den anpassade ALC, måste vi separera dessa två delar av modulen i olika kataloger.</span><span class="sxs-lookup"><span data-stu-id="86278-304">To make sure the default ALC's dependency probing logic does not resolve the dependencies to be loaded into the custom ALC, we need to separate these two parts of the module in different directories.</span></span> <span data-ttu-id="86278-305">Den nya modulen layout har följande struktur:</span><span class="sxs-lookup"><span data-stu-id="86278-305">The new module layout has the following structure:</span></span>

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

<span data-ttu-id="86278-306">För att se hur implementeringen ändras börjar vi med implementeringen av `AlcModule.Engine.dll` :</span><span class="sxs-lookup"><span data-stu-id="86278-306">To see how the implementation changes, we'll start with the implementation of `AlcModule.Engine.dll`:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

<span data-ttu-id="86278-307">Det här är en enkel behållare för beroendet, `Shared.Dependency.dll` men du bör tänka på det som .NET API för dina funktioner som cmdletarna i den andra sammansättnings omslutning för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86278-307">This is a simple container for the dependency, `Shared.Dependency.dll`, but you should think of it as the .NET API for your functionality that the cmdlets in the other assembly wrap for PowerShell.</span></span>

<span data-ttu-id="86278-308">Cmdleten `AlcModule.Cmdlets.dll` ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-308">The cmdlet in `AlcModule.Cmdlets.dll` looks like this:</span></span>

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="86278-309">Om vi nu skulle läsa in **AlcModule** och köra `Test-AlcModule` , får vi en `FileNotFoundException` när standard-ALC försöker läsa in `Alc.Engine.dll` för att köra `EndProcessing()` .</span><span class="sxs-lookup"><span data-stu-id="86278-309">At this point, if we were to load **AlcModule** and run `Test-AlcModule`, we get a `FileNotFoundException` when the default ALC tries to load `Alc.Engine.dll` to run `EndProcessing()`.</span></span> <span data-ttu-id="86278-310">Detta är bra eftersom det innebär att standard-ALC inte kan hitta de beroenden som vi vill dölja.</span><span class="sxs-lookup"><span data-stu-id="86278-310">This is good, since it means the default ALC can't find the dependencies we want to hide.</span></span>

<span data-ttu-id="86278-311">Nu måste vi lägga till kod till `AlcModule.Cmdlets.dll` så att den vet hur man kan lösa det `AlcModule.Engine.dll` .</span><span class="sxs-lookup"><span data-stu-id="86278-311">Now we need to add code to `AlcModule.Cmdlets.dll` so that it knows how to resolve `AlcModule.Engine.dll`.</span></span> <span data-ttu-id="86278-312">Först måste vi definiera vår anpassade ALC som kommer att lösa sammansättningar från vår katalog för modulen `Dependencies` :</span><span class="sxs-lookup"><span data-stu-id="86278-312">First we must define our custom ALC that will resolve assemblies from our module's `Dependencies` directory:</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _dependencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                _dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

<span data-ttu-id="86278-313">Sedan måste vi koppla upp vår anpassade ALC till standard händelsen för ALC `Resolving` , vilket är ALC-versionen av `AssemblyResolve` händelsen i program domäner.</span><span class="sxs-lookup"><span data-stu-id="86278-313">Then we need to hook up our custom ALC to the default ALC's `Resolving` event, which is the ALC version of the `AssemblyResolve` event on Application Domains.</span></span> <span data-ttu-id="86278-314">Den här händelsen utlöses för att hitta `AlcModule.Engine.dll` när `EndProcessing()` anropas.</span><span class="sxs-lookup"><span data-stu-id="86278-314">This event is fired to find `AlcModule.Engine.dll` when `EndProcessing()` is called.</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

<span data-ttu-id="86278-315">Med den nya implementeringen tar du en titt på sekvensen av anrop som inträffar när modulen läses in och `Test-AlcModule` körs:</span><span class="sxs-lookup"><span data-stu-id="86278-315">With the new implementation, take a look at the sequence of calls that occurs when the module is loaded and `Test-AlcModule` is run:</span></span>

![Sekvens diagram över anrop med hjälp av den anpassade ALC för att läsa in beroenden](./media/resolving-dependency-conflicts/alc-sequence.png)

<span data-ttu-id="86278-317">Några intressanta punkter är:</span><span class="sxs-lookup"><span data-stu-id="86278-317">Some points of interest are:</span></span>

- <span data-ttu-id="86278-318">`IModuleAssemblyInitializer`Körs först när modulen läser in och anger `Resolving` händelsen.</span><span class="sxs-lookup"><span data-stu-id="86278-318">The `IModuleAssemblyInitializer` is run first when the module loads and sets the `Resolving` event.</span></span>
- <span data-ttu-id="86278-319">Vi läser inte in beroenden förrän körs `Test-AlcModule` och dess `EndProcessing()` metod anropas.</span><span class="sxs-lookup"><span data-stu-id="86278-319">We don't load the dependencies until `Test-AlcModule` is run and its `EndProcessing()` method is called.</span></span>
- <span data-ttu-id="86278-320">När `EndProcessing()` anropas, kan inte standard-ALC hitta `AlcModule.Engine.dll` och Utlös `Resolving` händelsen.</span><span class="sxs-lookup"><span data-stu-id="86278-320">When `EndProcessing()` is called, the default ALC fails to find `AlcModule.Engine.dll` and fires the `Resolving` event.</span></span>
- <span data-ttu-id="86278-321">Vår händelse hanterare kopplar upp den anpassade ALC till standardvärdet för ALC och inläsningar `AlcModule.Engine.dll` .</span><span class="sxs-lookup"><span data-stu-id="86278-321">Our event handler hooks up the custom ALC to the default ALC and loads `AlcModule.Engine.dll` only.</span></span>
- <span data-ttu-id="86278-322">När `AlcEngine.Use()` anropas i används `AlcModule.Engine.dll` den anpassade ALC igen för att lösa problemet `Shared.Dependency.dll` .</span><span class="sxs-lookup"><span data-stu-id="86278-322">When `AlcEngine.Use()` is called within `AlcModule.Engine.dll`, the custom ALC again kicks in to resolve `Shared.Dependency.dll`.</span></span> <span data-ttu-id="86278-323">Mer specifikt laddar den alltid  `Shared.Dependency.dll` ut eftersom den aldrig står i konflikt med något i standard-ALC och bara ser ut i vår `Dependencies` katalog.</span><span class="sxs-lookup"><span data-stu-id="86278-323">Specifically, it always loads _our_ `Shared.Dependency.dll` since it never conflicts with anything in the default ALC and only looks in our `Dependencies` directory.</span></span>

<span data-ttu-id="86278-324">Genom att sätta samman implementeringen ser vår nya källkod ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-324">Assembling the implementation, our new source code layout looks like this:</span></span>

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

<span data-ttu-id="86278-325">AlcModule. cmdlets. CSPROJ ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-325">AlcModule.Cmdlets.csproj looks like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="86278-326">AlcModule. Engine. CSPROJ ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="86278-326">AlcModule.Engine.csproj looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="86278-327">Så när vi bygger modulen är vår strategi:</span><span class="sxs-lookup"><span data-stu-id="86278-327">So, when we build the module, our strategy is:</span></span>

- <span data-ttu-id="86278-328">Konstruktion `AlcModule.Engine`</span><span class="sxs-lookup"><span data-stu-id="86278-328">Build `AlcModule.Engine`</span></span>
- <span data-ttu-id="86278-329">Konstruktion `AlcModule.Cmdlets`</span><span class="sxs-lookup"><span data-stu-id="86278-329">Build `AlcModule.Cmdlets`</span></span>
- <span data-ttu-id="86278-330">Kopiera allt från `AlcModule.Engine` till `Dependencies` katalogen och kom ihåg vad vi kopierade</span><span class="sxs-lookup"><span data-stu-id="86278-330">Copy everything from `AlcModule.Engine` into the `Dependencies` directory, and remember what we copied</span></span>
- <span data-ttu-id="86278-331">Kopiera allt från `AlcModule.Cmdlets` det som inte fanns i `AlcModule.Engine` Bask module-katalogen</span><span class="sxs-lookup"><span data-stu-id="86278-331">Copy everything from `AlcModule.Cmdlets` that wasn't in `AlcModule.Engine` into the base module directory</span></span>

<span data-ttu-id="86278-332">Eftersom modulens layout här är så viktigt att beroendet skiljs åt är det ett build-skript som ska användas från käll roten:</span><span class="sxs-lookup"><span data-stu-id="86278-332">Since the module layout here is so crucial to dependency separation, here's a build script to use from the source root:</span></span>

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

<span data-ttu-id="86278-333">Slutligen har vi ett allmänt sätt att använda en sammansättnings inläsnings kontext för att isolera vår moduls beroenden som är stabila med tiden när fler beroenden läggs till.</span><span class="sxs-lookup"><span data-stu-id="86278-333">Finally, we have a general way to use an Assembly Load Context to isolate our module's dependencies that remains robust over time as more dependencies are added.</span></span>

<span data-ttu-id="86278-334">För ett mer detaljerat exempel går du till den här [GitHub-lagringsplatsen](https://github.com/rjmholt/ModuleDependencyIsolationExample).</span><span class="sxs-lookup"><span data-stu-id="86278-334">For a more detailed example, go to this [GitHub repository](https://github.com/rjmholt/ModuleDependencyIsolationExample).</span></span> <span data-ttu-id="86278-335">Det här exemplet visar hur du migrerar en modul för att använda en ALC, samtidigt som modulen fungerar i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86278-335">This example demonstrates how to migrate a module to use an ALC, while keeping that module working in .NET Framework.</span></span> <span data-ttu-id="86278-336">Det visar också hur du använder .NET standard och PowerShell standard för att förenkla kärn implementeringen.</span><span class="sxs-lookup"><span data-stu-id="86278-336">It also show how to use .NET Standard and PowerShell Standard to simplify the core implementation.</span></span>

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a><span data-ttu-id="86278-337">Sammansättnings lösa hanterare för inläsning sida vid sida med `Assembly.LoadFile()`</span><span class="sxs-lookup"><span data-stu-id="86278-337">Assembly resolve handler for side-by-side loading with `Assembly.LoadFile()`</span></span>

<span data-ttu-id="86278-338">En annan, eventuellt enklare, metod för att få en sammansättning sida vid sida är att koppla upp en `AssemblyResolve` händelse till `Assembly.LoadFile()` .</span><span class="sxs-lookup"><span data-stu-id="86278-338">Another, possibly simpler, way to achieve side-by-side assembly loading is to hook up an `AssemblyResolve` event to `Assembly.LoadFile()`.</span></span> <span data-ttu-id="86278-339">Användningen `Assembly.LoadFile()` av har fördelen att vara den enklaste lösningen att implementera och fungerar med både .net Core och .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86278-339">Using `Assembly.LoadFile()` has the advantage of being the simplest solution to implement and works with both .NET Core and .NET Framework.</span></span>

<span data-ttu-id="86278-340">För att kunna visa detta tar vi en titt på ett snabbt exempel på en implementering som kombinerar idéer från vårt dynamiska bindnings exempel för omdirigering och sammansättnings exemplet för sammansättnings inläsning ovan.</span><span class="sxs-lookup"><span data-stu-id="86278-340">To show this, let's take a look at a quick example of an implementation that combines ideas from our dynamic binding redirect example, and the Assembly Load Context example above.</span></span>

<span data-ttu-id="86278-341">Vi anropar den här modulen **LoadFileModule**, som har ett trivial-kommando `Test-LoadFile [-Path] <path>` .</span><span class="sxs-lookup"><span data-stu-id="86278-341">We'll call this module **LoadFileModule**, which has a trivial command `Test-LoadFile [-Path] <path>`.</span></span> <span data-ttu-id="86278-342">Den här modulen tar ett beroende på `CsvHelper` sammansättningen (version 15.0.5).</span><span class="sxs-lookup"><span data-stu-id="86278-342">This module takes a dependency on the `CsvHelper` assembly (version 15.0.5).</span></span>

<span data-ttu-id="86278-343">Precis som med ALC-modulen måste vi först dela upp modulen i två delar.</span><span class="sxs-lookup"><span data-stu-id="86278-343">As with the ALC module, we must first split up the module into two pieces.</span></span>

<span data-ttu-id="86278-344">Den första delen utför den faktiska implementeringen `LoadFileModule.Engine` :</span><span class="sxs-lookup"><span data-stu-id="86278-344">The first part does the actual implementation, `LoadFileModule.Engine`:</span></span>

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

<span data-ttu-id="86278-345">Den andra delen är vad PowerShell läser in direkt `LoadFileModule.Cmdlets` .</span><span class="sxs-lookup"><span data-stu-id="86278-345">The second part is what PowerShell loads directly, `LoadFileModule.Cmdlets`.</span></span> <span data-ttu-id="86278-346">Vi använder en strategi som liknar ALC-modulen, där vi isolerar beroenden i en separat katalog.</span><span class="sxs-lookup"><span data-stu-id="86278-346">We use a strategy similar to the ALC module, where we isolate dependencies in a separate directory.</span></span> <span data-ttu-id="86278-347">Men den här gången läser vi in alla sammansättningar i med en lös händelse i stället för bara `LoadFileModule.Engine.dll` .</span><span class="sxs-lookup"><span data-stu-id="86278-347">But this time, we load all assemblies in with a resolve event rather than just `LoadFileModule.Engine.dll`.</span></span>

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

<span data-ttu-id="86278-348">Slutligen liknar layouten för modulen också ALC-modulen:</span><span class="sxs-lookup"><span data-stu-id="86278-348">Finally, the layout of the module is also similar to the ALC module:</span></span>

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

<span data-ttu-id="86278-349">Med den här strukturen har **LoadFileModule** nu stöd för att läsas in tillsammans med andra moduler med ett beroende av **CsvHelper**.</span><span class="sxs-lookup"><span data-stu-id="86278-349">With this structure in place, **LoadFileModule** now supports being loaded alongside other modules with a dependency on **CsvHelper**.</span></span>

<span data-ttu-id="86278-350">Eftersom vår hanterare gäller för **alla** `AssemblyResolve` händelser i program domänen måste vi göra några specifika design alternativ här:</span><span class="sxs-lookup"><span data-stu-id="86278-350">Because our handler applies to **all** `AssemblyResolve` events across the Application Domain, we need to make some specific design choices here:</span></span>

- <span data-ttu-id="86278-351">För att begränsa fönstret där vår händelse kan störa annan inläsning börjar vi bara hantera allmän beroende inläsning efter `LoadFileModule.Engine.dll` har lästs in.</span><span class="sxs-lookup"><span data-stu-id="86278-351">To narrow the window in which our event may interfere with other loading, we only start handling general dependency loading after `LoadFileModule.Engine.dll` has been loaded.</span></span>
- <span data-ttu-id="86278-352">Vi push `LoadFileModule.Engine.dll` -överför till katalogen med beroenden, så att den läses in av ett `LoadFile()` samtal i stället för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86278-352">We push `LoadFileModule.Engine.dll` out into the Dependencies directory, so that it's loaded by a `LoadFile()` call rather than by PowerShell.</span></span> <span data-ttu-id="86278-353">Det innebär att den egna beroende inläsningen alltid höjer en `AssemblyResolve` händelse, även om ett annat `CsvHelper.dll` (till exempel) läses in i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86278-353">This means its own dependency loads always raise an `AssemblyResolve` event, even if another `CsvHelper.dll` (for example) is loaded in PowerShell.</span></span>
  <span data-ttu-id="86278-354">Det ger oss möjlighet att hitta rätt beroende.</span><span class="sxs-lookup"><span data-stu-id="86278-354">This gives us the opportunity to find the correct dependency.</span></span>
- <span data-ttu-id="86278-355">Eftersom vi bara måste matcha de olika beroendena för vår modul tvingas vi att koda en ord lista med beroende namn och versioner till vår hanterare.</span><span class="sxs-lookup"><span data-stu-id="86278-355">Since we must only resolve the specific dependencies for our module, we're forced to code a dictionary of dependency names and versions into our handler.</span></span> <span data-ttu-id="86278-356">I vårt särskilda fall skulle det vara möjligt att använda `ResolveEventArgs.RequestingAssembly` egenskapen för att ta reda på om den `CsvHelper` begärs av vår modul.</span><span class="sxs-lookup"><span data-stu-id="86278-356">In our particular case, it would be possible to use the `ResolveEventArgs.RequestingAssembly` property to work out whether `CsvHelper` is being requested by our module.</span></span> <span data-ttu-id="86278-357">Men det fungerar inte för beroenden av beroenden. till exempel om `CsvHelper` en händelse aktive ras `AssemblyResolve` .</span><span class="sxs-lookup"><span data-stu-id="86278-357">But this doesn't work for dependencies of dependencies; for example, if `CsvHelper` itself raised an `AssemblyResolve` event.</span></span> <span data-ttu-id="86278-358">Det finns andra, svårare sätt att göra detta, till exempel jämföra begärda sammansättningar med metadata för sammansättningar i `Dependencies` katalogen.</span><span class="sxs-lookup"><span data-stu-id="86278-358">There are other, harder ways to do this, such as comparing requested assemblies to the metadata of assemblies in the `Dependencies` directory.</span></span> <span data-ttu-id="86278-359">I det här exemplet har vi gjort den här kontrollen mer utförligt för att både Markera problemet och förenkla exemplet.</span><span class="sxs-lookup"><span data-stu-id="86278-359">But, in this example, we've made this checking more explicit to both highlight the issue and simplify the example.</span></span>

<span data-ttu-id="86278-360">Detta är den viktigaste skillnaden mellan `LoadFile()` strategin och ALC-strategin: `AssemblyResolve` händelsen måste betjäna alla belastningar i program domänen, vilket gör det mycket svårare att hålla vår beroende lösning att trasslar med andra moduler.</span><span class="sxs-lookup"><span data-stu-id="86278-360">This is the key difference between the `LoadFile()` strategy and the ALC strategy: the `AssemblyResolve` event must service all loads in the Application Domain, making it much harder to keep our dependency resolution from being tangled with other modules.</span></span> <span data-ttu-id="86278-361">Men bristen på ALCs i .NET Framework gör det här alternativet värdefullt att förstå.</span><span class="sxs-lookup"><span data-stu-id="86278-361">However, the lack of ALCs in .NET Framework makes this option worth understanding.</span></span>

### <a name="custom-application-domains"></a><span data-ttu-id="86278-362">Anpassade program domäner</span><span class="sxs-lookup"><span data-stu-id="86278-362">Custom Application Domains</span></span>

<span data-ttu-id="86278-363">Det sista och mest extrema alternativet för sammansättnings isolering är att använda anpassade program domäner.</span><span class="sxs-lookup"><span data-stu-id="86278-363">The final and most extreme option for assembly isolation is to use custom Application Domains.</span></span>
<span data-ttu-id="86278-364">Program domäner (används i plural) är endast tillgängliga i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86278-364">Application Domains (used in the plural) are only available in .NET Framework.</span></span> <span data-ttu-id="86278-365">De används för att tillhandahålla isolering i processen mellan delar av ett .NET-program.</span><span class="sxs-lookup"><span data-stu-id="86278-365">They are used to provide in-process isolation between parts of a .NET application.</span></span> <span data-ttu-id="86278-366">En av användnings områdena är att isolera sammansättnings belastningar från varandra i samma process.</span><span class="sxs-lookup"><span data-stu-id="86278-366">One of the uses is to isolate assembly loads from each other within the same process.</span></span>

<span data-ttu-id="86278-367">Program domäner är dock gränser för serialisering.</span><span class="sxs-lookup"><span data-stu-id="86278-367">However, Application Domains are serialization boundaries.</span></span> <span data-ttu-id="86278-368">Objekt i en program domän kan inte refereras och användas direkt av objekt i en annan program domän.</span><span class="sxs-lookup"><span data-stu-id="86278-368">Objects in one Application Domain can't be referenced and used directly by objects in another Application Domain.</span></span> <span data-ttu-id="86278-369">Du kan undvika detta genom att implementera `MarshalByRefObject` .</span><span class="sxs-lookup"><span data-stu-id="86278-369">You can work around this by implementing `MarshalByRefObject`.</span></span> <span data-ttu-id="86278-370">Men när du inte styr typerna, vilket ofta är fallet med beroenden, är det inte möjligt att tvinga fram en implementering här.</span><span class="sxs-lookup"><span data-stu-id="86278-370">But when you don't control the types, as is often the case with dependencies, it's not possible to force an implementation here.</span></span> <span data-ttu-id="86278-371">Den enda lösningen är att göra stora arkitektoniska ändringar.</span><span class="sxs-lookup"><span data-stu-id="86278-371">The only solution is to make large architectural changes.</span></span> <span data-ttu-id="86278-372">Serialiseringens gränser har också allvarliga prestanda konsekvenser.</span><span class="sxs-lookup"><span data-stu-id="86278-372">The serialization boundary also has serious performance implications.</span></span>

<span data-ttu-id="86278-373">Eftersom program domäner har denna allvarliga begränsning, är komplicerade att implementera och bara fungerar i .NET Framework, ger vi inget exempel på hur du kan använda dem här.</span><span class="sxs-lookup"><span data-stu-id="86278-373">Because Application Domains have this serious limitation, are complicated to implement, and only work in .NET Framework, we won't give an example of how you might use them here.</span></span> <span data-ttu-id="86278-374">Även om de är värda att nämnas som en möjlighet, är de inte rekommenderade.</span><span class="sxs-lookup"><span data-stu-id="86278-374">While they're worth mentioning as a possibility, they're not recommended.</span></span>

<span data-ttu-id="86278-375">Om du är intresse rad av att försöka använda en anpassad program domän kan följande länkar hjälpa dig:</span><span class="sxs-lookup"><span data-stu-id="86278-375">If you're interested in trying to use a custom Application Domain, the following links might help:</span></span>

- [<span data-ttu-id="86278-376">Konceptuell dokumentation om program domäner</span><span class="sxs-lookup"><span data-stu-id="86278-376">Conceptual documentation on Application Domains</span></span>](/dotnet/framework/app-domains/application-domains)
- [<span data-ttu-id="86278-377">Exempel på användning av program domäner</span><span class="sxs-lookup"><span data-stu-id="86278-377">Examples for using Application Domains</span></span>](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a><span data-ttu-id="86278-378">Lösningar för beroende konflikter som inte fungerar för PowerShell</span><span class="sxs-lookup"><span data-stu-id="86278-378">Solutions for dependency conflicts that don't work for PowerShell</span></span>

<span data-ttu-id="86278-379">Slutligen kommer vi att ta itu med några möjligheter som inträffar när du genomsöker .NET-beroende konflikter i .NET som kan se löfte, men vanligt vis inte fungerar för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86278-379">Finally, we'll address some possibilities that come up when researching .NET dependency conflicts in .NET that can look promising, but generally won't work for PowerShell.</span></span>

<span data-ttu-id="86278-380">Dessa lösningar har ett gemensamt tema som de är ändringar i distributions konfigurationen för en miljö där du styr programmet och eventuellt hela datorn.</span><span class="sxs-lookup"><span data-stu-id="86278-380">These solutions have the common theme that they are changes to deployment configurations for an environment where you control the application and possibly the entire machine.</span></span> <span data-ttu-id="86278-381">Dessa lösningar är riktade mot scenarier som webb servrar och andra program som distribueras till Server miljöer, där miljön är avsedd att vara värd för programmet och är kostnads fritt att konfigureras av distributions användaren.</span><span class="sxs-lookup"><span data-stu-id="86278-381">These solutions are oriented toward scenarios like web servers and other applications deployed to server environments, where the environment is intended to host the application and is free to be configured by the deploying user.</span></span> <span data-ttu-id="86278-382">De brukar också vara mycket .NET Framework orienterade, vilket innebär att de inte fungerar med PowerShell 6 eller senare.</span><span class="sxs-lookup"><span data-stu-id="86278-382">They also tend to be very much .NET Framework oriented, meaning they do not work with PowerShell 6 or above.</span></span>

<span data-ttu-id="86278-383">Om du vet att modulen endast används i Windows PowerShell 5,1-miljöer som du har total kontroll över, kan vissa av dessa alternativ vara.</span><span class="sxs-lookup"><span data-stu-id="86278-383">If you know that your module is only used in Windows PowerShell 5.1 environments that you have total control over, some of these may be options.</span></span> <span data-ttu-id="86278-384">I allmänhet **bör moduler inte ändra globalt dator tillstånd som detta**.</span><span class="sxs-lookup"><span data-stu-id="86278-384">In general however, **modules should not modify global machine state like this**.</span></span> <span data-ttu-id="86278-385">Den kan avbryta konfigurationer som orsakar problem i `powershell.exe` , andra moduler eller andra beroende program som orsakar att modulen kraschar på oväntade sätt.</span><span class="sxs-lookup"><span data-stu-id="86278-385">It can break configurations that cause problems in `powershell.exe`, other modules, or other dependent applications that cause your module to fail in unexpected ways.</span></span>

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a><span data-ttu-id="86278-386">Statisk bindning omdirigera med app.config för att framtvinga användning av samma beroende version</span><span class="sxs-lookup"><span data-stu-id="86278-386">Static binding redirect with app.config to force using the same dependency version</span></span>

<span data-ttu-id="86278-387">.NET Framework program kan dra nytta av en `app.config` fil för att konfigurera vissa av programmets beteenden i deklarativ form.</span><span class="sxs-lookup"><span data-stu-id="86278-387">.NET Framework applications can take advantage of an `app.config` file to configure some of the application's behaviors declaratively.</span></span> <span data-ttu-id="86278-388">Det går att skriva en `app.config` post som konfigurerar sammansättnings bindning för att omdirigera sammansättnings inläsning till en viss version.</span><span class="sxs-lookup"><span data-stu-id="86278-388">It's possible to write an `app.config` entry that configures assembly binding to redirect assembly loading to a particular version.</span></span>

<span data-ttu-id="86278-389">Två problem med detta för PowerShell är:</span><span class="sxs-lookup"><span data-stu-id="86278-389">Two issues with this for PowerShell are:</span></span>

- <span data-ttu-id="86278-390">.NET Core stöder inte `app.config` , så den här lösningen gäller endast för `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="86278-390">.NET Core does not support `app.config`, so this solution only applies to `powershell.exe`.</span></span>
- <span data-ttu-id="86278-391">`powershell.exe` är ett delat program som finns i `System32` katalogen.</span><span class="sxs-lookup"><span data-stu-id="86278-391">`powershell.exe` is a shared application that lives in the `System32` directory.</span></span> <span data-ttu-id="86278-392">Det är troligt att modulen inte kan ändra innehållet på många system.</span><span class="sxs-lookup"><span data-stu-id="86278-392">It's likely that your module won't be able to modify its contents on many systems.</span></span> <span data-ttu-id="86278-393">Även om det kan ändra det kan det `app.config` bryta en befintlig konfiguration eller påverka inläsningen av andra moduler.</span><span class="sxs-lookup"><span data-stu-id="86278-393">Even if it can, modifying the `app.config` could break an existing configuration or affect the loading of other modules.</span></span>

### <a name="setting-codebase-with-appconfig"></a><span data-ttu-id="86278-394">Ange `codebase` med app.config</span><span class="sxs-lookup"><span data-stu-id="86278-394">Setting `codebase` with app.config</span></span>

<span data-ttu-id="86278-395">Av samma skäl kommer att försöka konfigurera `codebase` inställningen i `app.config` inte att fungera i PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="86278-395">For the same reasons, trying to configure the `codebase` setting in `app.config` is not going to work in PowerShell modules.</span></span>

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a><span data-ttu-id="86278-396">Installera beroenden i GAC (Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="86278-396">Installing dependencies to the Global Assembly Cache (GAC)</span></span>

<span data-ttu-id="86278-397">Ett annat sätt att lösa beroende versions konflikter i .NET Framework är att installera beroenden till GAC, så att olika versioner kan läsas in sida vid sida från GAC.</span><span class="sxs-lookup"><span data-stu-id="86278-397">Another way to resolve dependency version conflicts in .NET Framework is to install dependencies to the GAC, so that different versions can be loaded side-by-side from the GAC.</span></span>

<span data-ttu-id="86278-398">För PowerShell-moduler är problemen här:</span><span class="sxs-lookup"><span data-stu-id="86278-398">Again, for PowerShell modules, the chief issues here are:</span></span>

- <span data-ttu-id="86278-399">Den globala sammansättningscachen gäller endast .NET Framework, så det här är inte hjälp i PowerShell 6 och senare.</span><span class="sxs-lookup"><span data-stu-id="86278-399">The GAC only applies to .NET Framework, so this does not help in PowerShell 6 and above.</span></span>
- <span data-ttu-id="86278-400">Att installera sammansättningar i GAC är en ändring av global dator status och kan orsaka sido effekter i andra program eller i andra moduler.</span><span class="sxs-lookup"><span data-stu-id="86278-400">Installing assemblies to the GAC is a modification of global machine state and may cause side-effects in other applications or to other modules.</span></span> <span data-ttu-id="86278-401">Det kan också vara svårt att göra korrekt, även om modulen har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="86278-401">It may also be difficult to do correctly, even when your module has the required access privileges.</span></span> <span data-ttu-id="86278-402">Att få IT-fel kan orsaka allvarliga, datorövergripande problem i andra .NET-program.</span><span class="sxs-lookup"><span data-stu-id="86278-402">Getting it wrong could cause serious, machine-wide issues in other .NET applications.</span></span>

## <a name="further-reading"></a><span data-ttu-id="86278-403">Ytterligare läsning</span><span class="sxs-lookup"><span data-stu-id="86278-403">Further reading</span></span>

<span data-ttu-id="86278-404">Det finns mycket mer att läsa på .NET-sammansättning versions beroende konflikter.</span><span class="sxs-lookup"><span data-stu-id="86278-404">There's plenty more to read on .NET assembly version dependency conflicts.</span></span> <span data-ttu-id="86278-405">Här är några saker som är bra att säga:</span><span class="sxs-lookup"><span data-stu-id="86278-405">Here are some nice jumping off points:</span></span>

- [<span data-ttu-id="86278-406">.NET: sammansättningar i .NET</span><span class="sxs-lookup"><span data-stu-id="86278-406">.NET: Assemblies in .NET</span></span>](/dotnet/standard/assembly/)
- [<span data-ttu-id="86278-407">.NET Core: algoritmen för inläsning av hanterad sammansättning</span><span class="sxs-lookup"><span data-stu-id="86278-407">.NET Core: The managed assembly loading algorithm</span></span>](/dotnet/core/dependency-loading/loading-managed)
- [<span data-ttu-id="86278-408">.NET Core: förstå system. Runtime. Loader. AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="86278-408">.NET Core: Understanding System.Runtime.Loader.AssemblyLoadContext</span></span>](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [<span data-ttu-id="86278-409">.NET Core: diskussion om inläsnings lösningar sida vid sida</span><span class="sxs-lookup"><span data-stu-id="86278-409">.NET Core: Discussion about side-by-side assembly loading solutions</span></span>](https://github.com/dotnet/runtime/issues/13471)
- [<span data-ttu-id="86278-410">.NET Framework: omdirigering av sammansättnings versioner</span><span class="sxs-lookup"><span data-stu-id="86278-410">.NET Framework: Redirecting assembly versions</span></span>](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [<span data-ttu-id="86278-411">.NET Framework: metod tips för sammansättnings inläsning</span><span class="sxs-lookup"><span data-stu-id="86278-411">.NET Framework: Best practices for assembly loading</span></span>](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [<span data-ttu-id="86278-412">.NET Framework: hur körningen hittar sammansättningar</span><span class="sxs-lookup"><span data-stu-id="86278-412">.NET Framework: How the runtime locates assemblies</span></span>](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [<span data-ttu-id="86278-413">.NET Framework: lös sammansättnings belastningar</span><span class="sxs-lookup"><span data-stu-id="86278-413">.NET Framework: Resolve assembly loads</span></span>](/dotnet/standard/assembly/resolve-loads)
- [<span data-ttu-id="86278-414">StackOverflow: sammansättnings bindning omdirigera, hur och varför?</span><span class="sxs-lookup"><span data-stu-id="86278-414">StackOverflow: Assembly binding redirect, how and why?</span></span>](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why)
- [<span data-ttu-id="86278-415">PowerShell: diskussion om att implementera AssemblyLoadContexts</span><span class="sxs-lookup"><span data-stu-id="86278-415">PowerShell: Discussion about implementing AssemblyLoadContexts</span></span>](https://github.com/PowerShell/PowerShell/issues/11571)
- [<span data-ttu-id="86278-416">PowerShell: `Assembly.LoadFile()` läses inte in i standard AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="86278-416">PowerShell: `Assembly.LoadFile()` doesn't load into default AssemblyLoadContext</span></span>](https://github.com/PowerShell/PowerShell/issues/12052)
- [<span data-ttu-id="86278-417">Rick-Strahl: när ett .NET-sammansättnings beroende hämtas läses in?</span><span class="sxs-lookup"><span data-stu-id="86278-417">Rick Strahl: When does a .NET assembly dependency get loaded?</span></span>](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded)
- [<span data-ttu-id="86278-418">Jon Skeet: Sammanfattning av versions hantering i .NET</span><span class="sxs-lookup"><span data-stu-id="86278-418">Jon Skeet: Summary of versioning in .NET</span></span>](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/)
- [<span data-ttu-id="86278-419">Nate McMaster: djupgående att gå in i .NET Core-primitiver</span><span class="sxs-lookup"><span data-stu-id="86278-419">Nate McMaster: Deep dive into .NET Core primitives</span></span>](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/)
