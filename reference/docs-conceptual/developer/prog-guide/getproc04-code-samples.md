---
title: GetProc04-kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b90b7e96c1454e57df93863b526758f25d9be690
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771965"
---
# <a name="getproc04-code-samples"></a>GetProc04 – kodexempel

Här är kod exemplen för GetProc04-exempel-cmdleten. Detta är det `Get-Process` cmdlet-exempel som beskrivs i [lägga till fel rapportering som inte avslutas till din cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md). Den här `Get-Process` cmdleten anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) när ett ogiltigt åtgärds undantag genereras vid hämtning av process information.

> [!NOTE]
> Du kan hämta C#-källfilen (getprov04.cs) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.

Fullständig exempel kod finns i följande avsnitt.

|Språk|Avsnitt|
|--------------|-----------|
|C#|[GetProc04 (C#) – kodexempel](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 (VB.NET) – kodexempel](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
