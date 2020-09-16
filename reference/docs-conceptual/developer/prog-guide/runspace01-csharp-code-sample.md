---
title: Kod exempel för Runspace01 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 418162731b4a98989642e1c61c655fdb0f002698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787072"
---
# <a name="runspace01-c-code-sample"></a>Runspace01 (C#) – kodexempel

Här är kod exemplen för körnings utrymme som beskrivs i [skapa ett konsol program som kör ett angivet kommando](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).
För att göra detta anropar programmet en körnings utrymme och anropar sedan ett kommando. (Observera att det här programmet inte anger körnings utrymme konfigurations information eller inte uttryckligen skapar en pipeline). Kommandot som anropas är `Get-Process` cmdleten.

> [!NOTE]
> Du kan hämta C#-källfilen (runspace01.cs) för den här körnings utrymme med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components.
> Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
