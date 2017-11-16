---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: b813fcac547c8069e84741081a3ceb00044bab87
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseaddontool-object"></a>Objektet ISEAddOnTool
  En **ISEAddonTool** -objektet representerar ett installerat tilläggsverktyg som ger ytterligare funktioner toWindows PowerShell ISE. Ett exempel är den **kommandon** verktyg som du kan visa genom att klicka på **visa**, sedan **Visa kommandot tillägg**. Det här verktyget är sedan tillgängliga för dig genom att ändra de olika tillgängliga **ISEAddOnTool** objekt.

 Varje tilläggsverktyg kan associeras med fönstret lodrät eller vågrät ruta. Den lodräta rutan dockas till högra kanten av Windows PowerShell ISE. Den vågräta rutan dockas till nedre kant.

 Varje PowerShell-flik i Windows PowerShell ISE kan ha en egen uppsättning tilläggsverktyg installerad. Se [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) och [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) åtkomst till samlingen av verktyg som är tillgängliga för den markerade fliken eller samma egenskaper på någon av de **PowerShellTab** objekt i den [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) samlingsobjektet.

## <a name="methods"></a>Metoder
 Det finns inga Windows PowerShell ISE-specifika metoder tillgängliga för objekt i den här klassen.

## <a name="properties"></a>Egenskaper

### <a name="control"></a>Kontroll
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Den **kontrollen** egenskapen ger läsbehörighet till många av information om kommandon tilläggsverktyg.

```
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

### <a name="isvisible"></a>IsVisible
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Boolesk egenskap som anger om verktyget tillägg är synliga i dess tilldelade rutan. Du kan ange om den är synlig i **IsVisible** egenskapen **$false** att dölja verktyget eller ange den **IsVisible** egenskapen **$true** att göra ett tilläggsverktyg som visas i PowerShell på fliken. Observera att när ett tilläggsverktyg är dold kan den inte längre tillgängligt via den **CurrentVisibleHorizontalTool** eller **CurrentVisibleVerticalTool** objekt och därför kan inte göras synligt med hjälp av den här egenskapen för objektet.

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

### <a name="name"></a>Namn
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Den skrivskyddade egenskapen som hämtar namnet på tilläggsverktyg.

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## <a name="see-also"></a>Se även
- [Objektet ISEAddOnToolCollection](The-ISEAddOnToolCollection-Object.md)
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)

