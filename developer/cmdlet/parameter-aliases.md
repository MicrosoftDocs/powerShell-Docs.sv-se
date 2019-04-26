---
title: Parameteralias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067594"
---
# <a name="parameter-aliases"></a><span data-ttu-id="53f0e-102">Parameteralias</span><span class="sxs-lookup"><span data-stu-id="53f0e-102">Parameter Aliases</span></span>

<span data-ttu-id="53f0e-103">Cmdlet-parametrarna kan också ha alias.</span><span class="sxs-lookup"><span data-stu-id="53f0e-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="53f0e-104">Du kan använda alias i stället för i parameternamnen när du skriver eller ange parametern i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="53f0e-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="53f0e-105">Fördelarna med att använda alias</span><span class="sxs-lookup"><span data-stu-id="53f0e-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="53f0e-106">Att lägga till alias i Parametrar ger följande fördelar.</span><span class="sxs-lookup"><span data-stu-id="53f0e-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="53f0e-107">Du kan ange en genväg så att användaren inte behöver använda det fullständiga parameternamnet när cmdlet anropas.</span><span class="sxs-lookup"><span data-stu-id="53f0e-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="53f0e-108">Du kan exempelvis använda aliaset ”CN” i stället för parameternamnet ”datornamn”.</span><span class="sxs-lookup"><span data-stu-id="53f0e-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="53f0e-109">Du kan definiera flera alias om du vill ge olika namn för samma parameter.</span><span class="sxs-lookup"><span data-stu-id="53f0e-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="53f0e-110">Du kanske vill definiera flera alias om du ska arbeta med flera användargrupper som refererar till samma data på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="53f0e-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="53f0e-111">Du kan ge bakåtkompatibilitet kompatibilitet för befintliga skript om namnet på en parameter ändras.</span><span class="sxs-lookup"><span data-stu-id="53f0e-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="53f0e-112">Genom att använda attributet Alias tillsammans med attributet ValueFromPipelineByName kan definiera du en parameter för cmdlet: att binda till olika objekttyper.</span><span class="sxs-lookup"><span data-stu-id="53f0e-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="53f0e-113">Anta exempelvis att du har två objekt av olika typer och det första objektet hade en skrivare egenskap och det andra objektet hade en redigerare-egenskap.</span><span class="sxs-lookup"><span data-stu-id="53f0e-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="53f0e-114">Om din cmdlet hade en parameter som hade skrivaren och redigerare alias och cmdleten accepterat indata från pipeline i egenskapsnamn, cmdlet: kan bindas till båda objekt med hjälp av två parameteralias.</span><span class="sxs-lookup"><span data-stu-id="53f0e-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="53f0e-115">Mer information om alias som kan användas med specifika parametrar finns i [vanliga parameternamn](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="53f0e-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="53f0e-116">Definiera Parameteralias</span><span class="sxs-lookup"><span data-stu-id="53f0e-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="53f0e-117">Deklarera Alias-attributet för att definiera ett alias för en parameter, enligt följande parameterdeklaration.</span><span class="sxs-lookup"><span data-stu-id="53f0e-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="53f0e-118">I det här exemplet definieras flera alias för samma parameter.</span><span class="sxs-lookup"><span data-stu-id="53f0e-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="53f0e-119">(Mer information finns i[så deklarera Cmdlet-parametrarna](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="53f0e-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="53f0e-120">Se även</span><span class="sxs-lookup"><span data-stu-id="53f0e-120">See Also</span></span>

[<span data-ttu-id="53f0e-121">Vanliga parameternamn</span><span class="sxs-lookup"><span data-stu-id="53f0e-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="53f0e-122">Hur du deklarera Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="53f0e-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="53f0e-123">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="53f0e-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
