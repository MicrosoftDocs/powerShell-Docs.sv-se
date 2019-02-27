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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845278"
---
# <a name="cmdlet-dynamic-parameters"></a>Dynamiska cmdlet-parametrar

Cmdlet: ar kan definiera parametrar som är tillgängliga för användare under särskilda villkor, till exempel när argumentet för en annan parameter är ett specifikt värde. Dessa parametrar har lagts till under körning och kallas *dynamiska parametrar* eftersom de läggs endast när de behövs. Du kan till exempel utforma en cmdlet som lägger till flera parametrar endast när en viss växel-parameter anges.

> [!NOTE]
> Leverantörer och Windows PowerShell-funktioner kan du också definiera dynamiska parametrar.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Dynamiska parametrar i Windows PowerShell-Cmdlets

Windows PowerShell använder dynamiska parametrar i flera av dess provider-cmdletar. Till exempel den `Get-Item` och `Get-ChildItem` cmdletar lägger du till en `CodeSigningCert` parametern vid körning när den `Path` parametern för cmdlet: en anger providern certifikatsökväg. Om den `Path` parametern för cmdlet: en anger en sökväg för en annan leverantör i `CodeSigningCert` parametern är inte tillgänglig.

Följande exempel visar hur `CodeSigningCert` parameter läggs vid körning när den `Get-Item` cmdleten körs.

Windows PowerShell-körning har lagt till parametern i det första exemplet och cmdlet: en har genomförts.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

I det andra exemplet en filsystem-enhet har angetts och returneras ett fel. Felmeddelandet indikerar att den `CodeSigningCert` parametern kan inte hittas.

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

## <a name="support-for-dynamic-parameters"></a>Stöd för dynamiska parametrar

För dynamiska parametrar måste måste cmdlet-koden innehålla följande element.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) det här gränssnittet använder den metod som hämtar de dynamiska parametrarna.

Exempel:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) den här metoden hämtar-objektet som innehåller definitionerna som dynamisk parameter.

Exempel:

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

Den här klassen definierar parametrar som ska läggas till dynamiska parametern-klassen. Den här klassen måste innehålla ett parametern-attribut för varje parameter och eventuella valfria Alias och verifiering på attribut som krävs av cmdlet: en.

Exempel:

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

Exempel på att en cmdlet som har stöd för dynamiska parametrar, se [så deklarera dynamiska parametrar](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Se även

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Hur du deklarera dynamiska parametrar](./how-to-declare-dynamic-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
