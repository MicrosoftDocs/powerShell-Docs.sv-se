---
title: Windows PowerShell formatering filer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 49344d32dfcef36a904772b4a7237646a63cb12a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065390"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell-formateringsfiler

Windows PowerShell innehåller flera formatering filer (. format.ps1xml) som finns i installationskatalogen (`$pshome`). Var och en av de här filerna definierar standardvisningen för en specifik uppsättning .NET-objekt. De här filerna ska aldrig ändras. Du kan dock använda dem som en referens för att skapa en egen anpassad formatering filer.

Certificate.Format.ps1xml definierar visning av objekt i arkivet, till exempel x.509-certifikat och certifikatarkiv.

DotNetTypes.Format.ps1xml definierar visningen av diverse .NET-objekt, till exempel CultureInfo och FileVersionInfo EventLogEntry objekt.

FileSystem.Format.ps1xml definierar visningen av filsystemsobjekt, till exempel fil- och objekt.

Help.Format.ps1xml definierar olika vyer som används av den [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet, till exempel detaljerade vyer för fullständig, parametrar och exempel.

PowerShellCore.Format.ps1xml definierar visningen av de objekt som genereras av Windows PowerShell core-cmdletar, till exempel objekten som returneras av den [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) och [Get-historik](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdletar.

PowerShellTrace.Format.ps1xml definierar visningen av spårningsobjekt, till exempel de som genererats av den [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.

Registry.Format.ps1xml definierar visning av registret objekt, till exempel nyckeln och post-objekt.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
