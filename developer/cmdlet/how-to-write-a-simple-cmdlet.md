---
title: Hur du skriver en enkel Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251463"
---
# <a name="how-to-write-a-cmdlet"></a>Hur du skriver en cmdlet

Den här artikeln visar hur du skriver en cmdlet. Den `Send-Greeting` cmdlet tar ett enda användarnamn som indata och sedan skriver en hälsning för denna användare. Även om cmdleten inte gör mycket arbete visar det här exemplet de viktigaste avsnitten av en cmdlet.

## <a name="steps-to-write-a-cmdlet"></a>Steg för att skriva en cmdlet

1. Du kan deklarera klassen som en cmdlet genom att använda den **Cmdlet** attribut. Den **Cmdlet** attributet anger verb och substantiv för cmdlet-namn.

   Mer information om den **Cmdlet** attributet, se [CmdletAttribute deklarationen](cmdlet-attribute-declaration.md).

2. Ange namnet på klassen.

3. Ange att cmdleten härleds från någon av följande klasser:

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Om du vill definiera parametrar för cmdleten använda det **parametern** attribut. I det här fallet krävs bara en parameter har angetts.

   Mer information om den **parametern** attributet, se [ParameterAttribute deklarationen](parameter-attribute-declaration.md).

5. Åsidosätta indata metoden som bearbetar indata bearbetades. I det här fallet den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden åsidosätts.

6. Om du vill skriva hälsningen använder-metoden [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
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

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute deklaration](cmdlet-attribute-declaration.md)

[ParameterAttribute deklaration](parameter-attribute-declaration.md)

[Skriva en Windows PowerShell-Cmdlet](writing-a-windows-powershell-cmdlet.md)