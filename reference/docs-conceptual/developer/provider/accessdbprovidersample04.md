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
ms.openlocfilehash: 7096f8066568c214a5902f6943a2c093932d3b56
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356863"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Det här exemplet visar hur du skriver över container metoder för att stödja anrop till `Copy-Item`-, `Get-ChildItem`-, `New-Item`-och `Remove-Item`-cmdletar. Dessa metoder bör implementeras när data lagret innehåller objekt som är behållare. En behållare är en grupp underordnade objekt under ett gemensamt överordnat objekt. Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

## <a name="demonstrates"></a>Visat

> [!IMPORTANT]
> Din leverantörs klass kommer förmodligen att härledas från [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Det här exemplet demonstrerar följande:

- Deklarerar attributet `CmdletProvider`.

- Definiera en leverantörs klass som härleds från klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

- Skriv över metoden [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) för att ändra beteendet för `Copy-Item`-cmdleten, vilket gör att användaren kan kopiera objekt från en plats till en annan. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Copy-Item`-cmdleten.)

- Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) för att ändra beteendet för Get-ChildItems-cmdleten, vilket gör att användaren kan hämta de underordnade objekten till det överordnade objektet. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till get-ChildItems-cmdlet: en.)

- Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) för att ändra beteendet för Get-ChildItems-cmdleten när parametern `Name` för cmdleten har angetts.

- Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) för att ändra beteendet för `New-Item`-cmdleten, vilket gör att användaren kan lägga till objekt i data lagret. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `New-Item`-cmdleten.)

- Skriv över metoden [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) för att ändra beteendet för `Remove-Item`-cmdleten. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Remove-Item`-cmdleten.)

## <a name="example"></a>Exempel

Det här exemplet visar hur du skriver över de metoder som behövs för att kopiera, skapa och ta bort objekt, samt metoder för att hämta underordnade objekt till ett överordnat objekt.

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Se även

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Designa din Windows PowerShell-Provider](./provider-types.md)
