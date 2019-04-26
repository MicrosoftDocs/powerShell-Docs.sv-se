---
title: Anropar Cmdlets och skript i en Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067679"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Anropa cmdlets och skript inuti en cmdlet

En cmdlet kan anropa andra cmdlet: ar och skript från i indata metoden-cmdlet: ens bearbetades. På så sätt kan du lägga till funktioner för befintliga cmdlets och skript till din cmdlet utan att behöva skriva om koden.

## <a name="the-invoke-method"></a>Den anropa metod

Alla cmdletar kan anropa en befintlig cmdlet genom att anropa den [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metod inifrån indata som bearbetar metod, till exempel [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), det vill säga åsidosätts av cmdlet: en. Men du kan anropa dessa cmdlets som härleds direkt från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klass. Du kan inte anropa en cmdlet som härleds från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klass.

Den [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metoden har följande varianter.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) denna variant anropar cmdlet-objektet och returnerar en samling objekt av typen ”T”.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) denna variant anropar cmdlet-objektet och returnerar en starkt typifierad emumerator. Den här variant gör att användaren kan använda objekten i samlingen för att utföra anpassade åtgärder.

## <a name="examples"></a>Exempel

|Exempel|Beskrivning|
|-------------|-----------------|
|[Anropar cmdletar i en Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|Det här exemplet visar hur du anropar en cmdlet från inom en annan cmdlet.|
|[Aktivera skript i en Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|Det här exemplet visar hur du anropar ett skript som har angetts till cmdleten från en annan cmdlet.|

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
