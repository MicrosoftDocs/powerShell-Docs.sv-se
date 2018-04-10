---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
title: exempelmall av ett känt problem eller begränsning uppskrivning
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
>Obs: ge en föreslagna beskrivande rubrik och en kort beskrivning

## <a name="example-erroneous-executionpolicy-errors"></a>Exempel: Felaktiga ExecutionPolicy fel ##
Användningen av PowerShell-moduler och DSC-resurser kan resultera i fel som rapporteras om körningsprincipen på Windows 7.

### <a name="resolution"></a>Lösning

Lös problemet genom att ange den **ExecutionPolicy** till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):

```powershell
Set-ExecutionPolicy RemoteSigned
```