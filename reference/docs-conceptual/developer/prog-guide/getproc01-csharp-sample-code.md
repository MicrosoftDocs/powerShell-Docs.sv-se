---
title: GetProc01 (C#) exempel kod | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 883beb9dd1328a1897b9b61656a98cf515a21be7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778901"
---
# <a name="getproc01-c-sample-code"></a>GetProc01 (C#) – kodexempel

Följande kod visar implementeringen av GetProc01-exempel-cmdlet: en. Observera att cmdleten är förenklad genom att lämna det faktiska arbetet med process hämtning till metoden [system. Diagnostics. process. GetProcesses *](/dotnet/api/System.Diagnostics.Process.GetProcesses) .

> [!NOTE]
> Du kan hämta C#-källfilen (getproc01.cs) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
