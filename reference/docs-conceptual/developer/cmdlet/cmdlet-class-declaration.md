---
title: Cmdlet-klass deklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 979025ad5c34ab73dcc23d0e38ffb9acc431f15a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354889"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="afdaf-102">Cmdlet-klassdeklaration</span><span class="sxs-lookup"><span data-stu-id="afdaf-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="afdaf-103">En Microsoft .NET Framework-klass deklareras som en cmdlet genom att ange **cmdlet** -attributet som metadata för klassen.</span><span class="sxs-lookup"><span data-stu-id="afdaf-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="afdaf-104">( **Cmdlet** -attributet är det enda obligatoriska attributet för alla cmdletar).</span><span class="sxs-lookup"><span data-stu-id="afdaf-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="afdaf-105">När du anger **cmdlet** -attributet måste du ange verb-och-Substantiv-paret som identifierar cmdleten för användaren.</span><span class="sxs-lookup"><span data-stu-id="afdaf-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="afdaf-106">Och du måste beskriva de Windows PowerShell-funktioner som stöds av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="afdaf-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="afdaf-107">Mer information om den deklarationssyntax som används för att ange **cmdlet** -attributet finns i deklaration av [cmdlet-attribut](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="afdaf-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="afdaf-108">**Cmdlet** -attributet definieras av klassen [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="afdaf-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="afdaf-109">Egenskaperna för den här klassen motsvarar de deklarations parametrar som används när du deklarerar attributet.</span><span class="sxs-lookup"><span data-stu-id="afdaf-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="afdaf-110">Substantiv</span><span class="sxs-lookup"><span data-stu-id="afdaf-110">Nouns</span></span>

<span data-ttu-id="afdaf-111">Substantiv för cmdleten anger de resurser som cmdleten fungerar på.</span><span class="sxs-lookup"><span data-stu-id="afdaf-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="afdaf-112">Substantivet särskiljer dina cmdletar från andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="afdaf-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="afdaf-113">Substantiv i cmdlet-namn måste vara unika, och när det gäller generiska substantiv, till exempel *Server*, är det bäst att lägga till ett kort prefix som särskiljer din resurs från andra liknande resurser.</span><span class="sxs-lookup"><span data-stu-id="afdaf-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="afdaf-114">Till exempel är ett cmdlet-namn som innehåller ett substantiv med ett prefix `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="afdaf-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="afdaf-115">Kombinationen av ett visst substantiv med ett mer allmänt verb gör det möjligt för användaren att snabbt hitta cmdleten genom sin åtgärd och sedan identifiera cmdleten med dess resurs samtidigt som den undviker onödiga cmdlet-namnmatchning.</span><span class="sxs-lookup"><span data-stu-id="afdaf-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="afdaf-116">En lista med specialtecken som inte kan användas i cmdlet-namn finns i [nödvändiga utvecklings rikt linjer](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="afdaf-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="afdaf-117">Verb</span><span class="sxs-lookup"><span data-stu-id="afdaf-117">Verbs</span></span>

<span data-ttu-id="afdaf-118">När du anger ett verb kräver utvecklings rikt linjerna att du använder ett av de fördefinierade verben som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="afdaf-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="afdaf-119">Genom att använda någon av dessa fördefinierade verb säkerställer du konsekvensen mellan de cmdletar som du skriver och de cmdletar som skrivs av Microsoft och andra.</span><span class="sxs-lookup"><span data-stu-id="afdaf-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="afdaf-120">Till exempel används verbet "Get" för cmdlets som hämtar data.</span><span class="sxs-lookup"><span data-stu-id="afdaf-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="afdaf-121">Mer information om rikt linjer för verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="afdaf-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="afdaf-122">En lista med specialtecken som inte kan användas i cmdlet-namn finns i [nödvändiga utvecklings rikt linjer](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="afdaf-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="afdaf-123">Stöd för Windows PowerShell-funktioner</span><span class="sxs-lookup"><span data-stu-id="afdaf-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="afdaf-124">Med **cmdlet** -attributet kan du också ange att din cmdlet stöder några av de vanliga funktioner som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="afdaf-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="afdaf-125">Detta omfattar stöd för vanliga funktioner, till exempel bekräftelse av användar feedback (kallas stöd för ShouldProcess-funktionen) och stöd för transaktioner.</span><span class="sxs-lookup"><span data-stu-id="afdaf-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="afdaf-126">(Stöd för transaktioner infördes i Windows PowerShell 2,0).</span><span class="sxs-lookup"><span data-stu-id="afdaf-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="afdaf-127">Mer information om den deklarationssyntax som används för att ange **cmdlet** -attributet finns i deklaration av [cmdlet-attribut](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="afdaf-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="afdaf-128">Definition av cmdlet-klass</span><span class="sxs-lookup"><span data-stu-id="afdaf-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="afdaf-129">Följande kod är definitionen för en GetProc-cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="afdaf-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="afdaf-130">Observera att Pascal-höljet används och att namnet på klassen innehåller verbets verb och substantiv.</span><span class="sxs-lookup"><span data-stu-id="afdaf-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="afdaf-131">Pascal-hölje</span><span class="sxs-lookup"><span data-stu-id="afdaf-131">Pascal Casing</span></span>

<span data-ttu-id="afdaf-132">När du namnger cmdletar använder du Pascal-Skift läge.</span><span class="sxs-lookup"><span data-stu-id="afdaf-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="afdaf-133">Till exempel visar `Get-Item`-och `Get-ItemProperty`-cmdlets det korrekta sättet att använda versaler när du namnger cmdlets.</span><span class="sxs-lookup"><span data-stu-id="afdaf-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="afdaf-134">Se även</span><span class="sxs-lookup"><span data-stu-id="afdaf-134">See Also</span></span>

[<span data-ttu-id="afdaf-135">System. Management. Automation. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="afdaf-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="afdaf-136">CmdletAttribute-deklaration</span><span class="sxs-lookup"><span data-stu-id="afdaf-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="afdaf-137">Cmdlet-verb</span><span class="sxs-lookup"><span data-stu-id="afdaf-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="afdaf-138">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="afdaf-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="afdaf-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="afdaf-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
