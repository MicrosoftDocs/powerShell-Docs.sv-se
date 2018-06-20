---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: ISEAddOnTool-objektet
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954814"
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="2b282-103">ISEAddOnTool-objektet</span><span class="sxs-lookup"><span data-stu-id="2b282-103">The ISEAddOnTool Object</span></span>

<span data-ttu-id="2b282-104">En **ISEAddonTool** -objektet representerar ett installerat tilläggsverktyg som ger ytterligare funktioner toWindows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b282-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="2b282-105">Ett exempel är den **kommandon** verktyg som du kan visa genom att klicka på **visa**, sedan **Visa kommandot tillägg**.</span><span class="sxs-lookup"><span data-stu-id="2b282-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="2b282-106">Det här verktyget är sedan tillgängliga för dig genom att ändra de olika tillgängliga **ISEAddOnTool** objekt.</span><span class="sxs-lookup"><span data-stu-id="2b282-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

<span data-ttu-id="2b282-107">Varje tilläggsverktyg kan associeras med fönstret lodrät eller vågrät ruta.</span><span class="sxs-lookup"><span data-stu-id="2b282-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="2b282-108">Den lodräta rutan dockas till högra kanten av Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b282-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="2b282-109">Den vågräta rutan dockas till nedre kant.</span><span class="sxs-lookup"><span data-stu-id="2b282-109">The horizontal pane is docked to the bottom edge.</span></span>

<span data-ttu-id="2b282-110">Varje PowerShell-flik i Windows PowerShell ISE kan ha en egen uppsättning tilläggsverktyg installerad.</span><span class="sxs-lookup"><span data-stu-id="2b282-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="2b282-111">Se [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) och [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) åtkomst till samlingen av verktyg som är tillgängliga för den markerade fliken eller samma egenskaper på någon av de **PowerShellTab** objekt i den [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) samlingsobjektet.</span><span class="sxs-lookup"><span data-stu-id="2b282-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="2b282-112">Metoder</span><span class="sxs-lookup"><span data-stu-id="2b282-112">Methods</span></span>

<span data-ttu-id="2b282-113">Det finns inga Windows PowerShell ISE-specifika metoder tillgängliga för objekt i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="2b282-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="2b282-114">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="2b282-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="2b282-115">Kontroll</span><span class="sxs-lookup"><span data-stu-id="2b282-115">Control</span></span>

<span data-ttu-id="2b282-116">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="2b282-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="2b282-117">Den **kontrollen** egenskapen ger läsbehörighet till många av information om kommandon tilläggsverktyg.</span><span class="sxs-lookup"><span data-stu-id="2b282-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

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

### <a name="isvisible"></a><span data-ttu-id="2b282-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="2b282-118">IsVisible</span></span>

<span data-ttu-id="2b282-119">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="2b282-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="2b282-120">Boolesk egenskap som anger om verktyget tillägg är synliga i dess tilldelade rutan.</span><span class="sxs-lookup"><span data-stu-id="2b282-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="2b282-121">Du kan ange om den är synlig i **IsVisible** egenskapen **$false** att dölja verktyget eller ange den **IsVisible** egenskapen **$true** att göra ett tilläggsverktyg som visas i PowerShell på fliken. Observera att när ett tilläggsverktyg är dold kan den inte längre tillgängligt via den **CurrentVisibleHorizontalTool** eller **CurrentVisibleVerticalTool** objekt och därför kan inte göras synligt med hjälp av den här egenskapen för objektet.</span><span class="sxs-lookup"><span data-stu-id="2b282-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a><span data-ttu-id="2b282-122">Namn</span><span class="sxs-lookup"><span data-stu-id="2b282-122">Name</span></span>

<span data-ttu-id="2b282-123">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="2b282-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="2b282-124">Den skrivskyddade egenskapen som hämtar namnet på tilläggsverktyg.</span><span class="sxs-lookup"><span data-stu-id="2b282-124">The read-only property that gets the name of the add-on tool.</span></span>

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a><span data-ttu-id="2b282-125">Se även</span><span class="sxs-lookup"><span data-stu-id="2b282-125">See Also</span></span>

- [<span data-ttu-id="2b282-126">Objektet ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="2b282-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="2b282-127">Syftet med Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="2b282-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2b282-128">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="2b282-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)