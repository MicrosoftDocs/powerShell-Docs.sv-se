---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet ValidatePattern
description: Deklaration av attributet ValidatePattern
ms.openlocfilehash: 364f63d2c52563eaefe64bcbb2bbae511bccb074
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646169"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="21636-103">Deklaration av attributet ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="21636-103">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="21636-104">Attributet ValidatePattern anger ett mönster för reguljära uttryck som validerar argumentet för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="21636-104">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="21636-105">Det här attributet kan också användas av Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="21636-105">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="21636-106">När ValidatePattern anropas i en cmdlet konverterar Windows PowerShell-körningsmiljön argumentet för cmdlet-parametern till en sträng och jämför sedan strängen med det mönster som anges av attributet ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="21636-106">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="21636-107">Cmdleten körs bara om den konverterade sträng representationen för argumentet och den angivna mönster matchningen.</span><span class="sxs-lookup"><span data-stu-id="21636-107">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="21636-108">Om de inte matchar uppstår ett fel i Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="21636-108">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="21636-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="21636-109">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="21636-110">Parametrar</span><span class="sxs-lookup"><span data-stu-id="21636-110">Parameters</span></span>

<span data-ttu-id="21636-111">`RegexString` ([System. String](/dotnet/api/System.String)) krävs.</span><span class="sxs-lookup"><span data-stu-id="21636-111">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="21636-112">Anger ett reguljärt uttryck som validerar parameter argumentet.</span><span class="sxs-lookup"><span data-stu-id="21636-112">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="21636-113">Alternativ ([system. text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="21636-113">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="21636-114">Anger en bitvis kombination av [system. text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) -flaggor som anger alternativ för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="21636-114">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="21636-115">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="21636-115">Remarks</span></span>

- <span data-ttu-id="21636-116">Det här attributet kan bara användas en gång per parameter.</span><span class="sxs-lookup"><span data-stu-id="21636-116">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="21636-117">Du kan använda- `Option` parametern för attributet för att ytterligare definiera mönstret.</span><span class="sxs-lookup"><span data-stu-id="21636-117">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="21636-118">Du kan till exempel göra mönster Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="21636-118">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="21636-119">Om attributet används för en samling måste varje element i samlingen matcha mönstret.</span><span class="sxs-lookup"><span data-stu-id="21636-119">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="21636-120">Attributet ValidatePattern definieras av klassen [system. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .</span><span class="sxs-lookup"><span data-stu-id="21636-120">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="21636-121">Se även</span><span class="sxs-lookup"><span data-stu-id="21636-121">See Also</span></span>

[<span data-ttu-id="21636-122">System. Management. Automation. Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="21636-122">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="21636-123">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="21636-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
