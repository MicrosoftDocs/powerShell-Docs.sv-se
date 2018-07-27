---
ms.topic: reference
keywords: PowerShell cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268307"
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>SAMMANFATTNING

Konfigurerar Windows PowerShell Web Access-webbprogram i IIS.

## <a name="syntax"></a>SYNTAX

### <a name="default"></a>Standard
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESKRIVNING

Den **Install-PswaWebApplication** cmdlet konfigurerar Windows PowerShell Web Access-webbprogram.
Denna cmdlet installerar webbprogrammet, kopplar det till en webbplats och kan även skapa en test SSL certifikatet med den **useTestCertificate** parametern. För säkerhet orsaker webbadministratörer bör inte använda ett testcertifikat för produktionsmiljöer.

## <a name="parameters"></a>PARAMETRAR

### <a name="-usetestcertificate"></a>-UseTestCertificate

Anger att ett testcertifikat skapas. Om den här parametern anges till true, och sedan denna cmdlet skapar ett testcertifikat och konfigurerar det webbaserade programmet i Windows PowerShell-webbåtkomst och använda certifikat för HTTPS-begäranden. Om den här parametern är inställd på false, skapas ingen certifikat eller en bindning. Ange värdet till false om ett annat certifikat används för Windows PowerShell Web Access.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | med namnet                                |
| Standardvärde                        | SANT                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-webapplicationname"></a>-WebApplicationName

Anger namnet för ditt webbprogram. Detta visas som den sista delen av URL: en Windows PowerShell Web Access.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | 1                                    |
| Standardvärde                        | pswa                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-websitename"></a>-WebbPlatsensNamn

Anger namnet på Web Server (IIS)-webbplats som du vill installera den här Windows PowerShell Web Access-webbprogram.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | med namnet                                |
| Standardvärde                        | Default Web Site                     |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-confirm"></a>-Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

|||
|-|-|
| Obligatorisk?                            | falskt                                |
| Placering?                            | med namnet                                |
| Standardvärde                        | falskt                                |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-whatif"></a>-WhatIf

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

|||
|-|-|
| Obligatorisk?                            | falskt                                |
| Placering?                            | med namnet                                |
| Standardvärde                        | falskt                                |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Denna cmdlet har stöd för parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable. Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INDATA

Den här cmdleten tar inga indata.

## <a name="outputs"></a>UTDATA

Denna cmdlet genererar inga utdata.

## <a name="examples"></a>EXEMPEL

### <a name="example-1"></a>EXEMPEL 1

Det här exemplet installerar PSWA webbprogrammet med standardvärden för de **WebApplicationName** (*pswa*) och **WebbPlatsensNamn** (*Default Web Site* ) parametrar.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>EXEMPEL 2

Det här exemplet installerar PSWA webbprogrammet med ett testcertifikat och använder standardvärden för de **WebApplicationName** och **WebbPlatsensNamn** parametrar.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Närliggande information

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)