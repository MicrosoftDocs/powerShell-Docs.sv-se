---
title: Så här skriver du en PowerShell-modul för binär | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357409"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="d3140-102">Skriva en binär PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="d3140-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="d3140-103">En binär modul kan vara vilken sammansättning som helst (. dll) som innehåller cmdlet-klasser.</span><span class="sxs-lookup"><span data-stu-id="d3140-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="d3140-104">Som standard importeras alla cmdletar i sammansättningen när den binära modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="d3140-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="d3140-105">Du kan dock begränsa de cmdlet: ar som importeras genom att skapa ett modulens manifest vars rotnod är sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="d3140-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="d3140-106">(Till exempel kan Manifestets CmdletsToExport-nyckel endast användas för att exportera de cmdlets som behövs.) Dessutom kan en binär modul innehålla ytterligare filer, en katalog struktur och andra delar av användbar hanterings information som en enskild cmdlet inte kan.</span><span class="sxs-lookup"><span data-stu-id="d3140-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="d3140-107">Följande procedur beskriver hur du skapar och installerar en PowerShell-modul för binär.</span><span class="sxs-lookup"><span data-stu-id="d3140-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="d3140-108">Skapa och installera en PowerShell-modul för binär</span><span class="sxs-lookup"><span data-stu-id="d3140-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="d3140-109">Skapa en binär PowerShell-lösning (till exempel en cmdlet skriven C#i), med de funktioner du behöver och kontrol lera att den fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="d3140-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="d3140-110">I ett kod perspektiv är kärnan i en binär modul bara en cmdlet-sammansättning.</span><span class="sxs-lookup"><span data-stu-id="d3140-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="d3140-111">I själva verket behandlar PowerShell en enda cmdlet-sammansättning som en modul, vad gäller inläsning och avlastning, utan extra ansträngning på den delen av utvecklaren.</span><span class="sxs-lookup"><span data-stu-id="d3140-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="d3140-112">Mer information om hur du skriver en cmdlet finns i [skriva en Windows PowerShell-cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="d3140-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="d3140-113">Om det behövs kan du skapa resten av lösningen: (ytterligare cmdlets, XML-filer och så vidare) och beskriv dem med ett modul manifest.</span><span class="sxs-lookup"><span data-stu-id="d3140-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="d3140-114">Förutom att beskriva cmdlet-sammansättningarna i lösningen kan ett modul manifest beskriva hur du vill att modulen ska exporteras och importeras, vilka cmdlets som ska exponeras och vilka ytterligare filer som ska ingå i modulen.</span><span class="sxs-lookup"><span data-stu-id="d3140-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="d3140-115">Som tidigare nämnts kan PowerShell behandla en binär cmdlet som en modul utan ytterligare arbete.</span><span class="sxs-lookup"><span data-stu-id="d3140-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="d3140-116">Därför är ett modul manifest användbart för att kombinera flera filer till ett enda paket, eller för att explicit kontrol lera publikationen för en viss sammansättning.</span><span class="sxs-lookup"><span data-stu-id="d3140-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="d3140-117">Mer information finns i [så här skriver du ett manifest för PowerShell-modul](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="d3140-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="d3140-118">Följande kod är ett mycket enkelt C# kodblock som innehåller tre cmdletar i samma fil som kan användas som en modul.</span><span class="sxs-lookup"><span data-stu-id="d3140-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="d3140-119">Paketera din lösning och spara paketet till någonstans i sökvägen till PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="d3140-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="d3140-120">Den globala miljövariabeln `PSModulePath` beskriver standard Sök vägarna som PowerShell använder för att hitta modulen.</span><span class="sxs-lookup"><span data-stu-id="d3140-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="d3140-121">En gemensam sökväg för att spara en modul på ett system skulle till exempel vara `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="d3140-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="d3140-122">Om du inte använder standard Sök vägarna måste du uttryckligen ange platsen för modulen under installationen.</span><span class="sxs-lookup"><span data-stu-id="d3140-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="d3140-123">Se till att skapa en mapp för att spara modulen i, eftersom du kanske behöver mappen för att lagra flera sammansättningar och filer för din lösning.</span><span class="sxs-lookup"><span data-stu-id="d3140-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="d3140-124">Observera att tekniskt sett du inte behöver installera modulen var som helst på `PSModulePath` – de är bara de standard platser som PowerShell söker efter din modul.</span><span class="sxs-lookup"><span data-stu-id="d3140-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="d3140-125">Men det anses vara bästa praxis, om du inte har en bra anledning att lagra modulen någon annan stans.</span><span class="sxs-lookup"><span data-stu-id="d3140-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="d3140-126">Mer information finns i [installera en PowerShell-modul](./installing-a-powershell-module.md) och [ändra installations Sök vägen för PowerShell-modulen](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="d3140-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="d3140-127">Importera modulen till PowerShell med ett anrop till [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="d3140-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="d3140-128">Genom att anropa [import-modulen](/powershell/module/Microsoft.PowerShell.Core/Import-Module) läses modulen in i aktivt minne.</span><span class="sxs-lookup"><span data-stu-id="d3140-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="d3140-129">Om du använder PowerShell 3,0 och senare, behöver du bara anropa namnet på din modul i koden för att importera den. Mer information finns i [Importera en PowerShell-modul](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="d3140-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="d3140-130">Importera snapin-sammansättningar som moduler</span><span class="sxs-lookup"><span data-stu-id="d3140-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="d3140-131">Cmdlets och providrar som finns i snapin-sammansättningar kan läsas in som binära moduler.</span><span class="sxs-lookup"><span data-stu-id="d3140-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="d3140-132">När sammansättningarna för snapin-modulen läses in som binära moduler, är cmdletarna och providers i snapin-modulen tillgängliga för användaren, men snapin-klassen i sammansättningen ignoreras och snapin-modulen är inte registrerad.</span><span class="sxs-lookup"><span data-stu-id="d3140-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="d3140-133">Därför kan snapin-cmdlet: arna som tillhandahålls av Windows PowerShell inte identifiera snapin-modulen även om de cmdlets och providers är tillgängliga för sessionen.</span><span class="sxs-lookup"><span data-stu-id="d3140-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="d3140-134">Dessutom går det inte att importera formaterings-och filfiler som snapin-modulen refererar till som en del av en binär modul.</span><span class="sxs-lookup"><span data-stu-id="d3140-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="d3140-135">För att importera format och typer av filer måste du skapa ett modul manifest.</span><span class="sxs-lookup"><span data-stu-id="d3140-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="d3140-136">Se [hur du skriver ett manifest för PowerShell-modul](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="d3140-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d3140-137">Se även</span><span class="sxs-lookup"><span data-stu-id="d3140-137">See Also</span></span>

[<span data-ttu-id="d3140-138">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="d3140-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
