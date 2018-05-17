---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Inbyggda Desired State Configuration-resurser för Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
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