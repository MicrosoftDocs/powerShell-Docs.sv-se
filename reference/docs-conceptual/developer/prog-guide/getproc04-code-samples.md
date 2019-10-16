---
title: GetProc04-kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352642"
---
# <a name="getproc04-code-samples"></a>GetProc04 – kodexempel

Här är kod exemplen för GetProc04-exempel-cmdleten. Detta är `Get-Process`-cmdlet-exemplet som beskrivs i [lägga till ej avslutande fel rapportering till din cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md). Denna `Get-Process`-cmdlet anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) när ett ogiltigt åtgärds undantag genereras vid hämtning av process information.

> [!NOTE]
> Du kan ladda ned C# käll filen (getprov04.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .

Fullständig exempel kod finns i följande avsnitt.

|Språk|Ämne|
|--------------|-----------|
|C#|[GetProc04 (C#) exempel kod](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 (VB.NET) exempel kod](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>Se även

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)