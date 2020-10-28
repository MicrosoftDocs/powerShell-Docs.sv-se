---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02 (C#) – kodexempel
description: GetProc02 (C#) – kodexempel
ms.openlocfilehash: da04b4184de10f4bd734ce0a5892527073b6e622
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657261"
---
# <a name="getproc02-c-sample-code"></a>GetProc02 (C#) – kodexempel

Följande kod visar implementeringen av en `Get-Process` cmdlet som accepterar kommando rads ingångar. Observera att den här implementeringen definierar en `Name` parameter för att tillåta kommando rads indata och använder metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka utdata till pipelinen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
