---
ms.date: 09/13/2016
ms.topic: reference
title: Exempel på cmdlet-kod
description: Exempel på cmdlet-kod
ms.openlocfilehash: 91dd2019300504697ad9a7a0c155a04600d09c58
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652914"
---
# <a name="examples-of-cmdlet-code"></a>Exempel på cmdlet-kod

Det här avsnittet innehåller exempel på en cmdlet-kod som du kan använda för att börja skriva dina egna cmdletar.

> [!IMPORTANT]
> Om du vill ha steg-för-steg-instruktioner för att skriva cmdlet: ar, se [självstudier för att skriva cmdletar](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>I det här avsnittet

Så [här skriver du en enkel cmdlet](./how-to-write-a-simple-cmdlet.md) I det här exemplet visas den grundläggande strukturen för cmdlet-kod.

[Så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md) Det här exemplet visar hur du deklarerar olika typer av parametrar.

[Så här deklarerar du parameter uppsättningar](./how-to-declare-parameter-sets.md) Det här exemplet visar hur du deklarerar uppsättningar med parametrar som kan ändra vilken åtgärd en cmdlet utför.

[Verifiera parameter ingångar](./how-to-validate-parameter-input.md) I de här exemplen visas hur du verifierar parameter ingångar.

[Så här deklarerar du dynamiska parametrar](./how-to-declare-dynamic-parameters.md) Det här exemplet visar hur du deklarerar en parameter som läggs till vid körning.

[Så här anropar du skript i en cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) Det här exemplet visar hur du anropar ett skript som anges för en cmdlet.

[Åsidosätta indata bearbetnings metoder](./how-to-override-input-processing-methods.md) I de här exemplen visas den grundläggande struktur som används för att åsidosätta metoderna BeginProcessing, ProcessRecord och EndProcessing.

[Så här stöder du ShouldProcess-anrop](./how-to-request-confirmations.md) Det här exemplet visar hur metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ska anropas inifrån en cmdlet.

[Så här stöder du transaktioner](./how-to-support-transactions.md) Det här exemplet visar hur du anger att cmdleten stöder transaktioner och hur du implementerar den åtgärd som vidtas när cmdleten används i en transaktion.

[Så här stöder du jobb](./how-to-support-jobs.md) Det här exemplet visar hur du stöder jobb när du skriver-cmdletar.

[Så här anropar du en cmdlet inifrån en cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) Det här exemplet visar hur du anropar en cmdlet från en annan cmdlet, vilket gör att du kan lägga till funktionerna i den anropade cmdleten till den cmdlet som du utvecklar.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
