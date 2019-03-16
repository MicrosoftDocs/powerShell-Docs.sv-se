---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055554"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Det här exemplet visas hur du skriver över innehåll metoder för att stödja anrop till den `Clear-Content`, `Get-Content`, och `Set-Content` cmdletar. Dessa metoder bör implementeras när användaren behöver för att hantera innehåll över hur objekten i datalagret. Providerklass i det här exemplet kommer från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass och det implementerar den [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) gränssnitt.

## <a name="demonstrates"></a>Visar

> [!IMPORTANT]
> Din providerklass kommer troligen härleder från en av följande klasser och eventuellt implementera andra provider-gränssnitt:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klass. Se [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class. Se [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass.
>
> Mer information om hur du väljer vilken providerklass som härleds från baserat på provider-funktioner kan du läsa [designa din Windows PowerShell-providern](./provider-types.md).

Detta exempel visar följande:

- Deklarera de `CmdletProvider` attribut.

- Definiera en providerklass som härleds från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klass och som förklarar den [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) gränssnitt.

- Skriver över den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metod för att ändra funktionssättet för den `Clear-Content` cmdlet, där användaren kan ta bort innehållet från ett objekt. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Clear-Content` cmdlet: en.)

- Skriver över den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metod för att ändra funktionssättet för den `Get-Content` cmdlet, så att användaren att hämta innehållet i ett objekt. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Get-Content` cmdlet: en.).

- Skriver över den [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) metod för att ändra funktionssättet för den `Set-Content` cmdlet, så att användaren att uppdatera innehållet i ett objekt. (Det här exemplet visar inte hur du lägger till dynamiska parametrar till den `Set-Content` cmdlet: en.)

## <a name="example"></a>Exempel

Detta exempel visar hur du skriver över de metoder som krävs för att rensa, hämta och ange innehållet för objekt i en Microsoft Access-data.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Se även

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Designa din Windows PowerShell-providern](./provider-types.md)