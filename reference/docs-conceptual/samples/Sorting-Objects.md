---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Sortera objekt
description: Med Sort-Object cmdlet kan du sortera en samling objekt på en eller flera egenskaper.
ms.openlocfilehash: 836207adfc566003e9714e45920d9b4e24a677e9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501022"
---
# <a name="sorting-objects"></a><span data-ttu-id="c0952-104">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="c0952-104">Sorting Objects</span></span>

<span data-ttu-id="c0952-105">Vi kan organisera visade data för att göra det enklare att söka igenom dem med hjälp av `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0952-105">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="c0952-106">`Sort-Object` tar namnet på en eller flera egenskaper att sortera på och returnerar data sorterade efter värdena för dessa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c0952-106">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="c0952-107">Grundläggande sortering</span><span class="sxs-lookup"><span data-stu-id="c0952-107">Basic sorting</span></span>

<span data-ttu-id="c0952-108">Ta hänsyn till problemet med att lista under kataloger och filer i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0952-108">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="c0952-109">Om vi vill sortera efter **LastWriteTime** och sedan efter **namn**, kan vi göra det genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="c0952-109">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="c0952-110">Du kan också sortera objekten i omvänd ordning genom att ange parametern för **fallande** växel.</span><span class="sxs-lookup"><span data-stu-id="c0952-110">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="c0952-111">Använda hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="c0952-111">Using hash tables</span></span>

<span data-ttu-id="c0952-112">Du kan sortera olika egenskaper i olika beställningar genom att använda hash-tabeller i en matris.</span><span class="sxs-lookup"><span data-stu-id="c0952-112">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="c0952-113">Varje hash-tabell använder en **uttrycks** nyckel för att ange egenskaps namnet som sträng och en **stigande** eller **fallande** nyckel för att ange sorterings ordningen efter `$true` eller `$false` .</span><span class="sxs-lookup"><span data-stu-id="c0952-113">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="c0952-114">**Uttrycks** nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="c0952-114">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="c0952-115">Den **stigande** eller **fallande** nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="c0952-115">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="c0952-116">I följande exempel sorteras objekt i fallande **LastWriteTime** ordning och stigande **namn** ordning.</span><span class="sxs-lookup"><span data-stu-id="c0952-116">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="c0952-117">Du kan också ange en script block till **uttrycks** nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c0952-117">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="c0952-118">När du kör `Sort-Object` cmdleten körs script block och resultatet används för sortering.</span><span class="sxs-lookup"><span data-stu-id="c0952-118">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="c0952-119">I följande exempel sorteras objekt i fallande ordning efter tidsintervallet mellan **CreationTime** och **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="c0952-119">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="c0952-120">Tips</span><span class="sxs-lookup"><span data-stu-id="c0952-120">Tips</span></span>

<span data-ttu-id="c0952-121">Du kan utelämna **egenskaps** parameterns namn enligt följande:</span><span class="sxs-lookup"><span data-stu-id="c0952-121">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="c0952-122">Förutom kan du referera till `Sort-Object` med dess inbyggda alias `sort` :</span><span class="sxs-lookup"><span data-stu-id="c0952-122">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="c0952-123">Nycklarna i hash-tabellerna för sortering kan förkortas enligt följande:</span><span class="sxs-lookup"><span data-stu-id="c0952-123">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="c0952-124">I det här exemplet står **e** står för **uttrycket**, **d** står för **fallande**och **en** står för **stigande**.</span><span class="sxs-lookup"><span data-stu-id="c0952-124">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="c0952-125">För att förbättra läsbarheten kan du placera hash-tabellerna i en separat variabel:</span><span class="sxs-lookup"><span data-stu-id="c0952-125">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
