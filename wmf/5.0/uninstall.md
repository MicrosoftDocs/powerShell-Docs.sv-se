---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057537"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="79337-102">Anvisningar för avinstallation</span><span class="sxs-lookup"><span data-stu-id="79337-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="79337-103">Med hjälp av Kommandotolken</span><span class="sxs-lookup"><span data-stu-id="79337-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="79337-104">Öppna **Kommandotolken.**</span><span class="sxs-lookup"><span data-stu-id="79337-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="79337-105">Kör den [Windows Update fristående starta](https://support.microsoft.com/en-us/kb/934307) enligt nedan:</span><span class="sxs-lookup"><span data-stu-id="79337-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="79337-106">På Windows Server 2012 R2 och Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="79337-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="79337-107">På Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="79337-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="79337-108">På Windows Server 2008 R2 SP1 och Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="79337-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="79337-109">Med hjälp av Kontrollpanelen</span><span class="sxs-lookup"><span data-stu-id="79337-109">Using Control Panel</span></span>
1.  <span data-ttu-id="79337-110">Öppna **Kontrollpanelen.**</span><span class="sxs-lookup"><span data-stu-id="79337-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="79337-111">Öppna **program**, öppna sedan **avinstallera ett program.**</span><span class="sxs-lookup"><span data-stu-id="79337-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="79337-112">Klicka på **Visa installerade uppdateringar.**</span><span class="sxs-lookup"><span data-stu-id="79337-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="79337-113">Välj **Windows Management Framework 5.0** i listan över installerade uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="79337-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="79337-114">Detta motsvarar *KB3134758*, *KB3134759*, eller *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="79337-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="79337-115">Klicka på **avinstallera.**</span><span class="sxs-lookup"><span data-stu-id="79337-115">Click **Uninstall.**</span></span>
