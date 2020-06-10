---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: c0efd10680d3323b6c8d932604176c4425e7266a
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633370"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Det här exemplet visar hur du skriver över container metoder för att stödja anrop `Copy-Item` till `Get-ChildItem` `New-Item` cmdletarna,, och `Remove-Item` . Dessa metoder bör implementeras när data lagret innehåller objekt som är behållare. En behållare är en grupp underordnade objekt under ett gemensamt överordnat objekt. Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

## <a name="demonstrates"></a>Demonstrationer

> [!IMPORTANT]
> Din leverantörs klass kommer förmodligen att härledas från [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Det här exemplet demonstrerar följande:

- Attributet deklareras `CmdletProvider` .
- Definiera en leverantörs klass som härleds från klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .
- Skriv över metoden [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) för att ändra beteendet för `Copy-Item` cmdleten, så att användaren kan kopiera objekt från en plats till en annan. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Copy-Item` cmdleten.)
- Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) för att ändra beteendet för Get-ChildItems-cmdleten, vilket gör att användaren kan hämta de underordnade objekten till det överordnade objektet. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till get-ChildItems-cmdlet: en.)
- Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) för att ändra beteendet för Get-ChildItems-cmdleten när `Name` parametern för cmdlet: en anges.
- Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) för att ändra beteendet för `New-Item` cmdleten, vilket gör att användaren kan lägga till objekt i data lagret. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `New-Item` cmdleten.)
- Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) för att ändra funktions sättet för `Remove-Item` cmdleten. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Remove-Item` cmdleten.)

## <a name="example"></a>Exempel

Det här exemplet visar hur du skriver över de metoder som behövs för att kopiera, skapa och ta bort objekt, samt metoder för att hämta underordnade objekt till ett överordnat objekt.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>Se även

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Designa en Windows PowerShell-provider](./provider-types.md)
