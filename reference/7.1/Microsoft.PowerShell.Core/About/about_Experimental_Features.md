---
description: Stöd för experimentella funktioner i PowerShell är en mekanism för experimentella funktioner som kan användas tillsammans med befintliga stabila funktioner i PowerShell-eller PowerShell-moduler.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om experimentella funktioner
ms.openlocfilehash: fb13d605607b3f6daaba30cef9e7ee339221191c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271064"
---
# <a name="experimental-features"></a><span data-ttu-id="305c2-104">Experimentella funktioner</span><span class="sxs-lookup"><span data-stu-id="305c2-104">Experimental Features</span></span>

<span data-ttu-id="305c2-105">Stöd för experimentella funktioner i PowerShell är en mekanism för experimentella funktioner som kan användas tillsammans med befintliga stabila funktioner i PowerShell-eller PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="305c2-105">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="305c2-106">En experimentell funktion är en där designen inte har slutförts.</span><span class="sxs-lookup"><span data-stu-id="305c2-106">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="305c2-107">Funktionen är tillgänglig för användare att testa och ge feedback.</span><span class="sxs-lookup"><span data-stu-id="305c2-107">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="305c2-108">När en experimentell funktion har slutförts blir design ändringarna ändringar.</span><span class="sxs-lookup"><span data-stu-id="305c2-108">Once an experimental feature is finalized, the design changes become breaking changes.</span></span> <span data-ttu-id="305c2-109">Experimentella funktioner är inte avsedda att användas i produktion eftersom ändringarna kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="305c2-109">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span>

<span data-ttu-id="305c2-110">Experimentella funktioner är inaktiverade som standard och måste aktive ras explicit av användaren eller administratören av systemet.</span><span class="sxs-lookup"><span data-stu-id="305c2-110">Experimental features are disabled by default and need to be explicitly enabled by the user or administrator of the system.</span></span>

<span data-ttu-id="305c2-111">Aktiverade experimentella funktioner visas i `powershell.config.json` filen i `$PSHOME` för alla användare eller i den användarspecifika konfigurations filen för en speciell användare.</span><span class="sxs-lookup"><span data-stu-id="305c2-111">Enabled experimental features are listed in the `powershell.config.json` file in `$PSHOME` for all users or the user-specific configuration file for a specific user.</span></span>

> [!NOTE]
> <span data-ttu-id="305c2-112">Experimentella funktioner som är aktiverade i användar konfigurations filen prioriteras framför experimentella funktioner som anges i system konfigurations filen.</span><span class="sxs-lookup"><span data-stu-id="305c2-112">Experimental features enabled in the user configuration file take precedence over experimental features listed in the system configuration file.</span></span>

## <a name="the-experimental-attribute"></a><span data-ttu-id="305c2-113">Det experimentella attributet</span><span class="sxs-lookup"><span data-stu-id="305c2-113">The Experimental Attribute</span></span>

<span data-ttu-id="305c2-114">Använd `Experimental` attributet för att deklarera kod som experiment.</span><span class="sxs-lookup"><span data-stu-id="305c2-114">Use the `Experimental` attribute to declare some code as experimental.</span></span>

<span data-ttu-id="305c2-115">Använd följande syntax för att deklarera `Experimental` attributet som tillhandahåller namnet på experimentell funktion och åtgärden som ska vidtas om experimentell funktion är aktive rad:</span><span class="sxs-lookup"><span data-stu-id="305c2-115">Use the following syntax to declare the `Experimental` attribute providing the name of the experimental feature and the action to take if the experimental feature is enabled:</span></span>

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

<span data-ttu-id="305c2-116">För moduler måste du `NameOfExperimentalFeature` följa formuläret för `<modulename>.<experimentname>` .</span><span class="sxs-lookup"><span data-stu-id="305c2-116">For modules, the `NameOfExperimentalFeature` must follow the form of `<modulename>.<experimentname>`.</span></span> <span data-ttu-id="305c2-117">`ExperimentAction`Parametern måste anges och de enda giltiga värdena är:</span><span class="sxs-lookup"><span data-stu-id="305c2-117">The `ExperimentAction` parameter must be specified and the only valid values are:</span></span>

- <span data-ttu-id="305c2-118">`Show` innebär att du kan visa den här experimentella funktionen om funktionen är aktive rad</span><span class="sxs-lookup"><span data-stu-id="305c2-118">`Show` means to show this experimental feature if the feature is enabled</span></span>
- <span data-ttu-id="305c2-119">`Hide` innebär att du kan dölja den här experimentella funktionen om funktionen är aktive rad</span><span class="sxs-lookup"><span data-stu-id="305c2-119">`Hide` means to hide this experimental feature if the feature is enabled</span></span>

### <a name="declaring-experimental-features-in-modules-written-in-c"></a><span data-ttu-id="305c2-120">Deklarera experimentella funktioner i moduler som skrivits i C\#</span><span class="sxs-lookup"><span data-stu-id="305c2-120">Declaring Experimental Features in Modules Written in C\#</span></span>

<span data-ttu-id="305c2-121">De utvecklare som vill använda experimentella funktions flaggor kan deklarera en cmdlet som experiment genom att använda- `Experimental` attributet.</span><span class="sxs-lookup"><span data-stu-id="305c2-121">Module authors who want to use the Experimental Feature flags can declare a cmdlet as experimental by using the `Experimental` attribute.</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a><span data-ttu-id="305c2-122">Deklarera experimentella funktioner i moduler som skrivits i PowerShell</span><span class="sxs-lookup"><span data-stu-id="305c2-122">Declaring Experimental Features in Modules written in PowerShell</span></span>

<span data-ttu-id="305c2-123">En modul som skrivits i PowerShell kan också använda `Experimental` attributet för att deklarera experimentella cmdlets:</span><span class="sxs-lookup"><span data-stu-id="305c2-123">Module written in PowerShell can also use the `Experimental` attribute to declare experimental cmdlets:</span></span>

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a><span data-ttu-id="305c2-124">Ömsesidigt uteslutande experimentella funktioner</span><span class="sxs-lookup"><span data-stu-id="305c2-124">Mutually Exclusive Experimental Features</span></span>

<span data-ttu-id="305c2-125">Det finns fall där en experimentell funktion inte kan befinna sig sida vid sida med en befintlig funktion eller en annan experimentell funktion.</span><span class="sxs-lookup"><span data-stu-id="305c2-125">There are cases where an experimental feature cannot co-exist side-by-side with an existing feature or another experimental feature.</span></span>

<span data-ttu-id="305c2-126">Du kan till exempel ha en experimentell cmdlet som åsidosätter en befintlig cmdlet.</span><span class="sxs-lookup"><span data-stu-id="305c2-126">For example, you can have an experimental cmdlet that overrides an existing cmdlet.</span></span> <span data-ttu-id="305c2-127">De två versionerna kan inte finnas sida vid sida.</span><span class="sxs-lookup"><span data-stu-id="305c2-127">The two versions can't coexist side by side.</span></span> <span data-ttu-id="305c2-128">`ExperimentAction.Hide`Inställningen tillåter bara att en av de två cmdletarna är aktive rad i taget.</span><span class="sxs-lookup"><span data-stu-id="305c2-128">The `ExperimentAction.Hide` setting allows only one of the two cmdlets to be enabled at one time.</span></span>

<span data-ttu-id="305c2-129">I det här exemplet skapar vi en ny experimentell `Invoke-WebRequest` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="305c2-129">In this example, we create a new experimental `Invoke-WebRequest` cmdlet.</span></span>
<span data-ttu-id="305c2-130">`InvokeWebRequestCommand` innehåller den icke-experimentella implementeringen.</span><span class="sxs-lookup"><span data-stu-id="305c2-130">`InvokeWebRequestCommand` contains the non-experimental implementation.</span></span>
<span data-ttu-id="305c2-131">`InvokeWebRequestCommandV2` innehåller experimentell version av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="305c2-131">`InvokeWebRequestCommandV2` contains the experimental version of the cmdlet.</span></span>

<span data-ttu-id="305c2-132">Användningen av `ExperimentAction.Hide` tillåter endast att en av de två funktionerna aktive ras vid en tidpunkt:</span><span class="sxs-lookup"><span data-stu-id="305c2-132">The use of `ExperimentAction.Hide` will allow only one of the two features to be enabled at one time:</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

<span data-ttu-id="305c2-133">När `MyWebCmdlets.PSWebCmdletV2` experimentell funktion är aktive rad är den befintliga `InvokeWebRequestCommand` implementeringen dold och `InvokeWebRequestCommandV2` ger implementeringen av `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="305c2-133">When the `MyWebCmdlets.PSWebCmdletV2` experimental feature is enabled, the existing `InvokeWebRequestCommand` implementation is hidden and the `InvokeWebRequestCommandV2` provides the implementation of `Invoke-WebRequest`.</span></span>

<span data-ttu-id="305c2-134">Detta gör att användarna kan prova den nya cmdleten och ge feedback och sedan återgå till den icke-experimentella versionen när det behövs.</span><span class="sxs-lookup"><span data-stu-id="305c2-134">This allows users to try out the new cmdlet and provide feedback then revert to the non-experimental version when needed.</span></span>

### <a name="experimental-parameters-in-cmdlets"></a><span data-ttu-id="305c2-135">Experimentella parametrar i cmdletar</span><span class="sxs-lookup"><span data-stu-id="305c2-135">Experimental Parameters in Cmdlets</span></span>

<span data-ttu-id="305c2-136">`Experimental`Attributet kan också tillämpas på enskilda parametrar.</span><span class="sxs-lookup"><span data-stu-id="305c2-136">The `Experimental` attribute can also be applied to individual parameters.</span></span> <span data-ttu-id="305c2-137">På så sätt kan du skapa en experimentell uppsättning parametrar för en befintlig cmdlet i stället för en helt ny cmdlet.</span><span class="sxs-lookup"><span data-stu-id="305c2-137">This allows you to create an experimental set of parameters for an existing cmdlet rather than an entirely new cmdlet.</span></span>

<span data-ttu-id="305c2-138">Här är ett exempel i C#:</span><span class="sxs-lookup"><span data-stu-id="305c2-138">Here is an example in C#:</span></span>

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

<span data-ttu-id="305c2-139">Här är ett annat exempel i PowerShell-skript:</span><span class="sxs-lookup"><span data-stu-id="305c2-139">Here is a different example in PowerShell script:</span></span>

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a><span data-ttu-id="305c2-140">Kontrollerar om en experimentell funktion är aktive rad</span><span class="sxs-lookup"><span data-stu-id="305c2-140">Checking if an Experimental Feature is Enabled</span></span>

<span data-ttu-id="305c2-141">I din kod måste du kontrol lera om din experimentella funktion är aktive rad innan du vidtar lämpliga åtgärder.</span><span class="sxs-lookup"><span data-stu-id="305c2-141">In your code, you will need to check if your experimental feature is enabled before taking appropriate action.</span></span> <span data-ttu-id="305c2-142">Du kan avgöra om en experimentell funktion är aktive rad med den statiska `IsEnabled()` metoden i `System.Management.Automation.ExperimentalFeature` klassen.</span><span class="sxs-lookup"><span data-stu-id="305c2-142">You can determine if an experimental feature is enabled using the static `IsEnabled()` method on the `System.Management.Automation.ExperimentalFeature` class.</span></span>

<span data-ttu-id="305c2-143">Här är ett exempel i C#:</span><span class="sxs-lookup"><span data-stu-id="305c2-143">Here is an example in C#:</span></span>

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

<span data-ttu-id="305c2-144">Här är ett exempel i PowerShell-skript:</span><span class="sxs-lookup"><span data-stu-id="305c2-144">Here is an example in PowerShell script:</span></span>

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a><span data-ttu-id="305c2-145">Se även</span><span class="sxs-lookup"><span data-stu-id="305c2-145">See also</span></span>

[<span data-ttu-id="305c2-146">Aktivera – ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="305c2-146">Enable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[<span data-ttu-id="305c2-147">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="305c2-147">Disable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[<span data-ttu-id="305c2-148">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="305c2-148">Get-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)

