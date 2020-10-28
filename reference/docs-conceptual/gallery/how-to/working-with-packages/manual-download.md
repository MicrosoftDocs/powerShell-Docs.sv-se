---
ms.date: 09/11/2018
title: Manuell paketnedladdning
description: Beskriver hur du manuellt laddar ned ett paket från PowerShell-galleriet.
ms.openlocfilehash: 50cd51d970bf21f8e957e60ceed2e98f306b57ab
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662284"
---
# <a name="manual-package-download"></a>Manuell paketnedladdning

PowerShell-galleriet har stöd för att ladda ned ett paket från webbplatsen direkt, utan att använda PowerShellGet-cmdletar. Du kan ladda ned alla paket som NuGet-paket ( `.nupkg` ), som du sedan kan kopiera till en intern lagrings plats.

> [!NOTE]
> Manuell paket hämtning är **inte** avsedd som ersättning för `Install-Module` cmdleten.
> Om du hämtar paketet installeras inte modulen eller skriptet. Beroenden ingår inte i NuGet-paketet som hämtats. Följande instruktioner anges endast i referens syfte.

## <a name="using-manual-download-to-acquire-a-package"></a>Använda manuell nedladdning för att hämta ett paket

Varje sida har en länk för manuell hämtning, som du ser här:

![Sidan paket visning med installations alternativ](media/manual-download/packagedisplaypagewithpseditions.png)

Om du vill ladda ned manuellt klickar **du på Hämta RAW nupkg-filen** . En kopia av paketet kopieras till download-mappen för din webbläsare med namnet `<name>.<version>.nupkg` .

Ett NuGet-paket är ett ZIP-arkiv med extra filer som innehåller information om paketets innehåll. Vissa webbläsare, till exempel Internet Explorer, ersätter `.nupkg` fil tillägget automatiskt med `.zip` . Om du vill expandera paketet, byter du namn på `.nupkg` filen till `.zip` , om det behövs, och extraherar sedan innehållet till en lokal mapp.

En NuGet-paketfil innehåller följande **NuGet element** som inte ingår i den ursprungliga paketerade koden:

- En mapp med namnet `_rels` – innehåller en `.rels` fil som visar beroenden
- En mapp med namnet `package` – innehåller NuGet data
- En fil med namnet `[Content_Types].xml` – beskriver hur tillägg som PowerShellGet fungerar med NuGet
- En fil med namnet `<name>.nuspec` -innehåller mängden av metadata

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Installera PowerShell-moduler från ett NuGet-paket

> [!NOTE]
> Dessa instruktioner ger **inte** samma resultat som körs `Install-Module` . De här anvisningarna uppfyller minimi kraven. De är inte avsedda att ersätta `Install-Module` .
> Vissa steg som utförs av `Install-Module` ingår inte.

Det enklaste sättet är att ta bort de NuGet elementen från mappen. Att ta bort elementen lämnar PowerShell-koden som skapats av paketets författare.
En lista över NuGet element finns i [använda manuell hämtning för att hämta ett paket](#using-manual-download-to-acquire-a-package).

Stegen är följande:

1. Avblockera den Internet-hämtade NuGet Package ( `.nupkg` )-filen, till exempel med hjälp av `Unblock-File -Path C:\Downloads\module.nupkg` cmdlet.
1. Extrahera innehållet i NuGet-paketet till en lokal mapp.
1. Ta bort de NuGet elementen från mappen.
1. Byt namn på mappen. Standard namnet på mappen är vanligt vis `<name>.<version>` . Versionen kan inkludera `-prerelease` om modulen är Taggad som en för hands version. Byt namn på mappen till bara modulnamnet. Till exempel `azurerm.storage.5.0.4-preview` blir `azurerm.storage` .
1. Kopiera mappen till en av mapparna i `$env:PSModulePath value` . `$env:PSModulePath` är en semikolonavgränsad uppsättning med sökvägar som PowerShell ska söka efter moduler i.

> [!IMPORTANT]
> Den manuella hämtningen innehåller inte några beroenden som krävs av modulen. Om paketet har beroenden måste de installeras i systemet för att modulen ska fungera korrekt. PowerShell-galleriet visar alla beroenden som krävs av paketet.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Installera PowerShell-skript från ett NuGet-paket

> [!NOTE]
> Dessa instruktioner ger **inte** samma resultat som körs `Install-Script` . De här anvisningarna uppfyller minimi kraven. De är inte avsedda att ersätta `Install-Script` .

Den enklaste metoden är att extrahera NuGet-paketet och sedan använda skriptet direkt.

Stegen är följande:

1. Avblockera den Internet-hämtade NuGet Package ( `.nupkg` )-filen, till exempel med hjälp av `Unblock-File -Path C:\Downloads\package.nupkg` cmdlet.
1. Extrahera innehållet i NuGet-paketet.
1. `.PS1`Filen i mappen kan användas direkt från den här platsen.
1. Du kan ta bort de NuGet elementen i mappen.

En lista över NuGet element finns i [använda manuell hämtning för att hämta ett paket](#using-manual-download-to-acquire-a-package).

> [!IMPORTANT]
> Den manuella hämtningen innehåller inte några beroenden som krävs av modulen. Om paketet har beroenden måste de installeras i systemet för att modulen ska fungera korrekt. PowerShell-galleriet visar alla beroenden som krävs av paketet.
