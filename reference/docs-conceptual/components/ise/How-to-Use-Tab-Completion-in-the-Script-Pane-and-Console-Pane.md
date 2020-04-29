---
ms.date: 01/02/2020
keywords: PowerShell, cmdlet
title: Använd tabbifyllning i skriptfönstret och konsolfönstret
ms.openlocfilehash: 07cf9ff75db8d33ed018542153bfcd7503035e40
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737091"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="2f691-103">Använd tabbifyllning i skriptfönstret och konsolfönstret</span><span class="sxs-lookup"><span data-stu-id="2f691-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="2f691-104">Ifyllning av flikar ger automatisk hjälp när du skriver i skript fönstret eller i kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="2f691-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="2f691-105">Använd följande steg för att dra nytta av den här funktionen:</span><span class="sxs-lookup"><span data-stu-id="2f691-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="2f691-106">Så här slutför du en kommando post automatiskt</span><span class="sxs-lookup"><span data-stu-id="2f691-106">To automatically complete a command entry</span></span>

<span data-ttu-id="2f691-107">Skriv några tecken i ett kommando i kommando fönstret eller skript rutan och tryck sedan på <kbd>TABB</kbd> för att välja önskad slut för ande text.</span><span class="sxs-lookup"><span data-stu-id="2f691-107">In the Command Pane or Script Pane, type a few characters of a command and then press <kbd>TAB</kbd> to select the desired completion text.</span></span> <span data-ttu-id="2f691-108">Om flera objekt börjar med texten som du ursprungligen skrev in, fortsätter du att trycka på <kbd>TABB</kbd> tills det önskade objektet visas.</span><span class="sxs-lookup"><span data-stu-id="2f691-108">If multiple items begin with the text that you initially typed, then continue pressing <kbd>TAB</kbd> until the item you want appears.</span></span> <span data-ttu-id="2f691-109">TABB-slutförande kan hjälpa dig att skriva ett cmdlet-namn, parameter namn, variabel namn, objekt egenskaps namn eller en fil Sök väg.</span><span class="sxs-lookup"><span data-stu-id="2f691-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="2f691-110">När du trycker på <kbd>fliken</kbd> i skript fönstret utförs automatiskt ett kommando när du redigerar `.ps1`, `.psd1`eller `.psm1` filer.</span><span class="sxs-lookup"><span data-stu-id="2f691-110">In the Script Pane, pressing <kbd>TAB</kbd> will automatically complete a command only when you are editing `.ps1`, `.psd1`, or `.psm1` files.</span></span> <span data-ttu-id="2f691-111">TABB-slutförande fungerar när som helst när du skriver i kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="2f691-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="2f691-112">Så här slutför du en cmdlet-parameter post automatiskt</span><span class="sxs-lookup"><span data-stu-id="2f691-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="2f691-113">I kommando fönstret eller skript rutan skriver du en cmdlet följt av ett streck och trycker sedan på <kbd>TABB</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2f691-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press <kbd>TAB</kbd>.</span></span>

<span data-ttu-id="2f691-114">Skriv `Get-Process -` till exempel och tryck på <kbd>TABB</kbd> flera gånger för att visa var och en av parametrarna för cmdleten i tur och retur.</span><span class="sxs-lookup"><span data-stu-id="2f691-114">For example, type `Get-Process -` and then press <kbd>TAB</kbd> multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f691-115">Se även</span><span class="sxs-lookup"><span data-stu-id="2f691-115">See Also</span></span>

- [<span data-ttu-id="2f691-116">Vi presenterar Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="2f691-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="2f691-117">Så här skapar du en PowerShell-flik</span><span class="sxs-lookup"><span data-stu-id="2f691-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
