---
title: Provider-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844802"
---
# <a name="provider-samples"></a>Providerexempel

Det här avsnittet innehåller exempel på över providers som kommer åt Microsoft Access-databas. De här exemplen omfattar providerklasserna som härleds från alla grundläggande providerklasser.

## <a name="in-this-section"></a>I detta avsnitt

Det här avsnittet innehåller följande ämnen:

[AccessDBProviderSample01 exempel](./accessdbprovidersample01.md) i det här exemplet visar hur du deklarera providerklass som härleds direkt från den [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klass. Det är här ingår endast för fullständighetens skull.

[AccessDBProviderSample02](./accessdbprovidersample02.md) det här exemplet visas hur du skriver över den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) och [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metoder som stöder anrop till den `New-PSDrive` och `Remove-PSDrive` cmdletar. Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klass.

[AccessDBProviderSample03](./accessdbprovidersample03.md) det här exemplet visas hur du skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoder som stöder anrop till den `Get-Item` och `Set-Item` cmdletar. Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.

[AccessDBProviderSample04](./accessdbprovidersample04.md) det här exemplet visas hur du skriver över behållare metoder för att stödja anrop till den `Copy-Item`, `Get-ChildItem`, `New-Item`, och `Remove-Item` cmdletar. Dessa metoder bör implementeras när datalagret innehåller objekt som är behållare. En behållare är en grupp med underordnade objekt under en gemensam överordnad artikel. Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klass.

[AccessDBProviderSample05](./accessdbprovidersample05.md) det här exemplet visas hur du skriver över behållare metoder för att stödja anrop till den `Move-Item` och `Join-Path` cmdletar. Dessa metoder bör implementeras när användaren behöver för att flytta objekt i en behållare och om datalagret innehåller kapslade behållare. Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass.

[AccessDBProviderSample06](./accessdbprovidersample06.md) det här exemplet visas hur du skriver över innehåll metoder för att stödja anrop till den `Clear-Content`, `Get-Content`, och `Set-Content` cmdletar. Dessa metoder bör implementeras när användaren behöver för att hantera innehåll över hur objekten i datalagret. Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass och det implementerar den [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) gränssnitt.

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-providern](./writing-a-windows-powershell-provider.md)