---
ms.date: 09/13/2016
ms.topic: reference
title: Deklarera cmdlet-parametrar
description: Deklarera cmdlet-parametrar
ms.openlocfilehash: ed53f9788c9afb142b137e08966dff33551b9d0f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667104"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="021e3-103">Deklarera cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="021e3-103">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="021e3-104">I de här exemplen visas hur du deklarerar namngivna, positionerade, obligatoriska, valfria och växla parametrar.</span><span class="sxs-lookup"><span data-stu-id="021e3-104">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="021e3-105">De här exemplen visar också hur du definierar ett parameter Ali Aset.</span><span class="sxs-lookup"><span data-stu-id="021e3-105">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="021e3-106">Så här deklarerar du en namngiven parameter</span><span class="sxs-lookup"><span data-stu-id="021e3-106">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="021e3-107">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="021e3-107">Define a public property as shown in the following code.</span></span> <span data-ttu-id="021e3-108">När du lägger till attributet parameter utelämnar du `Position` nyckelordet från attributet.</span><span class="sxs-lookup"><span data-stu-id="021e3-108">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="021e3-109">Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="021e3-109">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="021e3-110">Så här deklarerar du en positions parameter</span><span class="sxs-lookup"><span data-stu-id="021e3-110">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="021e3-111">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="021e3-111">Define a public property as shown in the following code.</span></span> <span data-ttu-id="021e3-112">När du lägger till attributet parameter anger du `Position` nyckelordet till argument positionen.</span><span class="sxs-lookup"><span data-stu-id="021e3-112">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="021e3-113">Värdet 0 anger den första positionen.</span><span class="sxs-lookup"><span data-stu-id="021e3-113">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="021e3-114">Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="021e3-114">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="021e3-115">Så här deklarerar du en obligatorisk parameter</span><span class="sxs-lookup"><span data-stu-id="021e3-115">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="021e3-116">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="021e3-116">Define a public property as shown in the following code.</span></span> <span data-ttu-id="021e3-117">När du lägger till attributet parameter anger du `Mandatory` nyckelordet till `true` .</span><span class="sxs-lookup"><span data-stu-id="021e3-117">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="021e3-118">Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="021e3-118">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="021e3-119">Så här deklarerar du en valfri parameter</span><span class="sxs-lookup"><span data-stu-id="021e3-119">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="021e3-120">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="021e3-120">Define a public property as shown in the following code.</span></span> <span data-ttu-id="021e3-121">När du lägger till attributet parameter utelämnar du `Mandatory` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="021e3-121">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="021e3-122">Så här deklarerar du en växel parameter</span><span class="sxs-lookup"><span data-stu-id="021e3-122">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="021e3-123">Definiera en offentlig egenskap som typ [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)och deklarera sedan attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="021e3-123">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="021e3-124">Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="021e3-124">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="021e3-125">Så här deklarerar du en parameter med alias</span><span class="sxs-lookup"><span data-stu-id="021e3-125">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="021e3-126">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="021e3-126">Define a public property as shown in the following code.</span></span> <span data-ttu-id="021e3-127">Lägg till ett alias som visar ett alias för parametern.</span><span class="sxs-lookup"><span data-stu-id="021e3-127">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="021e3-128">I det här exemplet definieras tre alias för samma parameter.</span><span class="sxs-lookup"><span data-stu-id="021e3-128">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="021e3-129">Det första aliaset innehåller en genväg.</span><span class="sxs-lookup"><span data-stu-id="021e3-129">The first alias provides a shortcut.</span></span> <span data-ttu-id="021e3-130">Det andra och tredje aliaset ger namn som du kan använda för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="021e3-130">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="021e3-131">Mer information om alias-attributet finns i [deklarationen alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="021e3-131">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="021e3-132">Se även</span><span class="sxs-lookup"><span data-stu-id="021e3-132">See Also</span></span>

[<span data-ttu-id="021e3-133">System. Management. Automation. SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="021e3-133">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="021e3-134">Deklaration av attributet Parameter</span><span class="sxs-lookup"><span data-stu-id="021e3-134">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="021e3-135">Deklaration av attributet Alias</span><span class="sxs-lookup"><span data-stu-id="021e3-135">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="021e3-136">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="021e3-136">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
