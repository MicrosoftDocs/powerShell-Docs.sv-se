---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="8dc67-102">Get-ChildItem har - djup parameter</span><span class="sxs-lookup"><span data-stu-id="8dc67-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="8dc67-103">**Get-ChildItem** har nu en **– djup** parameter som du använder med **– Recurse** att begränsa rekursion:</span><span class="sxs-lookup"><span data-stu-id="8dc67-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="8dc67-104">PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 0</span><span class="sxs-lookup"><span data-stu-id="8dc67-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="8dc67-105">Katalog: C:\\användare\\slee\\hämtar\\exempel</span><span class="sxs-lookup"><span data-stu-id="8dc67-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="8dc67-106">Läge LastWriteTime längd namn</span><span class="sxs-lookup"><span data-stu-id="8dc67-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="8dc67-107">d – 4-14/2015 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="8dc67-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="8dc67-108">-a – 4-14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="8dc67-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="8dc67-109">-a – 4-14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="8dc67-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="8dc67-110">-a – 4-14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="8dc67-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="8dc67-111">PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 1</span><span class="sxs-lookup"><span data-stu-id="8dc67-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="8dc67-112">Katalog: C:\\användare\\slee\\hämtar\\exempel</span><span class="sxs-lookup"><span data-stu-id="8dc67-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="8dc67-113">Läge LastWriteTime längd namn</span><span class="sxs-lookup"><span data-stu-id="8dc67-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="8dc67-114">d – 4-14/2015 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="8dc67-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="8dc67-115">-a – 4-14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="8dc67-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="8dc67-116">-a – 4-14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="8dc67-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="8dc67-117">-a – 4-14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="8dc67-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="8dc67-118">Katalog: C:\\användare\\slee\\hämtar\\exempel\\Depth0</span><span class="sxs-lookup"><span data-stu-id="8dc67-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="8dc67-119">Läge LastWriteTime längd namn</span><span class="sxs-lookup"><span data-stu-id="8dc67-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="8dc67-120">d – 4-14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="8dc67-120">d----- 4/14/2015 5:33 PM Depth1</span></span>

