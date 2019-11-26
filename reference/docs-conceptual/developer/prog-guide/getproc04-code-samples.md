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
ms.openlocfilehash: 8326d1f47ce07698f09ade9ba97154ecc358465a
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417451"
---
# <a name="getproc04-code-samples"></a>GetProc04 – kodexempel

Här är kod exemplen för GetProc04-exempel-cmdleten. Detta är `Get-Process` cmdlet-exemplet som beskrivs i [lägga till fel rapportering som inte avslutas till din cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md). Den här `Get-Process` cmdleten anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) när ett ogiltigt åtgärds undantag genereras vid hämtning av process information.

> [!NOTE]
> Du kan ladda ned C# käll filen (getprov04.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .

Fullständig exempel kod finns i följande avsnitt.

|Språk|Avsnitt|
|--------------|-----------|
|C#|[GetProc04 (C#) exempel kod](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 (VB.NET) exempel kod](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>Se även

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
