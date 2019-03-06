---
title: RunSpace05 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429575"
---
# <a name="runspace05-code-sample"></a>RunSpace05 – kodexempel

Här är källkoden för Runspace05-exemplet som beskrivs i [konfigurerar en Körningsutrymme med RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). Detta exempel visar hur du skapar körningsutrymme konfigurationsinformation, skapa ett körningsutrymme, skapa en pipeline med ett enda kommando och sedan köra pipelinen. Kommandot som körs är den `Get-Process` cmdlet.

> [!NOTE]
> Du kan ladda ned den C# källfilen (runspace05.cs) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.

## <a name="code-sample"></a>Kodexempel

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)