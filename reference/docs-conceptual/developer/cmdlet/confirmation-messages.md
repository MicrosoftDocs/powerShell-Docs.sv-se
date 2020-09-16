---
title: Bekräftelse meddelanden | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8f8192f6ed96b1eeb22e3b28ce1366eee8e7c16a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782199"
---
# <a name="confirmation-messages"></a>Bekräftelsemeddelanden

Här är olika bekräftelse meddelanden som kan visas beroende på varianterna för [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -metoder som anropas.

> [!IMPORTANT]
> Exempel kod som visar hur du begär bekräftelser finns i [så här begär du bekräftelser](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Ange resursen

Du kan ange den resurs som ska ändras genom att anropa [system. Management. Automation. cmdlet. ShouldProcess% 2a? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) -metoden. I det här fallet kan du ange resursen med hjälp av `target` -parametern för-metoden och åtgärden läggs till av Windows PowerShell. I följande meddelande är texten "min resurs" den resurs som är aktive ras och åtgärden är namnet på kommandot som gör anropet.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Om användaren väljer **Ja** eller **Ja till alla** i bekräftelse förfrågningen (som visas i följande exempel), görs ett anrop till metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , vilket gör att ett andra bekräftelse meddelande visas.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Ange åtgärden och resursen

Du kan ange den resurs som ska ändras och åtgärden som kommandot ska utföra genom att anropa [system. Management. Automation. cmdlet. ShouldProcess% 2a? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) -metoden. I det här fallet kan du ange resursen med hjälp av- `target` parametern och åtgärden med hjälp av- `target` parametern. I följande meddelande är texten "min resurs" den resurs som har åtgärd ATS och "mina åtgärder" är den åtgärd som ska utföras.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Om användaren väljer **Ja** eller **Ja till alla** i föregående meddelande, görs ett anrop till metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , vilket gör att ett andra bekräftelse meddelande visas.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
