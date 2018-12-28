---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Bilaga 2 Skapa en anpassad PowerShell-genväg
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405989"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="0ffe5-103">Bilaga 2 – Skapa en anpassad PowerShell-genväg</span><span class="sxs-lookup"><span data-stu-id="0ffe5-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="0ffe5-104">Följande procedur beskriver hur du skapar en genväg till Windows PowerShell som har flera praktiska alternativ för anpassade.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="0ffe5-105">Skapa en genväg som pekar på Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="0ffe5-106">Högerklicka på genvägen och klicka sedan på **egenskaper**.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="0ffe5-107">Klicka på den **alternativ** fliken.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="0ffe5-108">I den **redigeringsalternativ** väljer den **Snabbredigering** markerar du kryssrutan.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="0ffe5-109">Den här inställningen kan du välja text i Windows PowerShell-konsolfönster genom att dra vänster musknapp och den kan du kopiera text till Urklipp genom att trycka på RETUR eller genom att högerklicka på musen.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="0ffe5-110">I den **redigeringsalternativ** väljer den **infogningsläge** markerar du kryssrutan.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="0ffe5-111">Den här inställningen kan du högerklicka i konsolfönstret för att automatiskt klistra in text från Urklipp.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="0ffe5-112">I den **Kommandohistorik** avsnittet anger eller väljer ett tal mellan 1 och 999 i den **buffertstorleken** box.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="0ffe5-113">Detta anger antalet skrivna kommandon som sparas i konsolen buffert.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="0ffe5-114">I den **Kommandohistorik** väljer den **ta bort dubbletter** kryssrutan för att undvika upprepade kommandon från konsolen bufferten.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="0ffe5-115">Klicka på den **Layout** fliken.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="0ffe5-116">I den **skärmbufferten** Skriv ett tal mellan 1 och 9999 i den **höjd** box.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="0ffe5-117">Höjd representerar antalet rader med utdata som är buffrade.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="0ffe5-118">Det här är det maximala antalet rader som kvarhålls för att visa när du bläddrar igenom konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="0ffe5-119">Om det här värdet är lägre än höjden visas i den **fönsterstorlek** avsnittet fönstret storlek höjden minskas automatiskt till samma värde.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="0ffe5-120">I den **fönsterstorlek** Skriv ett tal mellan 1 och 9999 för bredd.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="0ffe5-121">Detta representerar antalet tecken som visas i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="0ffe5-122">Standardbredden är 80 och Windows PowerShell-utdata formatering är avsedd för den här bredden.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="0ffe5-123">Om du vill placera konsolen vid en viss på skrivbordet när den öppnas, avmarkera de **låta systemet placera fönstret** kryssrutan i den **fönstret position** , och sedan ändra värdena i  **Vänster** och **upp** rutorna i den **fönstret position** avsnittet.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="0ffe5-124">Klicka på **OK**.</span><span class="sxs-lookup"><span data-stu-id="0ffe5-124">Click **OK**.</span></span>