---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Bilaga 2 Skapa en anpassad PowerShell-genväg
ms.openlocfilehash: 6f1a6a8187b1797103e3620b2cf9155978807ea5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030300"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="c4052-103">Bilaga 2 – Skapa en anpassad PowerShell-genväg</span><span class="sxs-lookup"><span data-stu-id="c4052-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="c4052-104">Följande procedur beskriver hur du skapar en genväg till Windows PowerShell som har flera praktiska alternativ anpassade.</span><span class="sxs-lookup"><span data-stu-id="c4052-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="c4052-105">Skapa en genväg som pekar på PowerShell. exe.</span><span class="sxs-lookup"><span data-stu-id="c4052-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="c4052-106">Högerklicka på genvägen och klicka sedan på **Egenskaper**.</span><span class="sxs-lookup"><span data-stu-id="c4052-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="c4052-107">Klicka på fliken **Alternativ**.</span><span class="sxs-lookup"><span data-stu-id="c4052-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="c4052-108">I avsnittet **Redigera alternativ** markerar du kryss rutan **Snabb redigering** .</span><span class="sxs-lookup"><span data-stu-id="c4052-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="c4052-109">Med den här inställningen kan du välja text i fönstret Windows PowerShell-konsol genom att dra den vänstra mus knappen, så att du kan kopiera text till Urklipp genom att trycka på RETUR eller genom att högerklicka på musen.</span><span class="sxs-lookup"><span data-stu-id="c4052-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="c4052-110">I avsnittet **Redigera alternativ** markerar du kryss rutan **infognings läge** .</span><span class="sxs-lookup"><span data-stu-id="c4052-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="c4052-111">Med den här inställningen kan du högerklicka i konsol fönstret för att automatiskt klistra in text från Urklipp.</span><span class="sxs-lookup"><span data-stu-id="c4052-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="c4052-112">I avsnittet **kommando historik** skriver eller väljer du ett tal mellan 1 och 999 i rutan **Buffertstorlek** .</span><span class="sxs-lookup"><span data-stu-id="c4052-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="c4052-113">Detta anger antalet skrivna kommandon som ska behållas i-konsolens buffert.</span><span class="sxs-lookup"><span data-stu-id="c4052-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="c4052-114">I avsnittet **kommando historik** markerar du kryss rutan **ta bort gamla dubbletter** för att ta bort upprepade kommandon från-konsolens buffert.</span><span class="sxs-lookup"><span data-stu-id="c4052-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="c4052-115">Klicka på fliken **layout** .</span><span class="sxs-lookup"><span data-stu-id="c4052-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="c4052-116">I avsnittet **skärmlayout** anger du ett tal mellan 1 och 9999 i rutan **höjd** .</span><span class="sxs-lookup"><span data-stu-id="c4052-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="c4052-117">Höjden representerar antalet rader utdata som buffras.</span><span class="sxs-lookup"><span data-stu-id="c4052-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="c4052-118">Detta är det maximala antalet rader som behålls för visning när du bläddrar i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="c4052-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="c4052-119">Om det här talet är lägre än den höjd som visas i avsnittet **fönster storlek** , minskas fönstrets storleks höjd automatiskt till samma värde.</span><span class="sxs-lookup"><span data-stu-id="c4052-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="c4052-120">I avsnittet **fönster storlek** anger du en siffra mellan 1 och 9999 för bredden.</span><span class="sxs-lookup"><span data-stu-id="c4052-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="c4052-121">Detta representerar antalet tecken som visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="c4052-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="c4052-122">Standard bredden är 80 och Windows PowerShell: s utdataformat är utformad för den här bredden.</span><span class="sxs-lookup"><span data-stu-id="c4052-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="c4052-123">Om du vill placera konsolen vid en viss punkt på Skriv bordet när den öppnas, avmarkerar du kryss rutan **Låt system positions fönstret** i avsnittet **fönster placering** och ändrar sedan värdena i rutorna till **vänster** och **överkant** i avsnittet **fönster placering** .</span><span class="sxs-lookup"><span data-stu-id="c4052-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="c4052-124">Klicka på **OK**.</span><span class="sxs-lookup"><span data-stu-id="c4052-124">Click **OK**.</span></span>
