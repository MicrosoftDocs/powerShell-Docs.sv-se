---
title: Providertyper | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 37689571eb1650e5991af2e7002cd037ae99dd68
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080924"
---
# <a name="provider-types"></a>Typer av providers

Leverantörer definiera sina grundläggande funktioner genom att ändra hur cmdlets för provider (som anges av Windows PowerShell) utföra sina åtgärder. Leverantörer kan till exempel använda standardfunktionerna i den `Get-Item` cmdlet eller att de kan ändra hur cmdleten fungerar när du hämtar objekt från datalagret. Providerfunktioner som beskrivs i det här avsnittet innehåller funktioner som definierats genom att skriva över metoder från leverantören basklasser och gränssnitt.

> [!NOTE]
> Provider-funktioner som har fördefinierats av Windows PowerShell, se [providern funktioner](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6).

## <a name="drive-enabled-providers"></a>Enhet-aktiverade Providers

Enhet-aktiverade providers Ange standard enheterna tillgängliga för användaren och Tillåt användaren att lägga till eller ta bort enheter. I de flesta fall är providers enhet-aktiverade providers eftersom de kräver vissa standardenheten för att få åtkomst till datalagret. Men när du skriver en egen provider du kanske eller kanske inte vill tillåta användare att skapa och ta bort enheter.

Om du vill skapa en enhet-aktiverad provider, providerklass måste komma från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass eller en annan klass som härleds från klassen. Den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klassen definierar följande metoder för att implementera de standard-enheterna av providern och stöd för den `New-PSDrive` och `Remove-PSDrive` cmdletar. I de flesta fall för att stödja en provider-cmdlet du måste skriva över den metod som Windows PowerShell-motorn anropar för att anropa cmdlet, som den `NewDrive` metod för den `New-PSDrive` där du kan också skriva över ett annat sätt, till exempel `NewDriveDynamicParameters`, för att lägga till dynamiska parametrar till cmdleten.

- Den [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metoden definierar de standard-enheter som är tillgängligt för användaren när providern används.

- Den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metoder definierar hur din provider stöder den `New-PSDrive` provider-cmdlet. Denna cmdlet gör att användaren kan skapa enheter att få åtkomst till datalagret.

- Den [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoden definierar hur din provider stöder den `Remove-PSDrive` provider-cmdlet. Denna cmdlet gör att användaren kan ta bort enheter från datalagret.

## <a name="item-enabled-providers"></a>Objekt-aktiverade Providers

Objekt-aktiverade providers Tillåt användare att hämta, ange eller ta bort objekt i datalagret. Ett ”objekt” är en del av det datalager som användaren kan komma åt eller hantera oberoende av varandra. Om du vill skapa ett objekt-aktiverad provider, providerklass måste komma från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass eller en annan klass som härleds från klassen.

Den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klassen definierar följande metoder för att implementera cmdlets för specifika provider. I de flesta fall för att stödja en provider-cmdlet du måste skriva över den metod som Windows PowerShell-motorn anropar för att anropa cmdlet, som den `ClearItem` metod för den `Clear-Item` där du kan också skriva över ett annat sätt, till exempel `ClearItemDynamicParameters`, för att lägga till dynamiska parametrar till cmdleten.

- Den [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) och [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metoder Definiera hur din provider stöder den `Clear-Item` provider-cmdlet. Denna cmdlet gör att användaren kan ta bort värdet för ett objekt i datalagret.

- Den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metoder definiera hur din provider stöder den `Get-Item` provider-cmdlet. Denna cmdlet används att hämta data från datalagret.

- Den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) och [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metoder definiera hur din provider stöder den `Set-Item` provider-cmdlet. Denna cmdlet används att uppdatera värdena för objekt i datalagret.

- Den [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) och [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) metoder Definiera hur din provider stöder den `Invoke-Item` provider-cmdlet. Denna cmdlet gör att användaren kan utföra den standardåtgärd som anges av objektet.

- Den [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) och [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) metoder Definiera hur din provider stöder den `Test-Path` provider-cmdlet. Denna cmdlet kan användaren för att avgöra om det finns alla element i en sökväg.

  Utöver de metoder som används för att implementera provider-cmdlet: ar, den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klassen definierar också följande metoder:

- Den [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) metoden gör att användaren kan använda jokertecken när du anger sökväg för provider.

- Den [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) används för att avgöra om en sökväg är syntaktiskt och semantiskt giltig för providern.

## <a name="container-enabled-providers"></a>Behållare-aktiverade Providers

Behållare-aktiverade providers Tillåt användare att hantera objekt som är behållare. En behållare är en grupp med underordnade objekt under en gemensam överordnad artikel. Om du vill skapa en behållare-aktiverad provider, providerklass måste komma från den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klass eller en annan klass som härleds från klassen.

> [!IMPORTANT]
> Behållare-aktiverade providers inte åtkomst till datalager som innehåller kapslade behållare. Om ett underordnat objekt för en behållare är en annan behållare, måste du implementera en Navigering-aktiverad provider.

Den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klassen definierar följande metoder för att implementera cmdlets för specifika provider. I de flesta fall för att stödja en provider-cmdlet du måste skriva över den metod som Windows PowerShell-motorn anropar för att anropa cmdlet, som den `CopyItem` metod för den `Copy-Item` där du kan också skriva över ett annat sätt, till exempel `CopyItemDynamicParameters`, för att lägga till dynamiska parametrar till cmdleten.

- Den [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) och [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) metoder som definierar hur din provider stöder den `Copy-Item` provider-cmdlet. Denna cmdlet gör att användaren kan kopiera ett objekt från en plats till en annan.

- Den [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) och [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) metoder definiera hur din provider stöder den `Get-ChildItem` provider-cmdlet. Denna cmdlet används att hämta de underordnade objekten i den överordnade artikeln.

- Den [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) och [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) metoder definiera hur din provider stöder den `Get-ChildItem` providern cmdlet om dess `Name` parameter har angetts.

- Den [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) och [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) metoder som definierar hur din provider stöder den `New-Item` provider-cmdlet. Denna cmdlet gör att användaren kan skapa nya objekt i datalagret.

- Den [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) och [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metoder som definierar hur din provider stöder den `Remove-Item` provider-cmdlet. Denna cmdlet gör att användaren kan ta bort objekt från datalagret.

- Den [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) och [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) metoder som definierar hur din provider stöder den `Rename-Item` provider-cmdlet. Denna cmdlet gör att användaren att byta namn på objekten i datalagret.

  Utöver de metoder som används för att implementera provider-cmdlet: ar, den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klassen definierar också följande metoder:

- Den [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) metoden kan användas av providerklassen för att avgöra om ett objekt har underordnade objekt.

- Den [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) metoden kan användas av providerklassen för att skapa en ny sökväg för provider-specifik från en angiven sökväg.

## <a name="navigation-enabled-providers"></a>Navigering-aktiverade Providers

Navigering-aktiverade providers Tillåt användare att flytta objekt i datalagret. Om du vill skapa en navigering aktiverat provider, providerklass måste komma från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass.

Den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klassen definierar följande metoder för att implementera cmdlets för specifika provider. I de flesta fall för att stödja en provider-cmdlet du måste skriva över den metod som Windows PowerShell-motorn anropar för att anropa cmdlet, som den `MoveItem` metod för den `Move-Item` där du kan också skriva över ett annat sätt, till exempel `MoveItemDynamicParameters`, för att lägga till dynamiska parametrar till cmdleten.

- Den [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) och [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) metoder som definierar hur din provider stöder den `Move-Item` provider-cmdlet. Denna cmdlet gör att användaren kan flytta ett objekt från en plats i arkivet till en annan plats.

- Den [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metoden definierar hur din provider stöder den `Join-Path` provider-cmdlet. Denna cmdlet gör att användaren kan kombinera ett överordnade och underordnade vägsegment för att skapa en provider-internt sökväg.

  Utöver de metoder som används för att implementera provider-cmdlet: ar, den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klassen definierar också följande metoder:

- Den [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) extraheras namnet på den underordnade noden i en sökväg.

- Den [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metoden extraherar den överordnade delen av en sökväg.

- Den [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) metoden anger om objektet är ett objekt i behållaren. I det här sammanhanget är en uppsättning underordnade objekt under en gemensam överordnad artikel i en behållare.

- Den [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metoden returnerar en sökväg till ett objekt som är relativ till en angiven sökväg för grundläggande.

## <a name="content-enabled-providers"></a>Innehåll-aktiverade Providers

Innehåll-aktiverade providers Tillåt användare att ta bort, hämta eller ange innehållet för objekt i ett datalager. Till exempel kan filsystem-providern du ta bort, hämta och ange innehållet i filer i filsystemet. Om du vill skapa en aktiverad innehållsleverantören providerklassen måste implementera-metoderna i den [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) gränssnitt.

Den [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -gränssnittet definierar följande metoder för att implementera cmdlets för specifika provider. I de flesta fall för att stödja en provider-cmdlet du måste skriva över den metod som Windows PowerShell-motorn anropar för att anropa cmdlet, som den `ClearContent` metod för den `Clear-Content` där du kan också skriva över ett annat sätt, till exempel `ClearContentDynamicParameters`, för att lägga till dynamiska parametrar till cmdleten.

- Den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) och [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)metoder definiera hur din provider stöder den `Clear-Content` provider-cmdlet. Denna cmdlet gör att användaren kan ta bort innehållet i ett objekt utan att ta bort objektet.

- Den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) och [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metoder definiera hur din provider stöder den `Get-Content` provider-cmdlet. Denna cmdlet gör att användaren att hämta innehållet i ett objekt. Den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metoden returnerar en [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) gränssnitt som definierar de metoder som används för att läsa innehållet.

- Den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) och [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metoder definiera hur din provider stöder den `Set-Content` provider-cmdlet. Denna cmdlet används att uppdatera innehållet i ett objekt. Den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metoden returnerar en [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) gränssnitt som definierar de metoder som används för att skriva innehållet.

## <a name="property-enabled-providers"></a>Egenskapen-aktiverade Providers

Egenskapen-aktiverade providers Tillåt användare att hantera egenskaper för objekt i datalagret. Om du vill skapa en egenskap-aktiverad provider, providerklass måste implementera-metoderna i den [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) gränssnitt. I de flesta fall för att stödja en provider-cmdlet du måste skriva över den metod som Windows PowerShell-motorn anropar för att anropa cmdlet, som den `ClearProperty` metoden för cmdleten Clear-egenskapen, och du kan också du kan skriva över ett annat sätt, till exempel `ClearPropertyDynamicParameters`, för att lägga till dynamiska parametrar till cmdleten.

Den [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) -gränssnittet definierar följande metoder för att implementera cmdlets för specifika provider:

- Den [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) och [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metoder definiera hur din provider stöder den `Clear-ItemProperty` provider-cmdlet. Denna cmdlet gör att användaren kan ta bort värdet för en egenskap.

- Den [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) och [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)metoder definiera hur din provider stöder den `Get-ItemProperty` provider-cmdlet. Denna cmdlet gör att användaren att hämta egenskapen för ett objekt.

- Den [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) och [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)metoder definiera hur din provider stöder den `Set-ItemProperty` provider-cmdlet. Denna cmdlet används att uppdatera egenskaperna för ett objekt.

  Den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) -gränssnittet definierar följande metoder för att implementera cmdlets för specifika provider:

- Den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) metoder definiera hur din provider stöder den `Copy-ItemProperty` provider-cmdlet. Denna cmdlet gör att användaren kan kopiera en egenskap och dess värde från en plats till en annan.

- Den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) metoder definiera hur din provider stöder den `Move-ItemProperty` provider-cmdlet. Denna cmdlet gör att användaren kan flytta en egenskap och dess värde från en plats till en annan.

- Den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) metoder definiera hur din provider stöder den `New-ItemProperty` provider-cmdlet. Denna cmdlet gör att användaren kan skapa en ny egenskap och ange värdet.

- Den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) metoder definiera hur din provider stöder den `Remove-ItemProperty` cmdlet. Denna cmdlet gör att användaren kan ta bort en egenskap och dess värde.

- Den [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) och [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) metoder definiera hur din provider stöder den `Rename-ItemProperty` cmdlet. Denna cmdlet gör att användaren kan ändra namnet på en egenskap.

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-providern](./writing-a-windows-powershell-provider.md)