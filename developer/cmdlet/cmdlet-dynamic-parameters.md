---
title: Parametrar för cmdleten dynamisk | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068546"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="a08f3-102">Dynamiska cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="a08f3-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="a08f3-103">Cmdlet: ar kan definiera parametrar som är tillgängliga för användare under särskilda villkor, till exempel när argumentet för en annan parameter är ett specifikt värde.</span><span class="sxs-lookup"><span data-stu-id="a08f3-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="a08f3-104">Dessa parametrar har lagts till under körning och kallas *dynamiska parametrar* eftersom de läggs endast när de behövs.</span><span class="sxs-lookup"><span data-stu-id="a08f3-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="a08f3-105">Du kan till exempel utforma en cmdlet som lägger till flera parametrar endast när en viss växel-parameter anges.</span><span class="sxs-lookup"><span data-stu-id="a08f3-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="a08f3-106">Leverantörer och Windows PowerShell-funktioner kan du också definiera dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="a08f3-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="a08f3-107">Dynamiska parametrar i Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a08f3-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="a08f3-108">Windows PowerShell använder dynamiska parametrar i flera av dess provider-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="a08f3-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="a08f3-109">Till exempel den `Get-Item` och `Get-ChildItem` cmdletar lägger du till en `CodeSigningCert` parametern vid körning när den `Path` parametern för cmdlet: en anger providern certifikatsökväg.</span><span class="sxs-lookup"><span data-stu-id="a08f3-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="a08f3-110">Om den `Path` parametern för cmdlet: en anger en sökväg för en annan leverantör i `CodeSigningCert` parametern är inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="a08f3-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="a08f3-111">Följande exempel visar hur `CodeSigningCert` parameter läggs vid körning när den `Get-Item` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="a08f3-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="a08f3-112">Windows PowerShell-körning har lagt till parametern i det första exemplet och cmdlet: en har genomförts.</span><span class="sxs-lookup"><span data-stu-id="a08f3-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="a08f3-113">I det andra exemplet en filsystem-enhet har angetts och returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="a08f3-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="a08f3-114">Felmeddelandet indikerar att den `CodeSigningCert` parametern kan inte hittas.</span><span class="sxs-lookup"><span data-stu-id="a08f3-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="a08f3-115">Stöd för dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="a08f3-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="a08f3-116">För dynamiska parametrar måste måste cmdlet-koden innehålla följande element.</span><span class="sxs-lookup"><span data-stu-id="a08f3-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="a08f3-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) det här gränssnittet använder den metod som hämtar de dynamiska parametrarna.</span><span class="sxs-lookup"><span data-stu-id="a08f3-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="a08f3-118">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a08f3-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="a08f3-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) den här metoden hämtar-objektet som innehåller definitionerna som dynamisk parameter.</span><span class="sxs-lookup"><span data-stu-id="a08f3-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="a08f3-120">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a08f3-120">Example:</span></span>

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

<span data-ttu-id="a08f3-121">Den här klassen definierar parametrar som ska läggas till dynamiska parametern-klassen.</span><span class="sxs-lookup"><span data-stu-id="a08f3-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="a08f3-122">Den här klassen måste innehålla ett parametern-attribut för varje parameter och eventuella valfria Alias och verifiering på attribut som krävs av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="a08f3-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="a08f3-123">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a08f3-123">Example:</span></span>

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

<span data-ttu-id="a08f3-124">Exempel på att en cmdlet som har stöd för dynamiska parametrar, se [så deklarera dynamiska parametrar](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a08f3-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a08f3-125">Se även</span><span class="sxs-lookup"><span data-stu-id="a08f3-125">See Also</span></span>

[<span data-ttu-id="a08f3-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="a08f3-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="a08f3-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="a08f3-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="a08f3-128">Hur du deklarera dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="a08f3-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="a08f3-129">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a08f3-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
