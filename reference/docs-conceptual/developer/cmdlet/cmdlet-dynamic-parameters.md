---
ms.date: 09/13/2016
ms.topic: reference
title: Dynamiska cmdlet-parametrar
description: Dynamiska cmdlet-parametrar
ms.openlocfilehash: b44dda2354e8b689e419c7bf4deefadfc4edcb07
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653430"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="5a202-103">Dynamiska cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="5a202-103">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="5a202-104">Cmdletar kan definiera parametrar som är tillgängliga för användaren under särskilda villkor, till exempel när argumentet för en annan parameter är ett visst värde.</span><span class="sxs-lookup"><span data-stu-id="5a202-104">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="5a202-105">Dessa parametrar läggs till vid körning och kallas dynamiska parametrar eftersom de bara läggs till vid behov.</span><span class="sxs-lookup"><span data-stu-id="5a202-105">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="5a202-106">Du kan till exempel skapa en cmdlet som bara lägger till flera parametrar när en specifik växel parameter anges.</span><span class="sxs-lookup"><span data-stu-id="5a202-106">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="5a202-107">Providers och PowerShell-funktioner kan också definiera dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="5a202-107">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="5a202-108">Dynamiska parametrar i PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="5a202-108">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="5a202-109">PowerShell använder dynamiska parametrar i flera av dess Provider-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="5a202-109">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="5a202-110">Till exempel `Get-Item` `Get-ChildItem` lägger cmdletarna och lägger till en **CodeSigningCert** -parameter vid körning när parametern **Path** anger sökvägen till **certifikat** leverantören.</span><span class="sxs-lookup"><span data-stu-id="5a202-110">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="5a202-111">Om parametern **Path** anger en sökväg för en annan provider är parametern **CodeSigningCert** inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="5a202-111">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="5a202-112">I följande exempel visas hur **CodeSigningCert** -parametern läggs till vid körning när körs `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="5a202-112">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="5a202-113">I det här exemplet har PowerShell-körningsmiljön lagt till parametern och cmdleten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5a202-113">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="5a202-114">I det här exemplet anges en **fil Systems** enhet och ett fel returneras.</span><span class="sxs-lookup"><span data-stu-id="5a202-114">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="5a202-115">Fel meddelandet anger att parametern **CodeSigningCert** inte kan hittas.</span><span class="sxs-lookup"><span data-stu-id="5a202-115">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="5a202-116">Stöd för dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="5a202-116">Support for dynamic parameters</span></span>

<span data-ttu-id="5a202-117">För att stödja dynamiska parametrar måste följande element ingå i cmdlet-koden.</span><span class="sxs-lookup"><span data-stu-id="5a202-117">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="5a202-118">Gränssnitt</span><span class="sxs-lookup"><span data-stu-id="5a202-118">Interface</span></span>

<span data-ttu-id="5a202-119">[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="5a202-119">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="5a202-120">Det här gränssnittet innehåller den metod som hämtar dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="5a202-120">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="5a202-121">Exempel:</span><span class="sxs-lookup"><span data-stu-id="5a202-121">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="5a202-122">Metod</span><span class="sxs-lookup"><span data-stu-id="5a202-122">Method</span></span>

<span data-ttu-id="5a202-123">[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="5a202-123">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="5a202-124">Den här metoden hämtar objektet som innehåller definitionerna för dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="5a202-124">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="5a202-125">Exempel:</span><span class="sxs-lookup"><span data-stu-id="5a202-125">For example:</span></span>

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

### <a name="class"></a><span data-ttu-id="5a202-126">Klass</span><span class="sxs-lookup"><span data-stu-id="5a202-126">Class</span></span>

<span data-ttu-id="5a202-127">En klass som definierar de dynamiska parametrar som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="5a202-127">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="5a202-128">Den här klassen måste innehålla ett **parameter** -attribut för varje parameter och eventuella valfria **alias** -och **verifierings** -attribut som behövs för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5a202-128">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="5a202-129">Exempel:</span><span class="sxs-lookup"><span data-stu-id="5a202-129">For example:</span></span>

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

<span data-ttu-id="5a202-130">Ett fullständigt exempel på en cmdlet som stöder dynamiska parametrar finns i [så här deklarerar du dynamiska parametrar](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5a202-130">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a202-131">Se även</span><span class="sxs-lookup"><span data-stu-id="5a202-131">See also</span></span>

[<span data-ttu-id="5a202-132">System. Management. Automation. IDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="5a202-132">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="5a202-133">System. Management. Automation. IDynamicParameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="5a202-133">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="5a202-134">Deklarera dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="5a202-134">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="5a202-135">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="5a202-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
