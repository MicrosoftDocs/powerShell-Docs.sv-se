---
title: Så här skriver du en enkel cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356254"
---
# <a name="how-to-write-a-cmdlet"></a>Så här skriver du en cmdlet

Den här artikeln visar hur du skriver en cmdlet. Cmdleten `Send-Greeting` tar ett enda användar namn som indata och skriver sedan en hälsning till användaren. Även om cmdleten inte fungerar mycket, visar det här exemplet de viktigaste avsnitten i en cmdlet.

## <a name="steps-to-write-a-cmdlet"></a>Steg för att skriva en cmdlet

1. Om du vill deklarera klassen som en-cmdlet använder du **cmdlet** -attributet. **Cmdlet** -attributet anger verbet och Substantiv för cmdlet-namnet.

   Mer information om **cmdlet** -attributet finns i [CmdletAttribute-deklaration](cmdlet-attribute-declaration.md).

2. Ange namnet på klassen.

3. Ange att cmdleten härleds från någon av följande klasser:

   * [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Om du vill definiera parametrarna för cmdleten använder du attributet **parameter** . I det här fallet anges bara en obligatorisk parameter.

   Mer information om attributet **parameter** finns i ParameterAttribute- [deklaration](parameter-attribute-declaration.md).

5. Åsidosätt den metod för bearbetning av indata som bearbetar indata. I det här fallet åsidosätts metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

6. Om du vill skriva hälsningen använder du metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   Hälsningen visas i följande format:

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Exempel

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Se även

[System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute-deklaration](cmdlet-attribute-declaration.md)

[ParameterAttribute-deklaration](parameter-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](writing-a-windows-powershell-cmdlet.md)