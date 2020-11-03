---
description: Beskriver ett språk kommando som du kan använda för att köra instruktions listor baserat på resultatet av en eller flera villkorliga tester.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 8b1be96167dab47e7e15e3e5b89c46126f117541
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272109"
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

## <a name="see-also"></a>SE ÄVEN

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Switch](about_Switch.md)
