---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ba8b4e0e3952226407f00dea8b32785633256089
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="522b0-103">Objektet ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="522b0-103">The ISEAddOnToolCollection Object</span></span>
  <span data-ttu-id="522b0-104">Den **ISEAddOnToolCollection** objekt är en samling **ISEAddOnTool** objekt.</span><span class="sxs-lookup"><span data-stu-id="522b0-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="522b0-105">Ett exempel är den **$psISE.CurrentPowerShellTab.VerticalAddOnTools** objekt.</span><span class="sxs-lookup"><span data-stu-id="522b0-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="522b0-106">Metoder</span><span class="sxs-lookup"><span data-stu-id="522b0-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="522b0-107">Lägg till\( namn, kontrolltyp, \[IsVisible\]\)</span><span class="sxs-lookup"><span data-stu-id="522b0-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>
  <span data-ttu-id="522b0-108">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="522b0-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="522b0-109">Lägger till ett nytt tilläggsverktyg i samlingen.</span><span class="sxs-lookup"><span data-stu-id="522b0-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="522b0-110">Returnerar den nytillagda tilläggsverktyg.</span><span class="sxs-lookup"><span data-stu-id="522b0-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="522b0-111">Innan du kör det här kommandot måste du installera verktyget tillägg på den lokala datorn och att läsa in sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="522b0-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

 <span data-ttu-id="522b0-112">**Namnet** -sträng Anger visningsnamnet för verktyget tillägg som har lagts till i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="522b0-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

 <span data-ttu-id="522b0-113">**Kontrolltyp** -typen anger den kontroll som har lagts till.</span><span class="sxs-lookup"><span data-stu-id="522b0-113">**ControlType** -Type Specifies the control that is added.</span></span>

 <span data-ttu-id="522b0-114">**\[IsVisible\]**  -valfritt booleskt om **$true**, verktyget tillägg visas omedelbart i associerade verktygsfönstret.</span><span class="sxs-lookup"><span data-stu-id="522b0-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="522b0-115">Ta bort\( objekt\)</span><span class="sxs-lookup"><span data-stu-id="522b0-115">Remove\( Item \)</span></span>
  <span data-ttu-id="522b0-116">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="522b0-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="522b0-117">Tar bort den angivna tilläggsverktyg från samlingen.</span><span class="sxs-lookup"><span data-stu-id="522b0-117">Removes the specified add-on tool from the collection.</span></span>

 <span data-ttu-id="522b0-118">**Objektet** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool anger objektet som ska tas bort från Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="522b0-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="522b0-119">SetSelectedPowerShellTab\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="522b0-119">SetSelectedPowerShellTab\( psTab \)</span></span>
  <span data-ttu-id="522b0-120">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="522b0-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="522b0-121">Väljer du PowerShell fliken som den **psTab** parametern anger.</span><span class="sxs-lookup"><span data-stu-id="522b0-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="522b0-122">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab i PowerShell tab för att markera.</span><span class="sxs-lookup"><span data-stu-id="522b0-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a><span data-ttu-id="522b0-123">Ta bort\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="522b0-123">Remove\( psTab \)</span></span>
  <span data-ttu-id="522b0-124">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="522b0-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="522b0-125">Tar bort PowerShell fliken som den **psTab** parametern anger.</span><span class="sxs-lookup"><span data-stu-id="522b0-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="522b0-126">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab i PowerShell fliken om du vill ta bort.</span><span class="sxs-lookup"><span data-stu-id="522b0-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="522b0-127">Se även</span><span class="sxs-lookup"><span data-stu-id="522b0-127">See Also</span></span>
- [<span data-ttu-id="522b0-128">Objektet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="522b0-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="522b0-129">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="522b0-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="522b0-130">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="522b0-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="522b0-131">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="522b0-131">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
