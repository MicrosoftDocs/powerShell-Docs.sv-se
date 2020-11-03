---
description: Beskriver ett språk kommando som du kan använda för att köra instruktions listor baserat på resultatet av en eller flera villkorliga tester.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 33c0050cb5f8c3dfa623213b288ef3a84d10099d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270182"
---
# <a name="about-if"></a>Om

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver ett språk kommando som du kan använda för att köra instruktions listor baserat på resultatet av en eller flera villkorliga tester.

## <a name="long-description"></a>LÅNG BESKRIVNING

Du kan använda `If` instruktionen för att köra kodblock om ett angivet villkorligt test utvärderas till sant. Du kan också ange en eller flera ytterligare villkorliga tester som ska köras om alla tidigare tester utvärderas till false. Slutligen kan du ange ytterligare ett kodblock som körs om inga andra tidigare villkorliga test utvärderas som sant.

### <a name="syntax"></a>Syntax

I följande exempel visas `If` syntaxen för uttrycket:

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

När du kör en `If` instruktion utvärderar PowerShell `<test1>` villkors uttrycket som sant eller falskt. Om `<test1>` är true, `<statement list 1>` körs och PowerShell avslutar `If` instruktionen. Om `<test1>` är falskt utvärderar PowerShell det villkor som anges av `<test2>` villkors instruktionen.

Om `<test2>` är true, `<statement list 2>` körs och PowerShell avslutar `If` instruktionen. Om både `<test1>` och `<test2>` utvärderas till false `<statement list 3` körs det> kod blocket och PowerShell avslutar IF-instruktionen.

Du kan använda flera ElseIf-instruktioner för att kedja samman en serie villkorliga tester. Så att varje test bara körs om alla tidigare tester är falska.
Om du behöver skapa en `If` instruktion som innehåller många ElseIf-instruktioner bör du använda en switch-instruktion i stället.

Exempel:

Den enklaste `If` instruktionen innehåller ett enda kommando och innehåller inte några ElseIf-instruktioner eller andra instruktioner. I följande exempel visas den enklaste formen av `If` instruktionen:

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

I det här exemplet, om variabeln $a är större än 2, utvärderas villkoret till sant och instruktions listan körs. Men om $a är mindre än eller lika med 2 eller inte är en befintlig variabel `If` visas inget meddelande i instruktionen.

Genom att lägga till en Else-instruktion visas ett meddelande när $a är mindre än eller lika med 2. Som nästa exempel visar:

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

För att ytterligare förfina det här exemplet kan du använda ElseIf-instruktionen för att visa ett meddelande när värdet för $a är lika med 2. Som nästa exempel visar:

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

### <a name="using-the-ternary-operator-syntax"></a>Använda syntaxen för ternär operator

PowerShell 7,0 introducerade en ny syntax med ternär operatorn. Det följer syntaxen för C# ternär operator:

```Syntax
<condition> ? <if-true> : <if-false>
```

Ternär operatorn beter sig som den förenklade `if-else` instruktionen. `<condition>`Uttrycket utvärderas och resultatet konverteras till ett booleskt värde för att avgöra vilken gren som ska utvärderas härnäst:

- `<if-true>`Uttrycket körs om `<condition>` uttrycket är sant
- `<if-false>`Uttrycket körs om `<condition>` uttrycket är falskt

Ett exempel:

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

I det här exemplet `$message` finns värdet "sökväg finns" när `Test-Path` returnerar `$true` . När `Test-Path` returnerar returneras `$false` `$message` "sökvägen hittades inte".

```powershell
$service = Get-Service BITS
$service.Status -eq 'Running' ? (Stop-Service $service) : (Start-Service $service)
```

I det här exemplet, om tjänsten körs, stoppas den, och om dess **status inte är igång startas** den.

## <a name="see-also"></a>SE ÄVEN

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Switch](about_Switch.md)

