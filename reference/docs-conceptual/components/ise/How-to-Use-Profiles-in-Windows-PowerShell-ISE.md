---
ms.date: 01/02/2020
keywords: PowerShell, cmdlet
title: Använd profiler Windows PowerShell ISE
ms.openlocfilehash: da7dc2f234ad0c2968fbb213e9e57da875f456e4
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736257"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Använd profiler Windows PowerShell ISE

I det här avsnittet beskrivs hur du använder profiler i Windows PowerShell® Integrated Scripting Environment (ISE). Innan du utför uppgifterna i det här avsnittet rekommenderar vi att du granskar [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)eller i konsol fönstret, skriver `Get-Help about_Profiles` och trycker på <kbd>RETUR</kbd>.

En profil är ett Windows PowerShell ISE-skript som körs automatiskt när du startar en ny session.
Du kan skapa en eller flera Windows PowerShell-profiler för Windows PowerShell ISE och använda dem för att lägga till konfigurera Windows PowerShell-eller Windows PowerShell ISE-miljön, förbereda den för användning med variabler, alias, funktioner och färg och teckensnitt inställningar som du vill ska vara tillgängliga. En profil påverkar varje Windows PowerShell ISE session som du startar.

> [!NOTE]
> Windows PowerShell-körnings principen avgör om du kan köra skript och läsa in en profil.
> Standard körnings principen "begränsad" förhindrar att alla skript körs, inklusive profiler.
> Om du använder principen "begränsad" går det inte att läsa in profilen. Mer information om körnings principer finns [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Välja en profil som ska användas i Windows PowerShell ISE

Windows PowerShell ISE stöder profiler för den aktuella användaren och alla användare. Det stöder också de Windows PowerShell-profiler som gäller för alla värdar.

Den profil som du använder bestäms av hur du använder Windows PowerShell och Windows PowerShell ISE.

- Om du bara använder Windows PowerShell ISE för att köra Windows PowerShell sparar du alla objekt i någon av de ISE-/regionsspecifika profilerna, till exempel **CurrentUserCurrentHost** -profilen för Windows PowerShell ISE eller **AllUsersCurrentHost** -profilen för Windows PowerShell ISE.

- Om du använder flera värd program för att köra Windows PowerShell sparar du funktioner, alias, variabler och kommandon i en profil som påverkar alla värd program, till exempel CurrentUserAllHosts eller **AllUsersAllHosts** -profilen, och sparar ISE-/regionsspecifika funktioner, till exempel färg-och teckensnitts anpassning i **CurrentUserCurrentHost** -profilen för Windows PowerShell ISE profil eller **AllUsersCurrentHost** -profilen för Windows PowerShell ISE.

Följande är profiler som kan skapas och användas i Windows PowerShell ISE. Varje profil sparas på en egen angiven sökväg.

|           Profiltyp           |                   Profilsökvägen                   |
| -------------------------------- | ------------------------------------------------ |
| **Aktuell användare, PowerShell ISE** | `$PROFILE.CurrentUserCurrentHost` eller `$PROFILE` |
| **Alla användare, PowerShell ISE**    | `$PROFILE.AllUsersCurrentHost`                   |
| **Aktuell användare, alla värdar**      | `$PROFILE.CurrentUserAllHosts`                   |
| **Alla användare, alla värdar**         | `$PROFILE.AllUsersAllHosts`                      |

## <a name="to-create-a-new-profile"></a>Så här skapar du en ny profil

Kör följande kommando för att skapa en ny profil för "aktuell användare, Windows PowerShell ISE":

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

Kör det här kommandot om du vill skapa en ny "alla användare, Windows PowerShell ISE"-profil:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Om du vill skapa en ny "aktuell användare, alla värdar"-profil kör du följande kommando:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Om du vill skapa en ny profil för alla användare, alla värdar skriver du:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Redigera en profil

1. Öppna profilen genom att köra kommandot `psEdit` med variabeln som anger den profil som du vill redigera. Om du till exempel vill öppna profilen "aktuell användare, Windows PowerShell ISE" skriver du: `psEdit $PROFILE`

2. Lägg till några objekt i din profil. Nedan följer några exempel på hur du kan komma igång:

   - Ändra standard bakgrunds färgen för konsol fönstret till blått i profil fil typen: `$psISE.Options.OutputPaneBackground = 'blue'`. Mer information om variabeln `$psISE` finns [Windows PowerShell ISE referens för objekt modell](object-model/The-ISE-Object-Model-Hierarchy.md).

   - Om du vill ändra tecken storleken till 20, i profil fil typen: `$psISE.Options.FontSize =20`

3. Spara profil filen genom att klicka på **Spara**på **Arkiv** -menyn. Nästa gången du öppnar Windows PowerShell ISE tillämpas dina anpassningar.

## <a name="see-also"></a>Se även

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Vi presenterar Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
