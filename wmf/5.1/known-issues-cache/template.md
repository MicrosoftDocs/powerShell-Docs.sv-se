---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
title: "exempelmall av ett känt problem eller begränsning uppskrivning"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
>Obs: ge en föreslagna beskrivande rubrik och en kort beskrivning

## <a name="example-erroneous-executionpolicy-errors"></a>Exempel: Felaktiga ExecutionPolicy fel ##
Användningen av PowerShell-moduler och DSC-resurser kan resultera i fel som rapporteras om körningsprincipen på Windows 7.

### <a name="resolution"></a>Lösning

Lös problemet genom att ange den **ExecutionPolicy** till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):

```powershell
Set-ExecutionPolicy RemoteSigned
```

