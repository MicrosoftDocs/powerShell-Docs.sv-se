---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085308"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="27e5b-102">Get-ChildItem har parametern - Depth</span><span class="sxs-lookup"><span data-stu-id="27e5b-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="27e5b-103">**Get-ChildItem** har nu en **– djup** parameter som du använder med **– Recurse** att begränsa rekursion:</span><span class="sxs-lookup"><span data-stu-id="27e5b-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="27e5b-104">PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 0</span><span class="sxs-lookup"><span data-stu-id="27e5b-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="27e5b-105">Katalog: C:\\användare\\slee\\hämtar\\exempel</span><span class="sxs-lookup"><span data-stu-id="27e5b-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="27e5b-106">Läget LastWriteTime längd namn</span><span class="sxs-lookup"><span data-stu-id="27e5b-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="27e5b-107">d---4/14/2015 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="27e5b-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="27e5b-108">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="27e5b-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="27e5b-109">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="27e5b-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="27e5b-110">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="27e5b-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="27e5b-111">PS C:\\användare\\slee\\hämtar\\exempel&gt; Get-ChildItem-Recurse - djup 1</span><span class="sxs-lookup"><span data-stu-id="27e5b-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="27e5b-112">Katalog: C:\\användare\\slee\\hämtar\\exempel</span><span class="sxs-lookup"><span data-stu-id="27e5b-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="27e5b-113">Läget LastWriteTime längd namn</span><span class="sxs-lookup"><span data-stu-id="27e5b-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="27e5b-114">d---4/14/2015 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="27e5b-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="27e5b-115">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="27e5b-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="27e5b-116">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="27e5b-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="27e5b-117">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="27e5b-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="27e5b-118">Katalog: C:\\användare\\slee\\hämtar\\exempel\\Depth0</span><span class="sxs-lookup"><span data-stu-id="27e5b-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="27e5b-119">Läget LastWriteTime längd namn</span><span class="sxs-lookup"><span data-stu-id="27e5b-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="27e5b-120">d---4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="27e5b-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
