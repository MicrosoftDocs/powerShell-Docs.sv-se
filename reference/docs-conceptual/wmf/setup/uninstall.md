---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Avinstallera WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145217"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="6d45c-103">Avinstallations anvisningar</span><span class="sxs-lookup"><span data-stu-id="6d45c-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="6d45c-104">Använda kommando tolken</span><span class="sxs-lookup"><span data-stu-id="6d45c-104">Using Command Prompt</span></span>

1. <span data-ttu-id="6d45c-105">Öppna **kommando tolken.**</span><span class="sxs-lookup"><span data-stu-id="6d45c-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="6d45c-106">Kör [Windows Update fristående start](https://support.microsoft.com/en-us/kb/934307) programmet som det visas nedan:</span><span class="sxs-lookup"><span data-stu-id="6d45c-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="6d45c-107">På Windows Server 2012 R2 och Windows 8,1:</span><span class="sxs-lookup"><span data-stu-id="6d45c-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="6d45c-108">På Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="6d45c-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="6d45c-109">På Windows Server 2008 R2 SP1 och Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="6d45c-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="6d45c-110">Använda kontroll panelen</span><span class="sxs-lookup"><span data-stu-id="6d45c-110">Using Control Panel</span></span>

1. <span data-ttu-id="6d45c-111">Öppna **kontroll panelen.**</span><span class="sxs-lookup"><span data-stu-id="6d45c-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="6d45c-112">Öppna **program**och öppna sedan **Avinstallera ett program.**</span><span class="sxs-lookup"><span data-stu-id="6d45c-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="6d45c-113">Klicka på **Visa installerade uppdateringar.**</span><span class="sxs-lookup"><span data-stu-id="6d45c-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="6d45c-114">Välj **Windows Management Framework 5,0** i listan över installerade uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="6d45c-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="6d45c-115">Detta motsvarar *KB3134758*, *KB3134759*eller *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="6d45c-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="6d45c-116">Klicka på **Avinstallera.**</span><span class="sxs-lookup"><span data-stu-id="6d45c-116">Click **Uninstall.**</span></span>
