---
title: Så här deklarerar du cmdlet-parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356401"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="f1303-102">Deklarera cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="f1303-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="f1303-103">I de här exemplen visas hur du deklarerar namngivna, positionerade, obligatoriska, valfria och växla parametrar.</span><span class="sxs-lookup"><span data-stu-id="f1303-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="f1303-104">De här exemplen visar också hur du definierar ett parameter Ali Aset.</span><span class="sxs-lookup"><span data-stu-id="f1303-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="f1303-105">Så här deklarerar du en namngiven parameter</span><span class="sxs-lookup"><span data-stu-id="f1303-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="f1303-106">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="f1303-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="f1303-107">När du lägger till attributet parameter utelämnar du nyckelordet `Position` från attributet.</span><span class="sxs-lookup"><span data-stu-id="f1303-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="f1303-108">Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f1303-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="f1303-109">Så här deklarerar du en positions parameter</span><span class="sxs-lookup"><span data-stu-id="f1303-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="f1303-110">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="f1303-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="f1303-111">När du lägger till attributet parameter anger du nyckelordet `Position` till argument positionen.</span><span class="sxs-lookup"><span data-stu-id="f1303-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="f1303-112">Värdet 0 anger den första positionen.</span><span class="sxs-lookup"><span data-stu-id="f1303-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="f1303-113">Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f1303-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="f1303-114">Så här deklarerar du en obligatorisk parameter</span><span class="sxs-lookup"><span data-stu-id="f1303-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="f1303-115">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="f1303-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="f1303-116">När du lägger till attributet parameter ställer du in nyckelordet `Mandatory` till `true`.</span><span class="sxs-lookup"><span data-stu-id="f1303-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="f1303-117">Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f1303-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="f1303-118">Så här deklarerar du en valfri parameter</span><span class="sxs-lookup"><span data-stu-id="f1303-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="f1303-119">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="f1303-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="f1303-120">När du lägger till attributet parameter utelämnar du nyckelordet `Mandatory`.</span><span class="sxs-lookup"><span data-stu-id="f1303-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="f1303-121">Så här deklarerar du en växel parameter</span><span class="sxs-lookup"><span data-stu-id="f1303-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="f1303-122">Definiera en offentlig egenskap som typ [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)och deklarera sedan attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="f1303-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="f1303-123">Mer information om attributet parameter finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f1303-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="f1303-124">Så här deklarerar du en parameter med alias</span><span class="sxs-lookup"><span data-stu-id="f1303-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="f1303-125">Definiera en offentlig egenskap som visas i följande kod.</span><span class="sxs-lookup"><span data-stu-id="f1303-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="f1303-126">Lägg till ett alias som visar ett alias för parametern.</span><span class="sxs-lookup"><span data-stu-id="f1303-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="f1303-127">I det här exemplet definieras tre alias för samma parameter.</span><span class="sxs-lookup"><span data-stu-id="f1303-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="f1303-128">Det första aliaset innehåller en genväg.</span><span class="sxs-lookup"><span data-stu-id="f1303-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="f1303-129">Det andra och tredje aliaset ger namn som du kan använda för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="f1303-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="f1303-130">Mer information om alias-attributet finns i [deklarationen alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f1303-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1303-131">Se även</span><span class="sxs-lookup"><span data-stu-id="f1303-131">See Also</span></span>

[<span data-ttu-id="f1303-132">System. Management. Automation. SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="f1303-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="f1303-133">Deklaration av parameter attribut</span><span class="sxs-lookup"><span data-stu-id="f1303-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="f1303-134">Deklaration av alias-attribut</span><span class="sxs-lookup"><span data-stu-id="f1303-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="f1303-135">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f1303-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
