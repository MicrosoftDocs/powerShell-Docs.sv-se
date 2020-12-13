---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc01 (C#) – kodexempel
description: GetProc01 (C#) – kodexempel
ms.openlocfilehash: 79509ff12afb32c907058f4ddb0c707f3823857a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654477"
---
# <a name="getproc01-c-sample-code"></a>GetProc01 (C#) – kodexempel

Följande kod visar implementeringen av GetProc01-exempel-cmdlet: en. Observera att cmdleten är förenklad genom att lämna det faktiska arbetet med process hämtning till metoden [system. Diagnostics. process. GetProcesses *](/dotnet/api/System.Diagnostics.Process.GetProcesses) .

> [!NOTE]
> Du kan hämta C#-källfilen (getproc01.cs) för den här Get-Proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0-komponenter för körning. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
