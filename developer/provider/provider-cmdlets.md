---
title: Cmdlets för provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080959"
---
# <a name="provider-cmdlets"></a>Cmdlets för providers

De cmdletar som användaren kan köra för att hantera ett datalager kallas cmdlets provider. För att stödja dessa cmdlets, måste du skriva över några av de metoder som definieras av de grundläggande providerklasserna och gränssnitten.

## <a name="provider-cmdlets"></a>Cmdlets för provider

Här följer de provider-cmdletar som kan köras av användaren:

### <a name="psdrive-cmdlets"></a>PSDrive-cmdletar

- `Get-PSDrive`: Denna cmdlet returnerar Windows PowerShell-enheter i den aktuella sessionen. Du behöver inte skriva över andra metoder för att stödja denna cmdlet.

- `New-PSDrive`: Denna cmdlet gör att användaren kan skapa Windows PowerShell-enheter att få åtkomst till datalagret. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metoder.

- `Remove-PSDrive`: Denna cmdlet gör att användaren kan ta bort Windows PowerShell-enheter som har åtkomst till datalagret. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metod.

### <a name="item-cmdlets"></a>Artikel-cmdletar

- `Clear-Item`: Denna cmdlet gör att användaren kan ta bort värdet för ett objekt i datalagret. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) och [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metoder.

- `Copy-Item`: Denna cmdlet gör att användaren kan kopiera ett objekt från en plats till en annan. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) och [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) metoder.

- `Get-Item`: Denna cmdlet används att hämta data från datalagret. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metoder.

- `Get-ChildItem`: Denna cmdlet används att hämta de underordnade objekten i den överordnade artikeln. För att stödja denna cmdlet, skriver du över följande metoder:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Denna cmdlet gör att användaren kan utföra den standardåtgärd som anges av objektet. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) och [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) metoder.

- `Move-Item`: Denna cmdlet gör att användaren kan flytta ett objekt från en plats till en annan plats. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) och [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s metoder.

- `New-ItemProperty`: Denna cmdlet gör att användaren kan skapa ett nytt objekt i datalagret.

- `Remove-Item`: Denna cmdlet gör att användaren kan ta bort objekt från datalagret. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) och [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metoder.

- `Rename-Item`: Denna cmdlet gör att användaren att byta namn på objekten i datalagret. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) och [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) metoder.

- `Set-Item`: Denna cmdlet används att uppdatera värdena för objekt i datalagret. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) och [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metoder.

### <a name="item-content-cmdlets"></a>Innehåll artikel-cmdletar

- `Add-Content`: Denna cmdlet gör att användaren kan lägga till innehåll på ett objekt.

- `Clear-Content`: Denna cmdlet gör att användaren kan ta bort innehållet från ett objekt utan att ta bort objektet. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) och [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) metoder.

- `Get-Content`: Denna cmdlet gör att användaren att hämta innehållet i ett objekt. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) och [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metoder. Den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metoden returnerar en [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) gränssnitt som definierar de metoder som används för att läsa innehållet.

- `Set-Content`: Denna cmdlet används att uppdatera innehållet i ett objekt. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) och [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metoder. Den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metoden returnerar en [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) gränssnitt som definierar de metoder som används för att skriva innehållet.

### <a name="item-property-cmdlets"></a>Artikel-cmdletar för egenskapen

- `Clear-ItemProperty`: Denna cmdlet gör att användaren kan ta bort värdet för en egenskap. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) och [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metoder.

- `Copy-ItemProperty`: Denna cmdlet gör att användaren kan kopiera en egenskap och dess värde från en plats till en annan. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) metoder.

- `Get-ItemProperty`: Denna cmdlet hämtar egenskaperna för ett objekt. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) och [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) metoder.

- `Move-ItemProperty`: Denna cmdlet gör att användaren kan flytta en egenskap och dess värde från en plats till en annan. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) metoder.

- `New-ItemProperty`: Denna cmdlet gör att användaren kan skapa en ny egenskap och ange värdet. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) metoder.

- `Remove-ItemProperty`: Denna cmdlet gör att användaren kan ta bort en egenskap och dess värde. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) metoder.

- `Rename-ItemProperty`: Denna cmdlet gör att användaren kan ändra namnet på en egenskap. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) metoder.

- `Set-ItemProperty`: Denna cmdlet används att uppdatera egenskaperna för ett objekt. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) och [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) metoder.

### <a name="location-cmdlets"></a>Plats-cmdletar

- `Get-Location`: Hämtar information om den aktuella platsen fungerar. Du behöver inte skriva över andra metoder för att stödja denna cmdlet.

- `Pop-Location`: Denna cmdlet ändrar den aktuella platsen till den plats som nyligen pushas till stacken. Du behöver inte skriva över andra metoder för att stödja denna cmdlet.

- `Push-Location`: Denna cmdlet lägger till den aktuella platsen högst upp i en lista över platser (”stackar”). Du behöver inte skriva över andra metoder för att stödja denna cmdlet.

- `Set-Location`: Denna cmdlet anger den aktuella fungerande platsen till en angiven plats. Du behöver inte skriva över andra metoder för att stödja denna cmdlet.

### <a name="path-cmdlets"></a>Sökväg-cmdletar

- `Join-Path`: Denna cmdlet gör att användaren kan kombinera ett överordnade och underordnade vägsegment för att skapa en provider-internt sökväg. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metod.

- `Convert-Path`: Denna cmdlet konverterar en sökväg från en Windows PowerShell-sökväg till en sökväg för Windows PowerShell-providern.

- `Split-Path`: Returnerar den angivna delen av en sökväg.

- `Resolve-Path`: Matchar jokertecken i en sökväg och visar sökvägen innehållet.

- `Test-Path`: Denna cmdlet avgör om det finns alla element i en sökväg. För denna cmdlet måste du skriva över den [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) och [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) metoder.

### <a name="psprovider-cmdlets"></a>PSProvider-cmdletar

- `Get-PSProvider`: Denna cmdlet returnerar information om leverantörerna som är tillgängliga i sessionen. Du behöver inte skriva över andra metoder för att stödja denna cmdlet.