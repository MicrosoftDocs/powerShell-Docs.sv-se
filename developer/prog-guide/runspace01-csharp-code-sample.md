---
title: Runspace01 (C#)-kodexemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735049"
---
# <a name="runspace01-c-code-sample"></a>Runspace01 (C#) – kodexempel

Här följer kodexempel för körningsutrymmet som beskrivs i [och skapa en konsolen programmet som kör ett kommando som angetts](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program). Om du vill göra detta måste programmet anropar ett körningsutrymme och anropar sedan ett kommando. (Observera att det här programmet inte anger konfigurationsinformation för körningsutrymme eller gör det uttryckligen skapa en pipeline). Kommandot som anropas är den `Get-Process` cmdlet.

> [!NOTE]
> Du kan ladda ned den C# källfilen (runspace01.cs) för den här körningsutrymme med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.

## <a name="code-sample"></a>Kodexempel

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)