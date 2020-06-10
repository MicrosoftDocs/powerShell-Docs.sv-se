---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 86daab97236ca4be94669f107d5a03abea6f6c91
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633404"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Det här exemplet visar hur du skriver över [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoder för att stödja anrop till `Get-Item` `Set-Item` cmdletarna och. Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

## <a name="demonstrates"></a>Demonstrationer

> [!IMPORTANT]
> Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:
>
> - Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .
> - Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Se [AccessDBProviderSample04](./accessdbprovidersample04.md).
> - Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Se [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).

Det här exemplet demonstrerar följande:

- Attributet deklareras `CmdletProvider` .
- Definiera en leverantörs klass som härleds från klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .
- Skriv över metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) för att ändra beteendet för `New-PSDrive` cmdleten, så att användaren kan skapa nya enheter.
  (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `New-PSDrive` cmdleten.)
- Skriva över metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) för att stödja borttagning av befintliga enheter.
- Skriv över metoden [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) för att ändra beteendet för `Get-Item` cmdleten, så att användaren kan hämta objekt från data lagret. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Get-Item` cmdleten.)
- Skriv över metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) för att ändra beteendet för `Set-Item` cmdleten, så att användaren kan uppdatera objekten i data lagret. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Get-Item` cmdleten.)
- Skriv över metoden [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) för att ändra funktions sättet för `Test-Path` cmdleten. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Test-Path` cmdleten.)
- Skriv över metoden [system. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) för att avgöra om den angivna sökvägen är giltig.

## <a name="example"></a>Exempel

Det här exemplet visar hur du skriver över de metoder som behövs för att hämta och ange objekt i en Microsoft Access-databas.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs" range="11-976":::

## <a name="see-also"></a>Se även

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Designa en Windows PowerShell-provider](./provider-types.md)
