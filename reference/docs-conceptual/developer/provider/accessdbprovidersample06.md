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
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356856"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Det här exemplet visar hur du skriver över innehålls metoder för att stödja anrop till `Clear-Content`-, `Get-Content`-och `Set-Content`-cmdletar. Dessa metoder bör implementeras när användaren behöver hantera innehållet i objekten i data lagret. Provider-klassen i det här exemplet härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) och implementerar gränssnittet [system. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

## <a name="demonstrates"></a>Visat

> [!IMPORTANT]
> Din leverantörs klass kommer förmodligen att härledas från någon av följande klasser och kan eventuellt implementera andra Provider-gränssnitt:
>
> -   Klassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Se [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   Klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Se [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   Klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .
>
> Mer information om hur du väljer vilken leverantörs klass som ska härledas från baserat på funktioner i providern finns i [utforma din Windows PowerShell-Provider](./provider-types.md).

Det här exemplet demonstrerar följande:

- Deklarerar attributet `CmdletProvider`.

- Definiera en leverantörs klass som härleds från klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) och som deklarerar [system. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -gränssnittet.

- Skriv över metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) för att ändra beteendet för `Clear-Content`-cmdleten, så att användaren kan ta bort innehållet från ett objekt. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Clear-Content`-cmdleten.)

- Skriv över metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) för att ändra beteendet för `Get-Content`-cmdleten, så att användaren kan hämta innehållet i ett objekt. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Get-Content`-cmdlet.).

- Skriv över metoden [Microsoft. PowerShell. commands. Filesystemprovider. Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) för att ändra beteendet för `Set-Content`-cmdleten, så att användaren kan uppdatera innehållet i ett objekt. (Det här exemplet visar inte hur du lägger till dynamiska parametrar i `Set-Content`-cmdleten.)

## <a name="example"></a>Exempel

Det här exemplet visar hur du skriver över de metoder som behövs för att rensa, hämta och ange innehållet i objekt i en Microsoft Access-databas.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Se även

[System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Designa din Windows PowerShell-Provider](./provider-types.md)
