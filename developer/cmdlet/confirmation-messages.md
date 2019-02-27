---
title: Bekräftelsemeddelanden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850605"
---
# <a name="confirmation-messages"></a>Bekräftelsemeddelanden

Här följer olika bekräftelsemeddelanden som kan visas beroende på varianter av den [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder som anropas.

> [!IMPORTANT]
> Exempelkod som visar hur du begär bekräftelser, se [så begäran bekräftelser](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Att ange resursen

Du kan ange den resurs som håller på att ändras genom att anropa den [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) metod. I så fall kan du ange resursen med hjälp av den `target` -parametern för metoden och åtgärden läggs till av Windows PowerShell. I ett meddelande om texten ”MyResource” är den resurs som kördes på och åtgärden är namnet på det kommando som gör anropet.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Om användaren väljer **Ja** eller **Ja till alla** bekräftelsen be (som visas i följande exempel), ett anrop till den [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden görs, vilket leder till ett andra bekräftelsemeddelande som ska visas.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Anger åtgärden och resurs

Du kan ange den resurs som håller på att ändras och åtgärden som kommandot håller på att utföra genom att anropa den [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) metod. I så fall kan du ange resursen med hjälp av den `target` parametern och åtgärden med hjälp av den `target` parametern. I ett meddelande om texten ”MyResource” är den resurs som kördes på och ”MyAction” är en åtgärd som ska utföras.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Om användaren väljer **Ja** eller **Ja till alla** till föregående meddelande, ett anrop till den [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden görs, som orsakar en andra bekräftelsemeddelande som ska visas.

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

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
