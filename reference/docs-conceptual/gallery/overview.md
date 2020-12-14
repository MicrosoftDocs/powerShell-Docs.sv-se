---
ms.date: 12/01/2020
title: PowerShell-galleriet
description: PowerShell-galleriet är den centrala lagrings platsen för PowerShell-moduler, skript och DSC-resurser.
ms.openlocfilehash: f1ce6a8e2d5d72ac14cf3e4854626ef612d27891
ms.sourcegitcommit: 62282bb9c36fea3b4290b9263c1cd8e9ac216e29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96470323"
---
# <a name="the-powershell-gallery"></a>PowerShell-galleriet

PowerShell-galleriet är den centrala lagrings platsen för PowerShell-innehåll. I det kan du hitta användbara PowerShell-moduler som innehåller PowerShell-kommandon och DSC-resurser (Desired State Configuration).
Du kan också hitta PowerShell-skript, varav vissa kan innehålla PowerShell-arbetsflöden och en uppsättning aktiviteter och tillhandahålla sekvenseringen för dessa aktiviteter. Några av de här paketen har skapats av Microsoft och andra har skapats av PowerShell-communityn.

## <a name="powershellget-overview"></a>Översikt över PowerShellGet

Modulen PowerShellGet innehåller cmdlets för att upptäcka, installera, uppdatera och publicera PowerShell-paket som innehåller artefakter som moduler, DSC-resurser, roll funktioner och skript från [PowerShell-galleriet](https://www.PowerShellGallery.com) och andra privata databaser.

## <a name="getting-started-with-the-gallery"></a>Komma igång med galleriet

Den senaste versionen av PowerShellGet-modulen kräver att du installerar paket från galleriet. Fullständiga instruktioner finns i [Installera PowerShellGet](installing-psget.md) .

Se [Komma igång](getting-started.md) för mer information om hur du använder PowerShellGet-kommandon med galleriet. Du kan också köra *Update-Help -Module PowerShellGet* om du vill installera lokal hjälp för dessa kommandon.

## <a name="supported-operating-systems"></a>Operativsystem som stöds

För **PowerShellGet**-modulen krävs **PowerShell version 3.0 eller senare**.

**PowerShellGet** kräver .NET Framework 4,5 eller senare. Mer information finns i [installera .NET Framework för utvecklare](/dotnet/framework/install/guide-for-developers).

Eftersom **PowerShell Core** är plattforms oberoende och innebär det att den fungerar på Windows, Linux och MacOS, vilket även gör **PowerShellGet** tillgängliga på dessa system. En fullständig lista över system som stöds av **PowerShell Core** finns i [Installera PowerShell](/powershell/scripting/install/installing-powershell).

Många moduler som finns i galleriet har stöd för olika operativ system och har ytterligare krav.
Mer information finns i dokumentationen för modulerna.

## <a name="got-a-question-have-feedback"></a>Fick du en fråga? Har du feedback till oss?

Mer information om PowerShell-galleriet-och PowerShellGet finns på sidan [komma igång](getting-started.md) .

För att se aktuell status för PowerShell-galleriet tjänsterna, se sidan [PowerShell-galleriet status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) på GitHub.

Ge feedback och rapportera fel i [GitHub-lagringsplatsen](https://github.com/PowerShell/PowerShellGallery/issues).
