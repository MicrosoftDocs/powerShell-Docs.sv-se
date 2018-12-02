---
ms.date: 09/11/2018
contributor: JKeithB
keywords: galleriet, powershell, psgallery
title: Manuell paketnedladdning
ms.openlocfilehash: 57baa14089b803f58c42ccb54553ecace841e34b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742830"
---
# <a name="manual-package-download"></a>Manuell paketnedladdning

Powershell-galleriet har stöd för ett paket laddades ned från webbplatsen direkt, utan att använda PowerShellGet-cmdletar. Du kan hämta alla paket som en NuGet-paketet (.nupkg)-fil som du sedan kan kopiera till en intern lagringsplats.

> [!NOTE]
> Ladda ned manuell paket är **inte** avsedd som en ersättning för cmdleten Install-Module.
> Ladda ned paketet installerar inte modulen eller skript. Beroenden ingår inte i NuGet-paketet som hämtas. Följande instruktioner tillhandahålls endast för referens.

## <a name="using-manual-download-to-acquire-a-package"></a>Använda manuell hämtning för att hämta ett paket

Varje sida innehåller en länk för manuell hämtning, som visas här:

![Manuell hämtning](../../Images/packagedisplaypagewithpseditions.png)

Om du vill hämta manuellt klickar du på **Filnedladdning raw nupkg**. En kopia av paketet kopieras till mappen för din webbläsare med namnet `<name>.<version>.nupkg`.

Ett NuGet-paket är ett ZIP-arkiv med extra filer som innehåller information om innehållet i paketet. Vissa webbläsare, till exempel Internet Explorer automatiskt ersätta den `.nupkg` filnamnstillägget med `.zip`. För att expandera paketet, byta namn på den `.nupkg` filen till `.zip`vid behov, sedan extrahera innehållet till en lokal mapp.

En fil för NuGet-paketet innehåller följande NuGet-specifika element som inte ingår i den ursprungliga paketerade koden:

- En mapp med namnet `_rels` – innehåller en `.rels` -fil som innehåller beroenden
- En mapp med namnet `package` -innehåller NuGet-specifika data
- En fil med namnet `[Content_Types].xml` – beskriver hur filtillägg som PowerShellGet fungerar med NuGet
- En fil med namnet `<name>.nuspec` -innehåller stora mängd metadata

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Installera PowerShell-moduler från ett NuGet-paket

> [!NOTE]
> De här anvisningarna **inte** ger samma resultat som att köra `Install-Module`. De här anvisningarna uppfyller minimikraven. De är inte avsedda att ersätta `Install-Module`. Vissa steg som utförs av `Install-Module` ingår inte.

Den enklaste metoden är att ta bort NuGet-specifika elementen från mappen. Det innebär att PowerShell-kod som skapats av paketets upphovsman. Stegen är:

1. Extrahera innehållet i NuGet-paketet till en lokal mapp.
2. Ta bort NuGet-specifika elementen från mappen.
3. Byt namn på mappen. Standardnamnet på mappen är vanligtvis `<name>.<version>`. Versionen kan innehålla ”-förhandsversion” om modulen har märkts som en förhandsversion. Byt namn på mappen till bara modulens namn. Till exempel ”azurerm.storage.5.0.4 förhandsversion” till ”azurerm.storage”.
4. Kopiera mappen till en av mapparna i den `$env:PSModulePath value`. `$env:PSModulePath` är en semikolonavgränsad lista uppsättning sökvägar där PowerShell bör se ut för moduler.

> [!IMPORTANT]
> Manuell hämtning inkluderar inte eventuella beroenden som krävs av modulen. Om paketet har beroenden, måste de installeras i systemet så att den här modulen ska fungera korrekt. PowerShell-galleriet visar alla beroenden som krävs av paketet.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Installera PowerShell-skript från ett NuGet-paket

> [!NOTE]
> De här anvisningarna **inte** ger samma resultat som att köra `Install-Script`. De här anvisningarna uppfyller minimikraven. De är inte avsedda att ersätta `Install-Script`.

Den enklaste metoden är att extrahera NuGet-paketet, därefter använder du skriptet direkt. Stegen är:

1. Extrahera innehållet i NuGet-paketet.
2. Den `.PS1` filen i mappen kan användas direkt från den här platsen.
3. Du kan ta bort NuGet-specifika elementen i mappen.

> [!IMPORTANT]
> Manuell hämtning inkluderar inte eventuella beroenden som krävs av modulen. Om paketet har beroenden, måste de installeras i systemet så att den här modulen ska fungera korrekt. PowerShell-galleriet visar alla beroenden som krävs av paketet.
