---
ms.date: 06/12/2017
title: Avinstallera WMF 5.0
description: Den här artikeln förklarar hur du avinstallerar WMF från äldre versioner av Windows.
ms.openlocfilehash: d8078ea918db2c1cf9a7ddd6ea8d1413b593c0ff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660806"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="86181-103">Avinstallations anvisningar</span><span class="sxs-lookup"><span data-stu-id="86181-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="86181-104">Använda kommando tolken</span><span class="sxs-lookup"><span data-stu-id="86181-104">Using Command Prompt</span></span>

1. <span data-ttu-id="86181-105">Öppna **kommando tolken.**</span><span class="sxs-lookup"><span data-stu-id="86181-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="86181-106">Kör [Windows Update fristående start](https://support.microsoft.com/kb/934307) programmet som det visas nedan:</span><span class="sxs-lookup"><span data-stu-id="86181-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/kb/934307) as shown below:</span></span>

<span data-ttu-id="86181-107">På Windows Server 2012 R2 och Windows 8,1:</span><span class="sxs-lookup"><span data-stu-id="86181-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="86181-108">På Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="86181-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="86181-109">På Windows Server 2008 R2 SP1 och Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="86181-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="86181-110">Använda kontroll panelen</span><span class="sxs-lookup"><span data-stu-id="86181-110">Using Control Panel</span></span>

1. <span data-ttu-id="86181-111">Öppna **kontroll panelen.**</span><span class="sxs-lookup"><span data-stu-id="86181-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="86181-112">Öppna **program** och öppna sedan **Avinstallera ett program.**</span><span class="sxs-lookup"><span data-stu-id="86181-112">Open **Programs** , then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="86181-113">Klicka på **Visa installerade uppdateringar.**</span><span class="sxs-lookup"><span data-stu-id="86181-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="86181-114">Välj **Windows Management Framework 5,0** i listan över installerade uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="86181-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="86181-115">Detta motsvarar *KB3134758* , *KB3134759* eller *KB3134760* .</span><span class="sxs-lookup"><span data-stu-id="86181-115">This corresponds to *KB3134758* , *KB3134759* , or *KB3134760* .</span></span> <span data-ttu-id="86181-116">Klicka på **Avinstallera.**</span><span class="sxs-lookup"><span data-stu-id="86181-116">Click **Uninstall.**</span></span>
