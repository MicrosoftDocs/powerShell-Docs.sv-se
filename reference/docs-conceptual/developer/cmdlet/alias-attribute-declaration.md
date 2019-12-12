---
title: Deklaration av alias-attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359486"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="0251c-102">Deklaration av attributet Alias</span><span class="sxs-lookup"><span data-stu-id="0251c-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="0251c-103">Attributet alias gör att användaren kan ange olika namn för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="0251c-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="0251c-104">Alias kan användas för att ange genvägar för ett parameter namn, eller så kan de ange olika namn som passar för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="0251c-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="0251c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0251c-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="0251c-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="0251c-106">Parameters</span></span>

<span data-ttu-id="0251c-107">`aliasName` (sträng []) krävs.</span><span class="sxs-lookup"><span data-stu-id="0251c-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="0251c-108">Anger en uppsättning kommaavgränsade aliasnamn för cmdlet-parametern.</span><span class="sxs-lookup"><span data-stu-id="0251c-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="0251c-109">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0251c-109">Remarks</span></span>

- <span data-ttu-id="0251c-110">Attributet alias används med attributet parameter när du anger en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="0251c-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="0251c-111">Mer information om hur du deklarerar dessa attribut finns i [så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0251c-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="0251c-112">Varje aliasnamn måste vara unikt inom en-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0251c-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="0251c-113">Windows PowerShell söker inte efter dubbla aliasnamn.</span><span class="sxs-lookup"><span data-stu-id="0251c-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="0251c-114">Attributet alias används en gång för varje parameter i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0251c-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="0251c-115">Attributet alias definieras av klassen [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .</span><span class="sxs-lookup"><span data-stu-id="0251c-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0251c-116">Se även</span><span class="sxs-lookup"><span data-stu-id="0251c-116">See Also</span></span>

[<span data-ttu-id="0251c-117">Parameter-alias</span><span class="sxs-lookup"><span data-stu-id="0251c-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="0251c-118">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="0251c-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
