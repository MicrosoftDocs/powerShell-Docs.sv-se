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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356842"
---
# <a name="provider-cmdlet-parameters"></a>Cmdlet-parametrar för providers

Provider-cmdletar levereras med en uppsättning statiska parametrar som är tillgängliga för alla providers som stöder-cmdleten, samt dynamiska parametrar som läggs till när användaren anger ett visst värde för vissa statiska parametrar i Provider-cmdleten.

## <a name="provider-cmdlet-static-parameters"></a>Statiska parametrar för provider cmdlet

Statiska parametrar definieras av Windows PowerShell. En stor uppsättning parametrar implementeras av Windows PowerShell för att tillhandahålla konsekvens i alla leverantörer och för att ge en enklare utvecklings upplevelse. Exempel på dessa parametrar är parametrarna `literalPath`, `exclude` och `include` för `Get-Item`-cmdleten. En mindre uppsättning parametrar kan skrivas över för att tillhandahålla åtgärder som är speciella för din Provider. Exempel på dessa parametrar är parametrarna `Path` och `Value` för cmdleten `Set-Item`. Här är en lista över de parametrar som kan skrivas över för provider-cmdletar.

`Clear-Content`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametern `Path` för cmdleten `Clear-Content` genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) .

`Clear-Item`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametern `Path` för cmdleten `Clear-Item` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) .

`Clear-ItemProperty`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path` och `Name` i cmdleten `Clear-ItemProperty` genom att implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) .

`Copy-Item`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path`, `Destination` och `Recurse` i `Copy-Item`-cmdleten genom att implementera [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metodsignatur.

Get-ChildItems-cmdlet du kan definiera hur providern ska använda värdena som skickas till parametrarna `Path` och `Recurse` för cmdleten `Get-ChildItem` genom att implementera [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) och metoderna [system. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) .

`Get-Content`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametern `Path` för cmdleten `Get-Content` genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) .

`Get-Item`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametern `Path` för cmdleten `Get-Item` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) .

`Get-ItemProperty`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path` och `Name` i cmdleten `Get-ItemProperty` genom att implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) .

`Invoke-Item`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametern `Path` för cmdleten `Invoke-Item` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

`Move-Item`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path` och `Destination` i cmdleten `Move-Item` genom att implementera metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) .

`New-Item`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path`, `ItemType` och `Value` i `New-Item`-cmdleten genom att implementera [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodsignatur.

`New-ItemProperty`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path`, `Name`, `PropertyType` och `Value` i cmdleten `New-ItemProperty` genom att implementera [Microsoft. PowerShell. commands. Registryprovider. newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) metodsignatur.

`Remove-Item` du kan definiera hur providern ska använda värdena som skickas till parametrarna `Path` och `Recurse` för cmdleten `Remove-Item` genom att implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) .

`Remove-ItemProperty` du kan definiera hur providern ska använda värdena som skickas till parametrarna `Path` och `Name` för cmdleten `Remove-ItemProperty` genom att implementera [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removeproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) metodsignatur.

`Rename-Item`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path` och `NewName` i cmdleten `Rename-Item` genom att implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) .

`Rename-ItemProperty` du kan definiera hur leverantören ska använda värdena som skickas till parametrarna `Path`, `NewName` och `Name` i `Rename-ItemProperty`-cmdleten genom att implementera [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty * ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)metoden.

`Set-Content`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametern `Path` för cmdleten `Set-Content` genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) .

`Set-Item`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path` och `Value` i cmdleten `Set-Item` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) .

`Set-ItemProperty`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametrarna `Path` och `Value` i cmdleten `Set-Item` genom att implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .

`Test-Path`-cmdlet kan du definiera hur providern ska använda värdena som skickas till parametern `Path` för cmdleten `Test-Path` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

Dessutom kan du inte ange egenskaperna för dessa parametrar, t. ex. om de är valfria eller obligatoriska, eller så kan du inte ge dessa parametrar ett alias eller ange något av verifierings-attributen. Du kan däremot ange parameter egenskaper i fristående cmdlets med hjälp av attribut som `Parameters`-attributet.

## <a name="provider-cmdlet-dynamic-parameters"></a>Dynamiska parametrar för provider-cmdlet

Dynamiska parametrar för cmdlet-providers liknar dynamiska providrar för fristående cmdlets. I båda fallen läggs parametrarna till i cmdleten när användaren anger ett visst värde för en av standard parametrarna, till exempel parametern `path`. Alla statiska parametrar kan dock inte användas för att utlösa tillägg av dynamiska parametrar. Mer information om dynamiska parametrar finns i [dynamisk parameter för provider cmdlet](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Se även

[Dynamiska parametrar för provider-cmdlet](./provider-cmdlet-dynamic-parameters.md)

[Skriva en Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)