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
# <a name="sorting-objects"></a><span data-ttu-id="53ae6-103">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="53ae6-103">Sorting Objects</span></span>

<span data-ttu-id="53ae6-104">Vi kan ordna data som visas så att de blir enklare att skanna med hjälp av den `Sort-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53ae6-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="53ae6-105">`Sort-Object` tar namnet på en eller flera egenskaper för att sortera efter och returnerar data som sorterats genom att värdena för dessa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="53ae6-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="53ae6-106">Grundläggande sortering</span><span class="sxs-lookup"><span data-stu-id="53ae6-106">Basic sorting</span></span>

<span data-ttu-id="53ae6-107">Överväg att problemet med att visa en lista över undermappar och filer i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="53ae6-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="53ae6-108">Om vi vill sortera efter **LastWriteTime** och sedan efter **namn**, kan vi göra det genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="53ae6-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="53ae6-109">Du kan också sortera objekten i omvänd ordning genom att ange den **fallande** växla parametern.</span><span class="sxs-lookup"><span data-stu-id="53ae6-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="53ae6-110">Med hjälp av hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="53ae6-110">Using hash tables</span></span>

<span data-ttu-id="53ae6-111">Du kan sortera olika egenskaper i olika ordning med hjälp av hash-tabeller i en matris.</span><span class="sxs-lookup"><span data-stu-id="53ae6-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="53ae6-112">Varje hashtabellen använder en **uttryck** nyckel för att ange egenskapsnamnet på som sträng och en **stigande** eller **fallande** för att ange sorteringsordning genom `$true` eller `$false`.</span><span class="sxs-lookup"><span data-stu-id="53ae6-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="53ae6-113">Den **uttryck** nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="53ae6-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="53ae6-114">Den **stigande** eller **fallande** nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="53ae6-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="53ae6-115">I följande exempel sorterar objekt i fallande **LastWriteTime** ordning och stigande **namn** ordning.</span><span class="sxs-lookup"><span data-stu-id="53ae6-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="53ae6-116">Du kan också ange en scriptblock till den **uttryck** nyckel.</span><span class="sxs-lookup"><span data-stu-id="53ae6-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="53ae6-117">När du kör den `Sort-Object` cmdlet, körs scriptblock och resultatet används för sortering.</span><span class="sxs-lookup"><span data-stu-id="53ae6-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="53ae6-118">I följande exempel sorterar objekt i fallande ordning efter tidsintervallet mellan **CreationTime** och **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="53ae6-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="53ae6-119">Tips</span><span class="sxs-lookup"><span data-stu-id="53ae6-119">Tips</span></span>

<span data-ttu-id="53ae6-120">Du kan utelämna den **egenskapen** parameternamnet på följande:</span><span class="sxs-lookup"><span data-stu-id="53ae6-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="53ae6-121">Förutom, du kan referera till `Sort-Object` av dess inbyggda alias `sort`:</span><span class="sxs-lookup"><span data-stu-id="53ae6-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="53ae6-122">Nycklar i hash-tabeller för att sortera kan förkortas på följande:</span><span class="sxs-lookup"><span data-stu-id="53ae6-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="53ae6-123">I det här exemplet på **e** står för **uttryck**, **d** står för **fallande**, och **en** står för **stigande**.</span><span class="sxs-lookup"><span data-stu-id="53ae6-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="53ae6-124">För att förbättra läsbarheten, kan du placera hash-tabeller i en separat variabel:</span><span class="sxs-lookup"><span data-stu-id="53ae6-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
