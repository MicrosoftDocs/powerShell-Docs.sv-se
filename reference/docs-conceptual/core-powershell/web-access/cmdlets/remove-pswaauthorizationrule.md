---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: ta bort pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: a8304b68a446de0be98aa732304c71302fb8389e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>SAMMANFATTNING

Tar bort en angiven auktoriseringsregel från Windows PowerShell® Web Access.

## <a name="syntax"></a>SYNTAX

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Regeln
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESKRIVNING

Tar bort en angiven auktoriseringsregel från Windows PowerShell Web Access.

## <a name="parameters"></a>PARAMETRAR

### <a name="-force"></a>-Force

Kör cmdleten utan att fråga efter bekräftelse. Som standard begär cmdlet bekräftelse innan du fortsätter.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

Anger identifierare (ID) av en eller flera regler för att ta bort.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | 2                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByValue, ByPropertyName)       |
| Acceptera jokertecken?          | falskt                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Regel &lt;PswaAuthorizationRule\[\]&gt;

Anger regler för att ta bort.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | 2                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByValue)                       |
| Acceptera jokertecken?          | falskt                                |

### <a name="-confirm"></a>-Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

|||  
|-|-|
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | falskt                                |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-whatif"></a>-WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

|||  
|-|-|
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | falskt                                |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.
Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INDATA

### <a name="int"></a>int\[\]

Denna cmdlet accepterar en heltalsmatris eller en matris med PswaAuthorizationRule-objekt.

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

Denna cmdlet accepterar en heltalsmatris eller en matris med PswaAuthorizationRule-objekt.

## <a name="outputs"></a>UTDATA

Denna cmdlet ger inga utdata.

## <a name="examples"></a>EXEMPEL

### <a name="example-1"></a>EXEMPEL 1

Det här exemplet tar bort auktoriseringsregeln med ID *2*.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>EXEMPEL 2 {#example-2 .subHeading}

Det här exemplet tar bort alla auktoriseringsregler och kräver bekräftelse av användaren.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>Närliggande information

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
