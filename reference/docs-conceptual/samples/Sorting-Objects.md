---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Sortera objekt
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030783"
---
# <a name="sorting-objects"></a>Sortera objekt

Vi kan ordna data som visas så att de blir enklare att skanna med hjälp av den `Sort-Object` cmdlet. `Sort-Object` tar namnet på en eller flera egenskaper för att sortera efter och returnerar data som sorterats genom att värdena för dessa egenskaper.

## <a name="basic-sorting"></a>Grundläggande sortering

Överväg att problemet med att visa en lista över undermappar och filer i den aktuella katalogen.
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

Du kan också sortera objekten i omvänd ordning genom att ange den **fallande** växla parametern.

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

## <a name="using-hash-tables"></a>Med hjälp av hash-tabeller

Du kan sortera olika egenskaper i olika ordning med hjälp av hash-tabeller i en matris.
Varje hashtabellen använder en **uttryck** nyckel för att ange egenskapsnamnet på som sträng och en **stigande** eller **fallande** för att ange sorteringsordning genom `$true` eller `$false`.
Den **uttryck** nyckeln är obligatorisk.
Den **stigande** eller **fallande** nyckeln är valfri.

I följande exempel sorterar objekt i fallande **LastWriteTime** ordning och stigande **namn** ordning.

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

Du kan också ange en scriptblock till den **uttryck** nyckel.
När du kör den `Sort-Object` cmdlet, körs scriptblock och resultatet används för sortering.

I följande exempel sorterar objekt i fallande ordning efter tidsintervallet mellan **CreationTime** och **LastWriteTime**.

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

Du kan utelämna den **egenskapen** parameternamnet på följande:

```powershell
Sort-Object LastWriteTime, Name
```

Förutom, du kan referera till `Sort-Object` av dess inbyggda alias `sort`:

```powershell
sort LastWriteTime, Name
```

Nycklar i hash-tabeller för att sortera kan förkortas på följande:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

I det här exemplet på **e** står för **uttryck**, **d** står för **fallande**, och **en** står för **stigande**.

För att förbättra läsbarheten, kan du placera hash-tabeller i en separat variabel:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
