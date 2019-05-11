---
title: Hur du skriver en binär PowerShell-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229330"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="f3ede-102">Skriva en binär PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="f3ede-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="f3ede-103">En binär modul kan vara valfri sammansättning (.dll) som innehåller cmdlet klasser.</span><span class="sxs-lookup"><span data-stu-id="f3ede-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="f3ede-104">Som standard importeras alla cmdletar i sammansättningen när binär modulen har importerats.</span><span class="sxs-lookup"><span data-stu-id="f3ede-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="f3ede-105">Du kan dock begränsa de cmdletar som har importerats genom att skapa ett modulmanifest vars rot-modulen är sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="f3ede-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="f3ede-106">(Till exempel nyckeln CmdletsToExport i manifestet kan användas för att exportera dessa cmdlets som krävs.) Dessutom kan kan en binär modul innehålla ytterligare filer, en katalogstruktur och andra delar av användbar information om att en enda cmdlet kan inte.</span><span class="sxs-lookup"><span data-stu-id="f3ede-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="f3ede-107">Följande procedur beskriver hur du skapar och installerar en binär PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="f3ede-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="f3ede-108">Hur du skapar och installerar en binär PowerShell-modulen</span><span class="sxs-lookup"><span data-stu-id="f3ede-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="f3ede-109">Skapa en binär PowerShell-lösning (till exempel en cmdlet som skrivits i C#), med funktionerna du behöver och se till att den körs korrekt.</span><span class="sxs-lookup"><span data-stu-id="f3ede-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="f3ede-110">Från en kod perspektiv är kärnan i en binär modul helt enkelt en cmdlet-sammansättning.</span><span class="sxs-lookup"><span data-stu-id="f3ede-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="f3ede-111">I själva verket behandlar PowerShell en enda cmdlet-sammansättning som en modul, när det gäller och avlastning med inget extra arbete för utvecklaren.</span><span class="sxs-lookup"><span data-stu-id="f3ede-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="f3ede-112">Läs mer om hur du skriver en cmdlet, [skriva en Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="f3ede-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="f3ede-113">Om det behövs skapar du resten av din lösning: (fler cmdlet: ar, XML-filer och så vidare) och beskriver dem med ett modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="f3ede-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="f3ede-114">Förutom som beskriver cmdlet-sammansättningar i din lösning, beskrivs ett modulmanifest hur du vill att din modul exporteras och importeras, vilka cmdletar visas och vilka ytterligare filer hamnar i modulen.</span><span class="sxs-lookup"><span data-stu-id="f3ede-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="f3ede-115">Som nämnts tidigare men kan PowerShell behandla en binär cmdlet som en modul med inget extra arbete.</span><span class="sxs-lookup"><span data-stu-id="f3ede-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="f3ede-116">Ett modulmanifest är därför användbart främst för att kombinera flera filer till ett enda paket eller uttryckligen styra publicering för en angiven sammansättning.</span><span class="sxs-lookup"><span data-stu-id="f3ede-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="f3ede-117">Mer information finns i [hur du skriver en PowerShell-modulen Manifest](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="f3ede-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="f3ede-118">Följande kod är ett mycket enkelt C# kodblock som innehåller tre cmdletar i samma fil som kan användas som en modul.</span><span class="sxs-lookup"><span data-stu-id="f3ede-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

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

3. <span data-ttu-id="f3ede-119">Paketera din lösning och spara paketet på en plats i PowerShell-modulens sökväg.</span><span class="sxs-lookup"><span data-stu-id="f3ede-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="f3ede-120">Den `PSModulePath` globala miljövariabeln beskriver standardsökvägarna som PowerShell använder för att leta upp din modul.</span><span class="sxs-lookup"><span data-stu-id="f3ede-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="f3ede-121">Till exempel en sökväg till att spara en modul i ett system är `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="f3ede-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="f3ede-122">Om du inte använder standardsökvägarna behöver att uttryckligen ange platsen för din modul under installationen.</span><span class="sxs-lookup"><span data-stu-id="f3ede-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="f3ede-123">Var noga med att skapa en mapp för att spara din modul, som du kan behöva mappen för att lagra flera sammansättningar och filer för din lösning.</span><span class="sxs-lookup"><span data-stu-id="f3ede-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="f3ede-124">Observera att tekniskt du inte behöver installera modulens var som helst på den `PSModulePath` – de är helt enkelt standardplatserna som PowerShell söker efter din modul.</span><span class="sxs-lookup"><span data-stu-id="f3ede-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="f3ede-125">Dock anses det bäst att göra det, såvida du inte har en bra anledning för att lagra modulens någon annanstans.</span><span class="sxs-lookup"><span data-stu-id="f3ede-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="f3ede-126">Mer information finns i [installerar ett PowerShell-modulen](./installing-a-powershell-module.md) och [ändra installationssökvägen för PowerShell-modulen](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="f3ede-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="f3ede-127">Importera din modul till PowerShell med ett anrop till [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="f3ede-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="f3ede-128">Anrop till [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ska läsa in din modul i active minnet.</span><span class="sxs-lookup"><span data-stu-id="f3ede-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="f3ede-129">Om du använder PowerShell 3.0 och senare kan bara anropa namnet på din modul i kod också importeras. Mer information finns i [importera en PowerShell-modul](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="f3ede-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="f3ede-130">Importera snapin-modulen sammansättningar som moduler</span><span class="sxs-lookup"><span data-stu-id="f3ede-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="f3ede-131">Cmdlets och providers som finns i snapin-modulen sammansättningar kan läsas som binära moduler.</span><span class="sxs-lookup"><span data-stu-id="f3ede-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="f3ede-132">När snapin-modulen-sammansättningar läses som binära moduler, cmdlets och providers i snapin-modulen är tillgängliga för användare, men snapin-modulen-klassen i sammansättningen ignoreras och snapin-modulen är inte registrerad.</span><span class="sxs-lookup"><span data-stu-id="f3ede-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="f3ede-133">Därför kan inte snapin-cmdletar som tillhandahålls av Windows PowerShell identifiera snapin-modulen även om cmdlets och providers är tillgängliga för sessionen.</span><span class="sxs-lookup"><span data-stu-id="f3ede-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="f3ede-134">Dessutom kan inte importeras alla filer för formatering eller typer som refereras av snapin-modulen som en del av en binär modul.</span><span class="sxs-lookup"><span data-stu-id="f3ede-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="f3ede-135">Om du vill importera filerna formatering och typer måste du skapa ett modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="f3ede-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="f3ede-136">Se, [hur du skriver ett PowerShell-modulen Manifest](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="f3ede-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3ede-137">Se även</span><span class="sxs-lookup"><span data-stu-id="f3ede-137">See Also</span></span>

[<span data-ttu-id="f3ede-138">Skriva ett Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="f3ede-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
