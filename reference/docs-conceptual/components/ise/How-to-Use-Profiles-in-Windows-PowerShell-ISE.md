---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Använd profiler Windows PowerShell ISE
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684467"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Använd profiler Windows PowerShell ISE

Det här avsnittet förklarar hur du använder profiler i Windows PowerShell® Integrated Scripting Environment (ISE). Vi rekommenderar att innan du utför uppgifterna i det här avsnittet måste du granska [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), eller i konsolfönstret, typ, `Get-Help about_Profiles` och tryck på **RETUR**.

En profil är ett Windows PowerShell ISE-skript som körs automatiskt när du startar en ny session.  Du kan skapa en eller flera Windows PowerShell-profiler för Windows PowerShell ISE och använda dem för att lägga till Konfigurera Windows PowerShell eller Windows PowerShell ISE-miljön, förbereder den för din användning, med variabler, alias, funktioner, och färg och teckensnitt inställningar som du efterfrågar tillgängliga. En profil påverkar alla Windows PowerShell ISE-session som du startar.

> [!NOTE]
> Windows PowerShell-körningsprincipen avgör om du kan köra skript och läsa in en profil. Standardprincipen för körning ”begränsad”, förhindrar alla skript från att köras, inklusive profiler. Om du använder principen ”begränsad” profilen kan inte läsas in. Läs mer om körningsprincipen [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Att välja en profil som används i Windows PowerShell ISE

Windows PowerShell ISE stöder profiler för den aktuella användaren och alla användare. Det stöder även de Windows PowerShell-profiler som gäller för alla värdar.

Den profil som du använder bestäms av hur du använder Windows PowerShell och Windows PowerShell ISE.

- Om du använder bara Windows PowerShell ISE för att köra Windows PowerShell, sparar du alla objekt i ett av ISE-specifika profiler, till exempel CurrentUserCurrentHost profilen för Windows PowerShell ISE eller AllUsersCurrentHost profilen för Windows PowerShell ISE.

- Om du använder flera värden program för att köra Windows PowerShell, spara dina funktioner, alias, variabler och kommandon i en profil som påverkar alla värden program, till exempel CurrentUserAllHosts eller profilen för AllUsersAllHosts och spara ISE-specifika funktioner, t.ex. färger och teckensnitt anpassning i CurrentUserCurrentHost profilen för Windows PowerShell ISE-profil eller AllUsersCurrentHost-profil för Windows PowerShell ISE.

Här följer profiler som skapas och används i Windows PowerShell ISE. Varje profil sparas till sin egen angiven sökväg.

| Profiltyp | Profilsökvägen |
| --- | --- |
| **Aktuell användare, PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost`, eller `$PROFILE` |
| **Alla användare, PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **Aktuell användare, alla värdar**| `$PROFILE.CurrentUserAllHosts` |
| **Alla användare, alla värdar** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Skapa en ny profil

Skapa en ny ”aktuella användare, Windows PowerShell ISE” profil, kör du följande kommando:

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

Att skapa en ny ”alla användare, Windows PowerShell ISE” profil, kör du följande kommando:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Om du vill skapa en ny ”aktuella användaren, alla är värd för” profil, kör du följande kommando:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Om du vill skapa en ny profil för ”alla användare, alla är värd för”, skriver du:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Så här redigerar du en profil

1. Öppna profilen genom att köra kommandot psedit med variabeln som anger den profil du vill redigera. Till exempel för att öppna den ”aktuella användaren, Windows PowerShell ISE” profil, skriver du: `psEdit $PROFILE`

2. Lägg till vissa objekt i din profil. Här följer några exempel för att komma igång:

   - Ändra bakgrundsfärgen som används av konsolfönstret till blått, i filen Profiltyp: `$psISE.Options.OutputPaneBackground = 'blue'` . Läs mer om variabeln $psISE [Windows PowerShell ISE-Objektmodellreferens](object-model/The-ISE-Object-Model-Hierarchy.md).

   - Ändra storlek till 20, i filen Profiltyp: `$psISE.Options.FontSize =20`

3. Spara fil för Konfigurationsprofil på den **filen** -menyn klickar du på **spara**. Nästa gång du öppnar Windows PowerShell ISE tillämpas anpassningarna.

## <a name="see-also"></a>Se även

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Introduktion till Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)