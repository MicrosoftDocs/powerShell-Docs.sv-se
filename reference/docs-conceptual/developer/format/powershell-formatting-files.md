---
title: Filer för Windows PowerShell-formatering | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355932"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell-formateringsfiler

Windows PowerShell innehåller flera formateringsattribut (. format. ps1xml) som finns i installations katalogen (`$pshome`). Var och en av dessa filer definierar standard visningen för en bestämd uppsättning .NET-objekt. De här filerna ska aldrig ändras. Du kan dock använda dem som referens för att skapa egna filer för anpassade filer.

`Certificate.Format.ps1xml` definierar visningen av objekt i certifikat arkivet, till exempel x. 509-certifikat och certifikat arkiv.

`DotNetTypes.Format.ps1xml` definierar visningen av diverse .NET-objekt som CultureInfo, FileVersionInfo och EventLogEntry-objekt.

`FileSystem.Format.ps1xml` definierar visningen av fil system objekt, till exempel fil-och katalog objekt.

`Help.Format.ps1xml` definierar de olika vyer som används av cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) , till exempel vyerna detaljerad, fullständig, parameter och exempel.

`PowerShellCore.Format.ps1xml` definierar visningen av objekt som skapats av Windows PowerShell Core-cmdletar, till exempel de objekt som returneras av cmdletarna [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) och [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) .

`PowerShellTrace.Format.ps1xml` definierar visningen av spårnings objekt, till exempel de som genereras av cmdleten [trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) .

`Registry.Format.ps1xml` definierar visningen av register objekt, till exempel nyckel-och post objekt.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
