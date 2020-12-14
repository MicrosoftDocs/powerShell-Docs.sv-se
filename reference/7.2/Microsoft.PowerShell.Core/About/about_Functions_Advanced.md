---
description: Introducerar avancerade funktioner som är ett sätt att skapa cmdlets med hjälp av skript.
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: a0b8b027c91f2adedfcecd07bfc80392c1b1e071
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708880"
---
# <a name="about-functions-advanced"></a><span data-ttu-id="c4ea9-103">Om functions Advanced</span><span class="sxs-lookup"><span data-stu-id="c4ea9-103">About Functions Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="c4ea9-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c4ea9-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="c4ea9-105">Introducerar avancerade funktioner som är ett sätt att skapa cmdlets med hjälp av skript.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-105">Introduces advanced functions that are a way to create cmdlets using scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="c4ea9-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c4ea9-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="c4ea9-107">En cmdlet är ett enda kommando som ingår i pipeline-semantiken för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-107">A cmdlet is a single command that participates in the pipeline semantics of PowerShell.</span></span> <span data-ttu-id="c4ea9-108">Detta inkluderar binära cmdlets, avancerade skript funktioner, CDXLM och arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-108">This includes binary cmdlets, advanced script functions, CDXML, and Workflows.</span></span>

<span data-ttu-id="c4ea9-109">Med avancerade funktioner kan du skapa cmdlets som är skrivna som en PowerShell-funktion.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-109">Advanced functions allow you create cmdlets that are written as a PowerShell function.</span></span> <span data-ttu-id="c4ea9-110">Med avancerade funktioner blir det enklare att skapa cmdlets utan att behöva skriva och kompilera en binär cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-110">Advanced functions make it easier to create cmdlets without having to write and compile a binary cmdlet.</span></span> <span data-ttu-id="c4ea9-111">Binära cmdlets är .NET-klasser som är skrivna på ett .NET-språk, till exempel C#.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-111">Binary cmdlets are .NET classes that are written in a .NET language such as C#.</span></span>

<span data-ttu-id="c4ea9-112">Avancerade funktioner använder `CmdletBinding` attributet för att identifiera dem som funktioner som fungerar som cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-112">Advanced functions use the `CmdletBinding` attribute to identify them as functions that act like cmdlets.</span></span> <span data-ttu-id="c4ea9-113">`CmdletBinding`Attributet liknar det cmdlet-attribut som används i kompilerade cmdlet-klasser för att identifiera klassen som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-113">The `CmdletBinding` attribute is similar to the Cmdlet attribute that is used in compiled cmdlet classes to identify the class as a cmdlet.</span></span> <span data-ttu-id="c4ea9-114">Mer information om det här attributet finns [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="c4ea9-114">For more information about this attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="c4ea9-115">I följande exempel visas en funktion som accepterar ett namn och som sedan skriver ut en hälsning med det angivna namnet.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-115">The following example shows a function that accepts a name and then prints a greeting using the supplied name.</span></span> <span data-ttu-id="c4ea9-116">Observera också att den här funktionen definierar ett namn som innehåller ett verb-(Send) och Substantiv-par (hälsning), som verb-Substantiv-paret för en kompilerad cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-116">Also notice that this function defines a name that includes a verb (Send) and noun (Greeting) pair like the verb-noun pair of a compiled cmdlet.</span></span> <span data-ttu-id="c4ea9-117">Funktioner behöver dock inte ha ett verb-Substantiv-namn.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-117">However, functions are not required to have a verb-noun name.</span></span>

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

<span data-ttu-id="c4ea9-118">Parametrarna för funktionen deklareras genom att använda attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-118">The parameters of the function are declared by using the Parameter attribute.</span></span>
<span data-ttu-id="c4ea9-119">Det här attributet kan endast användas eller kombineras med attributet alias eller med flera andra parametrar för parameter verifiering.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-119">This attribute can be used alone, or it can be combined with the Alias attribute or with several other parameter validation attributes.</span></span> <span data-ttu-id="c4ea9-120">Mer information om hur du deklarerar parametrar (inklusive dynamiska parametrar som läggs till vid körning) finns i [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c4ea9-120">For more information about how to declare parameters (including dynamic parameters that are added at runtime), see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

<span data-ttu-id="c4ea9-121">Det faktiska arbetet i föregående funktion utförs i process blocket, vilket motsvarar metoden ProcessingRecord som används av kompilerade cmdlets för att bearbeta data som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-121">The actual work of the previous function is performed in the Process block, which is equivalent to the ProcessingRecord method that is used by compiled cmdlets to process the data that is passed to the cmdlet.</span></span> <span data-ttu-id="c4ea9-122">Det här blocket, tillsammans med start-och slut blocken, beskrivs i [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) avsnittet.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-122">This block, along with the Begin and End blocks, is described in the [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) topic.</span></span>

<span data-ttu-id="c4ea9-123">Avancerade funktioner skiljer sig från kompilerade cmdlets på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="c4ea9-123">Advanced functions differ from compiled cmdlets in the following ways:</span></span>

- <span data-ttu-id="c4ea9-124">Den avancerade funktions parameter bindningen genererar inget undantag när en sträng mat ris är bunden till en boolesk parameter.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-124">Advanced function parameter binding does not throw an exception when an array of strings is bound to a Boolean parameter.</span></span>
- <span data-ttu-id="c4ea9-125">Attributet ValidateSet och ValidatePattern kan inte skicka namngivna parametrar.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-125">The ValidateSet attribute and the ValidatePattern attribute cannot pass named parameters.</span></span>
- <span data-ttu-id="c4ea9-126">Det går inte att använda avancerade funktioner i transaktioner.</span><span class="sxs-lookup"><span data-stu-id="c4ea9-126">Advanced functions cannot be used in transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4ea9-127">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="c4ea9-127">SEE ALSO</span></span>

[<span data-ttu-id="c4ea9-128">about_Functions</span><span class="sxs-lookup"><span data-stu-id="c4ea9-128">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="c4ea9-129">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="c4ea9-129">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="c4ea9-130">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="c4ea9-130">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="c4ea9-131">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="c4ea9-131">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="c4ea9-132">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="c4ea9-132">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
