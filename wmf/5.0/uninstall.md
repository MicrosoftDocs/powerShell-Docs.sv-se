---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688527"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="01382-102">Anvisningar för avinstallation</span><span class="sxs-lookup"><span data-stu-id="01382-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="01382-103">Med hjälp av Kommandotolken</span><span class="sxs-lookup"><span data-stu-id="01382-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="01382-104">Öppna **Kommandotolken.**</span><span class="sxs-lookup"><span data-stu-id="01382-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="01382-105">Kör den [Windows Update fristående starta](https://support.microsoft.com/en-us/kb/934307) enligt nedan:</span><span class="sxs-lookup"><span data-stu-id="01382-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="01382-106">På Windows Server 2012 R2 och Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="01382-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="01382-107">På Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="01382-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="01382-108">På Windows Server 2008 R2 SP1 och Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="01382-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="01382-109">Med hjälp av Kontrollpanelen</span><span class="sxs-lookup"><span data-stu-id="01382-109">Using Control Panel</span></span>
1.  <span data-ttu-id="01382-110">Öppna **Kontrollpanelen.**</span><span class="sxs-lookup"><span data-stu-id="01382-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="01382-111">Öppna **program**, öppna sedan **avinstallera ett program.**</span><span class="sxs-lookup"><span data-stu-id="01382-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="01382-112">Klicka på **Visa installerade uppdateringar.**</span><span class="sxs-lookup"><span data-stu-id="01382-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="01382-113">Välj **Windows Management Framework 5.0** i listan över installerade uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="01382-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="01382-114">Detta motsvarar *KB3134758*, *KB3134759*, eller *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="01382-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="01382-115">Klicka på **avinstallera.**</span><span class="sxs-lookup"><span data-stu-id="01382-115">Click **Uninstall.**</span></span>
