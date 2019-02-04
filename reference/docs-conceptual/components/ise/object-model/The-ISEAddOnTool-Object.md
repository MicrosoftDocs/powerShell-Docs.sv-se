---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISEAddOnTool-objektet
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687904"
---
# <a name="the-iseaddontool-object"></a>ISEAddOnTool-objektet

En **ISEAddonTool** -objektet representerar en installerade tilläggsverktyg som ger ytterligare funktioner toWindows PowerShell ISE. Ett exempel är den **kommandon** verktyg som du kan visa genom att klicka på **visa**, sedan **Visa kommandot tillägg**. Det här verktyget är sedan tillgängliga för dig genom att ändra de olika tillgängliga **ISEAddOnTool** objekt.

Varje tilläggsverktyg kan associeras med fönstret lodrät eller vågrät ruta. Den lodräta rutan är dockad till den högra kanten av Windows PowerShell ISE. Fönstret vågrät är dockad till nedre kant.

Varje PowerShell-flik i Windows PowerShell ISE kan ha en egen uppsättning tillägg tools har installerats. Se [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) och [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) till uppsättning av verktyg som är tillgängliga för den markerade fliken eller samma egenskaper på någon av de **PowerShellTab** objekt i den [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) samlingsobjektet.

## <a name="methods"></a>Metoder

Det finns inga Windows PowerShell ISE-specifika metoder tillgängliga för objekt i den här klassen.

## <a name="properties"></a>Egenskaper

### <a name="control"></a>Kontroll

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Den **kontroll** egenskapen ger läsåtkomst till många av information om kommandon tilläggsverktyg.

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

### <a name="isvisible"></a>IsVisible

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Den booleska egenskap som anger om verktyget tillägg är synliga i dess tilldelade rutan. Om den visas, kan du ange den **IsVisible** egenskap **$false** att dölja verktyget eller ange den **IsVisible** egenskap **$true** att göra ett tilläggsverktyg som är synliga på dess PowerShell-flik. Observera att när ett tilläggsverktyg är dold, är det inte längre är tillgängliga via den **CurrentVisibleHorizontalTool** eller **CurrentVisibleVerticalTool** objekt, och därför kan inte göras synliga med hjälp av den här egenskapen för objektet.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Namn

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som hämtar namnet på tilläggsverktyg.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a>Se även

- [The ISEAddOnToolCollection Object](The-ISEAddOnToolCollection-Object.md)
- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)