---
description: Beskriver hur du kommer åt objekt från arbets platsen i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: 77a6d7676e08c9a8c67fed38423406eddf004300
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271173"
---
# <a name="about_locations"></a>about_Locations

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver hur du kommer åt objekt från arbets platsen i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Den aktuella arbets platsen är standard platsen som kommando punkten används för.
Detta är alltså den plats som PowerShell använder om du inte anger en explicit sökväg till objektet eller platsen som påverkas av kommandot. I de flesta fall är den aktuella arbets platsen en enhet som nås via PowerShell-filsystem-providern och, i vissa fall, en katalog på den enheten.
Du kan till exempel ange den aktuella arbets platsen till följande plats:

```powershell
C:\Program Files\Windows PowerShell
```

Därför bearbetas alla kommandon från den här platsen om inte en annan sökväg uttryckligen anges.

PowerShell behåller den aktuella arbets platsen för varje enhet även om enheten inte är den aktuella enheten. På så sätt kan du komma åt objekt från den aktuella arbets platsen genom att bara referera till enheten på en annan plats.
Anta till exempel att din aktuella arbets plats är C: \\ Windows. Anta nu att du använder följande kommando för att ändra den aktuella arbets platsen till HKLM: Drive:

```powershell
Set-Location HKLM:
```

Även om din aktuella plats nu är register enheten, kan du fortfarande komma åt objekt i C: \\ Windows-katalogen genom att använda enheten c:, som visas i följande exempel:

```powershell
Get-ChildItem C:
```

PowerShell kommer att bli medlem i den aktuella arbets platsen för den enheten, så att den hämtar objekt från den katalogen. Resultatet blir detsamma om du körde följande kommando:

```powershell
Get-ChildItem C:\Windows
```

I PowerShell kan du använda kommandot Get-Location för att fastställa den aktuella arbets platsen och du kan använda kommandot Set-Location för att ange den aktuella arbets platsen. Följande kommando anger till exempel den aktuella arbets platsen till Windows-katalogen för enhet C:

```powershell
Set-Location c:\windows
```

När du har angett den aktuella arbets platsen kan du fortfarande komma åt objekt från andra enheter genom att inkludera enhets namnet (följt av ett kolon) i kommandot, som du ser i följande exempel:

```powershell
Get-ChildItem HKLM:\software
```

Exempel kommandot hämtar en lista över objekt i program varu behållaren för den lokala datahive-datorns Hive i registret.

Med PowerShell kan du också använda specialtecken för att representera den aktuella arbets platsen och dess överordnade plats. Använd en enda period för att representera den aktuella arbets platsen. Om du vill visa den överordnade platsen för den aktuella arbets platsen, använder du två punkter. Följande anger till exempel system-underkatalogen på den aktuella arbets platsen:

```powershell
Get-ChildItem .\system
```

Om den aktuella arbets platsen är C: \\ Windows returnerar det här kommandot en lista över alla objekt i C: \\ Windows- \\ systemet. Men om du använder två perioder används den överordnade katalogen i den aktuella arbets katalogen, som visas i följande exempel:

```powershell
Get-ChildItem ..\"program files"
```

I det här fallet behandlar PowerShell de två perioderna som C: Drive, så kommandot hämtar alla objekt i katalogen C: \\ Program Files.

En sökväg som börjar med ett snedstreck identifierar en sökväg från roten på den aktuella enheten. Om din aktuella arbets plats till exempel är C: \\ program \\ PowerShell, är roten på enheten C. Därför visar följande kommando alla objekt i C: \\ Windows-katalogen:

```powershell
Get-ChildItem \windows
```

Om du inte anger en sökväg som börjar med ett enhets namn, ett snedstreck eller en punkt när du anger namnet på en behållare eller ett objekt, förutsätts behållaren eller objektet vara placerat på den aktuella arbets platsen. Om din aktuella arbets plats exempelvis är C: \\ Windows, returnerar följande kommando alla objekt i katalogen C: \\ Windows \\ system:

```powershell
Get-ChildItem system
```

Om du anger ett fil namn i stället för ett katalog namn returnerar PowerShell information om filen (förutsatt att filen finns på den aktuella arbets platsen).

## <a name="see-also"></a>SE ÄVEN

[Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)

[about_Providers](about_Providers.md)

[about_Path_Syntax](about_Path_Syntax.md)
