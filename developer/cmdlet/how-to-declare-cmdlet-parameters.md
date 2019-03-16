---
title: Hur du deklarera Cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059175"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="1779e-102">Deklarera cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="1779e-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="1779e-103">De här exemplen visar hur du deklarera namngivna, namngivna, obligatorisk, valfri och växla parametrar.</span><span class="sxs-lookup"><span data-stu-id="1779e-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="1779e-104">De här exemplen visar också hur du definierar ett parameteralias.</span><span class="sxs-lookup"><span data-stu-id="1779e-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="1779e-105">Hur du deklarera en namngiven Parameter</span><span class="sxs-lookup"><span data-stu-id="1779e-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="1779e-106">Definiera en offentlig egenskap enligt följande kod.</span><span class="sxs-lookup"><span data-stu-id="1779e-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1779e-107">När du lägger till parametern-attributet utelämna den `Position` nyckelord från attributet.</span><span class="sxs-lookup"><span data-stu-id="1779e-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1779e-108">Läs mer om parameterattributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1779e-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="1779e-109">Hur du deklarera ett namngivna parametern</span><span class="sxs-lookup"><span data-stu-id="1779e-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="1779e-110">Definiera en offentlig egenskap enligt följande kod.</span><span class="sxs-lookup"><span data-stu-id="1779e-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1779e-111">När du lägger till parametern-attributet i `Position` nyckelord till argumentet positionen.</span><span class="sxs-lookup"><span data-stu-id="1779e-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="1779e-112">Värdet 0 anger den första positionen.</span><span class="sxs-lookup"><span data-stu-id="1779e-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1779e-113">Läs mer om parameterattributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1779e-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="1779e-114">Hur du deklarera en obligatorisk Parameter</span><span class="sxs-lookup"><span data-stu-id="1779e-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="1779e-115">Definiera en offentlig egenskap enligt följande kod.</span><span class="sxs-lookup"><span data-stu-id="1779e-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1779e-116">När du lägger till parametern-attributet i `Mandatory` nyckelord till `true`.</span><span class="sxs-lookup"><span data-stu-id="1779e-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1779e-117">Läs mer om parameterattributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1779e-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="1779e-118">Hur du deklarera en valfri Parameter</span><span class="sxs-lookup"><span data-stu-id="1779e-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="1779e-119">Definiera en offentlig egenskap enligt följande kod.</span><span class="sxs-lookup"><span data-stu-id="1779e-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1779e-120">När du lägger till parametern-attributet utelämna den `Mandatory` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="1779e-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="1779e-121">Hur du deklarera ett växlingsparametern</span><span class="sxs-lookup"><span data-stu-id="1779e-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="1779e-122">Definiera en offentlig egenskap som typen [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), och sedan deklarera parametern-attributet.</span><span class="sxs-lookup"><span data-stu-id="1779e-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="1779e-123">Läs mer om parameterattributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1779e-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="1779e-124">Hur du deklarera en Parameter med alias</span><span class="sxs-lookup"><span data-stu-id="1779e-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="1779e-125">Definiera en offentlig egenskap enligt följande kod.</span><span class="sxs-lookup"><span data-stu-id="1779e-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1779e-126">Lägg till ett Alias-attribut som visas tillgängliga alias för parametern.</span><span class="sxs-lookup"><span data-stu-id="1779e-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="1779e-127">I det här exemplet definieras tre alias för samma parameter.</span><span class="sxs-lookup"><span data-stu-id="1779e-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="1779e-128">Det första aliaset innehåller en genväg.</span><span class="sxs-lookup"><span data-stu-id="1779e-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="1779e-129">Andra och tredje alias ger namn som du kan använda för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="1779e-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="1779e-130">Läs mer om attributet Alias [Alias attributet deklarationen](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1779e-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1779e-131">Se även</span><span class="sxs-lookup"><span data-stu-id="1779e-131">See Also</span></span>

[<span data-ttu-id="1779e-132">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="1779e-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="1779e-133">Attributet parameterdeklaration</span><span class="sxs-lookup"><span data-stu-id="1779e-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="1779e-134">Aliasdeklaration av attribut</span><span class="sxs-lookup"><span data-stu-id="1779e-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="1779e-135">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1779e-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
