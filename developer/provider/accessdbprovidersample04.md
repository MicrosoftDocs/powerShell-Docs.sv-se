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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057628"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Det här exemplet visas hur du skriver över behållare metoder för att stödja anrop till den `Copy-Item`, `Get-ChildItem`, `New-Item`, och `Remove-Item` cmdletar. Dessa metoder bör implementeras när datalagret innehåller objekt som är behållare. En behållare är en grupp med underordnade objekt under en gemensam överordnad artikel. Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klass.

## <a name="demonstrates"></a>Visar

> [!IMPORTANT]
> Din providerklass kommer troligen härleds från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Detta exempel visar följande:

- Deklarera de `CmdletProvider` attribut.

- Definiera en providerklass som härleds från den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klass.

- Skriver över den [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metod för att ändra funktionssättet för den `Copy-Item` cmdlet som används att kopiera objekt från en plats till en annan. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Copy-Item` cmdlet: en.)

- Skriver över den [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod för att ändra funktionssättet för cmdleten Get-ChildItems, vilket gör att användaren kan hämta de underordnade objekten i den överordnade artikeln . (Det här exemplet visar inte hur du lägger till dynamiska parametrar för cmdleten Get-ChildItems.)

- Skriver över den [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metod för att ändra funktionssättet för cmdleten Get-ChildItems när den `Name` parametern för cmdlet har angetts.

- Skriver över den [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metod för att ändra funktionssättet för den `New-Item` cmdleten, som gör att användaren kan lägga till objekt i datalagret. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `New-Item` cmdlet: en.)

- Skriver över den [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metod för att ändra funktionssättet för den `Remove-Item` cmdlet. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Remove-Item` cmdlet: en.)

## <a name="example"></a>Exempel

Detta exempel visar hur du skriver över de metoder som krävs för att kopiera, skapa och ta bort objekt samt metoder för att hämta underordnat objekt för en överordnad artikel.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Se även

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Designa din Windows PowerShell-providern](./provider-types.md)