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
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849198"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Det här exemplet visas hur du skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) och [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoder för att stödja anrop till den `Get-Item` och `Set-Item` cmdletar. Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.

## <a name="demonstrates"></a>Visar

> [!IMPORTANT]
> Din providerklass kommer troligen härleder från en av följande klasser och eventuellt implementera andra provider-gränssnitt:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class. Se [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass. Se [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Mer information om hur du väljer vilken providerklass som härleds från baserat på provider-funktioner kan du läsa [designa din Windows PowerShell-providern](./provider-types.md).

Detta exempel visar följande:

- Deklarera de `CmdletProvider` attribut.

- Definiera en providerklass som härleds från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass.

- Skriver över den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metod för att ändra funktionssättet för den `New-PSDrive` cmdlet, där användaren kan skapa nya enheter. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `New-PSDrive` cmdlet: en.)

- Skriver över den [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metod för att stödja ta bort befintliga enheter.

- Skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metod för att ändra funktionssättet för den `Get-Item` cmdlet, där användaren kan hämta objekt från datalagret. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Get-Item` cmdlet: en.)

- Skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metod för att ändra funktionssättet för den `Set-Item` cmdlet, så att användaren kan uppdatera objekt i datalagret. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Get-Item` cmdlet: en.)

- Skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metod för att ändra funktionssättet för den `Test-Path` cmdlet. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Test-Path` cmdlet: en.)

- Skriver över den [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metod för att avgöra om den angivna sökvägen är giltig.

## <a name="example"></a>Exempel

Detta exempel visar hur du skriver över de metoder som krävs för att hämta och ange objekt i en Microsoft Access-data.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Se även

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Designa din Windows PowerShell-providern](./provider-types.md)