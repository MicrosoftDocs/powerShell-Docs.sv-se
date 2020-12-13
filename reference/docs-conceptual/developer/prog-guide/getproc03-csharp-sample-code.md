---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc03 (C#) – kodexempel
description: GetProc03 (C#) – kodexempel
ms.openlocfilehash: c81ba04b2b335f4ce992c6b3ed2f019cf6d7d20f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355586"
---
# <a name="getproc03-c-sample-code"></a>GetProc03 (C#) – kodexempel

Följande kod visar implementeringen av en `Get-Process` cmdlet som kan acceptera pipeline-inmatade. Den här implementeringen definierar en `Name` parameter som accepterar pipeline-indata, hämtar process information från den lokala datorn baserat på de angivna namnen och använder sedan metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka objekt till pipelinen.

> [!NOTE]
> Du kan hämta C#-källfilen (getprov03.cs) för den här Get-Proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0-komponenter för körning. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
