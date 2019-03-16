---
title: Cmdlet klassdeklarationen | Microsoft Docs
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
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055095"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="7ab19-102">Cmdlet-klassdeklaration</span><span class="sxs-lookup"><span data-stu-id="7ab19-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="7ab19-103">En Microsoft .NET Framework-klass deklareras som en cmdlet genom att ange den **Cmdlet** attribut som metadata för klassen.</span><span class="sxs-lookup"><span data-stu-id="7ab19-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="7ab19-104">(Den **Cmdlet** attributet är det enda obligatoriska attributet för alla cmdletar).</span><span class="sxs-lookup"><span data-stu-id="7ab19-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="7ab19-105">När du anger den **Cmdlet** attribut, måste du ange verb och substantiv-paret som identifierar cmdlet: en för användaren.</span><span class="sxs-lookup"><span data-stu-id="7ab19-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="7ab19-106">Och du måste beskriver funktioner i Windows PowerShell som har stöd för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7ab19-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="7ab19-107">Mer information om deklarationssyntax som används för att ange den **Cmdlet** attributet, se [Cmdlet attributet deklarationen](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7ab19-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7ab19-108">Den **Cmdlet** attributet definieras av den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="7ab19-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="7ab19-109">Egenskaperna för den här klassen motsvarar deklarationsparametrar som ska användas när du deklarerar attributet.</span><span class="sxs-lookup"><span data-stu-id="7ab19-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="7ab19-110">Substantiv</span><span class="sxs-lookup"><span data-stu-id="7ab19-110">Nouns</span></span>

<span data-ttu-id="7ab19-111">Substantiv-cmdlet: ens anger vilka resurser som cmdlet: en fungerar.</span><span class="sxs-lookup"><span data-stu-id="7ab19-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="7ab19-112">Substantivet särskiljer dina cmdletar från andra cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="7ab19-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="7ab19-113">Substantiv i cmdlet-namn måste vara specifikt, och när det gäller allmän substantiv som *server*, är det bäst att lägga till ett kort prefix som särskiljer resursen från andra liknande resurser.</span><span class="sxs-lookup"><span data-stu-id="7ab19-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="7ab19-114">Till exempel en cmdlet-namn som innehåller ett substantiv med prefixet är `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="7ab19-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="7ab19-115">Kombinationen av en specifik substantiv med en mer allmän verbet kan användaren snabbt kan hitta cmdlet: en av dess åtgärden och identifiera cmdlet: en av dess resurs samtidigt som du undviker onödiga cmdlet namn duplicering.</span><span class="sxs-lookup"><span data-stu-id="7ab19-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="7ab19-116">En lista över specialtecken som inte kan användas i cmdlet-namnen finns i [krävs utveckling riktlinjer](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="7ab19-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="7ab19-117">Verb</span><span class="sxs-lookup"><span data-stu-id="7ab19-117">Verbs</span></span>

<span data-ttu-id="7ab19-118">När du anger ett verb, kräver riktlinjer för utveckling att du använder någon av de fördefinierade verb som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ab19-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="7ab19-119">Med någon av dessa fördefinierade verb, säkerställer konsekvens mellan de cmdletar som du skriver och som har skrivits av Microsoft och andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="7ab19-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="7ab19-120">Till exempel används ”Get”-verb för cmdletar som hämtar data.</span><span class="sxs-lookup"><span data-stu-id="7ab19-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="7ab19-121">Läs mer om riktlinjer för verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="7ab19-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="7ab19-122">En lista över specialtecken som inte kan användas i cmdlet-namnen finns i [krävs utveckling riktlinjer](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="7ab19-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="7ab19-123">Stöd för Windows PowerShell-funktioner</span><span class="sxs-lookup"><span data-stu-id="7ab19-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="7ab19-124">Den **Cmdlet** attribut kan du ange att din cmdlet har stöd för några av de vanliga funktioner som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ab19-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="7ab19-125">Detta inkluderar stöd för vanliga funktioner, till exempel feedback Användarbekräftelse (kallas stöd för ShouldProcess-funktionen) och stöd för transaktioner.</span><span class="sxs-lookup"><span data-stu-id="7ab19-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="7ab19-126">(Stöd för transaktioner introducerades i Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="7ab19-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="7ab19-127">Mer information om deklarationssyntax som används för att ange den **Cmdlet** attributet, se [Cmdlet attributet deklarationen](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7ab19-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="7ab19-128">Cmdlet-klassdefinition</span><span class="sxs-lookup"><span data-stu-id="7ab19-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="7ab19-129">Följande kod är definitionen för en GetProc cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="7ab19-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="7ab19-130">Observera att Pascal gemener och versaler används och att namnet på klassen innehåller verb och substantiv-cmdlet: ens.</span><span class="sxs-lookup"><span data-stu-id="7ab19-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="7ab19-131">Pascal gemener och versaler</span><span class="sxs-lookup"><span data-stu-id="7ab19-131">Pascal Casing</span></span>

<span data-ttu-id="7ab19-132">När du namnger cmdlet: ar, använda Pascal gemener och versaler.</span><span class="sxs-lookup"><span data-stu-id="7ab19-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="7ab19-133">Till exempel den `Get-Item` och `Get-ItemProperty` cmdletar visar det korrekta sättet att använda versaler när du namnger cmdletar.</span><span class="sxs-lookup"><span data-stu-id="7ab19-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ab19-134">Se även</span><span class="sxs-lookup"><span data-stu-id="7ab19-134">See Also</span></span>

[<span data-ttu-id="7ab19-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="7ab19-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="7ab19-136">CmdletAttribute deklaration</span><span class="sxs-lookup"><span data-stu-id="7ab19-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="7ab19-137">Cmdlet Verb namn</span><span class="sxs-lookup"><span data-stu-id="7ab19-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="7ab19-138">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ab19-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="7ab19-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7ab19-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
