---
title: Providern cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057050"
---
# <a name="provider-cmdlet-parameters"></a>Cmdlet-parametrar för providers

Cmdlets för provider levereras med en uppsättning statiska parametrar som är tillgängliga för alla leverantörer som har stöd för cmdlet: en, samt som dynamiska parametrar som läggs till när användaren anger ett visst värde för vissa statiska parametrar för providern cmdlet: ar.

## <a name="provider-cmdlet-static-parameters"></a>Providern Cmdlet statisk parametrar

Statisk parametrar definieras av Windows PowerShell. Ett stort antal för dessa parametrar implementeras av Windows PowerShell så att alla leverantörer och för att tillhandahålla en enklare utvecklingsupplevelse. Exempel på dessa parametrar är den `literalPath`, `exclude`, och `include` parametrarna för den `Get-Item` cmdlet. En mindre uppsättning parametrarna kan åsidosättas för att tillhandahålla åtgärder som är specifika för leverantören. Exempel på dessa parametrar är den `Path` och `Value` -parametern för den `Set-Item` cmdlet. Här är en lista över de parametrar som kan skrivas över för provider-cmdletar.

`Clear-Content` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` -parametern för den `Clear-Content` cmdlet genom att implementera den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)metod.

`Clear-Item` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` -parametern för den `Clear-Item` cmdlet genom att implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) metoden.

`Clear-ItemProperty` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` och `Name` parametrarna för den `Clear-ItemProperty` cmdlet genom att implementera den [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metod.

`Copy-Item` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path`, `Destination`, och `Recurse` parametrarna för den `Copy-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metod.

Get-ChildItems cmdlet kan du definiera hur leverantören använder de värden som skickas till den `Path` och `Recurse` parametrarna för den `Get-ChildItem` cmdlet genom att implementera den [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) och [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metoder.

`Get-Content` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` -parametern för den `Get-Content` cmdlet genom att implementera den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metod.

`Get-Item` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` -parametern för den `Get-Item` cmdlet genom att implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metod.

`Get-ItemProperty` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` och `Name` parametrarna för den `Get-ItemProperty` cmdlet genom att implementera den [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) metod.

`Invoke-Item` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` -parametern för den `Invoke-Item` cmdlet genom att implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)metod.

`Move-Item` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` och `Destination` parametrarna för den `Move-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metod.

`New-Item` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path`, `ItemType`, och `Value` parametrarna för den `New-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metod.

`New-ItemProperty` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path`, `Name`, `PropertyType`, och `Value` parametrarna för den `New-ItemProperty` cmdlet genom att implementera den [ Microsoft.PowerShell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) metod.

`Remove-Item` Du kan definiera hur leverantören använder de värden som skickas till den `Path` och `Recurse` parametrarna för den `Remove-Item` cmdlet genom att implementera den [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metod.

`Remove-ItemProperty` Du kan definiera hur leverantören använder de värden som skickas till den `Path` och `Name` parametrarna för den `Remove-ItemProperty` cmdlet genom att implementera den [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) metod.

`Rename-Item` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` och `NewName` parametrarna för den `Rename-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metod.

`Rename-ItemProperty` Du kan definiera hur leverantören använder de värden som skickas till den `Path`, `NewName`, och `Name` parametrarna för den `Rename-ItemProperty` cmdlet genom att implementera den [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) metod.

`Set-Content` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` -parametern för den `Set-Content` cmdlet genom att implementera den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metod.

`Set-Item` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` och `Value` parametrarna för den `Set-Item` cmdlet genom att implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metod.

`Set-ItemProperty` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` och `Value` parametrarna för den `Set-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metod.

`Test-Path` cmdlet: en kan du definiera hur leverantören använder de värden som skickas till den `Path` -parametern för den `Test-Path` cmdlet genom att implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)metod.

Dessutom kan du kan inte ange egenskaperna för dessa parametrar, till exempel om de är valfria eller krävs, eller kan du ge ett alias för dessa parametrar eller ange någon av attribut för verifiering. Du kan däremot ange parametern egenskaper i fristående cmdlets genom att använda attribut som den `Parameters` attribut.

## <a name="provider-cmdlet-dynamic-parameters"></a>Providern Cmdlet dynamiska parametrar

Dynamiska parametrar för cmdleten leverantörer liknar dynamisk providers för fristående cmdletar. I båda fallen parametrarna läggs till cmdleten när användaren anger ett visst värde för en av standardparametrarna som, till exempel den `path` parametern. Men kan inte alla statiska parametrar användas för att utlösa att lägga till dynamiska parametrar. Mer information om dynamiska parametrar finns i [providern Cmdlet dynamiska parametrar](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Se även

[Providern Cmdlet dynamiska parametrar](./provider-cmdlet-dynamic-parameters.md)

[Skriva ett Windows PowerShell-providern](./writing-a-windows-powershell-provider.md)