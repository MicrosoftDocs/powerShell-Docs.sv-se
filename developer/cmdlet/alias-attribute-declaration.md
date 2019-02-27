---
title: Alias attributet deklarationen | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846146"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="ae2b7-102">Deklaration av attributet Alias</span><span class="sxs-lookup"><span data-stu-id="ae2b7-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="ae2b7-103">Attributet Alias gör att användaren att ange olika namn för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="ae2b7-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="ae2b7-104">Alias kan användas för att tillhandahålla genvägar för ett parameternamn och de kan tillhandahålla olika namn som är lämpliga för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="ae2b7-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae2b7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ae2b7-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="ae2b7-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ae2b7-106">Parameters</span></span>

<span data-ttu-id="ae2b7-107">`aliasName` (String[]) Krävs.</span><span class="sxs-lookup"><span data-stu-id="ae2b7-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="ae2b7-108">Anger en uppsättning med CSV-aliasnamn för cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="ae2b7-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae2b7-109">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ae2b7-109">Remarks</span></span>

- <span data-ttu-id="ae2b7-110">Alias-attributet används med attributet Parameter när du anger en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="ae2b7-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="ae2b7-111">Mer information om hur du deklarera dessa attribut finns i [så deklarera Cmdlet-parametrarna](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ae2b7-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="ae2b7-112">Varje aliasnamn måste vara unika inom en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae2b7-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="ae2b7-113">Windows PowerShell kontrollerar inte om duplicerade aliasnamn.</span><span class="sxs-lookup"><span data-stu-id="ae2b7-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="ae2b7-114">Alias-attributet används en gång för varje parameter i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae2b7-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="ae2b7-115">Alias-attributet definieras av den [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="ae2b7-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae2b7-116">Se även</span><span class="sxs-lookup"><span data-stu-id="ae2b7-116">See Also</span></span>

[<span data-ttu-id="ae2b7-117">Parameteralias</span><span class="sxs-lookup"><span data-stu-id="ae2b7-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="ae2b7-118">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae2b7-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
