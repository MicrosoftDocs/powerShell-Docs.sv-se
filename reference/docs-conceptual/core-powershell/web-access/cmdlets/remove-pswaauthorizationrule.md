---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: ta bort pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

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
| Obligatorisk?                            | true                                 |
| Placering?                            | 2                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByValue, ByPropertyName)       |
| Acceptera jokertecken?          | falskt                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Regel &lt;PswaAuthorizationRule\[\]&gt;

Anger regler för att ta bort.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | true                                 |
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
