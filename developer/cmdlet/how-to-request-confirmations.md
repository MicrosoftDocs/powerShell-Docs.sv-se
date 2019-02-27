---
title: Hur du begär bekräftelser | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851998"
---
# <a name="how-to-request-confirmations"></a>Begära bekräftelser

Det här exemplet visar hur du anropar den [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder för att begära bekräftelser från den användaren innan en åtgärd utförs.

> [!IMPORTANT]
> Läs mer om hur Windows PowerShell hanterar dessa begäranden [begär bekräftelse](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Begär bekräftelse

1. Se till att den `SupportsShouldProcess` parametern för Cmdlet-attributet är inställd på `true`. (För det här är en parameter av CmdletBinding-attribut.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Lägg till en `Force` parameter i cmdlet: så att användaren kan åsidosätta en begäran om händelsebekräftelse.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Lägg till en `if` instruktion som använder returvärdet för den [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod för att avgöra om den [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden anropas.

4. Lägg till en andra `if` instruktion som använder returvärdet för den [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden och värdet för den `Force` parametern för att avgöra om åtgärden bör vara utföra.

## <a name="example"></a>Exempel

I följande kodexempel i [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder som anropas inifrån den åsidosättning av den [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod. Du kan också anropa metoderna från andra indata metoderna.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
