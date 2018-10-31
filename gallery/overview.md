---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery, psget
title: PowerShell-galleriet
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225626"
---
# <a name="the-powershell-gallery"></a>PowerShell-galleriet

PowerShell-galleriet är en central lagringsplats för PowerShell-innehåll. Du kan hitta användbar PowerShell-moduler som innehåller PowerShell-kommandon och Desired State Configuration (DSC) resurser i den.
Du kan också hitta PowerShell-skript, vilket kan innehålla PowerShell-arbetsflöden och som beskriver en uppsättning aktiviteter och ange ordningsföljd för dessa aktiviteter. Vissa av dessa paket skapats av Microsoft och andra skapats av PowerShell-communityn.

## <a name="powershellget-overview"></a>PowerShellGet-översikt

PowerShellGet-modulen innehåller cmdlets för identifiering, installera, uppdatera och publicera PowerShell-paket som innehåller artefakter som moduler, DSC-resurser, rollfunktioner och skript från den [PowerShell-galleriet](https://www.PowerShellGallery.com)och andra privata lagringsplatser.

## <a name="getting-started-with-the-gallery"></a>Komma igång med galleriet

Installera paket från galleriet krävs den senaste versionen av modulen PowerShellGet.
Se [installera PowerShellGet](installing-psget.md) fullständiga anvisningar.

Kolla in den [komma igång](getting-started.md) för mer information om hur du använder PowerShellGet-kommandon med galleriet. Du kan också köra *Update-Help-Module PowerShellGet* att installera lokal hjälp för dessa kommandon.

## <a name="supported-operating-systems"></a>Operativsystem som stöds

Den **PowerShellGet** modulen kräver **Windows PowerShell version 3.0 eller senare**, eller **PowerShell Core 6.0 eller nyare**.

En lämplig version av **Windows PowerShell** är tillgänglig för dessa operativsystem:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** kräver .NET Framework 4.5 eller senare. Du kan installera .NET Framework 4.5 eller senare från [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).

Eftersom **PowerShell Core** är plattformsoberoende och som innebär att det fungerar på Windows, Linux och MacOS, även gör **PowerShellGet** tillgänglig på dessa system. En fullständig lista över system som stöds av **PowerShell Core** Se [installera PowerShell](/powershell/scripting/setup/installing-powershell).

Många moduler i galleriet stöder olika operativsystem och har ytterligare krav. Läs dokumentationen för moduler för mer information.

## <a name="got-a-question-have-feedback"></a>En fråga? Har du feedback?

Mer information om PowerShell-galleriet och PowerShellGet finns i den [komma igång](getting-started.md) sidan. Ge feedback och rapportera problem med hjälp av [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).
