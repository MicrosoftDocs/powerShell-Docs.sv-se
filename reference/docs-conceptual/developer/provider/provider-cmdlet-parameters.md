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
ms.openlocfilehash: 8ce13032a55d164121a073ef94086dc1de09b902
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564214"
---
# <a name="provider-cmdlet-parameters"></a>Cmdlet-parametrar för providers

Provider-cmdletar levereras med en uppsättning statiska parametrar som är tillgängliga för alla providers som stöder-cmdleten, samt dynamiska parametrar som läggs till när användaren anger ett visst värde för vissa statiska parametrar i Provider-cmdleten.

## <a name="provider-cmdlet-static-parameters"></a>Statiska parametrar för provider cmdlet

Statiska parametrar definieras av Windows PowerShell. En stor uppsättning parametrar implementeras av Windows PowerShell för att tillhandahålla konsekvens i alla leverantörer och för att ge en enklare utvecklings upplevelse. Exempel på dessa parametrar är `literalPath` parametrarna, `exclude` och och `include` för `Get-Item` cmdleten. En mindre uppsättning parametrar kan skrivas över för att tillhandahålla åtgärder som är speciella för din Provider. Exempel på dessa parametrar är `Path` cmdlet- `Value` parametern och `Set-Item` . Här är en lista över de parametrar som kan skrivas över för provider-cmdletar.

`Clear-Content`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet-parametern `Clear-Content` genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) .

`Clear-Item`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet-parametern `Clear-Item` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) .

`Clear-ItemProperty`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet- `Name` parametrarna och genom att `Clear-ItemProperty` implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) .

`Copy-Item`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` parametrarna, `Destination` , och `Recurse` för `Copy-Item` cmdleten genom att implementera metoden [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) .

Get-ChildItems-cmdlet du kan definiera hur providern ska använda värdena som skickas till `Path` `Recurse` cmdlet-parametrarna och `Get-ChildItem` genom att implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) och [system. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) .

`Get-Content`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet-parametern `Get-Content` genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) .

`Get-Item`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet-parametern `Get-Item` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) .

`Get-ItemProperty`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet- `Name` parametrarna och genom att `Get-ItemProperty` implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) .

`Invoke-Item`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet-parametern `Invoke-Item` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

`Move-Item`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet- `Destination` parametrarna och genom att `Move-Item` implementera metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) .

`New-Item`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` parametrarna, `ItemType` , och `Value` för `New-Item` cmdleten genom att implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) .

`New-ItemProperty`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` `Name` `PropertyType` cmdleten,, och `Value` för `New-ItemProperty` cmdleten genom att implementera metoden [Microsoft. PowerShell. commands. Registryprovider. newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) .

`Remove-Item`Du kan definiera hur providern ska använda värdena som skickas till `Path` cmdlet- `Recurse` parametrarna och genom att `Remove-Item` implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) .

`Remove-ItemProperty`Du kan definiera hur providern ska använda värdena som skickas till `Path` cmdlet- `Name` parametrarna och genom att `Remove-ItemProperty` implementera metoden [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removeproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) .

`Rename-Item`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet- `NewName` parametrarna och genom att `Rename-Item` implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) .

`Rename-ItemProperty`Du kan definiera hur providern ska använda värdena som skickas till `Path` parametrarna, `NewName` , och `Name` för `Rename-ItemProperty` cmdleten genom att implementera metoden [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) .

`Set-Content`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet-parametern `Set-Content` genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) .

`Set-Item`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet- `Value` parametrarna och genom att `Set-Item` implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) .

`Set-ItemProperty`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet- `Value` parametrarna och genom att `Set-Item` implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .

`Test-Path`cmdlet kan du definiera hur providern ska använda värdena som skickas till `Path` cmdlet-parametern `Test-Path` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

Dessutom kan du inte ange egenskaperna för dessa parametrar, t. ex. om de är valfria eller obligatoriska, eller så kan du inte ge dessa parametrar ett alias eller ange något av verifierings-attributen. Du kan däremot ange parameter egenskaper i fristående cmdlets med hjälp av attribut som- `Parameters` attributet.

## <a name="provider-cmdlet-dynamic-parameters"></a>Dynamiska parametrar för provider-cmdlet

Dynamiska parametrar för cmdlet-providers liknar dynamiska providrar för fristående cmdlets. I båda fallen läggs parametrarna till i cmdleten när användaren anger ett visst värde för en av standard parametrarna, t `path` . ex. parametern. Alla statiska parametrar kan dock inte användas för att utlösa tillägg av dynamiska parametrar. Mer information om dynamiska parametrar finns i [dynamisk parameter för provider cmdlet](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Se även

[Dynamiska parametrar för provider-cmdlet](./provider-cmdlet-dynamic-parameters.md)

[Skriva en Windows PowerShell-provider](./writing-a-windows-powershell-provider.md)
