---
title: ValidatePattern-Attribute-deklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359144"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="3eb02-102">Deklaration av attributet ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="3eb02-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="3eb02-103">Attributet ValidatePattern anger ett mönster för reguljära uttryck som validerar argumentet för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="3eb02-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="3eb02-104">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="3eb02-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="3eb02-105">När ValidatePattern anropas i en cmdlet konverterar Windows PowerShell-körningsmiljön argumentet för cmdlet-parametern till en sträng och jämför sedan strängen med det mönster som anges av attributet ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="3eb02-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="3eb02-106">Cmdleten körs bara om den konverterade sträng representationen för argumentet och den angivna mönster matchningen.</span><span class="sxs-lookup"><span data-stu-id="3eb02-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="3eb02-107">Om de inte matchar uppstår ett fel i Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="3eb02-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="3eb02-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="3eb02-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="3eb02-109">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3eb02-109">Parameters</span></span>

<span data-ttu-id="3eb02-110">`RegexString` ([system. String](/dotnet/api/System.String)) krävs.</span><span class="sxs-lookup"><span data-stu-id="3eb02-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="3eb02-111">Anger ett reguljärt uttryck som validerar parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="3eb02-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="3eb02-112">Alternativ ([system. text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="3eb02-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="3eb02-113">Anger en bitvis kombination av [system. text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) -flaggor som anger alternativ för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="3eb02-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="3eb02-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3eb02-114">Remarks</span></span>

- <span data-ttu-id="3eb02-115">Det här attributet kan bara användas en gång per parameter.</span><span class="sxs-lookup"><span data-stu-id="3eb02-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="3eb02-116">Du kan använda parametern `Option` för attributet för att ytterligare definiera mönstret.</span><span class="sxs-lookup"><span data-stu-id="3eb02-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="3eb02-117">Du kan till exempel göra mönster Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="3eb02-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="3eb02-118">Om attributet används för en samling måste varje element i samlingen matcha mönstret.</span><span class="sxs-lookup"><span data-stu-id="3eb02-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="3eb02-119">Attributet ValidatePattern definieras av klassen [system. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .</span><span class="sxs-lookup"><span data-stu-id="3eb02-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3eb02-120">Se även</span><span class="sxs-lookup"><span data-stu-id="3eb02-120">See Also</span></span>

[<span data-ttu-id="3eb02-121">System. Management. Automation. Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="3eb02-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="3eb02-122">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="3eb02-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
