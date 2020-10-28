---
ms.date: 09/12/2016
ms.topic: reference
title: Cmdlets för providers
description: Cmdlets för providers
ms.openlocfilehash: 522dacfe4d7190c12ea0de148fe83bf6b5fed10f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662904"
---
# <a name="provider-cmdlets"></a>Cmdlets för providers

De cmdletar som användaren kan köra för att hantera ett data lager kallas för provider-cmdletar. Om du vill ha stöd för dessa cmdletar måste du skriva över några av de metoder som definierats av bas leverantörs klasserna och gränssnitten.

## <a name="provider-cmdlets"></a>Provider-cmdletar

Här är de Provider-cmdletar som kan köras av användaren:

### <a name="psdrive-cmdlets"></a>PSDrive-cmdletar

- `Get-PSDrive`: Den här cmdleten returnerar Windows PowerShell-enheter i den aktuella sessionen. Du behöver inte skriva över några metoder för att stödja denna cmdlet.

- `New-PSDrive`: Med den här cmdleten kan användaren skapa Windows PowerShell-enheter för att få åtkomst till data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

- `Remove-PSDrive`: Den här cmdleten låter användaren ta bort Windows PowerShell-enheter som har åtkomst till data lagret. För att stödja denna cmdlet skriver du över metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .

### <a name="item-cmdlets"></a>Objekt-cmdletar

- `Clear-Item`: Den här cmdleten låter användaren ta bort värdet för ett objekt i data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) och [system. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

- `Copy-Item`: Med den här cmdleten kan användaren kopiera ett objekt från en plats till en annan. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) och [system. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

- `Get-Item`: Den här cmdleten gör det möjligt för användaren att hämta data från data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. getItem,](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [system. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

- `Get-ChildItem`: Den här cmdleten låter användaren hämta de underordnade objekten till det överordnade objektet. Skriv över följande metoder för att stödja denna cmdlet:

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Den här cmdleten gör att användaren kan utföra den standard åtgärd som anges av objektet. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) och [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

- `Move-Item`: Den här cmdleten gör att användaren kan flytta ett objekt från en plats till en annan plats. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) och [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s.

- `New-ItemProperty`: Med den här cmdleten kan användaren skapa ett nytt objekt i data lagret.

- `Remove-Item`: Den här cmdleten låter användaren ta bort objekt från data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) och [system. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

- `Rename-Item`: Den här cmdleten gör att användaren kan byta namn på objekt i data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Containercmdletprovider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) och [system. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

- `Set-Item`: Den här cmdleten gör det möjligt för användaren att uppdatera värdena för objekt i data lagret. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. setItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) och [system. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

### <a name="item-content-cmdlets"></a>Cmdlets för objekt innehåll

- `Add-Content`: Den här cmdleten låter användaren lägga till innehåll till ett objekt.

- `Clear-Content`: Den här cmdleten gör att användaren kan ta bort innehåll från ett objekt utan att ta bort objektet. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) och [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .

- `Get-Content`: Den här cmdleten gör att användaren kan hämta innehållet i ett objekt. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) och [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) . Metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) returnerar ett [system. Management. Automation. Provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) -gränssnitt som definierar de metoder som används för att läsa innehållet.

- `Set-Content`: Den här cmdleten gör det möjligt för användaren att uppdatera innehållet i ett objekt. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) och [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) . Metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) returnerar ett [system. Management. Automation. Provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) -gränssnitt som definierar de metoder som används för att skriva innehållet.

### <a name="item-property-cmdlets"></a>Cmdletar för objekt egenskap

- `Clear-ItemProperty`: Den här cmdleten gör att användaren kan ta bort värdet för en egenskap. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) och [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) .

- `Copy-ItemProperty`: Med den här cmdleten kan användaren kopiera en egenskap och dess värde från en plats till en annan. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) och [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) .

- `Get-ItemProperty`: Den här cmdleten hämtar egenskaperna för ett objekt. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) och [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

- `Move-ItemProperty`: Den här cmdleten gör att användaren kan flytta en egenskap och dess värde från en plats till en annan. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) och [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) .

- `New-ItemProperty`: Den här cmdleten gör att användaren kan skapa en ny egenskap och ange dess värde. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) och [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

- `Remove-ItemProperty`: Den här cmdleten gör att användaren kan ta bort en egenskap och dess värde. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) och [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

- `Rename-ItemProperty`: Den här cmdleten gör att användaren kan ändra namnet på en egenskap. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) och [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

- `Set-ItemProperty`: Med den här cmdleten kan användaren uppdatera egenskaperna för ett objekt. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Ipropertycmdletprovider. setProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) och [system. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

### <a name="location-cmdlets"></a>Plats-cmdletar

- `Get-Location`: Hämtar information om den aktuella arbets platsen. Du behöver inte skriva över några metoder för att stödja denna cmdlet.

- `Pop-Location`: Den här cmdleten ändrar den aktuella platsen till den plats som senast skickas till stacken. Du behöver inte skriva över några metoder för att stödja denna cmdlet.

- `Push-Location`: Den här cmdleten lägger till den aktuella platsen överst i en lista över platser (en "stack"). Du behöver inte skriva över några metoder för att stödja denna cmdlet.

- `Set-Location`: Den här cmdleten anger den aktuella arbets platsen till en angiven plats. Du behöver inte skriva över några metoder för att stödja denna cmdlet.

### <a name="path-cmdlets"></a>Sök vägs-cmdletar

- `Join-Path`: Den här cmdleten låter användaren kombinera ett överordnat och underordnat Sök vägs segment för att skapa en provider-intern sökväg. För att stödja denna cmdlet skriver du över metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

- `Convert-Path`: Den här cmdleten konverterar en sökväg från en Windows PowerShell-sökväg till en sökväg för Windows PowerShell-providern.

- `Split-Path`: Returnerar den angivna delen av en sökväg.

- `Resolve-Path`: Matchar jokertecken i en sökväg och visar Sök vägs innehållet.

- `Test-Path`: Den här cmdleten avgör om alla element i en sökväg finns. För att stödja denna cmdlet skriver du över metoderna [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) och [system. Management. Automation. Provider. Itemcmdletprovider. Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) .

### <a name="psprovider-cmdlets"></a>PSProvider-cmdletar

- `Get-PSProvider`: Den här cmdleten returnerar information om de providers som är tillgängliga i sessionen. Du behöver inte skriva över några metoder för att stödja denna cmdlet.
