---
title: Provider-exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9eb8eb64bbe585ebd8024c0215853ff04a5c3e54
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778442"
---
# <a name="provider-samples"></a>Providerexempel

Det här avsnittet innehåller exempel på leverantörer som har åtkomst till en Microsoft Access-databas. Dessa exempel innehåller leverantörs klasser som härleds från alla bas leverantörs klasser.

## <a name="in-this-section"></a>I det här avsnittet

Det här avsnittet innehåller följande ämnen:

[AccessDBProviderSample01-exempel](./accessdbprovidersample01.md) Det här exemplet visar hur du deklarerar Provider-klassen som härleds direkt från klassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Den ingår bara här för fullständighet.

[AccessDBProviderSample02](./accessdbprovidersample02.md) Det här exemplet visar hur du skriver över [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoder för att stödja anrop till `New-PSDrive` `Remove-PSDrive` cmdletarna och. Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .

[AccessDBProviderSample03](./accessdbprovidersample03.md) Det här exemplet visar hur du skriver över [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoder för att stödja anrop till `Get-Item` `Set-Item` cmdletarna och. Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

[AccessDBProviderSample04](./accessdbprovidersample04.md) Det här exemplet visar hur du skriver över container metoder för att stödja anrop `Copy-Item` till `Get-ChildItem` `New-Item` cmdletarna,, och `Remove-Item` . Dessa metoder bör implementeras när data lagret innehåller objekt som är behållare. En behållare är en grupp underordnade objekt under ett gemensamt överordnat objekt. Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

[AccessDBProviderSample05](./accessdbprovidersample05.md) Det här exemplet visar hur du skriver över container metoder för att stödja anrop `Move-Item` till `Join-Path` cmdletarna och. Dessa metoder bör implementeras när användaren behöver flytta objekt i en behållare och om data lagret innehåller kapslade behållare. Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

[AccessDBProviderSample06](./accessdbprovidersample06.md) Det här exemplet visar hur du skriver över innehålls metoder för att stödja anrop `Clear-Content` till `Get-Content` `Set-Content` cmdletarna, och. Dessa metoder bör implementeras när användaren behöver hantera innehållet i objekten i data lagret. Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) och implementerar gränssnittet [system. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-provider](./writing-a-windows-powershell-provider.md)
