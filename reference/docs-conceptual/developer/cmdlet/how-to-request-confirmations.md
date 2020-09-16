---
title: Så här begär du bekräftelser | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebe928724f1b750afc11c1e3c1207375f4ec8e42
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784103"
---
# <a name="how-to-request-confirmations"></a>Begära bekräftelser

Det här exemplet visar hur du anropar metoderna [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) för att begära bekräftelser från användaren innan en åtgärd vidtas.

> [!IMPORTANT]
> Mer information om hur Windows PowerShell hanterar dessa förfrågningar finns i [begära bekräftelse](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Att begära bekräftelse

1. Se till att `SupportsShouldProcess` parametern för cmdlet-attributet är inställt på `true` . (För functions är det en parameter för attributet CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Lägg till en `Force` parameter till din cmdlet så att användaren kan åsidosätta en bekräftelse förfrågan.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Lägg till en `if` instruktion som använder returvärdet för metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) för att avgöra om metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) anropas.

4. Lägg till en andra `if` instruktion som använder returvärdet för metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) och värdet för `Force` parametern för att avgöra om åtgärden ska utföras.

## <a name="example"></a>Exempel

I följande kod exempel anropas metoderna [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . Automation. cmdlet. ShouldContinue från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . Men du kan också anropa dessa metoder från andra metoder för bearbetning av indata.

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

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
