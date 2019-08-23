---
title: Typer av leverantörer | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986661"
---
# <a name="provider-types"></a>Typer av providers

Providers definierar de grundläggande funktionerna genom att ändra hur providerns cmdlets, som tillhandahålls av PowerShell, utför sina åtgärder. Leverantörer kan till exempel använda standardfunktionaliteten för `Get-Item` cmdleten, eller så kan de ändra hur cmdleten fungerar när objekt hämtas från data lagret. Leverantörs funktionen som beskrivs i det här dokumentet innehåller funktioner som definieras genom att skriva över metoder från vissa providers bas klasser och gränssnitt.

> [!NOTE]
> För leverantörs funktioner som är fördefinierade i PowerShell, se [leverantörs funktioner](/previous-versions//ee126189(v=vs.85)).

## <a name="drive-enabled-providers"></a>Enhets aktiverade providrar

Enhets aktiverade providers anger de standard enheter som är tillgängliga för användaren och låter användaren lägga till eller ta bort enheter. I de flesta fall är providers enhets aktiverade providrar eftersom de kräver viss standardenhet för att få åtkomst till data lagret. Men när du skriver din egen Provider kanske du inte vill att användaren ska kunna skapa och ta bort enheter.

Om du vill skapa en enhets aktive rad Provider måste din leverantörs klass härledas från klassen [system. Management. Automation. Provider. DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) eller en annan klass som är härledd från den klassen. Klassen **system. Management. Automation. Provider. DriveCmdletProvider** definierar följande metoder för att implementera standard enheterna för providern och stöd `New-PSDrive` för-och `Remove-PSDrive` -cmdlets. I de flesta fall, för att stödja en provider-cmdlet måste du skriva över metoden som PowerShell-motorn anropar för att anropa cmdleten `NewDrive` , till exempel `New-PSDrive` metoden för cmdleten och eventuellt skriva över en `NewDriveDynamicParameters` andra metod, till exempel , för att lägga till dynamiska parametrar till cmdleten.

- Metoden [system. Management. Automation. Provider. DriveCmdletProvider. InitializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) definierar de standard enheter som är tillgängliga för användaren varje gång som providern används.

- Metoderna [system. Management. Automation. Provider. DriveCmdletProvider. NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. DriveCmdletProvider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) definierar hur providern stöder `New-PSDrive`Provider-cmdlet. Med den här cmdleten kan användaren skapa enheter för att få åtkomst till data lagret.

- Metoden [system. Management. Automation. Provider. DriveCmdletProvider. RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) definierar hur providern stöder `Remove-PSDrive` Provider-cmdleten. Med den här cmdleten kan användaren ta bort enheter från data lagret.

## <a name="item-enabled-providers"></a>Objekt aktiverade providers

Med objekt aktiverade providers kan användaren hämta, ange eller Rensa objekten i data lagret. Ett "objekt" är ett element i data lagret som användaren kan komma åt eller hantera separat. Om du vill skapa en objekt aktive rad Provider måste din leverantörs klass vara härledd från klassen [system. Management. Automation. Provider. ItemCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) eller en annan klass som är härledd från den klassen.

Klassen **system. Management. Automation. Provider. ItemCmdletProvider** definierar följande metoder för att implementera vissa Provider-cmdletar. I de flesta fall, för att stödja en provider-cmdlet måste du skriva över metoden som PowerShell-motorn anropar för att anropa cmdleten `ClearItem` , till exempel `Clear-Item` metoden för cmdleten och eventuellt skriva över en `ClearItemDynamicParameters` andra metod, till exempel , för att lägga till dynamiska parametrar till cmdleten.

- Metoderna [system. Management. Automation. Provider. ItemCmdletProvider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) och [system. Management. Automation. Provider. ItemCmdletProvider. ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) definierar hur providern stöder `Clear-Item`Provider-cmdlet. Med den här cmdleten kan användaren ta bort värdet för ett objekt i data lagret.

- Metoderna [system. Management. Automation. Provider. ItemCmdletProvider. getItem,](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [system. Management. Automation. Provider. ItemCmdletProvider. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) definierar hur `Get-Item` providern stöder Provider-cmdlet. Med den här cmdleten kan användaren hämta data från data lagret.

- Metoderna [system. Management. Automation. Provider. ItemCmdletProvider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) och [system. Management. Automation. Provider. ItemCmdletProvider. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) definierar hur `Set-Item` providern stöder Provider-cmdlet. Med den här cmdleten kan användaren uppdatera värdena för objekt i data lagret.

- Metoderna [system. Management. Automation. Provider. Itemcmdletprovider. InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) och [system. Management. Automation. Provider. Itemcmdletprovider. InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) definierar hur din Provider `Invoke-Item` stöder Provider-cmdleten. Med den här cmdleten kan användaren utföra standard åtgärden som anges av objektet.

- Metoderna [system. Management. Automation. Provider. ItemCmdletProvider. ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) och [system. Management. Automation. Provider. ItemCmdletProvider. ItemExistsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) definierar hur providern stöder `Test-Path`Provider-cmdlet. Med den här cmdleten kan användaren avgöra om alla element i en sökväg finns.

Förutom de metoder som används för att implementera Provider-cmdletar definierar klassen **system. Management. Automation. Provider. ItemCmdletProvider** även följande metoder:

- Metoden [system. Management. Automation. Provider. ItemCmdletProvider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) gör att användaren kan använda jokertecken när du anger sökvägen till providern.

- [System. Management. Automation. Provider. ItemCmdletProvider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) används för att avgöra om en sökväg är syntaktiskt och semantiskt giltig för providern.

## <a name="container-enabled-providers"></a>Behållare-aktiverade providrar

Med container-aktiverade providers kan användaren hantera objekt som är behållare. En behållare är en grupp underordnade objekt under ett gemensamt överordnat objekt. Om du vill skapa en container-aktiverad Provider måste din leverantörs klass härledas från klassen [system. Management. Automation. Provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) eller en annan klass som är härledd från den klassen.

> [!IMPORTANT]
> Container-aktiverade providrar kan inte komma åt data lager som innehåller kapslade behållare. Om ett underordnat objekt till en behållare är en annan behållare måste du implementera en navigerings aktive rad Provider.

Klassen **system. Management. Automation. Provider. ContainerCmdletProvider** definierar följande metoder för att implementera vissa Provider-cmdletar. I de flesta fall, för att stödja en provider-cmdlet måste du skriva över metoden som PowerShell-motorn anropar för att anropa cmdleten `CopyItem` , till exempel `Copy-Item` metoden för cmdleten och eventuellt skriva över en `CopyItemDynamicParameters` andra metod, till exempel , för att lägga till dynamiska parametrar till cmdleten.

- Metoderna [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) och [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) definierar hur providern stöder `Copy-Item` Provider-cmdlet. Med den här cmdleten kan användaren kopiera ett objekt från en plats till en annan.

- Metoderna [system. Management. Automation. Provider. ContainerCmdletProvider. GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) och [system. Management. Automation. Provider. ContainerCmdletProvider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) definierar hur din Provider `Get-ChildItem` stöder Provider-cmdleten. Med den här cmdleten kan användaren hämta de underordnade objekten till det överordnade objektet.

- Metoderna [system. Management. Automation. Provider. ContainerCmdletProvider. GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) och [system. Management. Automation. Provider. ContainerCmdletProvider. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) definierar hur din Provider stöder Provider-cmdleten om `Name` dess parameter har angetts. `Get-ChildItem`

- Metoderna [system. Management. Automation. Provider. ContainerCmdletProvider. NewItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) och [system. Management. Automation. Provider. ContainerCmdletProvider. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) definierar hur providern stöder `New-Item` Provider-cmdlet. Med den här cmdleten kan användaren skapa nya objekt i data lagret.

- Metoderna [system. Management. Automation. Provider. ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) och [system. Management. Automation. Provider. ContainerCmdletProvider. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) definierar hur providern stöder `Remove-Item` Provider-cmdlet. Med den här cmdleten kan användaren ta bort objekt från data lagret.

- Metoderna [system. Management. Automation. Provider. ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) och [system. Management. Automation. Provider. ContainerCmdletProvider. RenameItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) definierar hur providern stöder `Rename-Item` Provider-cmdlet. Med den här cmdleten kan användaren byta namn på objekt i data lagret.

Förutom de metoder som används för att implementera Provider-cmdletar definierar klassen **system. Management. Automation. Provider. ContainerCmdletProvider** även följande metoder:

- Metoden [system. Management. Automation. Provider. ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) kan användas av Provider-klassen för att avgöra om ett objekt har underordnade objekt.

- Metoden [system. Management. Automation. Provider. ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) kan användas av Provider-klassen för att skapa en ny provider-specifik sökväg från en angiven sökväg.

## <a name="navigation-enabled-providers"></a>Navigerings aktiverade providers

Navigerings aktiverade providers gör det möjligt för användaren att flytta objekt i data lagret. Om du vill skapa en navigerings aktive rad Provider måste din leverantörs klass vara härledd från klassen [system. Management. Automation. Provider. NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

Klassen **system. Management. Automation. Provider. NavigationCmdletProvider** definierar följande metoder för att implementera vissa Provider-cmdletar. I de flesta fall, för att stödja en provider-cmdlet måste du skriva över metoden som PowerShell-motorn anropar för att anropa cmdleten `MoveItem` , till exempel `Move-Item` metoden för cmdleten och eventuellt skriva över en `MoveItemDynamicParameters` andra metod, till exempel , för att lägga till dynamiska parametrar till cmdleten.

- Metoderna [system. Management. Automation. Provider. NavigationCmdletProvider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) och [system. Management. Automation. Provider. NavigationCmdletProvider. MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) definierar hur providern stöder `Move-Item` Provider-cmdlet. Med den här cmdleten kan användaren flytta ett objekt från en plats i arkivet till en annan plats.

- Metoden [system. Management. Automation. Provider. NavigationCmdletProvider. MakePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) definierar hur providern stöder `Join-Path` Provider-cmdleten. Med den här cmdleten kan användaren kombinera ett överordnat och underordnat Sök vägs segment för att skapa en provider-intern sökväg.

Förutom de metoder som används för att implementera Provider-cmdletar definierar klassen **system. Management. Automation. Provider. NavigationCmdletProvider** även följande metoder:

- Metoden [system. Management. Automation. Provider. NavigationCmdletProvider. GetChildName](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) extraherar namnet på den underordnade noden i en sökväg.

- Metoden [system. Management. Automation. Provider. NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) hämtar den överordnade delen av en sökväg.

- Metoden [system. Management. Automation. Provider. NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) bestämmer om objektet är ett behållar objekt. I det här sammanhanget är en behållare en grupp med underordnade objekt under ett gemensamt överordnat objekt.

- Metoden [system. Management. Automation. Provider. NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) returnerar en sökväg till ett objekt som är relaterat till en angiven bas Sök väg.

## <a name="content-enabled-providers"></a>Innehålls aktiverade providers

Med innehålls aktiverade providers kan användaren rensa, hämta eller ange innehållet i ett data lager.
Med fil uppsättnings leverantören kan du till exempel rensa, hämta och ange innehållet i filer i fil systemet. Om du vill skapa en innehålls aktive rad Provider måste din leverantörs klass implementera metoderna i [system. Management. Automation. Provider. IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -gränssnittet.

Gränssnittet **system. Management. Automation. Provider. IContentCmdletProvider** definierar följande metoder för att implementera vissa Provider-cmdletar. I de flesta fall, för att stödja en provider-cmdlet måste du skriva över metoden som PowerShell-motorn anropar för att anropa cmdleten `ClearContent` , till exempel `Clear-Content` metoden för cmdleten och eventuellt skriva över en `ClearContentDynamicParameters` andra metod, till exempel , för att lägga till dynamiska parametrar till cmdleten.

- Metoderna [system. Management. Automation. Provider. IContentCmdletProvider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) och [system. Management. Automation. Provider. IContentCmdletProvider. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) definierar hur din provider stöder `Clear-Content` Provider-cmdleten. Med den här cmdleten kan användaren ta bort innehållet i ett objekt utan att ta bort objektet.

- Metoderna [system. Management. Automation. Provider. IContentCmdletProvider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) och [system. Management. Automation. Provider. IContentCmdletProvider. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) definierar hur din Provider `Get-Content` stöder Provider-cmdleten. Med den här cmdleten kan användaren hämta innehållet i ett objekt. Metoden returnerar ett [system. Management. Automation. Provider. IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader) -gränssnitt som definierar de metoder som används för att läsa innehållet. `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader`

- Metoderna [system. Management. Automation. Provider. IContentCmdletProvider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) och [system. Management. Automation. Provider. IContentCmdletProvider. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) definierar hur din Provider `Set-Content` stöder Provider-cmdleten. Med den här cmdleten kan användaren uppdatera innehållet i ett objekt. Metoden returnerar ett [system. Management. Automation. Provider. IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) -gränssnitt som definierar de metoder som används för att skriva innehållet. `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter`

## <a name="property-enabled-providers"></a>Egenskaps-aktiverade providrar

Egenskaps-aktiverade providers gör att användaren kan hantera egenskaperna för objekten i data lagret.
Om du vill skapa en egenskaps aktive rad Provider måste din leverantörs klass implementera metoderna i [system. Management. Automation. Provider. IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) och [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)gränssnitt. I de flesta fall, för att stödja en provider-cmdlet måste du skriva över metoden som PowerShell-motorn anropar för att anropa cmdleten `ClearProperty` , till exempel metoden för cmdleten Clear-Property och eventuellt skriva över en andra metod, `ClearPropertyDynamicParameters` till exempel , för att lägga till dynamiska parametrar till cmdleten.

Gränssnittet **system. Management. Automation. Provider. IPropertyCmdletProvider** definierar följande metoder för att implementera vissa Provider-cmdlet: ar:

- Metoderna [system. Management. Automation. Provider. IPropertyCmdletProvider. ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) och [system. Management. Automation. Provider. IPropertyCmdletProvider. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) definierar hur din Provider `Clear-ItemProperty` stöder Provider-cmdleten. Med den här cmdleten kan användaren ta bort värdet för en egenskap.

- Metoderna [system. Management. Automation. Provider. IPropertyCmdletProvider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) och [system. Management. Automation. Provider. IPropertyCmdletProvider. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) definierar hur providern stöder `Get-ItemProperty` Provider-cmdleten. Med den här cmdleten kan användaren hämta egenskapen för ett objekt.

- Metoderna [system. Management. Automation. Provider. IPropertyCmdletProvider. setProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) och [system. Management. Automation. Provider. IPropertyCmdletProvider. SetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) definierar hur providern stöder `Set-ItemProperty` Provider-cmdleten. Med den här cmdleten kan användaren uppdatera egenskaperna för ett objekt.

  Gränssnittet **system. Management. Automation. Provider. IDynamicPropertyCmdletProvider** definierar följande metoder för att implementera vissa Provider-cmdlet: ar:

- Metoderna [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) och [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) definierar hur providern stöder `Copy-ItemProperty` Provider-cmdleten. Med den här cmdleten kan användaren kopiera en egenskap och dess värde från en plats till en annan.

- Metoderna [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) och [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) definierar hur providern stöder `Move-ItemProperty` Provider-cmdleten. Med den här cmdleten kan användaren flytta en egenskap och dess värde från en plats till en annan.

- Metoderna [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) och [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) definierar hur providern stöder `New-ItemProperty` Provider-cmdleten. Med den här cmdleten kan användaren skapa en ny egenskap och ange dess värde.

- Metoderna [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) och [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) definierar hur din provider stöder `Remove-ItemProperty` cmdleten. Med den här cmdleten kan användaren ta bort en egenskap och dess värde.

- Metoderna [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) och [system. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) definierar hur din provider stöder `Rename-ItemProperty` cmdleten. Med den här cmdleten kan användaren ändra namnet på en egenskap.

## <a name="see-also"></a>Se även

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Skriva en Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)
