---
description: Stöd för experimentella funktioner i PowerShell är en mekanism för experimentella funktioner som kan användas tillsammans med befintliga stabila funktioner i PowerShell-eller PowerShell-moduler.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om experimentella funktioner
ms.openlocfilehash: e53af155c2a8691e2e4d4cc6f47bfd5932801db9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272421"
---
# <a name="experimental-features"></a>Experimentella funktioner

Stöd för experimentella funktioner i PowerShell är en mekanism för experimentella funktioner som kan användas tillsammans med befintliga stabila funktioner i PowerShell-eller PowerShell-moduler.

En experimentell funktion är en där designen inte har slutförts. Funktionen är tillgänglig för användare att testa och ge feedback. När en experimentell funktion har slutförts blir design ändringarna ändringar. Experimentella funktioner är inte avsedda att användas i produktion eftersom ändringarna kan avbrytas.

Experimentella funktioner är inaktiverade som standard och måste aktive ras explicit av användaren eller administratören av systemet.

Aktiverade experimentella funktioner visas i `powershell.config.json` filen i `$PSHOME` för alla användare eller i den användarspecifika konfigurations filen för en speciell användare.

> [!NOTE]
> Experimentella funktioner som är aktiverade i användar konfigurations filen prioriteras framför experimentella funktioner som anges i system konfigurations filen.

## <a name="the-experimental-attribute"></a>Det experimentella attributet

Använd `Experimental` attributet för att deklarera kod som experiment.

Använd följande syntax för att deklarera `Experimental` attributet som tillhandahåller namnet på experimentell funktion och åtgärden som ska vidtas om experimentell funktion är aktive rad:

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

För moduler måste du `NameOfExperimentalFeature` följa formuläret för `<modulename>.<experimentname>` . `ExperimentAction`Parametern måste anges och de enda giltiga värdena är:

- `Show` innebär att du kan visa den här experimentella funktionen om funktionen är aktive rad
- `Hide` innebär att du kan dölja den här experimentella funktionen om funktionen är aktive rad

### <a name="declaring-experimental-features-in-modules-written-in-c"></a>Deklarera experimentella funktioner i moduler som skrivits i C\#

De utvecklare som vill använda experimentella funktions flaggor kan deklarera en cmdlet som experiment genom att använda- `Experimental` attributet.

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a>Deklarera experimentella funktioner i moduler som skrivits i PowerShell

En modul som skrivits i PowerShell kan också använda `Experimental` attributet för att deklarera experimentella cmdlets:

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a>Ömsesidigt uteslutande experimentella funktioner

Det finns fall där en experimentell funktion inte kan befinna sig sida vid sida med en befintlig funktion eller en annan experimentell funktion.

Du kan till exempel ha en experimentell cmdlet som åsidosätter en befintlig cmdlet. De två versionerna kan inte finnas sida vid sida. `ExperimentAction.Hide`Inställningen tillåter bara att en av de två cmdletarna är aktive rad i taget.

I det här exemplet skapar vi en ny experimentell `Invoke-WebRequest` cmdlet.
`InvokeWebRequestCommand` innehåller den icke-experimentella implementeringen.
`InvokeWebRequestCommandV2` innehåller experimentell version av cmdleten.

Användningen av `ExperimentAction.Hide` tillåter endast att en av de två funktionerna aktive ras vid en tidpunkt:

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

När `MyWebCmdlets.PSWebCmdletV2` experimentell funktion är aktive rad är den befintliga `InvokeWebRequestCommand` implementeringen dold och `InvokeWebRequestCommandV2` ger implementeringen av `Invoke-WebRequest` .

Detta gör att användarna kan prova den nya cmdleten och ge feedback och sedan återgå till den icke-experimentella versionen när det behövs.

### <a name="experimental-parameters-in-cmdlets"></a>Experimentella parametrar i cmdletar

`Experimental`Attributet kan också tillämpas på enskilda parametrar. På så sätt kan du skapa en experimentell uppsättning parametrar för en befintlig cmdlet i stället för en helt ny cmdlet.

Här är ett exempel i C#:

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

Här är ett annat exempel i PowerShell-skript:

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a>Kontrollerar om en experimentell funktion är aktive rad

I din kod måste du kontrol lera om din experimentella funktion är aktive rad innan du vidtar lämpliga åtgärder. Du kan avgöra om en experimentell funktion är aktive rad med den statiska `IsEnabled()` metoden i `System.Management.Automation.ExperimentalFeature` klassen.

Här är ett exempel i C#:

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

Här är ett exempel i PowerShell-skript:

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a>Se även

[Aktivera – ExperimentalFeature](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[Disable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[Get-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)
