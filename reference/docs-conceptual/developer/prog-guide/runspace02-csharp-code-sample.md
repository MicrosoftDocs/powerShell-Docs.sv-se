---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace02 (C#) – kodexempel
description: Runspace02 (C#) – kodexempel
ms.openlocfilehash: 9e2c0cf37d1bf12a92f4fbf781928c0241202915
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647452"
---
# <a name="runspace02-c-code-sample"></a>Runspace02 (C#) – kodexempel

Här är C#-käll koden för Runspace02-exemplet. I det här exemplet används klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra `Get-Process` cmdleten synkront. Windows Forms och data bindning används sedan för att visa resultaten i en DataGridView-kontroll

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
