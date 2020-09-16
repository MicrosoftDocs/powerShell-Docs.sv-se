---
title: GetProc02 (C#) exempel kod | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d9afa8fff23d99661987c067e8082a9294c12717
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787163"
---
# <a name="getproc02-c-sample-code"></a>GetProc02 (C#) – kodexempel

Följande kod visar implementeringen av en `Get-Process` cmdlet som accepterar kommando rads ingångar. Observera att den här implementeringen definierar en `Name` parameter för att tillåta kommando rads indata och använder metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka utdata till pipelinen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
