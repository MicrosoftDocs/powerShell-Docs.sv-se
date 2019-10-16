---
title: Anropar cmdlets och skript inom en cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355428"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Anropa cmdlets och skript inuti en cmdlet

En cmdlet kan anropa andra cmdletar och skript inifrån den ingående bearbetnings metoden för cmdleten. På så sätt kan du lägga till funktionerna i befintliga cmdlets och skript till din cmdlet utan att behöva skriva om koden.

## <a name="the-invoke-method"></a>Metoden Invoke

Alla cmdletar kan anropa en befintlig cmdlet genom att anropa metoden [system. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) inifrån en bearbetnings metod för indata, till exempel [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), som åsidosätts av cmdleten. Du kan dock bara anropa de cmdlet: ar som härleds direkt från klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . Det går inte att anropa en cmdlet som härleds från klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

Metoden [system. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) har följande varianter.

[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) den här varianten anropar cmdlet-objektet och returnerar en mängd "T"-typ objekt.

[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) den här varianten anropar cmdlet-objektet och returnerar en starkt skriven emumerator. Med den här varianten kan användaren använda objekten i samlingen för att utföra anpassade åtgärder.

## <a name="examples"></a>Exempel

|Exempel|Beskrivning|
|-------------|-----------------|
|[Anropa cmdlets i en cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|I det här exemplet visas hur du anropar en cmdlet från en annan cmdlet.|
|[Anropa skript i en cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|I det här exemplet visas hur du anropar ett skript som har angetts för cmdleten från en annan cmdlet.|

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
