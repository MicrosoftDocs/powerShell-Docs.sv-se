---
title: Exempel kod för Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: e9df44b17453e9f73f6eb388d9cbc8a69fce4ba2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356919"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell-exempelkod

Windows PowerShell®-exempel är tillgängliga via Windows SDK. Det här avsnittet innehåller exempel koden som finns i Windows SDK exempel.

> [!NOTE]
> När Windows SDK installeras skapas en **exempel** katalog där alla Windows PowerShell-exempel görs tillgängliga. En typisk installations katalog är **C:\Program\Microsoft SDKs\Windows\v6.0**.
> Starta Windows PowerShell och skriv **"CD Samples\SysMgmt\PowerShell"** för att hitta mappen Windows PowerShell-exempel. I det här dokumentet kallas Windows PowerShell-exempel katalogen **\<PowerShell-exempel >** .

## <a name="sample-code-listing"></a>Exempel kod lista

|Exempel kod|Beskrivning|
|-----------------|-----------------|
|[AccessDbProviderSample01 kod exempel](./accessdbprovidersample01-code-sample.md)|Detta är den provider som beskrivs i [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).|
|[AccessDbProviderSample02 kod exempel](./accessdbprovidersample02-code-sample.md)|Det här är den provider som beskrivs i [skapa en Windows PowerShell-enhets leverantör](./creating-a-windows-powershell-drive-provider.md).|
|[AccessDbProviderSample03 kod exempel](./accessdbprovidersample03-code-sample.md)|Detta är den provider som beskrivs i [skapa en Windows PowerShell-dataprovider](./creating-a-windows-powershell-item-provider.md).|
|[AccessDbProviderSample04 kod exempel](./accessdbprovidersample04-code-sample.md)|Detta är den provider som beskrivs i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).|
|[AccessDbProviderSample05 kod exempel](./accessdbprovidersample05-code-sample.md)|Detta är den provider som beskrivs i [skapa en Windows PowerShell-navigerings leverantör](./creating-a-windows-powershell-navigation-provider.md).|
|[AccessDbProviderSample06 kod exempel](./accessdbprovidersample06-code-sample.md)|Detta är den provider som beskrivs i [skapa en Windows PowerShell-innehålls leverantör](./creating-a-windows-powershell-content-provider.md).|
|[GetProc01 kod exempel](./getproc01-code-samples.md)|Detta är det grundläggande `Get-Process`-cmdlet-exemplet som beskrivs i [skapa din första cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[GetProc02 kod exempel](./getproc02-code-samples.md)|Detta är det `Get-Process`-cmdlet-exemplet [som beskrivs i lägga till parametrar som bearbetar kommando rads indatatyper](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[GetProc03 kod exempel](./getproc03-code-samples.md)|Detta är det `Get-Process`-cmdlet-exemplet [som beskrivs i lägga till parametrar som bearbetar pipeline-inflöden](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[GetProc04 kod exempel](./getproc04-code-samples.md)|Detta är `Get-Process`-cmdlet-exemplet som beskrivs i [lägga till ej avslutande fel rapportering till din cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[GetProc05 kod exempel](./getproc05-code-samples.md)|Denna `Get-Process`-cmdlet liknar den cmdlet som beskrivs i [lägga till ej avslutande fel rapportering till din cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[StopProc01 kod exempel](./stopproc01-code-samples.md)|Detta är `Stop-Process`-cmdlet-exemplet som beskrivs i [skapa en cmdlet som ändrar systemet](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[StopProcessSample04 kod exempel](./stopprocesssample04-code-samples.md)|Detta är det `Stop-Process`-cmdlet-exemplet som beskrivs i [lägga till parameter uppsättningar i en cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Runspace01 kod exempel](./runspace01-code-samples.md)|Detta är kod exemplen för körnings utrymme som beskrivs i [skapa ett konsol program som kör ett angivet kommando](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).|
|[Runspace02 kod exempel](./runspace02-code-samples.md)|I det här exemplet används klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra cmdleten `Get-Process` synkront.|
|[RunSpace03 kod exempel](./runspace03-code-samples.md)|Detta är kod exemplen för körnings utrymme som beskrivs i "skapa ett konsol program som kör ett angivet skript".|
|[RunSpace04 kod exempel](./runspace04-code-samples.md)|Det här är ett kod exempel för en körnings utrymme som använder klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra ett skript som genererar ett avslutande fel.|
|[RunSpace05 kod exempel](./runspace05-code-sample.md)|Det här är käll koden för Runspace05-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[RunSpace06 kod exempel](./runspace06-code-sample.md)|Det här är käll koden för Runspace06-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av en Windows PowerShell-snapin-modul](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[RunSpace07 kod exempel](./runspace07-code-sample.md)|Det här är käll koden för Runspace07-exemplet som beskrivs i [skapa ett konsol program som lägger till kommandon i en pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[RunSpace08 kod exempel](./runspace08-code-sample.md)|Det här är käll koden för Runspace08-exemplet som beskrivs i [skapa ett konsol program som lägger till parametrar till ett kommando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[RunSpace09 kod exempel](./runspace09-code-sample.md)|Det här är käll koden för Runspace09-exemplet som beskrivs i [skapa ett konsol program som anropar en pipeline asynkront](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[RunSpace10 kod exempel](./runspace10-code-sample.md)|Det här är käll koden för Runspace10-exemplet, som lägger till en cmdlet till [system. Management. Automation. körnings utrymmen. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) och använder sedan den ändrade konfigurations informationen för att skapa körnings utrymme.|

## <a name="see-also"></a>Se även

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)