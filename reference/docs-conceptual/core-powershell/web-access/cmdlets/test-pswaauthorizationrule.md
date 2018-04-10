---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: ed6d56b2f3c4ee4ac410cdaadda312bffe506ee9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Kontrollerar om det finns en regel för en specifik användare, dator eller slutpunkt.

## <a name="syntax"></a>SYNTAX

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>BESKRIVNING

Den **Test-PswaAuthorizationRule** cmdlet kontrollerar om det finns en regel för en specifik användare, dator eller slutpunkt.
Denna cmdlet kan också användas för att testa auktoriseringsregler för att verifiera att en viss användare, dator eller slutpunkt åtkomst-begäran är auktoriserad.
Som standard utvärderar den här cmdleten alla regler i auktoriseringsfilen.
Du kan dock ange en delmängd av regler som ska testas.

Du kan använda denna cmdlet för att felsöka autentiseringsfel.

Parametrarna för denna cmdlet motsvarar fälten på sidan Windows PowerShell® Web Access inloggning.

## <a name="parameters"></a>PARAMETRAR

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;sträng&gt;

Anger namnet på datorn för att testa.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | true                                 |
| Placering?                            | 2                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;sträng&gt;

Anger namnet på sessionskonfigurationen Windows PowerShell, även kallat endpoint eller runspace, om du vill testa.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | 3                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;Uri&gt;

Anger URI för att testa anslutningen.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | true                                 |
| Placering?                            | 2                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Anger en **PSCredential** objekt för ett användarkonto som du vill använda för att testa Windows PowerShell Web Access auktoriseringsregler. Om du inte lägga till den här parametern används cmdlet det inloggade användarkontot. Få en **PSCredential** -objektet, vilket krävs för att testa auktoriseringsregler från en fjärrdator, kör den [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Regel &lt;PswaAuthorizationRule\[\]&gt;

Anger en delmängd av regler som ska testas. Om den här parametern anges, testar denna cmdlet mot alla auktoriseringsregler.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByValue)                       |
| Acceptera jokertecken?          | falskt                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;sträng&gt;

Anger namnet på användaren att testa.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | true                                 |
| Placering?                            | 1                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.
Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INDATA

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Denna cmdlet accepterar en matris med PswaAuthorizationRule-objekt som indata.

## <a name="outputs"></a>UTDATA

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Denna cmdlet ger en matris med PswaAuthorizationRule objekt som utdata.

## <a name="examples"></a>EXEMPEL

### <a name="example-1"></a>EXEMPEL 1

Det här exemplet testar alla auktoriseringsregler för att visa alla regler som tillåter att användaren *contoso\\mhanson* att ansluta till datorn *srv2* och använda Windows PowerShell-sessionen konfiguration med namnet *testa*.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>EXEMPEL 2

Det här exemplet testerna alla auktoriseringsregler för att kontrollera vilka auktoriseringsregler som gäller för användaren *contoso\\mhanson*.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>Närliggande information

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)