---
title: Provider-cmdletar | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352404"
---
# <a name="provider-cmdlets"></a>Cmdlets för providers

De cmdletar som användaren kan köra för att hantera ett data lager kallas för provider-cmdletar. Om du vill ha stöd för dessa cmdletar måste du skriva över några av de metoder som definierats av bas leverantörs klasserna och gränssnitten.

## <a name="provider-cmdlets"></a>Provider-cmdletar

Här är de Provider-cmdletar som kan köras av användaren:

### <a name="psdrive-cmdlets"></a>PSDrive-cmdletar

- `Get-PSDrive`: den här cmdleten returnerar Windows PowerShell-enheter i den aktuella sessionen. Du behöver inte skriva över några metoder för att stödja denna cmdlet.

- `New-PSDrive`: med den här cmdleten kan användaren skapa Windows PowerShell-enheter för att få åtkomst till data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

- `Remove-PSDrive`: med den här cmdleten kan användaren ta bort Windows PowerShell-enheter som har åtkomst till data lagret. För att stödja denna cmdlet skriver du över metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .

### <a name="item-cmdlets"></a>Objekt-cmdletar

- `Clear-Item`: med den här cmdleten kan användaren ta bort värdet för ett objekt i data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) och [system. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

- `Copy-Item`: med den här cmdleten kan användaren kopiera ett objekt från en plats till en annan. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) och [system. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

- `Get-Item`: denna cmdlet gör det möjligt för användaren att hämta data från data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. getItem,](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [system. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

- `Get-ChildItem`: med den här cmdleten kan användaren hämta de underordnade objekten till det överordnade objektet. Skriv över följande metoder för att stödja denna cmdlet:

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: med den här cmdleten kan användaren utföra den standard åtgärd som anges av objektet. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) och [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

- `Move-Item`: med den här cmdleten kan användaren flytta ett objekt från en plats till en annan plats. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) och [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s.

- `New-ItemProperty`: med den här cmdleten kan användaren skapa ett nytt objekt i data lagret.

- `Remove-Item`: med den här cmdleten kan användaren ta bort objekt från data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) och [system. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

- `Rename-Item`: med den här cmdleten kan användaren byta namn på objekt i data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Containercmdletprovider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) och [system. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

- `Set-Item`: med den här cmdleten kan användaren uppdatera värdena för objekt i data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. setItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) och [system. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

### <a name="item-content-cmdlets"></a>Cmdlets för objekt innehåll

- `Add-Content`: med den här cmdleten kan användaren lägga till innehåll till ett objekt.

- `Clear-Content`: med den här cmdleten kan användaren ta bort innehåll från ett objekt utan att ta bort objektet. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) och [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .

- `Get-Content`: med den här cmdleten kan användaren hämta innehållet i ett objekt. För att stödja denna cmdlet skriver du över [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) och [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) indatametod. Metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) returnerar ett [system. Management. Automation. Provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) -gränssnitt som definierar de metoder som används för att läsa innehållet.

- `Set-Content`: med den här cmdleten kan användaren uppdatera innehållet i ett objekt. För att stödja denna cmdlet skriver du över [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) och [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) indatametod. Metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) returnerar ett [system. Management. Automation. Provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) -gränssnitt som definierar de metoder som används för att skriva innehållet.

### <a name="item-property-cmdlets"></a>Cmdletar för objekt egenskap

- `Clear-ItemProperty`: med den här cmdleten kan användaren ta bort värdet för en egenskap. För att stödja denna cmdlet skriver du över [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) och [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) indatametod.

- `Copy-ItemProperty`: med den här cmdleten kan användaren kopiera en egenskap och dess värde från en plats till en annan. För att stödja denna cmdlet skriver du över [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) och [ Metoderna system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) .

- `Get-ItemProperty`: denna cmdlet hämtar egenskaperna för ett objekt. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) och [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

- `Move-ItemProperty`: med den här cmdleten kan användaren flytta en egenskap och dess värde från en plats till en annan. För att stödja denna cmdlet skriver du över [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) och [ Metoderna system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) .

- `New-ItemProperty`: med den här cmdleten kan användaren skapa en ny egenskap och ange dess värde. För att stödja denna cmdlet skriver du över [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) och [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)metoder.

- `Remove-ItemProperty`: denna cmdlet gör det möjligt för användaren att ta bort en egenskap och dess värde. För att stödja denna cmdlet skriver du över [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) och [ Metoderna system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

- `Rename-ItemProperty`: med den här cmdleten kan användaren ändra namnet på en egenskap. För att stödja denna cmdlet skriver du över [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) och [ Metoderna system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

- `Set-ItemProperty`: med den här cmdleten kan användaren uppdatera egenskaperna för ett objekt. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) och [system. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

### <a name="location-cmdlets"></a>Plats-cmdletar

- `Get-Location`: hämtar information om den aktuella arbets platsen. Du behöver inte skriva över några metoder för att stödja denna cmdlet.

- `Pop-Location`: denna cmdlet ändrar den aktuella platsen till den plats som senast skickas till stacken. Du behöver inte skriva över några metoder för att stödja denna cmdlet.

- `Push-Location`: denna cmdlet lägger till den aktuella platsen överst i en lista över platser (en "stack"). Du behöver inte skriva över några metoder för att stödja denna cmdlet.

- `Set-Location`: denna cmdlet anger den aktuella arbets platsen till en angiven plats. Du behöver inte skriva över några metoder för att stödja denna cmdlet.

### <a name="path-cmdlets"></a>Sök vägs-cmdletar

- `Join-Path`: med den här cmdleten kan användaren kombinera ett överordnat och underordnat Sök vägs segment för att skapa en provider-intern sökväg. För att stödja denna cmdlet skriver du över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

- `Convert-Path`: denna cmdlet konverterar en sökväg från en Windows PowerShell-sökväg till en sökväg för Windows PowerShell-providern.

- `Split-Path`: returnerar den angivna delen av en sökväg.

- `Resolve-Path`: matchar jokertecken i en sökväg och visar Sök vägs innehållet.

- `Test-Path`: denna cmdlet avgör om alla element i en sökväg finns. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) och [system. Management. Automation. Provider. Itemcmdletprovider. Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) .

### <a name="psprovider-cmdlets"></a>PSProvider-cmdletar

- `Get-PSProvider`: den här cmdleten returnerar information om de providers som är tillgängliga i sessionen. Du behöver inte skriva över några metoder för att stödja denna cmdlet.