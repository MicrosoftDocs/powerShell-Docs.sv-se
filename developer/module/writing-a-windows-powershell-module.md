---
title: Skriva ett Windows PowerShell-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229347"
---
# <a name="writing-a-windows-powershell-module"></a>Skriva en Windows PowerShell-modul

Det här dokumentet är avsedd för administratörer, skript utvecklare och cmdlet-utvecklare som måste du paketera och distribuera sina Windows PowerShell-cmdlets. Genom att använda Windows PowerShell-moduler kan du paketera och distribuera dina Windows PowerShell-lösningar utan att använda ett kompilerade språk.

Windows PowerShell-moduler som gör det möjligt att partitionen, ordna och abstrahera dina Windows PowerShell-kod i självständig, återanvändbara enheter. Med dessa återanvändbara enheter, kan du enkelt dela dina moduler direkt med andra. Om du är skriptutvecklare kan du paketera om moduler från tredje part för att skapa anpassade skript-baserade program. Moduler, liknar moduler i andra skriptspråk som Perl och Python, aktivera produktionsklara scripting lösningar som använder återanvändningsbara, omdistribuerbara komponenter, med den ytterligare fördelen med att du kan paketera om och ett utkast av flera komponenter att Skapa anpassade lösningar.

I sina mest grundläggande Windows PowerShell behandlar alla giltiga Windows PowerShell-skriptkod som sparas i en .psm1-fil som en modul. PowerShell behandlar också automatiskt alla binära cmdlet-sammansättningen som en modul. Du kan dock också använda en modul (eller mer specifikt ett modulmanifest) om du vill slå samman en hel lösning. Följande scenarier beskriver vanliga användningsområden för Windows PowerShell-moduler.

### <a name="libraries"></a>Bibliotek

Moduler kan användas för att paketera och distribuera sammanhängande bibliotek med funktioner som utför vanliga uppgifter. Namnen på dessa funktioner delar vanligtvis en eller flera substantiv som motsvarar vanliga uppgiften som de ska användas för. Dessa funktioner kan också vara liknar .NET Framework-klasser i att de kan ha offentliga och privata medlemmar. Till exempel ett bibliotek som kan innehålla en uppsättning funktioner för filöverföringar. I det här fallet kan substantiv återger vanliga aktiviteten vara ”fil”.

### <a name="configuration"></a>Konfiguration

Moduler kan användas för att anpassa din miljö genom att lägga till specifika cmdletar, providers, funktioner och variabler.

### <a name="compiled-code-development-and-distribution"></a>Kompilerad Kodutveckling och Distribution

Cmdlet och providern utvecklare kan använda moduler för att testa och distribuera sina kompilerad kod utan att behöva skapa snapin-moduler. De kan importera den sammansättning som innehåller den kompilerade koden som en modul (en binär modul) utan att behöva skapa och registrera snapin-moduler.

## <a name="see-also"></a>Se även

[Förstå en Windows PowerShell-modul](./understanding-a-windows-powershell-module.md)

[Hur du skriver en PowerShell-skript-modul](./how-to-write-a-powershell-script-module.md)

[Hur du skriver en binär PowerShell-modul](./how-to-write-a-powershell-binary-module.md)

[Så här skriver du ett PowerShell-modulen Manifest](how-to-write-a-powershell-module-manifest.md)

[Ändra installationssökvägen PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importera en PowerShell-modul](./importing-a-powershell-module.md)

[Installera en PowerShell-modul](./installing-a-powershell-module.md)
