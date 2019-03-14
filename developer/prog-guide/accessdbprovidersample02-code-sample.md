---
title: AccessDbProviderSample02 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795495"
---
# <a name="accessdbprovidersample02-code-sample"></a>AccessDbProviderSample02 – kodexempel

Följande kod visar implementeringen av Windows PowerShell-providern som beskrivs i [skapar en Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md). Den här implementeringen skapar en sökväg, ansluter till en Access-databas och sedan tar bort enheten.

> [!NOTE]
> Du kan ladda ned den C# källfilen (AccessDBSampleProvider02.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.
>
> Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Kodexempel

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)