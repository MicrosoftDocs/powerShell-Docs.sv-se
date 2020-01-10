---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISEAddOnTool-objektet
ms.openlocfilehash: a5357005ec1a883f5a14882a42e3150e09ff33a2
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736138"
---
# <a name="the-iseaddontool-object"></a>ISEAddOnTool-objektet

Ett **ISEAddonTool** -objekt representerar ett installerat tilläggs verktyg som tillhandahåller ytterligare funktioner TOWINDOWS PowerShell ISE. Ett exempel är **kommando** verktyget som du kan visa genom att klicka på **Visa**och sedan på **Visa kommando tillägg**. Det här verktyget är sedan tillgängligt för dig genom att ändra de olika tillgängliga **ISEAddOnTool** -objekten.

Varje tilläggs verktyg kan associeras med antingen den lodräta rutan eller det vågräta fönstret. Den lodräta rutan är dockad till den högra kanten av Windows PowerShell ISE. Det vågräta fönstret är dockat till den nedre kanten.

Varje PowerShell-flik i Windows PowerShell ISE kan ha en egen uppsättning tilläggs verktyg installerade. Se [$psISE. CurrentPowerShellTab. HorizontalAddOnTools](The-PowerShellTab-Object.md) och [$psISE. CurrentPowerShellTab. VerticalAddOnTools](The-PowerShellTab-Object.md) för att få åtkomst till samlingen med verktyg som är tillgängliga för den valda fliken eller samma egenskaper för alla **PowerShellTab** -objekt i objektet [$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md) -samling.

## <a name="methods"></a>Metoder

Det finns inga Windows PowerShell ISE-/regionsspecifika metoder som är tillgängliga för objekt i den här klassen.

## <a name="properties"></a>Egenskaper

### <a name="control"></a>Kontroll

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Egenskapen **Control** ger Läs behörighet till många av detaljerna för kommando rads verktyget för tillägg.

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
```

```Output
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

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Den booleska egenskapen som anger om tilläggs verktyget är synligt i det tilldelade fönstret. Om den är synlig kan du ange egenskapen **IsVisible** till `$false` för att dölja verktyget, eller ange egenskapen **IsVisible** till `$true` för att göra ett tilläggs verktyg synligt på dess PowerShell-flik. Observera att när ett tilläggs verktyg är dolt är det inte längre tillgängligt via **CurrentVisibleHorizontalTool** -eller **CurrentVisibleVerticalTool** -objekten och kan därför inte visas med hjälp av den här egenskapen för objektet.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Namn

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som hämtar namnet på tilläggs verktyget.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
```

```Output
Commands
```

## <a name="see-also"></a>Se även

- [ISEAddOnToolCollection-objektet](The-ISEAddOnToolCollection-Object.md)
- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
