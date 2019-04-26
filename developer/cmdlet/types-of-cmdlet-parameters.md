---
title: Typer av Cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067203"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="96a69-102">Typer av cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="96a69-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="96a69-103">Det här avsnittet beskrivs de olika typerna av parametrar som du kan deklarera i cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="96a69-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="96a69-104">Cmdlet-parametrarna kan vara namngivna, namngivna, obligatorisk, valfri eller växla parametrar.</span><span class="sxs-lookup"><span data-stu-id="96a69-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="96a69-105">Namngivna och namngivna parametrar</span><span class="sxs-lookup"><span data-stu-id="96a69-105">Positional and Named Parameters</span></span>

<span data-ttu-id="96a69-106">Alla cmdlet-parametrarna är namngivna eller namngivna parametrar.</span><span class="sxs-lookup"><span data-stu-id="96a69-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="96a69-107">En namngiven parameter uppmanas att ange parameternamnet och argumentet när du anropar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96a69-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="96a69-108">Namngivna parametern kräver endast att du skriver argumenten i relativa ordning.</span><span class="sxs-lookup"><span data-stu-id="96a69-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="96a69-109">Systemet mappar sedan det första argumentet för Namnlös till den första namngivna parametern.</span><span class="sxs-lookup"><span data-stu-id="96a69-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="96a69-110">Systemet mappar det andra argumentet för Namnlös till andra icke namngivna parametern och så vidare.</span><span class="sxs-lookup"><span data-stu-id="96a69-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="96a69-111">Som standard är alla cmdlet-parametrarna namngivna parametrar.</span><span class="sxs-lookup"><span data-stu-id="96a69-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="96a69-112">För att definiera en namngiven parameter, utelämnar den `Position` nyckelord i den **parametern** attributet deklarationen enligt följande parameterdeklaration.</span><span class="sxs-lookup"><span data-stu-id="96a69-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="96a69-113">För att definiera en namngivna parametern, lägger du till den `Position` nyckelord i parametern attributet deklarationen och ange sedan en plats.</span><span class="sxs-lookup"><span data-stu-id="96a69-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="96a69-114">I följande exempel och den `UserName` parametern deklareras som en namngivna parametern med position 0.</span><span class="sxs-lookup"><span data-stu-id="96a69-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="96a69-115">Det innebär att det första argumentet för anropet automatiskt kommer att bindas till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="96a69-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="96a69-116">Cmdlet: en bra design rekommenderas att de mest använda parametrarna deklareras som positionsparametrar så att användaren inte behöver ange parameternamnet när cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="96a69-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="96a69-117">Namngivna och namngivna parametrar godkänner enda argument eller flera argument avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="96a69-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="96a69-118">Flera argument tillåts endast om parametern accepterar en samling, till exempel en matris med strängar.</span><span class="sxs-lookup"><span data-stu-id="96a69-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="96a69-119">Du kan blanda namngivna och namngivna parametrar i samma cmdlet.</span><span class="sxs-lookup"><span data-stu-id="96a69-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="96a69-120">I det här fallet systemet hämtar namngivna argument först och sedan försöker mappa de återstående icke namngivna argument till de namngivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="96a69-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="96a69-121">Kommandona i följande visar olika sätt som du kan ange enstaka eller flera argument för parametrarna för den `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="96a69-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="96a69-122">Observera att i de två senaste samplingarna **-namnet** behöver inte anges eftersom den `Name` parametern har definierats som en namngivna parametern.</span><span class="sxs-lookup"><span data-stu-id="96a69-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="96a69-123">Obligatoriska och valfria parametrar</span><span class="sxs-lookup"><span data-stu-id="96a69-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="96a69-124">Du kan också definiera parametrar för cmdleten som obligatoriska eller valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="96a69-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="96a69-125">(En obligatorisk parameter måste anges innan Windows PowerShell-runtime anropar cmdlet: en.)  Som standard definieras parametrar som valfria.</span><span class="sxs-lookup"><span data-stu-id="96a69-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="96a69-126">För att definiera en obligatorisk parameter, lägger du till den `Mandatory` nyckelord i parametern attributet deklarationen och ange den till `true`, enligt följande parameterdeklaration.</span><span class="sxs-lookup"><span data-stu-id="96a69-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="96a69-127">För att definiera en valfri parameter, utelämnar den `Mandatory` nyckelord i den **parametern** attributet deklarationen enligt följande parameterdeklaration.</span><span class="sxs-lookup"><span data-stu-id="96a69-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="96a69-128">Växla parametrar</span><span class="sxs-lookup"><span data-stu-id="96a69-128">Switch Parameters</span></span>

<span data-ttu-id="96a69-129">Windows PowerShell tillhandahåller en [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typ som kan du definiera en parameter vars värde ställs automatiskt in `false` om parametern inte anges när cmdlet anropas.</span><span class="sxs-lookup"><span data-stu-id="96a69-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="96a69-130">När det är möjligt använda växeln parametrar i stället för booleska parametrar.</span><span class="sxs-lookup"><span data-stu-id="96a69-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="96a69-131">Överväg följande exempel.</span><span class="sxs-lookup"><span data-stu-id="96a69-131">Consider the following sample.</span></span> <span data-ttu-id="96a69-132">Som standard skickar inte ett utdataobjekt av pipelinen i flera Windows PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="96a69-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="96a69-133">Dessa cmdletar har dock en `PassThru` växla parametern som åsidosätter standardbeteendet.</span><span class="sxs-lookup"><span data-stu-id="96a69-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="96a69-134">Om den `PassThru` parametern anges när dessa cmdletar kallas, cmdleten returnerar ett utdataobjekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="96a69-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="96a69-135">Om du behöver ha ett standardvärde för parametern `true` om parametern inte anges i anropet du överväga att byta plats uppfattning parametern.</span><span class="sxs-lookup"><span data-stu-id="96a69-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="96a69-136">För exemplet, i stället för ett booleskt värde för att ställa in parameterattributet `true`, deklarera egenskapen som den [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) skriver och sedan ange standardvärdet för parametern ska `false`.</span><span class="sxs-lookup"><span data-stu-id="96a69-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="96a69-137">Om du vill definiera en växlingsparametern deklarera egenskapen som den [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) skriver, enligt följande exempel.</span><span class="sxs-lookup"><span data-stu-id="96a69-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="96a69-138">Använd följande struktur inom någon av metoderna indata för att göra cmdleten agera på parametern när det har angetts.</span><span class="sxs-lookup"><span data-stu-id="96a69-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="96a69-139">Se även</span><span class="sxs-lookup"><span data-stu-id="96a69-139">See Also</span></span>

[<span data-ttu-id="96a69-140">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="96a69-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
