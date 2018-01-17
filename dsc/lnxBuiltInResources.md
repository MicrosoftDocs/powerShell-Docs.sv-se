---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Inbyggda Desired State Configuration-resurser för Linux"
ms.openlocfilehash: e268cb2ee8a246f18216b34e5e2a6d512f15e18c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Inbyggda Desired State Configuration-resurser för Linux

Resurser är byggstenar som du kan använda för att skriva ett skript med PowerShell önskad tillstånd Configuration (DSC). DSC för Linux innehåller en uppsättning inbyggda funktioner för att konfigurera resurser, till exempel filer och mappar, paket, miljövariabler och tjänster och processer.

## <a name="built-in-resources"></a>Inbyggda resurser 

Följande tabell innehåller en lista över de här resurserna och länkarna till avsnitt som beskrivs i detalj.

* [nxArchive resurs](lnxArchiveResource.md)– ger dig möjlighet att packa upp (.tar, .zip) arkivfiler vid en angiven sökväg.
* [nxEnvironment resurs](lnxEnvironmentResource.md)--hanterar miljövariabler på målnoder. 
* [nxFile resurs](lnxFileResource.md)--hanterar Linux-filer och kataloger. 
* [nxFileLine resurs](lnxFileLineResource.md)--hanterar enskilda rader i en Linux-fil. 
* [nxGroup resurs](lnxGroupResource.md)--hanterar lokala Linux-grupper. 
* [nxPackage resurs](lnxPackageResource.md)--hanterar paket på Linux-noder.
* [nxScript resurs](lnxScriptResource.md)--kör skript på målnoder.
* [nxService resurs](lnxServiceResource.md)--hanterar Linux-tjänster (Daemon).
* [nxSshAuthorizedKeys resurs](lnxSshAuthorizedKeysResource.md)--hanterar offentliga ssh nycklar för en Linux-användare. 
* [nxUser resurs](lnxUserResource.md)--hanterar lokala Linux-användare. 
  
