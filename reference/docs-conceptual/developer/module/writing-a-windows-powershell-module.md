---
ms.date: 09/13/2016
ms.topic: reference
title: Skriva en Windows PowerShell-modul
description: Skriva en Windows PowerShell-modul
ms.openlocfilehash: 307241f0fb4d12c1a5cbd651a0ae4d5303098b27
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659430"
---
# <a name="writing-a-windows-powershell-module"></a>Skriva en Windows PowerShell-modul

Det här dokumentet är skrivet för administratörer, skript utvecklare och cmdlet-utvecklare som behöver paketera och distribuera sina Windows PowerShell-cmdlets. Med hjälp av Windows PowerShell-moduler kan du paketera och distribuera dina Windows PowerShell-lösningar utan att använda ett kompilerat språk.

Med Windows PowerShell-moduler kan du partitionera, organisera och abstrakta din Windows PowerShell-kod i självständiga, återanvändbara enheter. Med dessa åter användnings bara enheter kan du enkelt dela dina moduler direkt med andra. Om du är en skript utvecklare kan du också paketera om moduler från tredje part för att skapa anpassade skriptbaserade program. Moduler som liknar moduler i andra skript språk, till exempel perl och python, möjliggör produktions klara skript lösningar som använder återanvändbara, distribuerbara komponenter, med den extra fördelen att du kan paketera och sammanställa flera komponenter för att skapa anpassade lösningar.

Windows PowerShell kommer att behandla alla giltiga Windows PowerShell-skript koder som sparats i en. psm1-fil som en modul. PowerShell kommer också automatiskt att behandla en binär cmdlet-sammansättning som en modul. Men du kan också använda en modul (eller mer specifikt ett modul manifest) för att bunta samman en hel lösning. I följande scenarier beskrivs vanliga användnings områden för Windows PowerShell-moduler.

### <a name="libraries"></a>Bibliotek

Moduler kan användas för att paketera och distribuera sammanhängande bibliotek med funktioner som utför vanliga uppgifter. Normalt delar namnen på dessa funktioner ett eller flera substantiv som återspeglar den vanliga uppgiften som de används för. Dessa funktioner kan också likna .NET Framework klasser i att de kan ha offentliga och privata medlemmar. Ett bibliotek kan till exempel innehålla en uppsättning funktioner för fil överföringar. I det här fallet kan substantiv som reflekterar den vanliga uppgiften vara "File".

### <a name="configuration"></a>Konfiguration

Moduler kan användas för att anpassa din miljö genom att lägga till vissa cmdlets, providrar, funktioner och variabler.

### <a name="compiled-code-development-and-distribution"></a>Kompilerad kod utveckling och distribution

Cmdlet-och Provider-utvecklare kan använda moduler för att testa och distribuera sin kompilerade kod utan att behöva skapa snapin-moduler. De kan importera den sammansättning som innehåller den kompilerade koden som en modul (en binär modul) utan att behöva skapa och registrera snapin-moduler.

## <a name="see-also"></a>Se även

[Förstå en Windows PowerShell-modul](./understanding-a-windows-powershell-module.md)

[Skriva en PowerShell-skriptmodul](./how-to-write-a-powershell-script-module.md)

[Skriva en binär PowerShell-modul](./how-to-write-a-powershell-binary-module.md)

[Skriva ett PowerShell-modulmanifest](how-to-write-a-powershell-module-manifest.md)

[Ändra installationssökvägen för PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importera en PowerShell-modul](./importing-a-powershell-module.md)

[Installera en PowerShell-modul](./installing-a-powershell-module.md)
