---
title: Typer av cmdlet-parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359180"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="18de5-102">Typer av cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="18de5-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="18de5-103">I det här avsnittet beskrivs de olika typerna av parametrar som du kan deklarera i-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="18de5-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="18de5-104">Cmdlet-parametrar kan vara positions, namngivna, obligatoriska, valfria eller växla parametrar.</span><span class="sxs-lookup"><span data-stu-id="18de5-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="18de5-105">Parametrar för position och namngivna</span><span class="sxs-lookup"><span data-stu-id="18de5-105">Positional and Named Parameters</span></span>

<span data-ttu-id="18de5-106">Alla cmdlet-parametrar är antingen namngivna eller positions parametrar.</span><span class="sxs-lookup"><span data-stu-id="18de5-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="18de5-107">En namngiven parameter kräver att du anger parameter namnet och argumentet när du anropar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="18de5-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="18de5-108">En positions parameter kräver bara att du skriver argumenten i relativ ordning.</span><span class="sxs-lookup"><span data-stu-id="18de5-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="18de5-109">Systemet mappar sedan det första argumentet utan namn till den första positions parametern.</span><span class="sxs-lookup"><span data-stu-id="18de5-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="18de5-110">Systemet mappar det andra namnlösa argumentet till den andra namnlösa parametern och så vidare.</span><span class="sxs-lookup"><span data-stu-id="18de5-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="18de5-111">Som standard är alla cmdlet-parametrar namngivna parametrar.</span><span class="sxs-lookup"><span data-stu-id="18de5-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="18de5-112">Om du vill definiera en namngiven parameter utelämnar du nyckelordet `Position` i **parameter** deklarationen, som du ser i följande parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="18de5-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="18de5-113">Om du vill definiera en positions parameter lägger du till nyckelordet `Position` i parameter deklarationen och anger sedan en position.</span><span class="sxs-lookup"><span data-stu-id="18de5-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="18de5-114">I följande exempel deklareras parametern `UserName` som en positions parameter med position 0.</span><span class="sxs-lookup"><span data-stu-id="18de5-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="18de5-115">Det innebär att det första argumentet för anropet automatiskt binds till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="18de5-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

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
> <span data-ttu-id="18de5-116">Lämplig cmdlet-design rekommenderar att de mest använda parametrarna deklareras som positions parametrar så att användaren inte behöver ange parameter namnet när cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="18de5-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="18de5-117">Positions-och namngivna parametrar accepterar enskilda argument eller flera argument avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="18de5-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="18de5-118">Flera argument tillåts endast om parametern accepterar en samling, till exempel en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="18de5-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="18de5-119">Du kan blanda positions-och namngivna parametrar i samma cmdlet.</span><span class="sxs-lookup"><span data-stu-id="18de5-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="18de5-120">I det här fallet hämtar systemet de namngivna argumenten först och försöker sedan mappa de återstående namnlösa argumenten till positions parametrarna.</span><span class="sxs-lookup"><span data-stu-id="18de5-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="18de5-121">Följande kommandon visar de olika sätt som du kan använda för att ange enstaka och flera argument för parametrarna i `Get-Command`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="18de5-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="18de5-122">Observera att i de två sista exemplen behöver inte **-Name** anges eftersom parametern `Name` definieras som en positions parameter.</span><span class="sxs-lookup"><span data-stu-id="18de5-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="18de5-123">Obligatoriska och valfria parametrar</span><span class="sxs-lookup"><span data-stu-id="18de5-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="18de5-124">Du kan också definiera cmdlet-parametrar som obligatoriska eller valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="18de5-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="18de5-125">(En obligatorisk parameter måste anges innan Windows PowerShell-körningsmiljön anropar cmdleten.)  Som standard definieras parametrar som valfria.</span><span class="sxs-lookup"><span data-stu-id="18de5-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="18de5-126">Om du vill definiera en obligatorisk parameter lägger du till nyckelordet `Mandatory` i parameter deklarationen och anger det till `true`, som du ser i följande parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="18de5-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="18de5-127">Om du vill definiera en valfri parameter utelämnar du nyckelordet `Mandatory` i **parameter** deklarationen, som du ser i följande parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="18de5-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="18de5-128">Växla parametrar</span><span class="sxs-lookup"><span data-stu-id="18de5-128">Switch Parameters</span></span>

<span data-ttu-id="18de5-129">Windows PowerShell innehåller en typ av [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) som gör att du kan definiera en parameter vars värde anges automatiskt till `false` om parametern inte anges när cmdleten anropas.</span><span class="sxs-lookup"><span data-stu-id="18de5-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="18de5-130">Använd när det är möjligt och Använd switch-parametrar i stället för booleska parametrar.</span><span class="sxs-lookup"><span data-stu-id="18de5-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="18de5-131">Överväg följande exempel.</span><span class="sxs-lookup"><span data-stu-id="18de5-131">Consider the following sample.</span></span> <span data-ttu-id="18de5-132">Som standard skickar flera Windows PowerShell-cmdlets inte ett utgående objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="18de5-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="18de5-133">Dessa cmdletar har dock en `PassThru`-växel parameter som åsidosätter standard beteendet.</span><span class="sxs-lookup"><span data-stu-id="18de5-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="18de5-134">Om parametern `PassThru` anges när dessa cmdletar anropas, returnerar cmdleten ett utgående objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="18de5-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="18de5-135">Om du behöver parametern för att ha standardvärdet `true` när parametern inte anges i anropet, bör du överväga att återställa meningen för parametern.</span><span class="sxs-lookup"><span data-stu-id="18de5-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="18de5-136">I stället för att ange attributet parameter till ett booleskt värde för `true`, deklarera egenskapen som [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -typ och ange sedan standardvärdet för parametern till `false`.</span><span class="sxs-lookup"><span data-stu-id="18de5-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="18de5-137">För att definiera en switch-parameter, deklarera egenskapen som [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -typ, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="18de5-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="18de5-138">Om du vill att cmdleten ska fungera på parametern när den har angetts använder du följande struktur i någon av metoderna för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="18de5-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="18de5-139">Se även</span><span class="sxs-lookup"><span data-stu-id="18de5-139">See Also</span></span>

[<span data-ttu-id="18de5-140">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="18de5-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
