---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Avinstallera WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856191"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="088c6-103">Anvisningar för avinstallation</span><span class="sxs-lookup"><span data-stu-id="088c6-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="088c6-104">Med hjälp av Kommandotolken</span><span class="sxs-lookup"><span data-stu-id="088c6-104">Using Command Prompt</span></span>

1. <span data-ttu-id="088c6-105">Öppna **Kommandotolken.**</span><span class="sxs-lookup"><span data-stu-id="088c6-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="088c6-106">Kör den [Windows Update fristående starta](https://support.microsoft.com/en-us/kb/934307) enligt nedan:</span><span class="sxs-lookup"><span data-stu-id="088c6-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="088c6-107">På Windows Server 2012 R2 och Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="088c6-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="088c6-108">På Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="088c6-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="088c6-109">På Windows Server 2008 R2 SP1 och Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="088c6-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="088c6-110">Med hjälp av Kontrollpanelen</span><span class="sxs-lookup"><span data-stu-id="088c6-110">Using Control Panel</span></span>

1. <span data-ttu-id="088c6-111">Öppna **Kontrollpanelen.**</span><span class="sxs-lookup"><span data-stu-id="088c6-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="088c6-112">Öppna **program**, öppna sedan **avinstallera ett program.**</span><span class="sxs-lookup"><span data-stu-id="088c6-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="088c6-113">Klicka på **Visa installerade uppdateringar.**</span><span class="sxs-lookup"><span data-stu-id="088c6-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="088c6-114">Välj **Windows Management Framework 5.0** i listan över installerade uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="088c6-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="088c6-115">Detta motsvarar *KB3134758*, *KB3134759*, eller *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="088c6-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="088c6-116">Klicka på **avinstallera.**</span><span class="sxs-lookup"><span data-stu-id="088c6-116">Click **Uninstall.**</span></span>
