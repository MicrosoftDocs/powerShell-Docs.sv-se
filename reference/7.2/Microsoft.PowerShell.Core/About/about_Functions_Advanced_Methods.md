---
description: Beskriver hur funktioner som anger `CmdletBinding` attributet kan använda de metoder och egenskaper som är tillgängliga för kompilerade cmdlets.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 13a9d7258f1a52d5fcbb2d8c55b91c8d6454452d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94711017"
---
# <a name="about-functions-advanced-methods"></a>Om functions avancerade metoder

## <a name="short-description"></a>Kort beskrivning

Beskriver hur funktioner som anger `CmdletBinding` attributet kan använda de metoder och egenskaper som är tillgängliga för kompilerade cmdlets.

## <a name="long-description"></a>Lång beskrivning

Funktioner som anger `CmdletBinding` attributet kan komma åt ett antal metoder och egenskaper via `$PSCmdlet` variabeln. Dessa metoder omfattar följande metoder:

- Ingångs bearbetnings metoder som kompilerade cmdlets använder för att utföra sitt arbete.
- `ShouldProcess`Metoderna och `ShouldContinue` som används för att få feedback från användaren innan en åtgärd utförs.
- `ThrowTerminatingError`Metoden för att generera fel poster.
- Flera `Write` metoder som returnerar olika typer av utdata.

Alla metoder och egenskaper för **PSCmdlet** -klassen är tillgängliga för avancerade funktioner. Mer information finns i [system. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).

Mer information om `CmdletBinding` attributet finns i [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).
**CmdletBindingAttribute** -klassen finns i [system. Management. Automation. cmdlet. CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute).

### <a name="input-processing-methods"></a>Metoder för bearbetning av indata

De metoder som beskrivs i det här avsnittet kallas för metoder för bearbetning av indata. För functions representeras dessa tre metoder av `Begin` `Process` funktionens,-och- `End` block. Du behöver inte använda något av dessa block i funktionerna.

> [!NOTE]
> Dessa block är också tillgängliga för funktioner som inte använder- `CmdletBinding` attributet.

#### <a name="begin"></a>Börja

Det här blocket används för att tillhandahålla valfri för bearbetning av en gång för funktionen.
PowerShell-körningen använder koden i det här blocket en gång för varje instans av funktionen i pipelinen.

#### <a name="process"></a>Process

Det här blocket används för att tillhandahålla post-för-post-bearbetning för funktionen. Du kan använda ett `Process` block utan att definiera de andra blocken. Antalet `Process` block körningar beror på hur du använder funktionen och vilka indatatyper funktionen tar emot.

Den automatiska variabeln `$_` eller `$PSItem` innehåller det aktuella objektet i pipelinen för användning i `Process` blocket. Den `$input` automatiska variabeln innehåller en uppräknare som endast är tillgänglig för funktioner och skript block.
Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).

- Genom att anropa funktionen i början eller utanför en pipeline körs `Process` blocket en gång.
- I en pipeline `Process` körs blocket en gång för varje indatamängd som når funktionen.
- Om pipeline-inflödet som når funktionen är tom `Process` körs **inte** blocket.
  - `Begin`Och- `End` blocken körs fortfarande.

> [!IMPORTANT]
> Om en funktions parameter är inställd på att acceptera pipeline-indata och ett `Process` block inte har definierats, kommer post by post-bearbetningen inte att fungera. I det här fallet körs bara en gång, oavsett inaktuella inuppgifter.

#### <a name="end"></a>Slut

Det här blocket används för att ge en valfri efter bearbetning för funktionen.

I följande exempel visas dispositionen för en funktion som innehåller ett `Begin` block för för bearbetning av en gång, ett `Process` block för bearbetning av flera poster och ett `End` block för bearbetning efter bearbetning i taget.

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> Om du använder antingen ett- `Begin` eller- `End` block måste du definiera alla tre blocken. När du använder alla tre blocken måste all PowerShell-kod finnas i ett av blocken.

### <a name="confirmation-methods"></a>Bekräftelse metoder

#### <a name="shouldprocess"></a>ShouldProcess

Den här metoden anropas för att begära bekräftelse från användaren innan funktionen utför en åtgärd som skulle ändra systemet. Funktionen kan fortsätta baserat på det booleska värde som returnerades av metoden. Den här metoden kan endast anropas från `Process{}` blocket för funktionen. `CmdletBinding`Attributet måste också deklarera att funktionen stöder `ShouldProcess` (som visas i föregående exempel).

Mer information om den här metoden finns i [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess).

Mer information om hur du begär en bekräftelse finns i [be om bekräftelse](/powershell/scripting/developer/cmdlet/requesting-confirmation).

#### <a name="shouldcontinue"></a>ShouldContinue

Den här metoden anropas för att begära ett andra bekräftelse meddelande. Den ska anropas när `ShouldProcess` metoden returnerar `$true` . Mer information om den här metoden finns i [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).

### <a name="error-methods"></a>Fel metoder

Funktioner kan anropa två olika metoder när fel inträffar. När ett icke-avslutande fel inträffar ska funktionen anropa `WriteError` metoden, som beskrivs i `Write` avsnittet metoder. När ett avslutande fel inträffar och funktionen inte kan fortsätta bör den anropa- `ThrowTerminatingError` metoden. Du kan också använda `Throw` instruktionen för att avsluta fel och cmdleten [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) för icke-avslutande fel.

Mer information finns i [system. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror).

### <a name="write-methods"></a>Skriv metoder

En funktion kan anropa följande metoder för att returnera olika typer av utdata.
Observera att inte alla utdata går till nästa-kommando i pipelinen. Du kan också använda olika `Write` cmdlets, till exempel `Write-Error` .

#### <a name="writecommanddetail"></a>WriteCommandDetail

Information om `WriteCommandDetails` -metoden finns i [system. Management. Automation. cmdlet. WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail).

#### <a name="writedebug"></a>WriteDebug

Om du vill ange information som kan användas för att felsöka en funktion kan du anropa-funktionen anropa `WriteDebug` metoden. `WriteDebug`Metoden visar fel söknings meddelanden för användaren. Mer information finns i [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug).

#### <a name="writeerror"></a>WriteError

Funktioner ska anropa den här metoden när icke-avslutande fel inträffar och funktionen är utformad för att fortsätta bearbeta poster. Mer information finns i [system. Management. Automation. cmdlet. WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror).

> [!NOTE]
> Om ett avslutande fel inträffar ska funktionen anropa [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) -metoden.

#### <a name="writeobject"></a>WriteObject

`WriteObject`Metoden gör att funktionen kan skicka ett objekt till nästa-kommando i pipelinen. I de flesta fall `WriteObject` är metoden som ska användas när funktionen returnerar data. Mer information finns i [system. Management. Automation. PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).

#### <a name="writeprogress"></a>WriteProgress

För funktioner med åtgärder som tar lång tid att slutföra, tillåter den här metoden att funktionen anropar `WriteProgress` metoden så att information om förloppet visas. Du kan till exempel Visa procent andelen som slutförts.
Mer information finns i [system. Management. Automation. PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).

#### <a name="writeverbose"></a>WriteVerbose

Om du vill ha detaljerad information om vad funktionen gör kan du göra så att funktionen anropar `WriteVerbose` metoden för att Visa utförliga meddelanden för användaren. Som standard visas inte utförliga meddelanden. Mer information finns i [system. Management. Automation. PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).

#### <a name="writewarning"></a>WriteWarning

Om du vill ange information om villkor som kan orsaka oväntade resultat kan du använda funktionen anropa WriteWarning-metoden för att Visa varnings meddelanden för användaren. Varnings meddelanden visas som standard. Mer information finns i [system. Management. Automation. PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).

> [!NOTE]
> Du kan också Visa varnings meddelanden genom `$WarningPreference` att konfigurera variabeln eller genom att använda `Verbose` `Debug` kommando rads alternativen och. Mer information om `$WarningPreference` variabeln finns i [about_Preference_Variables](about_Preference_Variables.md).

### <a name="other-methods-and-properties"></a>Andra metoder och egenskaper

Information om andra metoder och egenskaper som kan nås via `$PSCmdlet` variabeln finns i [system. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).

Egenskapen [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) låter dig till exempel se den parameter uppsättning som används. Med parameter uppsättningar kan du skapa en funktion som utför olika uppgifter baserat på de parametrar som anges när funktionen körs.

## <a name="see-also"></a>Se även

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Preference_Variables](about_Preference_Variables.md)

