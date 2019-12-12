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
# <a name="cmdlet-dynamic-parameters"></a>Dynamiska cmdlet-parametrar

Cmdletar kan definiera parametrar som är tillgängliga för användaren under särskilda villkor, till exempel när argumentet för en annan parameter är ett visst värde. Dessa parametrar läggs till vid körning och kallas dynamiska parametrar eftersom de bara läggs till vid behov. Du kan till exempel skapa en cmdlet som bara lägger till flera parametrar när en specifik växel parameter anges.

> [!NOTE]
> Providers och PowerShell-funktioner kan också definiera dynamiska parametrar.

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>Dynamiska parametrar i PowerShell-cmdletar

PowerShell använder dynamiska parametrar i flera av dess Provider-cmdletar. Till exempel lägger `Get-Item`-och `Get-ChildItem`-cmdletarna till en **CodeSigningCert** -parameter vid körning när parametern **Path** anger sökvägen till **certifikat** leverantören. Om parametern **Path** anger en sökväg för en annan provider är parametern **CodeSigningCert** inte tillgänglig.

I följande exempel visas hur **CodeSigningCert** -parametern läggs till vid körning när `Get-Item` körs.

I det här exemplet har PowerShell-körningsmiljön lagt till parametern och cmdleten har slutförts.

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

I det här exemplet anges en **fil Systems** enhet och ett fel returneras. Fel meddelandet anger att parametern **CodeSigningCert** inte kan hittas.

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

## <a name="support-for-dynamic-parameters"></a>Stöd för dynamiska parametrar

För att stödja dynamiska parametrar måste följande element ingå i cmdlet-koden.

### <a name="interface"></a>Gränssnitt

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).
Det här gränssnittet innehåller den metod som hämtar dynamiska parametrar.

Till exempel:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>Metod

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).
Den här metoden hämtar objektet som innehåller definitionerna för dynamiska parametrar.

Till exempel:

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

### <a name="class"></a>Klass

En klass som definierar de dynamiska parametrar som ska läggas till. Den här klassen måste innehålla ett **parameter** -attribut för varje parameter och eventuella valfria **alias** -och **verifierings** -attribut som behövs för cmdleten.

Till exempel:

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

Ett fullständigt exempel på en cmdlet som stöder dynamiska parametrar finns i [så här deklarerar du dynamiska parametrar](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Se även

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Så här deklarerar du dynamiska parametrar](./how-to-declare-dynamic-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
