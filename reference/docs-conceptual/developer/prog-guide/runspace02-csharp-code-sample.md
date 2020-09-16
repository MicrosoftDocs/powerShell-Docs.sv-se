---
title: Kod exempel för Runspace02 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1e58f035f20baa7443d9031499062a45beae01b9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778459"
---
# <a name="runspace02-c-code-sample"></a>Runspace02 (C#) – kodexempel

Här är C#-käll koden för Runspace02-exemplet. I det här exemplet används klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra `Get-Process` cmdleten synkront. Windows Forms och data bindning används sedan för att visa resultaten i en DataGridView-kontroll

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
