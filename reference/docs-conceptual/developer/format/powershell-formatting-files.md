---
title: Filer för Windows PowerShell-formatering | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 54fae12163f8d439c2acc24df17ed140a556cba0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783508"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell-formateringsfiler

Windows PowerShell innehåller flera formateringsattribut (.format.ps1XML) som finns i installations katalogen ( `$pshome` ). Var och en av dessa filer definierar standard visningen för en bestämd uppsättning .NET-objekt. De här filerna ska aldrig ändras. Du kan dock använda dem som referens för att skapa egna filer för anpassade filer.

`Certificate.Format.ps1xml` Definierar visning av objekt i certifikat arkivet, till exempel x. 509-certifikat och certifikat arkiv.

`DotNetTypes.Format.ps1xml` Definierar visning av andra .NET-objekt som CultureInfo, FileVersionInfo och EventLogEntry-objekt.

`FileSystem.Format.ps1xml` Definierar visning av fil system objekt, till exempel fil-och katalog objekt.

`Help.Format.ps1xml` Definierar de olika vyer som används av [Get-Help-](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdleten, till exempel vyerna detaljerad, fullständig, parameter och exempel.

`PowerShellCore.Format.ps1xml` Definierar visning av objekt som genererats av Windows PowerShell Core-cmdletar, till exempel de objekt som returneras av cmdletarna [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) och [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) .

`PowerShellTrace.Format.ps1xml` Definierar visning av spårnings objekt, till exempel de som genereras av cmdleten [trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) .

`Registry.Format.ps1xml` Definierar visning av register objekt, till exempel nyckel-och post objekt.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
