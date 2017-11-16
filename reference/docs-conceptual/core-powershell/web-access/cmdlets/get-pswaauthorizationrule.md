---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: "Hämta pswaauthorizationrule"
ms.technology: powershell
ms.openlocfilehash: eb9f42ab4d9cec111e03a096b2f00740e97ee1b7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>SAMMANFATTNING

Returnerar en uppsättning auktoriseringsregler för Windows PowerShell® Web Access.

## <a name="syntax"></a>Syntax

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>Namn
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>BESKRIVNING

Den **Get-PswaAuthorizationRule** cmdlet returnerar en uppsättning auktoriseringsregler för Windows PowerShell® Web Access.
Om varken den **Id** parametern eller **RuleName** parametern anges, och den här cmdleten visar alla regler. Den **Id** parametern kan användas för att filtrera resultaten.

## <a name="parameters"></a>PARAMETRAR

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Anger identifierare (ID) av regler som denna cmdlet ska få. Om inga-ID har angetts returnerar den här cmdleten alla auktoriseringsregler.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | 2                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByValue, ByPropertyName)       |
| Acceptera jokertecken?          | falskt                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;sträng\[\]&gt;

Anger namn på auktoriseringsregler för att hämta. Den här parametern returnerar de regler som matchar exakt Regelnamn strängar i denna matris.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | 2                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByValue, ByPropertyName)       |
| Acceptera jokertecken?          | falskt                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.
Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INDATA

### <a name="int"></a>int\[\]

Denna cmdlet accepterar en heltalsmatris eller en matris med strängvärden som indata.

### <a name="string"></a>Sträng\[\]

Denna cmdlet accepterar en heltalsmatris eller en matris med strängvärden som indata.

## <a name="outputs"></a>UTDATA

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Denna cmdlet ger ett PswaAuthorizationRule-objekt som utdata.


## <a name="examples"></a>EXEMPEL

### <a name="example-1"></a>EXEMPEL 1

Det här exemplet hämtar alla regler.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>EXEMPEL 2

Det här exemplet hämtar en regel med ID *2*.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>EXEMPEL 3 {#example-3 .subHeading}

Det här exemplet illustrerar hur cmdlet accepterar ett värde från pipeline.
Regel-id och ett namn för regeln skickas i denna cmdlet.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>Närliggande information

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
