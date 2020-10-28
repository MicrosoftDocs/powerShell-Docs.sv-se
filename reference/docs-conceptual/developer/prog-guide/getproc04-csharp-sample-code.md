---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04 (C#) – kodexempel
description: GetProc04 (C#) – kodexempel
ms.openlocfilehash: 80020b60a7ab34caec0c856b9b7d12021f4276b9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654384"
---
# <a name="getproc04-c-sample-code"></a>GetProc04 (C#) – kodexempel

Följande kod visar implementeringen av en `Get-Process` cmdlet som rapporterar att det inte går att avsluta fel. Den här implementeringen anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) för att rapportera att det inte går att avsluta fel.

> [!NOTE]
> Du kan hämta C#-källfilen (getprov04.cs) för den här Get-Proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0-komponenter för körning. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
