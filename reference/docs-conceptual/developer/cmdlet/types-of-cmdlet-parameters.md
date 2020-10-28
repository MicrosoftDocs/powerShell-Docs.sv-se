---
ms.date: 09/13/2016
ms.topic: reference
title: Typer av cmdlet-parametrar
description: Typer av cmdlet-parametrar
ms.openlocfilehash: 8daaa3c778396e06a826de3b93e0610c51160fb4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660491"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="c6569-103">Typer av cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="c6569-103">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="c6569-104">I det här avsnittet beskrivs de olika typerna av parametrar som du kan deklarera i-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="c6569-104">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="c6569-105">Cmdlet-parametrar kan vara positions, namngivna, obligatoriska, valfria eller växla parametrar.</span><span class="sxs-lookup"><span data-stu-id="c6569-105">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="c6569-106">Parametrar för position och namngivna</span><span class="sxs-lookup"><span data-stu-id="c6569-106">Positional and Named Parameters</span></span>

<span data-ttu-id="c6569-107">Alla cmdlet-parametrar är antingen namngivna eller positions parametrar.</span><span class="sxs-lookup"><span data-stu-id="c6569-107">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="c6569-108">En namngiven parameter kräver att du anger parameter namnet och argumentet när du anropar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c6569-108">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="c6569-109">En positions parameter kräver bara att du skriver argumenten i relativ ordning.</span><span class="sxs-lookup"><span data-stu-id="c6569-109">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="c6569-110">Systemet mappar sedan det första argumentet utan namn till den första positions parametern.</span><span class="sxs-lookup"><span data-stu-id="c6569-110">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="c6569-111">Systemet mappar det andra namnlösa argumentet till den andra namnlösa parametern och så vidare.</span><span class="sxs-lookup"><span data-stu-id="c6569-111">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="c6569-112">Som standard är alla cmdlet-parametrar namngivna parametrar.</span><span class="sxs-lookup"><span data-stu-id="c6569-112">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="c6569-113">Om du vill definiera en namngiven parameter utelämnar du `Position` nyckelordet i **parameter** -attributets deklaration, som du ser i följande parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="c6569-113">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="c6569-114">Om du vill definiera en positions parameter lägger du till `Position` nyckelordet i parametern parameter attribut och anger sedan en position.</span><span class="sxs-lookup"><span data-stu-id="c6569-114">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="c6569-115">I följande exempel `UserName` deklareras parametern som en positions parameter med position 0.</span><span class="sxs-lookup"><span data-stu-id="c6569-115">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="c6569-116">Det innebär att det första argumentet för anropet automatiskt binds till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="c6569-116">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

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
> <span data-ttu-id="c6569-117">Lämplig cmdlet-design rekommenderar att de mest använda parametrarna deklareras som positions parametrar så att användaren inte behöver ange parameter namnet när cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="c6569-117">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="c6569-118">Positions-och namngivna parametrar accepterar enskilda argument eller flera argument avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="c6569-118">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="c6569-119">Flera argument tillåts endast om parametern accepterar en samling, till exempel en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="c6569-119">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="c6569-120">Du kan blanda positions-och namngivna parametrar i samma cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c6569-120">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="c6569-121">I det här fallet hämtar systemet de namngivna argumenten först och försöker sedan mappa de återstående namnlösa argumenten till positions parametrarna.</span><span class="sxs-lookup"><span data-stu-id="c6569-121">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="c6569-122">Följande kommandon visar de olika sätt som du kan använda för att ange enstaka och flera argument för `Get-Command` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="c6569-122">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="c6569-123">Observera att i de två sista exemplen behöver **-namn** inte anges eftersom `Name` parametern definieras som en positions parameter.</span><span class="sxs-lookup"><span data-stu-id="c6569-123">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="c6569-124">Obligatoriska och valfria parametrar</span><span class="sxs-lookup"><span data-stu-id="c6569-124">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="c6569-125">Du kan också definiera cmdlet-parametrar som obligatoriska eller valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="c6569-125">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="c6569-126">(En obligatorisk parameter måste anges innan Windows PowerShell-körningsmiljön anropar cmdleten.)  Som standard definieras parametrar som valfria.</span><span class="sxs-lookup"><span data-stu-id="c6569-126">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="c6569-127">Om du vill definiera en obligatorisk parameter lägger du till `Mandatory` nyckelordet i parametern parameter-attribut och anger det till `true` , som du ser i följande parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="c6569-127">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="c6569-128">Om du vill definiera en valfri parameter utelämnar du `Mandatory` nyckelordet i **parameter** -attributets deklaration, som du ser i följande parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="c6569-128">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="c6569-129">Växla parametrar</span><span class="sxs-lookup"><span data-stu-id="c6569-129">Switch Parameters</span></span>

<span data-ttu-id="c6569-130">Windows PowerShell tillhandahåller en [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -typ som gör att du kan definiera en parameter vars värde automatiskt anges till `false` om parametern inte anges när cmdleten anropas.</span><span class="sxs-lookup"><span data-stu-id="c6569-130">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="c6569-131">Använd när det är möjligt och Använd switch-parametrar i stället för booleska parametrar.</span><span class="sxs-lookup"><span data-stu-id="c6569-131">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="c6569-132">Överväg följande exempel.</span><span class="sxs-lookup"><span data-stu-id="c6569-132">Consider the following sample.</span></span> <span data-ttu-id="c6569-133">Som standard skickar flera Windows PowerShell-cmdlets inte ett utgående objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c6569-133">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="c6569-134">Dessa cmdletar har dock en `PassThru` växel parameter som åsidosätter standard beteendet.</span><span class="sxs-lookup"><span data-stu-id="c6569-134">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="c6569-135">Om `PassThru` parametern anges när dessa cmdletar anropas, returnerar cmdleten ett utgående objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c6569-135">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="c6569-136">Om du behöver parametern för att ha ett standardvärde för `true` när parametern inte anges i anropet, bör du överväga att återställa meningen för parametern.</span><span class="sxs-lookup"><span data-stu-id="c6569-136">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="c6569-137">För exempel, i stället för att ange parametervärdet till ett booleskt värde `true` , deklarerar du egenskapen som [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -typ och anger sedan standardvärdet för parametern till `false` .</span><span class="sxs-lookup"><span data-stu-id="c6569-137">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="c6569-138">För att definiera en switch-parameter, deklarera egenskapen som [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -typ, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="c6569-138">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="c6569-139">Om du vill att cmdleten ska fungera på parametern när den har angetts använder du följande struktur i någon av metoderna för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="c6569-139">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c6569-140">Se även</span><span class="sxs-lookup"><span data-stu-id="c6569-140">See Also</span></span>

[<span data-ttu-id="c6569-141">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="c6569-141">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
