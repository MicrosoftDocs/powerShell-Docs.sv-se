---
description: Introducerar avancerade funktioner som är ett sätt att skapa cmdlets med hjälp av skript.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: 8f6964ee0b916163ea18e20ddbdf95d68e24f3fa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272576"
---
# <a name="about-functions-advanced"></a>Om functions Advanced

## <a name="short-description"></a>KORT BESKRIVNING
Introducerar avancerade funktioner som är ett sätt att skapa cmdlets med hjälp av skript.

## <a name="long-description"></a>LÅNG BESKRIVNING

En cmdlet är ett enda kommando som ingår i pipeline-semantiken för PowerShell. Detta inkluderar binära cmdlets, avancerade skript funktioner, CDXLM och arbets flöden.

Med avancerade funktioner kan du skapa cmdlets som är skrivna som en PowerShell-funktion. Med avancerade funktioner blir det enklare att skapa cmdlets utan att behöva skriva och kompilera en binär cmdlet. Binära cmdlets är .NET-klasser som är skrivna på ett .NET-språk, till exempel C#.

Avancerade funktioner använder `CmdletBinding` attributet för att identifiera dem som funktioner som fungerar som cmdlets. `CmdletBinding`Attributet liknar det cmdlet-attribut som används i kompilerade cmdlet-klasser för att identifiera klassen som en cmdlet. Mer information om det här attributet finns [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).

I följande exempel visas en funktion som accepterar ett namn och som sedan skriver ut en hälsning med det angivna namnet. Observera också att den här funktionen definierar ett namn som innehåller ett verb-(Send) och Substantiv-par (hälsning), som verb-Substantiv-paret för en kompilerad cmdlet. Funktioner behöver dock inte ha ett verb-Substantiv-namn.

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

Parametrarna för funktionen deklareras genom att använda attributet parameter.
Det här attributet kan endast användas eller kombineras med attributet alias eller med flera andra parametrar för parameter verifiering. Mer information om hur du deklarerar parametrar (inklusive dynamiska parametrar som läggs till vid körning) finns i [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

Det faktiska arbetet i föregående funktion utförs i process blocket, vilket motsvarar metoden ProcessingRecord som används av kompilerade cmdlets för att bearbeta data som skickas till cmdleten. Det här blocket, tillsammans med start-och slut blocken, beskrivs i [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) avsnittet.

Avancerade funktioner skiljer sig från kompilerade cmdlets på följande sätt:

- Den avancerade funktions parameter bindningen genererar inget undantag när en sträng mat ris är bunden till en boolesk parameter.
- Attributet ValidateSet och ValidatePattern kan inte skicka namngivna parametrar.
- Det går inte att använda avancerade funktioner i transaktioner.

## <a name="see-also"></a>SE ÄVEN

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
