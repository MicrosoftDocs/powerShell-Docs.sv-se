---
title: Parametrar för provider-cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356842"
---
# <a name="provider-cmdlet-parameters"></a>Cmdlet-parametrar för providers

Provider-cmdletar levereras med en uppsättning statiska parametrar som är tillgängliga för alla providers som stöder-cmdleten, samt dynamiska parametrar som läggs till när användaren anger ett visst värde för vissa statiska parametrar i Provider-cmdleten.

## <a name="provider-cmdlet-static-parameters"></a>Statiska parametrar för provider cmdlet

Statiska parametrar definieras av Windows PowerShell. En stor uppsättning parametrar implementeras av Windows PowerShell för att tillhandahålla konsekvens i alla leverantörer och för att ge en enklare utvecklings upplevelse. Exempel på dessa parametrar är parametrarna `literalPath`, `exclude`och `include` för `Get-Item`-cmdleten. En mindre uppsättning parametrar kan skrivas över för att tillhandahålla åtgärder som är speciella för din Provider. Exempel på dessa parametrar är `Path`-och `Value`-parametern för `Set-Item`-cmdleten. Här är en lista över de parametrar som kan skrivas över för provider-cmdletar.

`Clear-Content` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-parametern i `Clear-Content`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) .

`Clear-Item` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-parametern i `Clear-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) .

`Clear-ItemProperty` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-och `Name`-parametrarna i `Clear-ItemProperty`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) .

`Copy-Item` cmdleten kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path`, `Destination`och `Recurse` i `Copy-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) .

Get-ChildItems-cmdlet du kan definiera hur providern ska använda värdena som skickas till `Path`-och `Recurse`-parametrarna i `Get-ChildItem`-cmdleten genom att implementera [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) och [system. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metoder.

`Get-Content` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-parametern i `Get-Content`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) .

`Get-Item` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-parametern i `Get-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) .

`Get-ItemProperty` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-och `Name`-parametrarna i `Get-ItemProperty`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) .

`Invoke-Item` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-parametern i `Invoke-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

`Move-Item` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-och `Destination`-parametrarna i `Move-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) .

`New-Item` cmdleten kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path`, `ItemType`och `Value` i `New-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) .

`New-ItemProperty` cmdleten kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path`, `Name`, `PropertyType`och `Value` för den `New-ItemProperty` cmdleten genom att implementera metoden [Microsoft. PowerShell. commands. Registryprovider. newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) .

`Remove-Item` kan du definiera hur providern ska använda värdena som skickas till `Path`-och `Recurse`-parametrarna i `Remove-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) .

`Remove-ItemProperty` kan du definiera hur providern ska använda värdena som skickas till `Path`-och `Name`-parametrarna i `Remove-ItemProperty`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removeproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) .

`Rename-Item` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-och `NewName`-parametrarna i `Rename-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) .

`Rename-ItemProperty` kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path`, `NewName`och `Name` i `Rename-ItemProperty`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) .

`Set-Content` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-parametern i `Set-Content`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) .

`Set-Item` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-och `Value`-parametrarna i `Set-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) .

`Set-ItemProperty` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-och `Value`-parametrarna i `Set-Item`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .

`Test-Path` cmdleten kan du definiera hur providern ska använda värdena som skickas till `Path`-parametern i `Test-Path`-cmdleten genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

Dessutom kan du inte ange egenskaperna för dessa parametrar, t. ex. om de är valfria eller obligatoriska, eller så kan du inte ge dessa parametrar ett alias eller ange något av verifierings-attributen. Du kan däremot ange parameter egenskaper i fristående cmdlets med hjälp av attribut som `Parameters`-attributet.

## <a name="provider-cmdlet-dynamic-parameters"></a>Dynamiska parametrar för provider-cmdlet

Dynamiska parametrar för cmdlet-providers liknar dynamiska providrar för fristående cmdlets. I båda fallen läggs parametrarna till i cmdleten när användaren anger ett visst värde för en av standard parametrarna, till exempel parametern `path`. Alla statiska parametrar kan dock inte användas för att utlösa tillägg av dynamiska parametrar. Mer information om dynamiska parametrar finns i [dynamisk parameter för provider cmdlet](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Se även

[Dynamiska parametrar för provider-cmdlet](./provider-cmdlet-dynamic-parameters.md)

[Skriva en Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)