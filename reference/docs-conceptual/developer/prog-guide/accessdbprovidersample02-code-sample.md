---
title: AccessDbProviderSample02 kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ca7674ba5cff601394af4df20f0dda8794c14d22
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784817"
---
# <a name="accessdbprovidersample02-code-sample"></a>AccessDbProviderSample02 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapa en provider för Windows PowerShell-enheter](./creating-a-windows-powershell-drive-provider.md).
Den här implementeringen skapar en sökväg, skapar en anslutning till en Access-databas och tar sedan bort enheten.

> [!NOTE]
> Du kan hämta C#-källfilen (AccessDBSampleProvider02.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen. Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Kod exempel

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
