---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell-formateringsfiler
description: Windows PowerShell-formateringsfiler
ms.openlocfilehash: 7fa58a3463dc4b2a23d38d161d83387744334d44
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666373"
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
