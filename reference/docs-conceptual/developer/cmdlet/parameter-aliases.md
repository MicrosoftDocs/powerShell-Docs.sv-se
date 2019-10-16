---
title: Parameter Ali Aset | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359264"
---
# <a name="parameter-aliases"></a><span data-ttu-id="f82cd-102">Parameteralias</span><span class="sxs-lookup"><span data-stu-id="f82cd-102">Parameter Aliases</span></span>

<span data-ttu-id="f82cd-103">Cmdlet-parametrar kan också ha alias.</span><span class="sxs-lookup"><span data-stu-id="f82cd-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="f82cd-104">Du kan använda alias i stället för parameter namn när du skriver eller anger en parameter i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="f82cd-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="f82cd-105">Fördelar med att använda alias</span><span class="sxs-lookup"><span data-stu-id="f82cd-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="f82cd-106">Att lägga till alias i parametrar ger följande fördelar.</span><span class="sxs-lookup"><span data-stu-id="f82cd-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="f82cd-107">Du kan ange en genväg så att användaren inte behöver använda det fullständiga parameter namnet när cmdleten anropas.</span><span class="sxs-lookup"><span data-stu-id="f82cd-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="f82cd-108">Du kan till exempel använda aliaset "CN" i stället för parameter namnet "ComputerName".</span><span class="sxs-lookup"><span data-stu-id="f82cd-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="f82cd-109">Du kan definiera flera alias om du vill ange olika namn för samma parameter.</span><span class="sxs-lookup"><span data-stu-id="f82cd-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="f82cd-110">Du kanske vill definiera flera alias om du måste arbeta med flera användar grupper som refererar till samma data på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="f82cd-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="f82cd-111">Du kan ange bakåtkompatibilitet för befintliga skript om namnet på en parameter ändras.</span><span class="sxs-lookup"><span data-stu-id="f82cd-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="f82cd-112">Genom att använda attributet alias tillsammans med attributet ValueFromPipelineByName kan du definiera en parameter som tillåter att din cmdlet binder till olika objekt typer.</span><span class="sxs-lookup"><span data-stu-id="f82cd-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="f82cd-113">Anta till exempel att du har två objekt av olika typer och att det första objektet hade en skrivar egenskap och det andra objektet hade en redigerings egenskap.</span><span class="sxs-lookup"><span data-stu-id="f82cd-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="f82cd-114">Om cmdleten hade en parameter som hade Skriv-och redigerings Ali Aset och cmdleten accepterade pipeline-inflöden baserat på egenskaps namn, kan cmdlet: en binda till båda objekten med de två parameter-aliasen.</span><span class="sxs-lookup"><span data-stu-id="f82cd-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="f82cd-115">Mer information om alias som kan användas med vissa parametrar finns i [vanliga parameter namn](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="f82cd-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="f82cd-116">Definiera parameter-alias</span><span class="sxs-lookup"><span data-stu-id="f82cd-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="f82cd-117">Om du vill definiera ett alias för en parameter deklarerar du attributet alias, som du ser i följande parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="f82cd-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="f82cd-118">I det här exemplet definieras flera alias för samma parameter.</span><span class="sxs-lookup"><span data-stu-id="f82cd-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="f82cd-119">(Mer information finns i[så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="f82cd-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f82cd-120">Se även</span><span class="sxs-lookup"><span data-stu-id="f82cd-120">See Also</span></span>

[<span data-ttu-id="f82cd-121">Vanliga parameter namn</span><span class="sxs-lookup"><span data-stu-id="f82cd-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="f82cd-122">Så här deklarerar du cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="f82cd-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="f82cd-123">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f82cd-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
