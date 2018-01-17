---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: avinstallera pswawebapplication
ms.technology: powershell
ms.openlocfilehash: cc54c94426d754ff2d3bf658e3e92083f02cd6c7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

## <a name="synopsis"></a>SYNOPSIS

Avinstallerar Windows PowerShell® webbprogrammet.

## <a name="syntax"></a>SYNTAX

### <a name="default"></a>Standard
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESKRIVNING

Den **Uninstall-PswaWebApplication** cmdlet avinstallerar Windows PowerShell-webbprogram och tar bort webbplatsen från IIS. Cmdlet avinstallerar inte IIS eller andra funktioner som installeras eftersom de var krävs för Windows PowerShell för att köra.

## <a name="parameters"></a>PARAMETRAR

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Anger att testcertifikat som skapats av den **installera\_PswaWebApplication** cmdlet (med den **UseTestCertificate** parametern) tas bort.
Endast Testcertifikatet med samma namn som skapas av den **Install-PswaWebApplication** cmdlet tas bort.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | true                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;sträng&gt;

Anger namnet på webbprogrammet för att avinstallera.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | 1                                    |
| Standardvärde                        | pswa                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;sträng&gt;

Anger namnet på webbplatsen där webbprogrammet är installerat.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | Default Web Site                     |
| Acceptera pipelineindata?               | falskt                                |
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

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

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

Den här cmdleten tar inga indata.

## <a name="outputs"></a>UTDATA

Den här cmdleten returnerar inga utdata.

## <a name="examples"></a>EXEMPEL

### <a name="example-1"></a>EXEMPEL 1

Det här kommandot avinstallerar webbprogrammet för Windows PowerShell.
Du kan använda denna cmdlet för att avinstallera Windows PowerShell-webbprogrammet om du har installerat den med standardvärden.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>EXEMPEL 2

Det här kommandot avinstallerar Windows PowerShell-webbprogram och tar bort testcertifikat som är associerade med applikationen.
Du kan använda denna cmdlet för att avinstallera Windows PowerShell-webbprogrammet om du har installerat den med hjälp av standardinställningarna och skapa ett testcertifikat.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>EXEMPEL 3 {#example-3 .subHeading}

Det här kommandot avinstallerar webbprogrammet för Windows PowerShell när en anpassad webbplats och program som angavs under installationen.
Kommandot tar bort den webbplats med namnet *webbplats* och program med namnet *testprogram* och anger att testcertifikat som är associerade med applikationen också tas bort.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>Närliggande information

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
