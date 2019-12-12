---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISEAddOnTool-objektet
ms.openlocfilehash: c71602d200b941ed4fb142b9c35f0fe68982e3e9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028995"
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="73c55-103">ISEAddOnTool-objektet</span><span class="sxs-lookup"><span data-stu-id="73c55-103">The ISEAddOnTool Object</span></span>

<span data-ttu-id="73c55-104">Ett **ISEAddonTool** -objekt representerar ett installerat tilläggs verktyg som tillhandahåller ytterligare funktioner TOWINDOWS PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="73c55-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="73c55-105">Ett exempel är **kommando** verktyget som du kan visa genom att klicka på **Visa**och sedan på **Visa kommando tillägg**.</span><span class="sxs-lookup"><span data-stu-id="73c55-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="73c55-106">Det här verktyget är sedan tillgängligt för dig genom att ändra de olika tillgängliga **ISEAddOnTool** -objekten.</span><span class="sxs-lookup"><span data-stu-id="73c55-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

<span data-ttu-id="73c55-107">Varje tilläggs verktyg kan associeras med antingen den lodräta rutan eller det vågräta fönstret.</span><span class="sxs-lookup"><span data-stu-id="73c55-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="73c55-108">Den lodräta rutan är dockad till den högra kanten av Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="73c55-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="73c55-109">Det vågräta fönstret är dockat till den nedre kanten.</span><span class="sxs-lookup"><span data-stu-id="73c55-109">The horizontal pane is docked to the bottom edge.</span></span>

<span data-ttu-id="73c55-110">Varje PowerShell-flik i Windows PowerShell ISE kan ha en egen uppsättning tilläggs verktyg installerade.</span><span class="sxs-lookup"><span data-stu-id="73c55-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="73c55-111">Se [$psISE. CurrentPowerShellTab. HorizontalAddOnTools](The-PowerShellTab-Object.md) och [$psISE. CurrentPowerShellTab. VerticalAddOnTools](The-PowerShellTab-Object.md) för att få åtkomst till samlingen med verktyg som är tillgängliga för den valda fliken eller samma egenskaper för alla **PowerShellTab** -objekt i objektet [$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md) -samling.</span><span class="sxs-lookup"><span data-stu-id="73c55-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="73c55-112">Metoder</span><span class="sxs-lookup"><span data-stu-id="73c55-112">Methods</span></span>

<span data-ttu-id="73c55-113">Det finns inga Windows PowerShell ISE-/regionsspecifika metoder som är tillgängliga för objekt i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="73c55-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="73c55-114">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="73c55-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="73c55-115">Kontroll</span><span class="sxs-lookup"><span data-stu-id="73c55-115">Control</span></span>

<span data-ttu-id="73c55-116">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="73c55-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="73c55-117">Egenskapen **Control** ger Läs behörighet till många av detaljerna för kommando rads verktyget för tillägg.</span><span class="sxs-lookup"><span data-stu-id="73c55-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### <a name="isvisible"></a><span data-ttu-id="73c55-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="73c55-118">IsVisible</span></span>

<span data-ttu-id="73c55-119">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="73c55-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="73c55-120">Den booleska egenskapen som anger om tilläggs verktyget är synligt i det tilldelade fönstret.</span><span class="sxs-lookup"><span data-stu-id="73c55-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="73c55-121">Om den är synlig kan du ange egenskapen **IsVisible** till **$false** för att dölja verktyget, eller ange egenskapen **IsVisible** till **$True** för att göra ett tilläggs verktyg synligt på dess PowerShell-flik. Observera att när ett tilläggs verktyg är dolt är det inte längre tillgängligt via **CurrentVisibleHorizontalTool** -eller **CurrentVisibleVerticalTool** -objekten och kan därför inte visas med hjälp av den här egenskapen för objektet.</span><span class="sxs-lookup"><span data-stu-id="73c55-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a><span data-ttu-id="73c55-122">Namn</span><span class="sxs-lookup"><span data-stu-id="73c55-122">Name</span></span>

<span data-ttu-id="73c55-123">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="73c55-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="73c55-124">Den skrivskyddade egenskapen som hämtar namnet på tilläggs verktyget.</span><span class="sxs-lookup"><span data-stu-id="73c55-124">The read-only property that gets the name of the add-on tool.</span></span>

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a><span data-ttu-id="73c55-125">Se även</span><span class="sxs-lookup"><span data-stu-id="73c55-125">See Also</span></span>

- [<span data-ttu-id="73c55-126">ISEAddOnToolCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="73c55-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="73c55-127">Syftet med Windows PowerShell ISE-skriptets objekt modell</span><span class="sxs-lookup"><span data-stu-id="73c55-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="73c55-128">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="73c55-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
