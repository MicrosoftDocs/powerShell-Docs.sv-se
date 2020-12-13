---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-klassdeklaration
description: Cmdlet-klassdeklaration
ms.openlocfilehash: 854b0a4ca9f6c87c4fad3b71ee726beade585e02
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653496"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="e254c-103">Cmdlet-klassdeklaration</span><span class="sxs-lookup"><span data-stu-id="e254c-103">Cmdlet Class Declaration</span></span>

<span data-ttu-id="e254c-104">En Microsoft .NET Framework-klass deklareras som en cmdlet genom att ange **cmdlet** -attributet som metadata för klassen.</span><span class="sxs-lookup"><span data-stu-id="e254c-104">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="e254c-105">( **Cmdlet** -attributet är det enda obligatoriska attributet för alla cmdletar).</span><span class="sxs-lookup"><span data-stu-id="e254c-105">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span>
<span data-ttu-id="e254c-106">När du anger **cmdlet** -attributet måste du ange verb-och-Substantiv-paret som identifierar cmdleten för användaren.</span><span class="sxs-lookup"><span data-stu-id="e254c-106">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="e254c-107">Och du måste beskriva de Windows PowerShell-funktioner som stöds av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="e254c-107">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="e254c-108">Mer information om den deklarationssyntax som används för att ange **cmdlet** -attributet finns i deklaration av [cmdlet-attribut](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e254c-108">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e254c-109">**Cmdlet** -attributet definieras av klassen [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="e254c-109">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="e254c-110">Egenskaperna för den här klassen motsvarar de deklarations parametrar som används när du deklarerar attributet.</span><span class="sxs-lookup"><span data-stu-id="e254c-110">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="e254c-111">Substantiv</span><span class="sxs-lookup"><span data-stu-id="e254c-111">Nouns</span></span>

<span data-ttu-id="e254c-112">Substantiv för cmdleten anger de resurser som cmdleten fungerar på.</span><span class="sxs-lookup"><span data-stu-id="e254c-112">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="e254c-113">Substantivet särskiljer dina cmdletar från andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e254c-113">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="e254c-114">Substantiv i cmdlet-namn måste vara unika, och när det gäller generiska substantiv, till exempel *Server*, är det bäst att lägga till ett kort prefix som särskiljer din resurs från andra liknande resurser.</span><span class="sxs-lookup"><span data-stu-id="e254c-114">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="e254c-115">Till exempel är ett cmdlet-namn som innehåller ett substantiv med ett prefix `Get-SQLServer` .</span><span class="sxs-lookup"><span data-stu-id="e254c-115">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="e254c-116">Kombinationen av ett visst substantiv med ett mer allmänt verb gör det möjligt för användaren att snabbt hitta cmdleten genom sin åtgärd och sedan identifiera cmdleten med dess resurs samtidigt som den undviker onödiga cmdlet-namnmatchning.</span><span class="sxs-lookup"><span data-stu-id="e254c-116">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="e254c-117">En lista med specialtecken som inte kan användas i cmdlet-namn finns i [nödvändiga utvecklings rikt linjer](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="e254c-117">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="e254c-118">Verb</span><span class="sxs-lookup"><span data-stu-id="e254c-118">Verbs</span></span>

<span data-ttu-id="e254c-119">När du anger ett verb kräver utvecklings rikt linjerna att du använder ett av de fördefinierade verben som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e254c-119">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="e254c-120">Genom att använda någon av dessa fördefinierade verb säkerställer du konsekvensen mellan de cmdletar som du skriver och de cmdletar som skrivs av Microsoft och andra.</span><span class="sxs-lookup"><span data-stu-id="e254c-120">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="e254c-121">Till exempel används verbet "Get" för cmdlets som hämtar data.</span><span class="sxs-lookup"><span data-stu-id="e254c-121">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="e254c-122">Mer information om rikt linjer för verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="e254c-122">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="e254c-123">En lista med specialtecken som inte kan användas i cmdlet-namn finns i [nödvändiga utvecklings rikt linjer](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="e254c-123">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="e254c-124">Stöd för Windows PowerShell-funktioner</span><span class="sxs-lookup"><span data-stu-id="e254c-124">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="e254c-125">Med **cmdlet** -attributet kan du också ange att din cmdlet stöder några av de vanliga funktioner som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e254c-125">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="e254c-126">Detta omfattar stöd för vanliga funktioner, till exempel bekräftelse av användar feedback (kallas stöd för ShouldProcess-funktionen) och stöd för transaktioner.</span><span class="sxs-lookup"><span data-stu-id="e254c-126">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="e254c-127">(Stöd för transaktioner infördes i Windows PowerShell 2,0).</span><span class="sxs-lookup"><span data-stu-id="e254c-127">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="e254c-128">Mer information om den deklarationssyntax som används för att ange **cmdlet** -attributet finns i deklaration av [cmdlet-attribut](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e254c-128">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="e254c-129">Definition av cmdlet-klass</span><span class="sxs-lookup"><span data-stu-id="e254c-129">Cmdlet Class Definition</span></span>

<span data-ttu-id="e254c-130">Följande kod är definitionen för en GetProc-cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="e254c-130">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="e254c-131">Observera att Pascal-höljet används och att namnet på klassen innehåller verbets verb och substantiv.</span><span class="sxs-lookup"><span data-stu-id="e254c-131">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a><span data-ttu-id="e254c-132">Pascal-hölje</span><span class="sxs-lookup"><span data-stu-id="e254c-132">Pascal Casing</span></span>

<span data-ttu-id="e254c-133">När du namnger cmdletar använder du Pascal-Skift läge.</span><span class="sxs-lookup"><span data-stu-id="e254c-133">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="e254c-134">Till exempel `Get-Item` `Get-ItemProperty` visar cmdletarna och det korrekta sättet att använda versaler när du namnger cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e254c-134">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="e254c-135">Se även</span><span class="sxs-lookup"><span data-stu-id="e254c-135">See Also</span></span>

[<span data-ttu-id="e254c-136">System. Management. Automation. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="e254c-136">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="e254c-137">CmdletAttribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="e254c-137">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="e254c-138">Cmdlet-verb</span><span class="sxs-lookup"><span data-stu-id="e254c-138">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="e254c-139">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="e254c-139">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="e254c-140">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e254c-140">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
