---
description: Beskriver hur du skapar och använder en PowerShell-profil.
keywords: powershell,cmdlet
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 17b89df0ec0ce88127385287cee560996af7a628
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271503"
---
# <a name="about-profiles"></a>Om profiler

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du skapar och använder en PowerShell-profil.

## <a name="long-description"></a>Lång beskrivning

Du kan skapa en PowerShell-profil för att anpassa din miljö och lägga till sessionsbaserade element till varje PowerShell-session som du startar.

En PowerShell-profil är ett skript som körs när PowerShell startar. Du kan använda profilen som ett inloggnings skript för att anpassa miljön. Du kan lägga till kommandon, alias, funktioner, variabler, snapin-moduler, moduler och PowerShell-enheter. Du kan också lägga till andra sessionsbaserade element i din profil så att de är tillgängliga i varje session utan att behöva importera eller återskapa dem.

PowerShell stöder flera profiler för användare och värd program. Det skapar dock inte profilerna åt dig. I det här avsnittet beskrivs profilerna och hur du skapar och underhåller profiler på din dator.

Den förklarar hur du använder parametern **noprofil** i PowerShell-konsolen (PowerShell.exe) för att starta PowerShell utan några profiler. Och det förklarar resultatet av körnings principen för PowerShell på profiler.

## <a name="the-profile-files"></a>Profilmappar

PowerShell stöder flera profilmappar. Dessutom har PowerShell-värdprogram stöd för egna värdbaserade profiler.

PowerShell-konsolen stöder till exempel följande grundläggande profilmappar. Profilerna anges i prioritetsordning. Den första profilen har högst prioritet.

|Beskrivning               | Sökväg                                          |
|--------------------------|-----------------------------------------------|
|Alla användare, alla värdar      |$PSHOME \\Profile.ps1                           |
|Alla användare, aktuell värd   |$PSHOME \\Microsoft.PowerShell_profile.ps1      |
|Aktuell användare, alla värdar   |$Home \\ [My] Documents \\ WindowsPowerShell \\Profile.ps1 |
|Aktuell användare, aktuell värd|$Home \\ [My] Documents \\ WindowsPowerShell\\<br>Microsoft.PowerShell_profile.ps1 |

Profil Sök vägarna innehåller följande variabler:

- `$PSHOME`Variabeln som lagrar installations katalogen för PowerShell
- `$Home`Variabeln som lagrar den aktuella användarens arbets katalog

Dessutom kan andra program som är värdar för PowerShell stödja sina egna profiler. PowerShell (Integrated Scripting Environment) stöder till exempel följande värdbaserade profiler.

|Beskrivning               | Sökväg                                       |
|--------------------------|--------------------------------------------|
|Alla användare, aktuell värd   |$PSHOME \\Microsoft.PowerShellISE_profile.ps1|
|Aktuell användare, aktuell värd|$Home \\ [My] Documents \\ WindowsPowerShell\\<br>Microsoft.PowerShellISE_profile.ps1 |

I PowerShell-hjälpen är profilen "CurrentUser, aktuell värd" profilen som oftast kallas för "din PowerShell-profil".

## <a name="the-profile-variable"></a>Variabeln $PROFILE

Den `$PROFILE` automatiska variabeln lagrar Sök vägarna till de PowerShell-profiler som är tillgängliga i den aktuella sessionen.

Om du vill visa en profil Sök väg visar du värdet för `$PROFILE` variabeln. Du kan också använda `$PROFILE` variabeln i ett kommando för att representera en sökväg.

`$PROFILE`Variabeln lagrar sökvägen till profilen "aktuell användare, aktuell värd". De andra profilerna sparas i antecknings egenskaperna för `$PROFILE` variabeln.

`$PROFILE`Variabeln har till exempel följande värden i Windows PowerShell-konsolen.

|Beskrivning                |Name                              |
|---------------------------|----------------------------------|
|Aktuell användare, aktuell värd |`$PROFILE`                        |
|Aktuell användare, aktuell värd |`$PROFILE.CurrentUserCurrentHost` |
|Aktuell användare, alla värdar    |`$PROFILE.CurrentUserAllHosts`    |
|Alla användare, aktuell värd    |`$PROFILE.AllUsersCurrentHost`    |
|Alla användare, alla värdar       |`$PROFILE.AllUsersAllHosts`       |

Eftersom värdena i `$PROFILE` variabeln ändras för varje användare och i varje värd program, se till att du visar värdena för modellvariabler i varje PowerShell-värdprogram som du använder.

Om du vill se de aktuella värdena för `$PROFILE` variabeln skriver du:

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

Du kan använda `$PROFILE` variabeln i många kommandon. Följande kommando öppnar exempelvis profilen "aktuell användare, aktuell värd" i anteckningar:

```powershell
notepad $PROFILE
```

Följande kommando avgör om profilen "alla användare, alla värdar" har skapats på den lokala datorn:

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a>Så här skapar du en profil

Om du vill skapa en PowerShell-profil använder du följande kommando format:

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

Om du till exempel vill skapa en profil för den aktuella användaren i det aktuella PowerShell-värd programmet, använder du följande kommando:

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

I det här kommandot `If` förhindrar instruktionen att du skriver över en befintlig profil. Ersätt värdet för \<profile-path\> plats hållaren med sökvägen till den profil fil som du vill skapa.

> [!NOTE]
> Om du vill skapa profiler för alla användare i Windows Vista och senare versioner av Windows startar du PowerShell med alternativet **Kör som administratör** .

## <a name="how-to-edit-a-profile"></a>Så här redigerar du en profil

Du kan öppna en PowerShell-profil i en text redigerare, till exempel Anteckningar.

Om du vill öppna profilen för den aktuella användaren i det aktuella programmet för PowerShell-värd i anteckningar, skriver du:

```powershell
notepad $PROFILE
```

Ange profil namnet om du vill öppna andra profiler. Om du till exempel vill öppna profilen för alla användare av alla värd program skriver du:

```powershell
notepad $PROFILE.AllUsersAllHosts
```

Om du vill tillämpa ändringarna sparar du profil filen och startar sedan om PowerShell.

## <a name="how-to-choose-a-profile"></a>Så här väljer du en profil

Om du använder flera värd program ska du placera de objekt som du använder i alla värd program i din `$PROFILE.CurrentUserAllHosts` profil. Placera objekt som är specifika för ett värd program, till exempel ett kommando som anger bakgrunds färgen för ett värd program, i en profil som är specifik för värd programmet.

Om du är administratör som anpassar PowerShell för många användare följer du dessa rikt linjer:

- Lagra gemensamma objekt i `$PROFILE.AllUsersAllHosts` profilen
- Lagra objekt som är specifika för ett värd program i `$PROFILE.AllUsersCurrentHost` profiler som är specifika för värd programmet
- Lagra objekt för särskilda användare i användarspecifika profiler

Se till att kontrol lera om det finns någon speciell implementering av PowerShell-profiler i värd program dokumentationen.

## <a name="how-to-use-a-profile"></a>Använda en profil

Många av de objekt som du skapar i PowerShell och de flesta kommandon som du kör påverkar bara den aktuella sessionen. När du slutar sessionen tas objekten bort.

De sessionsbaserade kommandona och objekten innehåller variabler, inställningar för variabler, alias, funktioner, kommandon (förutom för [set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) och PowerShell-moduler som du lägger till i sessionen.

Om du vill spara objekten och göra dem tillgängliga i alla framtida sessioner, lägger du till dem i en PowerShell-profil.

Ett annat vanligt användnings sätt för profiler är att spara ofta använda funktioner, alias och variabler. När du sparar objekten i en profil kan du använda dem i en lämplig session utan att skapa om dem.

## <a name="how-to-start-a-profile"></a>Så här startar du en profil

När du öppnar profil filen är den tom. Du kan dock fylla det med variabler, alias och kommandon som du använder ofta.

Här är några förslag på hur du kan komma igång.

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a>Lägg till kommandon som gör det enkelt att öppna din profil

Detta är särskilt användbart om du använder en annan profil än profilen "aktuell användare, aktuell värd". Lägg till exempel till följande kommando:

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a>Lägg till en funktion som visar alias för alla cmdletar

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a>Anpassa konsolen

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a>Lägg till en anpassad PowerShell-prompt

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

Mer information om PowerShell-prompten finns [about_Prompts](about_Prompts.md).

## <a name="the-noprofile-parameter"></a>Parametern noprofile

Om du vill starta PowerShell utan profiler använder du parametern **noprofile** i **PowerShell.exe** , programmet som startar PowerShell.

Börja genom att öppna ett program som kan starta PowerShell, till exempel Cmd.exe eller PowerShell. Du kan också använda dialog rutan Kör i Windows.

Ange:

```
PowerShell -NoProfile
```

Om du vill ha en fullständig lista över parametrarna för PowerShell.exe skriver du:

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a>Profiler och körnings princip

Körnings principen för PowerShell bestämmer delvis om du kan köra skript och läsa in konfigurationsfiler, inklusive profilerna. Principen för **begränsade** körningar är standardinställningen. Det förhindrar att alla skript körs, inklusive profilerna. Om du använder principen "begränsad" körs inte profilen och dess innehåll tillämpas inte.

Ett `Set-ExecutionPolicy` kommando anger och ändrar din körnings princip. Det är ett av de få kommandon som gäller för alla PowerShell-sessioner eftersom värdet sparas i registret. Du behöver inte ange det när du öppnar-konsolen och du behöver inte lagra ett `Set-ExecutionPolicy` kommando i din profil.

## <a name="profiles-and-remote-sessions"></a>Profiler och fjärrsessioner

PowerShell-profiler körs inte automatiskt i fjärrsessioner, så kommandon som profiler lägger till finns inte i fjärrsessionen. Dessutom `$PROFILE` är den automatiska variabeln inte ifylld i fjärrsessioner.

Om du vill köra en profil i en session använder du cmdleten [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .

Följande kommando kör till exempel "aktuell användare, aktuell värd"-profil från den lokala datorn i sessionen i `$s` .

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

Följande kommando kör profilen "aktuell användare, aktuell värd" från fjärrdatorn i sessionen i `$s` . Eftersom `$PROFILE` variabeln inte är ifylld använder kommandot den explicita sökvägen till profilen. Vi använder en punkt källa-operator så att profilen körs i det aktuella omfånget på fjärrdatorn och inte i det egna omfånget.

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

När du har kört det här kommandot är de kommandon som profilen lägger till i sessionen tillgängliga i `$s` .

## <a name="see-also"></a>Se även

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Prompts](about_Prompts.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Signing](about_Signing.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
