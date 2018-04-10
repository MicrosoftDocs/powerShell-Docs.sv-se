---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 78ae7ecd40b4d8ad0a6750f43002986483ab18a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="5120e-102">Anvisningar för avinstallation</span><span class="sxs-lookup"><span data-stu-id="5120e-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="5120e-103">Med hjälp av Kommandotolken</span><span class="sxs-lookup"><span data-stu-id="5120e-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="5120e-104">Öppna **kommandotolk.**</span><span class="sxs-lookup"><span data-stu-id="5120e-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="5120e-105">Kör den [Windows Update fristående programstart](https://support.microsoft.com/en-us/kb/934307) enligt nedan:</span><span class="sxs-lookup"><span data-stu-id="5120e-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="5120e-106">På Windows Server 2012 R2 och Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="5120e-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="5120e-107">I Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="5120e-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="5120e-108">På Windows Server 2008 R2 SP1 och Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="5120e-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="5120e-109">Med hjälp av Kontrollpanelen</span><span class="sxs-lookup"><span data-stu-id="5120e-109">Using Control Panel</span></span>
1.  <span data-ttu-id="5120e-110">Öppna **Kontrollpanelen.**</span><span class="sxs-lookup"><span data-stu-id="5120e-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="5120e-111">Öppna **program**sedan öppnar **avinstallera ett program.**</span><span class="sxs-lookup"><span data-stu-id="5120e-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="5120e-112">Klicka på **Visa installerade uppdateringar.**</span><span class="sxs-lookup"><span data-stu-id="5120e-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="5120e-113">Välj **Windows Management Framework 5.0** från listan över installerade uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="5120e-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="5120e-114">Detta motsvarar *KB3134758*, *KB3134759*, eller *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="5120e-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="5120e-115">Klicka på **avinstallera.**</span><span class="sxs-lookup"><span data-stu-id="5120e-115">Click **Uninstall.**</span></span>