---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="6d790-102">Get-ChildItem har - djup parameter</span><span class="sxs-lookup"><span data-stu-id="6d790-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="6d790-103">**Get-ChildItem** har nu en **– djup** parameter som du använder med **– Recurse** att begränsa rekursion:</span><span class="sxs-lookup"><span data-stu-id="6d790-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="6d790-104">PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 0</span><span class="sxs-lookup"><span data-stu-id="6d790-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="6d790-105">Katalog: C:\\användare\\slee\\hämtar\\exempel</span><span class="sxs-lookup"><span data-stu-id="6d790-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="6d790-106">Läge LastWriteTime längd namn</span><span class="sxs-lookup"><span data-stu-id="6d790-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="6d790-107">d – 4-14/2015 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="6d790-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="6d790-108">-a – 4-14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="6d790-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="6d790-109">-a – 4-14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="6d790-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="6d790-110">-a – 4-14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="6d790-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="6d790-111">PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 1</span><span class="sxs-lookup"><span data-stu-id="6d790-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="6d790-112">Katalog: C:\\användare\\slee\\hämtar\\exempel</span><span class="sxs-lookup"><span data-stu-id="6d790-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="6d790-113">Läge LastWriteTime längd namn</span><span class="sxs-lookup"><span data-stu-id="6d790-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="6d790-114">d – 4-14/2015 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="6d790-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="6d790-115">-a – 4-14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="6d790-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="6d790-116">-a – 4-14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="6d790-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="6d790-117">-a – 4-14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="6d790-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="6d790-118">Katalog: C:\\användare\\slee\\hämtar\\exempel\\Depth0</span><span class="sxs-lookup"><span data-stu-id="6d790-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="6d790-119">Läge LastWriteTime längd namn</span><span class="sxs-lookup"><span data-stu-id="6d790-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="6d790-120">d – 4-14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="6d790-120">d----- 4/14/2015 5:33 PM Depth1</span></span>