---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: installera pswawebapplication
ms.technology: powershell
ms.openlocfilehash: a608a6272d3eae56ccf808b9d94525ca39df50cb
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>SAMMANFATTNING

Konfigurerar Windows PowerShell® Web Access-webbprogrammet i IIS.

## <a name="syntax"></a>SYNTAX

### <a name="default"></a>Standard
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESKRIVNING

Den **Install-PswaWebApplication** cmdlet konfigurerar Windows PowerShell Web Access-webbprogram. Denna cmdlet installerar cmdleten webbprogrammet, kopplas till en webbplats och du kan även skapa en test SSL certifikat med hjälp av den **useTestCertificate** parameter. Av säkerhetsskäl bör orsaker webbadministratörer inte använda ett testcertifikat för produktionsmiljöer.

## <a name="parameters"></a>PARAMETRAR

### <a name="-usetestcertificate"></a>-UseTestCertificate

Anger att ett testcertifikat skapas. Om den här parametern anges till true, och sedan denna cmdlet skapar ett testcertifikat och konfigurerar Windows PowerShell Web Access webbprogram att använda certifikat för HTTPS-begäranden. Om den här parametern är inställd på false, skapas inga certifikat eller bindning. Ange värdet till false om ett annat certifikat används för Windows PowerShell Web Access.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | SANT                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-webapplicationnameltstringgt"></a>-WebApplicationName&lt;sträng&gt;

Anger namnet för ditt webbprogram. Detta visas som den sista delen av URL: en Windows PowerShell Web Access.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | 1                                    |
| Standardvärde                        | pswa                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-websitenameltstringgt"></a>-WebSiteName&lt;sträng&gt;

Anger namnet på webbplatsen webbserver (IIS) som du vill installera det här webbprogrammet för Windows PowerShell Web Access.

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

Denna cmdlet ger inga utdata.

## <a name="examples"></a>EXEMPEL

### <a name="example-1"></a>EXEMPEL 1

Det här exemplet installerar PSWA webbprogrammet med standardvärden för de **WebApplicationName** (*pswa*) och **WebSiteName** (*Default Web Site* ) parametrar.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>EXEMPEL 2

Det här exemplet installerar PSWA webbprogrammet med ett testcertifikat, och använder standardvärden för de **WebApplicationName** och **WebSiteName** parametrar.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Närliggande information

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
