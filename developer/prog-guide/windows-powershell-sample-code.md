---
title: Windows PowerShell-exempelkoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: 264e9f7538e13b48d899e87541239250eb88f14e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081214"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell-exempelkod

Windows PowerShell® exempel är tillgängliga via Windows SDK. Det här avsnittet innehåller exempelkoden som finns i Windows SDK-prov.

> [!NOTE]
> När Windows SDK: N installeras en **exempel** katalog skapas alla Windows PowerShell-exempel är tillgängliga. En standardinstallation katalog är **C:\Program Files\Microsoft SDKs\Windows\v6.0**. Starta Windows PowerShell och skriv **”cd Samples\SysMgmt\PowerShell”** att hitta katalogen Windows PowerShell-exempel. I detta dokument, Windows PowerShell-exempel directory kallas  **\<PowerShell-exempel >**.

## <a name="sample-code-listing"></a>Exempel på kodlista

|Exempelkod|Beskrivning|
|-----------------|-----------------|
|[AccessDbProviderSample01 kodexempel](./accessdbprovidersample01-code-sample.md)|Detta är providern som beskrivs i [skapar en grundläggande Windows PowerShell-providern](./creating-a-basic-windows-powershell-provider.md).|
|[AccessDbProviderSample02 kodexempel](./accessdbprovidersample02-code-sample.md)|Detta är providern som beskrivs i [skapar en Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).|
|[AccessDbProviderSample03 kodexempel](./accessdbprovidersample03-code-sample.md)|Detta är providern som beskrivs i [skapar en Windows PowerShell-providern för objektet](./creating-a-windows-powershell-item-provider.md).|
|[AccessDbProviderSample04 kodexempel](./accessdbprovidersample04-code-sample.md)|Detta är providern som beskrivs i [skapar en Windows PowerShell-providern för behållaren](./creating-a-windows-powershell-container-provider.md).|
|[AccessDbProviderSample05 kodexempel](./accessdbprovidersample05-code-sample.md)|Detta är providern som beskrivs i [skapar en Windows PowerShell-providern för navigering](./creating-a-windows-powershell-navigation-provider.md).|
|[AccessDbProviderSample06 kodexempel](./accessdbprovidersample06-code-sample.md)|Detta är providern som beskrivs i [skapar en Windows PowerShell-innehållsleverantör](./creating-a-windows-powershell-content-provider.md).|
|[GetProc01 kodexempel](./getproc01-code-samples.md)|Det här är grundläggande `Get-Process` cmdlet-exemplet som beskrivs i [skapa din första cmdleten](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[GetProc02 kodexempel](./getproc02-code-samples.md)|Det här är den `Get-Process` cmdlet-exemplet som beskrivs i [att lägga till parametrar som processen Command-Line indata](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[GetProc03 kodexempel](./getproc03-code-samples.md)|Det här är den `Get-Process` cmdlet-exemplet som beskrivs i [att lägga till parametrar som indata från Pipeline processen](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[GetProc04 kodexempel](./getproc04-code-samples.md)|Det här är den `Get-Process` cmdlet-exemplet som beskrivs i [att lägga till oändliga felrapportering om du till din Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[GetProc05 kodexempel](./getproc05-code-samples.md)|Detta `Get-Process` cmdlet liknar den cmdlet som beskrivs i [att lägga till oändliga felrapportering om du till din Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[StopProc01 kodexempel](./stopproc01-code-samples.md)|Det här är den `Stop-Process` cmdlet-exemplet som beskrivs i [skapar en Cmdlet som ändrar systemet](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[StopProcessSample04 kodexempel](./stopprocesssample04-code-samples.md)|Det här är den `Stop-Process` cmdlet-exemplet som beskrivs i [att lägga till parametern anger att en Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Runspace01 kodexempel](./runspace01-code-samples.md)|Dessa är kodexempel för körningsutrymmet som beskrivs i [och skapa en konsolen programmet som kör ett kommando som angetts](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).|
|[Runspace02 kodexempel](./runspace02-code-samples.md)|Det här exemplet används den [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klassen för att köra den `Get-Process` cmdlet synkront.|
|[RunSpace03 kodexempel](./runspace03-code-samples.md)|Dessa är kodexempel för körningsutrymmet som beskrivs i [och skapa en konsolen program som använder ett skript som angetts](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).|
|[RunSpace04 kodexempel](./runspace04-code-samples.md)|Det här är ett kodexempel på för ett körningsutrymme som använder den [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klassen för att köra ett skript som genererar ett avslutande fel.|
|[RunSpace05 kodexempel](./runspace05-code-sample.md)|Det här är källkoden för Runspace05-exemplet som beskrivs i [konfigurerar en Körningsutrymme med RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[RunSpace06 kodexempel](./runspace06-code-sample.md)|Det här är källkoden för Runspace06-exemplet som beskrivs i [konfigurerar ett Körningsutrymme som en Windows PowerShell snapin-modulen](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[RunSpace07 kodexempel](./runspace07-code-sample.md)|Det här är källkoden för Runspace07-exemplet som beskrivs i [skapar ett program som lägger till konsolkommandon för en Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[RunSpace08 kodexempel](./runspace08-code-sample.md)|Det här är källkoden för Runspace08-exemplet som beskrivs i [skapar ett program som lägger till Konsolparametrar till ett kommando](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[RunSpace09 kodexempel](./runspace09-code-sample.md)|Det här är källkoden för Runspace09-exemplet som beskrivs i [skapar en konsolen program som anropar en Pipeline asynkront](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[RunSpace10 kodexempel](./runspace10-code-sample.md)|Det här är källkoden för Runspace10 samplet, som lägger till en cmdlet för att [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) och använder sedan den ändrade konfigurationsinformationen för att skapa körningsutrymmet.|

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)