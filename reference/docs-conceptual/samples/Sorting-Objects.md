---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Sortera objekt
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030783"
---
# <a name="sorting-objects"></a>Sortera objekt

Vi kan organisera visade data för att göra det enklare att söka igenom dem `Sort-Object` med hjälp av cmdleten. `Sort-Object`tar namnet på en eller flera egenskaper att sortera på och returnerar data sorterade efter värdena för dessa egenskaper.

## <a name="basic-sorting"></a>Grundläggande sortering

Ta hänsyn till problemet med att lista under kataloger och filer i den aktuella katalogen.
Om vi vill sortera efter **LastWriteTime** och sedan efter **namn**, kan vi göra det genom att skriva:

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

Du kan också sortera objekten i omvänd ordning genom att ange parametern för **fallande** växel.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>Använda hash-tabeller

Du kan sortera olika egenskaper i olika beställningar genom att använda hash-tabeller i en matris.
Varje hash-tabell använder en **uttrycks** nyckel för att ange egenskaps namnet som sträng och en **stigande** eller **fallande** nyckel för att ange sorterings ordningen efter `$true` eller `$false`.
**Uttrycks** nyckeln är obligatorisk.
Den **stigande** eller **fallande** nyckeln är valfri.

I följande exempel sorteras objekt i fallande **LastWriteTime** ordning och stigande **namn** ordning.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

Du kan också ange en script block till **uttrycks** nyckeln.
När du `Sort-Object` kör cmdleten körs script block och resultatet används för sortering.

I följande exempel sorteras objekt i fallande ordning efter tidsintervallet mellan **CreationTime** och **LastWriteTime**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>Tips

Du kan utelämna **egenskaps** parameterns namn enligt följande:

```powershell
Sort-Object LastWriteTime, Name
```

Förutom kan du referera till `Sort-Object` med dess inbyggda alias: `sort`

```powershell
sort LastWriteTime, Name
```

Nycklarna i hash-tabellerna för sortering kan förkortas enligt följande:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

I det här exemplet står **e** står för **uttrycket**, **d** står för **fallande**och **en** står för **stigande**.

För att förbättra läsbarheten kan du placera hash-tabellerna i en separat variabel:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
