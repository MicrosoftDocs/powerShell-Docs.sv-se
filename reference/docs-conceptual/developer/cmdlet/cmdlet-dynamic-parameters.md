---
title: Dynamiska cmdlet-parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359444"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="5df64-102">Dynamiska cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="5df64-102">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="5df64-103">Cmdletar kan definiera parametrar som är tillgängliga för användaren under särskilda villkor, till exempel när argumentet för en annan parameter är ett visst värde.</span><span class="sxs-lookup"><span data-stu-id="5df64-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="5df64-104">Dessa parametrar läggs till vid körning och kallas dynamiska parametrar eftersom de bara läggs till vid behov.</span><span class="sxs-lookup"><span data-stu-id="5df64-104">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="5df64-105">Du kan till exempel skapa en cmdlet som bara lägger till flera parametrar när en specifik växel parameter anges.</span><span class="sxs-lookup"><span data-stu-id="5df64-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="5df64-106">Providers och PowerShell-funktioner kan också definiera dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="5df64-106">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="5df64-107">Dynamiska parametrar i PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="5df64-107">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="5df64-108">PowerShell använder dynamiska parametrar i flera av dess Provider-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="5df64-108">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="5df64-109">Till exempel lägger `Get-Item`-och `Get-ChildItem`-cmdletarna till en **CodeSigningCert** -parameter vid körning när parametern **Path** anger sökvägen till **certifikat** leverantören.</span><span class="sxs-lookup"><span data-stu-id="5df64-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="5df64-110">Om parametern **Path** anger en sökväg för en annan provider är parametern **CodeSigningCert** inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="5df64-110">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="5df64-111">I följande exempel visas hur **CodeSigningCert** -parametern läggs till vid körning när `Get-Item` körs.</span><span class="sxs-lookup"><span data-stu-id="5df64-111">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="5df64-112">I det här exemplet har PowerShell-körningsmiljön lagt till parametern och cmdleten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5df64-112">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="5df64-113">I det här exemplet anges en **fil Systems** enhet och ett fel returneras.</span><span class="sxs-lookup"><span data-stu-id="5df64-113">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="5df64-114">Fel meddelandet anger att parametern **CodeSigningCert** inte kan hittas.</span><span class="sxs-lookup"><span data-stu-id="5df64-114">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

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

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="5df64-115">Stöd för dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="5df64-115">Support for dynamic parameters</span></span>

<span data-ttu-id="5df64-116">För att stödja dynamiska parametrar måste följande element ingå i cmdlet-koden.</span><span class="sxs-lookup"><span data-stu-id="5df64-116">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="5df64-117">Gränssnitt</span><span class="sxs-lookup"><span data-stu-id="5df64-117">Interface</span></span>

<span data-ttu-id="5df64-118">[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="5df64-118">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="5df64-119">Det här gränssnittet innehåller den metod som hämtar dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="5df64-119">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="5df64-120">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="5df64-120">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="5df64-121">Metod</span><span class="sxs-lookup"><span data-stu-id="5df64-121">Method</span></span>

<span data-ttu-id="5df64-122">[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="5df64-122">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="5df64-123">Den här metoden hämtar objektet som innehåller definitionerna för dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="5df64-123">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="5df64-124">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="5df64-124">For example:</span></span>

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

### <a name="class"></a><span data-ttu-id="5df64-125">Klass</span><span class="sxs-lookup"><span data-stu-id="5df64-125">Class</span></span>

<span data-ttu-id="5df64-126">En klass som definierar de dynamiska parametrar som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="5df64-126">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="5df64-127">Den här klassen måste innehålla ett **parameter** -attribut för varje parameter och eventuella valfria **alias** -och **verifierings** -attribut som behövs för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5df64-127">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="5df64-128">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="5df64-128">For example:</span></span>

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

<span data-ttu-id="5df64-129">Ett fullständigt exempel på en cmdlet som stöder dynamiska parametrar finns i [så här deklarerar du dynamiska parametrar](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5df64-129">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5df64-130">Se även</span><span class="sxs-lookup"><span data-stu-id="5df64-130">See also</span></span>

[<span data-ttu-id="5df64-131">System. Management. Automation. IDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="5df64-131">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="5df64-132">System. Management. Automation. IDynamicParameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="5df64-132">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="5df64-133">Så här deklarerar du dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="5df64-133">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="5df64-134">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="5df64-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
