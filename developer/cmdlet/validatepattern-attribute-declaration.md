---
title: Deklaration av ValidatePattern attribut | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067135"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="7bce4-102">Deklaration av attributet ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="7bce4-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="7bce4-103">Attributet ValidatePattern anger ett mönster för reguljärt uttryck som validerar argumentet för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="7bce4-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="7bce4-104">Det här attributet kan också användas i Windows PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="7bce4-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="7bce4-105">När ValidatePattern anropas i en cmdlet, Windows PowerShell-runtime Konverterar argumentet för cmdlet-parameter till en sträng och sedan jämförs strängen i mönstret som tillhandahålls av ValidatePattern-attributet.</span><span class="sxs-lookup"><span data-stu-id="7bce4-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="7bce4-106">Cmdleten körs bara om den konvertera strängrepresentationen av argumentet och det angivna mönstren matchar.</span><span class="sxs-lookup"><span data-stu-id="7bce4-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="7bce4-107">Om de inte matchar genereras ett fel av Windows PowerShell-körningen.</span><span class="sxs-lookup"><span data-stu-id="7bce4-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="7bce4-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="7bce4-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="7bce4-109">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7bce4-109">Parameters</span></span>

<span data-ttu-id="7bce4-110">`RegexString` ([System.String](/dotnet/api/System.String)) krävs.</span><span class="sxs-lookup"><span data-stu-id="7bce4-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="7bce4-111">Anger ett reguljärt uttryck som validerar Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="7bce4-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="7bce4-112">Alternativ ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) valfritt med namnet parametern.</span><span class="sxs-lookup"><span data-stu-id="7bce4-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="7bce4-113">Anger en bitvis kombination av [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flaggor som anger alternativ för reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="7bce4-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="7bce4-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7bce4-114">Remarks</span></span>

- <span data-ttu-id="7bce4-115">Det här attributet kan användas endast en gång per parametern.</span><span class="sxs-lookup"><span data-stu-id="7bce4-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="7bce4-116">Du kan använda den `Option` parametern för attributet för att definiera ytterligare mönstret.</span><span class="sxs-lookup"><span data-stu-id="7bce4-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="7bce4-117">Exempelvis kan göra du mönstret skiftlägeskänsligt.</span><span class="sxs-lookup"><span data-stu-id="7bce4-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="7bce4-118">Om det här attributet används för en samling, måste varje element i samlingen matcha mönstret.</span><span class="sxs-lookup"><span data-stu-id="7bce4-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="7bce4-119">Attributet ValidatePattern definieras av den [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="7bce4-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bce4-120">Se även</span><span class="sxs-lookup"><span data-stu-id="7bce4-120">See Also</span></span>

[<span data-ttu-id="7bce4-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="7bce4-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="7bce4-122">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7bce4-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
