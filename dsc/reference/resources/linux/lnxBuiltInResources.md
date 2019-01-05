---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Inbyggda Desired State Configuration-resurser för Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048714"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Inbyggda Desired State Configuration-resurser för Linux

Resurserna är byggstenar som du kan använda för att skriva ett skript med PowerShell Desired State Configuration (DSC). DSC för Linux levereras med en uppsättning inbyggda funktioner för att konfigurera resurser, till exempel filer och mappar, paket, miljövariabler och tjänster och processer.

## <a name="built-in-resources"></a>Inbyggda resurser

Följande tabell innehåller en lista över dessa resurser och länkar till ämnen som beskrivs i detalj.

* [nxArchive-resurs](lnxArchiveResource.md)– tillhandahåller en mekanism för att packa upp (.tar, .zip) arkivfiler på en specifik sökväg.
* [nxEnvironment-resurs](lnxEnvironmentResource.md)--hanterar miljövariabler på målnoder.
* [nxFile-resurs](lnxFileResource.md)--hanterar Linux-filer och kataloger.
* [nxFileLine-resurs](lnxFileLineResource.md)--hanterar enskilda rader i en Linux-fil.
* [nxGroup-resurs](lnxGroupResource.md)--hanterar lokala Linux-grupper.
* [nxPackage-resurs](lnxPackageResource.md)--hanterar paket på Linux-noder.
* [nxScript Resource](lnxScriptResource.md)--kör skript på målnoder.
* [nxService-resurs](lnxServiceResource.md)--hanterar Linux-tjänster (Daemon).
* [nxSshAuthorizedKeys-resurs](lnxSshAuthorizedKeysResource.md)--hanterar offentliga ssh-nycklar för en Linux-användare.
* [nxUser-resurs](lnxUserResource.md)--hanterar lokala Linux-användare.