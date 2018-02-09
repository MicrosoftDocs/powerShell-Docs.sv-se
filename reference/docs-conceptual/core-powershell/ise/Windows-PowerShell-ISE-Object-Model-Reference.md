---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Windows PowerShell ISE-objektmodellreferens
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 624ddca3895ba3e24bf52a27babdb07e8714baae
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/08/2018
---
# <a name="windows-powershell-ise-object-model-reference"></a><span data-ttu-id="16550-103">Windows PowerShell ISE-objektmodellreferens</span><span class="sxs-lookup"><span data-stu-id="16550-103">Windows PowerShell ISE Object Model Reference</span></span>
  
## <a name="object-model-reference"></a><span data-ttu-id="16550-104">Objektreferens för modellen</span><span class="sxs-lookup"><span data-stu-id="16550-104">Object Model Reference</span></span>
 <span data-ttu-id="16550-105">Det här avsnittet innehåller en referens om de underliggande klasser som definierar de olika objekt inWindows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="16550-105">This section provides a reference on the underlying classes that define the various objects inWindows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="16550-106">Objekten ordnade i deras hierarki finns [i ISE modellen objekthierarkin](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="16550-106">To see the objects organized in their hierarchy, see [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md).</span></span>

 <span data-ttu-id="16550-107">[Objektet ISEAddOnTool](The-ISEAddOnTool-Object.md) exempel: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span><span class="sxs-lookup"><span data-stu-id="16550-107">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) Examples: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span></span>

 <span data-ttu-id="16550-108">[Objektet ISEAddOnTool](The-ISEAddOnTool-Object.md) [ISEEditor objektet](The-ISEEditor-Object.md) exempel: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span><span class="sxs-lookup"><span data-stu-id="16550-108">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) [The ISEEditor Object](The-ISEEditor-Object.md) Examples: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span></span>

 <span data-ttu-id="16550-109">[Objektet ISEFile](The-ISEFile-Object.md) exempel: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span><span class="sxs-lookup"><span data-stu-id="16550-109">[The ISEFile Object](The-ISEFile-Object.md) Examples: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span></span>

 <span data-ttu-id="16550-110">[Objektet ISEFileCollection](The-ISEFileCollection-Object.md) exempel: $psISE.PowerShellTabs.Files.</span><span class="sxs-lookup"><span data-stu-id="16550-110">[The ISEFileCollection Object](The-ISEFileCollection-Object.md) Examples: $psISE.PowerShellTabs.Files.</span></span>

 <span data-ttu-id="16550-111">[Objektet ISEMenuItem](The-ISEMenuItem-Object.md) exempel: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span><span class="sxs-lookup"><span data-stu-id="16550-111">[The ISEMenuItem Object](The-ISEMenuItem-Object.md) Examples: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span></span>

 <span data-ttu-id="16550-112">[Objektet ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) exempel: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span><span class="sxs-lookup"><span data-stu-id="16550-112">[The ISEMenuItemCollection Object](The-ISEMenuItemCollection-Object.md) Example: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span></span>

 <span data-ttu-id="16550-113">[Objektet ISEOptions](The-ISEOptions-Object.md) exempel: $psISE.Options, $psISE.Options.DefaultOptions.</span><span class="sxs-lookup"><span data-stu-id="16550-113">[The ISEOptions Object](The-ISEOptions-Object.md) Examples: $psISE.Options, $psISE.Options.DefaultOptions.</span></span>

 <span data-ttu-id="16550-114">[Objektet ObjectModelRoot](The-ObjectModelRoot-Object.md) exempel: rotobjektet $psISE.</span><span class="sxs-lookup"><span data-stu-id="16550-114">[The ObjectModelRoot Object](The-ObjectModelRoot-Object.md) Example: The root $psISE object.</span></span>

 <span data-ttu-id="16550-115">[Objektet PowerShellTab](The-PowerShellTab-Object.md) exempel: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span><span class="sxs-lookup"><span data-stu-id="16550-115">[The PowerShellTab Object](The-PowerShellTab-Object.md) Examples: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span></span>

 <span data-ttu-id="16550-116">[Objektet PowerShellTabCollection](The-PowerShellTabCollection-Object.md) exempel: $psISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="16550-116">[The PowerShellTabCollection Object](The-PowerShellTabCollection-Object.md) Example: $psISE.PowerShellTabs.</span></span>

## <a name="see-also"></a><span data-ttu-id="16550-117">Se även</span><span class="sxs-lookup"><span data-stu-id="16550-117">See Also</span></span>
- [<span data-ttu-id="16550-118">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="16550-118">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
