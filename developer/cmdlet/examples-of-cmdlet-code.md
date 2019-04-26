---
title: Exempel på Cmdlet-kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068206"
---
# <a name="examples-of-cmdlet-code"></a>Exempel på cmdlet-kod

Det här avsnittet innehåller exempel på cmdlet-kod som du kan använda för att börja skriva din egen cmdletar.

> [!IMPORTANT]
> Om du vill stegvisa instruktioner för att skriva cmdlets, se [självstudier för skrivning cmdletar](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>I detta avsnitt

[Hur du skriver en enkel Cmdlet](./how-to-write-a-simple-cmdlet.md) det här exemplet visar den grundläggande strukturen i cmdlet-kod.

[Hur du deklarera Cmdlet-parametrarna](./how-to-declare-cmdlet-parameters.md) det här exemplet visar hur du deklarera de olika typerna av parametrar.

[Hur du deklarera parametern anger](./how-to-declare-parameter-sets.md) det här exemplet visar hur du deklarera uppsättningar med parametrar som kan ändra den åtgärd som en cmdlet utför.

[Så här för att verifiera parametern inkommande](./how-to-validate-parameter-input.md) exemplen visar hur du verifierar indata för parametern.

[Hur du deklarera dynamiska parametrar](./how-to-declare-dynamic-parameters.md) det här exemplet visar hur du deklarera en parameter som har lagts till under körning.

[Hur du anropar skript i en Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) det här exemplet visar hur du anropar ett skript som har angetts för en cmdlet.

[Åsidosätta indata bearbetningsmetoder](./how-to-override-input-processing-methods.md) alltså den grundläggande strukturen som används för att åsidosätta BeginProcessing och ProcessRecord EndProcessing metoder.

[Så här ShouldProcess supportsamtal](./how-to-request-confirmations.md) det här exemplet visar hur [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder ska anropas från en cmdlet.

[Hur du stöd för transaktioner](./how-to-support-transactions.md) det här exemplet visar hur du anger att cmdleten har stöd för transaktioner och hur du implementerar vad som händer när cmdlet: en används i en transaktion.

[Så här stöder jobb](./how-to-support-jobs.md) det här exemplet visar hur du ger stöd jobb när du skriver cmdletar.

[Hur du anropar en Cmdlet från inom en Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) det här exemplet visar hur du anropar en cmdlet från inom en annan cmdlet, där du kan lägga till funktioner för anropade cmdlet: en till den cmdlet som du utvecklar.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
