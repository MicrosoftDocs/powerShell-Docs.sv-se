---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="2dbcf-102">Anvisningar för avinstallation</span><span class="sxs-lookup"><span data-stu-id="2dbcf-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="2dbcf-103">Med hjälp av Kommandotolken</span><span class="sxs-lookup"><span data-stu-id="2dbcf-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="2dbcf-104">Öppna **kommandotolk.**</span><span class="sxs-lookup"><span data-stu-id="2dbcf-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="2dbcf-105">Kör den [Windows Update fristående programstart](https://support.microsoft.com/en-us/kb/934307) enligt nedan:</span><span class="sxs-lookup"><span data-stu-id="2dbcf-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="2dbcf-106">På Windows Server 2012 R2 och Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="2dbcf-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="2dbcf-107">I Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="2dbcf-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="2dbcf-108">På Windows Server 2008 R2 SP1 och Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="2dbcf-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="2dbcf-109">Med hjälp av Kontrollpanelen</span><span class="sxs-lookup"><span data-stu-id="2dbcf-109">Using Control Panel</span></span>
1.  <span data-ttu-id="2dbcf-110">Öppna **Kontrollpanelen.**</span><span class="sxs-lookup"><span data-stu-id="2dbcf-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="2dbcf-111">Öppna **program**sedan öppnar **avinstallera ett program.**</span><span class="sxs-lookup"><span data-stu-id="2dbcf-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="2dbcf-112">Klicka på **Visa installerade uppdateringar.**</span><span class="sxs-lookup"><span data-stu-id="2dbcf-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="2dbcf-113">Välj **Windows Management Framework 5.0** från listan över installerade uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="2dbcf-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="2dbcf-114">Detta motsvarar *KB3134758*, *KB3134759*, eller *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="2dbcf-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="2dbcf-115">Klicka på **avinstallera.**</span><span class="sxs-lookup"><span data-stu-id="2dbcf-115">Click **Uninstall.**</span></span>
