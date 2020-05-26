---
title: Migrera från Windows PowerShell 5.1 till PowerShell 7
description: Uppdatera från PowerShell 5,1 till PowerShell 7 för dina Windows-plattformar.
ms.date: 03/25/2020
ms.openlocfilehash: cb14a4f159b6dc33f31386da4264c0ebb640aef8
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810577"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a>Migrera från Windows PowerShell 5.1 till PowerShell 7

PowerShell 7 är utformat för molnbaserade, lokala miljöer och hybrid miljöer och är förpackat med förbättringar och [nya funktioner](../whats-new/What-s-New-in-PowerShell-70.md).

- Installerar och körs sida vid sida med Windows PowerShell
- Förbättrad kompatibilitet med befintliga Windows PowerShell-moduler
- Nya språk funktioner, t. ex. ternära operatörer och`ForEach-Object -Parallel`
- Förbättrade prestanda
- SSH-baserad fjärr kommunikation
- Samverkan mellan plattformar
- Stöd för Docker-behållare

PowerShell 7 fungerar sida vid sida med Windows PowerShell och du kan enkelt testa och jämföra versioner innan du distribuerar. Migrering är enkel, snabb och säker.

PowerShell 7 stöds i följande Windows-operativ system:

- Windows 8,1 och 10
- Windows Server 2012, 2012 R2, 2016 och 2019

PowerShell 7 körs också på macOS och flera Linux-distributioner. En lista över operativ system som stöds och information om support livs cykeln finns i [PowerShell-Supportens livs cykel](/powershell/scripting/powershell-support-lifecycle).

## <a name="installing-powershell-7"></a>Installera PowerShell 7

Det finns flera tillgängliga alternativ för att installera PowerShell 7 för flexibilitet och för att stödja behoven hos IT, DevOps-tekniker och utvecklare. I de flesta fall kan installations alternativen minskas till följande metoder:

- Distribuera PowerShell med [MSI-paketet](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)
- Distribuera PowerShell med [zip-paketet](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)

> [!NOTE]
> MSI-paketet kan distribueras och uppdateras med hanterings produkter som [System Center Configuration Manager (SCCM)](/configmgr/apps/). Hämta paketen från [GitHub release-sidan](https://github.com/PowerShell/PowerShell/releases).

För att distribuera MSI-paketet krävs administratörs behörighet. ZIP-paketet kan distribueras av vilken användare som helst. ZIP-paketet är det enklaste sättet att installera PowerShell 7 för testning innan du genomför en fullständig installation.

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a>Använda PowerShell 7 sida vid sida med Windows PowerShell 5,1

PowerShell 7 är utformat för att fungera tillsammans med Windows PowerShell 5,1. Följande funktioner säkerställer att din investering i PowerShell är skyddad och att migreringen till PowerShell 7 är enkel.

- Separat installations Sök väg och namn på körbar fil
- Separata PSModulePath
- Separata profiler för varje version
- Förbättrad modul-kompatibilitet
- Nya slut punkter för fjärrkommunikation
- Stöd för grup princip
- Separata händelse loggar

### <a name="separate-installation-path-and-executable-name"></a>Separat installations Sök väg och namn på körbar fil

PowerShell 7 installeras i en ny katalog, vilket möjliggör körning sida vid sida med Windows PowerShell 5,1.

Installera platser efter version:

- Windows PowerShell 5,1:`$env:WINDIR\System32\WindowsPowerShell\v1.0`
- PowerShell Core 6. x:`$env:ProgramFiles\PowerShell\6`
- PowerShell 7:`$env:ProgramFiles\PowerShell\7`

Den nya platsen läggs till i din sökväg så att du kan köra både Windows PowerShell 5,1 och PowerShell 7. Om du migrerar från PowerShell Core 6. x till PowerShell 7 tas PowerShell 6 bort och sökvägen ersätts.

I Windows PowerShell heter PowerShell-körbara filen `powershell.exe` . I version 6 och senare heter den körbara filen `pwsh.exe` . Det nya namnet gör det enkelt att stödja körning sida vid sida av båda versionerna.

### <a name="separate-psmodulepath"></a>Separata PSModulePath

Som standard är Windows PowerShell-och PowerShell 7 Store-moduler på olika platser. PowerShell 7 kombinerar dessa platser i `$Env:PSModulePath` miljö variabeln. När du importerar en modul efter namn, kontrollerar PowerShell platsen som anges av `$Env:PSModulePath` . Detta gör att PowerShell 7 kan läsa in både Core-och Desktop-moduler.

|            Installations omfång            |                Windows PowerShell 5,1                 |             PowerShell 7,0             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| PowerShell-moduler                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| Användaren är installerad<br>AllUsers-omfång    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| Användaren är installerad<br>CurrentUser-omfång | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

I följande exempel visas standardvärdena för `$Env:PSModulePath` för varje version.

- För Windows PowerShell 5,1:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- För PowerShell 7:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

Observera att PowerShell 7 innehåller sökvägar för Windows PowerShell och PowerShell 7-sökvägar för att tillhandahålla automatisk inläsning av moduler.

> [!NOTE]
> Det kan finnas ytterligare sökvägar om du har ändrat PSModulePath-miljövariabeln eller installerat anpassade moduler eller program.

Mer information finns `PSModulePath` i i [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).

Mer information om moduler finns i [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).

### <a name="separate-profiles"></a>Separata profiler

En PowerShell-profil är ett skript som körs när PowerShell startar. Det här skriptet anpassar din miljö genom att lägga till kommandon, alias, funktioner, variabler, moduler och PowerShell-enheter. Profil skriptet gör dessa anpassningar tillgängliga i varje session utan att behöva återskapa dem manuellt.

Sökvägen till profilens plats har ändrats i PowerShell 7.

- I Windows PowerShell 5,1 är sökvägen till profilen `$HOME\Documents\WindowsPowerShell` .
- I PowerShell 7 är platsen för profilen `$HOME\Documents\PowerShell` .

Profil fil namnen har också ändrats:

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

Mer information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a>PowerShell 7-kompatibilitet med Windows PowerShell 5,1-moduler

De flesta moduler som du använder i Windows PowerShell 5,1 fungerar redan med PowerShell 7, inklusive Azure PowerShell och Active Directory. Vi fortsätter att arbeta med andra team för att lägga till inbyggt PowerShell 7-stöd för fler moduler, inklusive Microsoft Graph, Office 365 och andra. Den aktuella listan över moduler som stöds finns i [PowerShell 7-modulens kompatibilitet](/powershell/scripting/whats-new/module-compatibility).

> [!NOTE]
> I Windows har vi också lagt till en **UseWindowsPowerShell** -växel för `Import-Module` att under lätta över gången till PowerShell 7 för de som använder inkompatibla moduler. Mer information om den här funktionen finns i [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).

### <a name="powershell-remoting"></a>PowerShell fjärrkommunikation

Med PowerShell-fjärrkommunikation kan du köra alla PowerShell-kommandon på en eller flera fjärrdatorer. Du kan upprätta beständiga anslutningar, starta interaktiva sessioner och köra skript på fjärrdatorer.

#### <a name="ws-management-remoting"></a>WS-Management Remoting

Windows PowerShell 5,1 och tidigare använder WS-Management-protokollet (WSMAN) för anslutnings förhandling och data transport. Windows Remote Management (WinRM) använder WSMAN-protokollet. Om WinRM har Aktiver ATS använder PowerShell 7 den befintliga Windows PowerShell 5,1-slutpunkten med namnet `Microsoft.PowerShell` för fjärr anslutningar. Kör cmdleten om du vill uppdatera PowerShell 7 för att ta med sin egen slut punkt `Enable-PSRemoting` . Information om hur du ansluter till vissa slut punkter finns i [WS-Management Remoting i PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)

Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.
Mer information, inklusive instruktioner, finns i [om krav för fjärrhantering](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Mer information om hur du arbetar med fjärr kommunikation finns i [om fjärran sluten](/powershell/module/microsoft.powershell.core/about/about_remote)

#### <a name="ssh-based-remoting"></a>SSH-baserad fjärr kommunikation

SSH-baserad fjärr kommunikation lades till i PowerShell Core 6. x för att stödja andra operativ system som inte kan använda Windows inbyggda komponenter som **WinRM**. SSH-fjärrkommunikation skapar en PowerShell-värd process på mål datorn som ett SSH-undersystem. Mer information och exempel på hur du konfigurerar SSH-baserad fjärr kommunikation i Windows eller Linux finns i: [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

> [!NOTE]
> PowerShell-galleriet (PSGallery) innehåller en modul och en cmdlet som automatiskt konfigurerar SSH-baserad fjärr kommunikation. Installera `Microsoft.PowerShell.RemotingTools` modulen från [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) och kör `Enable-SSH` cmdleten.

`New-PSSession` `Enter-PSSession` Cmdletarna, och `Invoke-Command` har nya parameter uppsättningar som stöder SSH-anslutningar.

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Om du vill skapa en fjärrsession anger du mål datorn med parametern **hostname** och anger användar namnet **med användar namnet.** När du kör cmdletarna interaktivt, uppmanas du att ange ett lösen ord.

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

Om du använder **hostname** -parametern anger du användar namns informationen följt av at-tecknet ( `@` ) följt av dator namnet.

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

Du kan konfigurera SSH-nyckel-autentisering med hjälp av en privat nyckel fil med parametern för nyckel **Sök** vägar.
Mer information finns i [openssh Key Management](/windows-server/administration/openssh/openssh_keymanagement).

### <a name="group-policy-supported"></a>grupprincip som stöds

PowerShell innehåller grupprincip inställningar som hjälper dig att definiera konsekventa alternativ värden för servrar i en företags miljö. Inställningarna omfattar:

- Konfiguration av konsolsession: anger en konfigurations slut punkt där PowerShell körs.
- Aktivera modul loggning: anger LogPipelineExecutionDetails-egenskapen för moduler.
- Aktivera loggning av PowerShell-skript block: aktiverar detaljerad loggning av alla PowerShell-skript.
- Aktivera skript körning: ställer in PowerShell-körnings principen.
- Aktivera PowerShell-avskrift: aktiverar insamling av indata och utdata från PowerShell-kommandon i textbaserade avskrifter.
- Ange standard Sök vägen för uppdatering-hjälp: Anger källan för uppdaterbar hjälp till en katalog, inte Internet.

Mer information finns i [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).

PowerShell 7 innehåller grupprincip mallar och ett installations skript i `$PSHOME` .

Grupprincip verktyg använder administrativa mallfiler ( `.admx` , `.adml` ) för att fylla i princip inställningar i användar gränssnittet. Detta gör det möjligt för administratörer att hantera registerbaserade princip inställningar. `InstallPSCorePolicyDefinitions.ps1`Skriptet installerar PowerShell Core administrativa mallar på den lokala datorn.

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a>Separata händelse loggar

Windows PowerShell-och PowerShell 7-logg händelser för att separera händelse loggar. Använd följande kommando för att hämta en lista över PowerShell-loggar.

```powershell
Get-WinEvent -ListLog *PowerShell*
```

Mer information finns i [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).

## <a name="improved-editing-experience-with-visual-studio-code"></a>Förbättrad redigerings upplevelse med Visual Studio Code

[Visual Studio Code (VSCode)](https://code.visualstudio.com/) med [PowerShell-tillägget](https://code.visualstudio.com/docs/languages/powershell) är den skript miljö som stöds för PowerShell 7. Windows PowerShell ISE (Integrated Scripting Environment) stöder enbart Windows PowerShell.

Det uppdaterade PowerShell-tillägget innehåller:

- Nytt ISE-kompatibelt läge
- PSReadLine i den integrerade konsolen, inklusive syntax för syntax, redigering på flera rader och bakåt-sökning
- Stabilitets-och prestanda förbättringar
- Ny CodeLens-integrering
- Förbättrad automatisk komplettering av sökvägen

Om du vill göra över gången till Visual Studio Code enklare använder du funktionen **Aktivera ISE-läge** som är tillgänglig i **kommando paletten**. Den här funktionen växlar VSCode till en typ av ISE-layout. Formatet ISE ger dig alla nya funktioner och funktioner i PowerShell i en välbekant användar upplevelse.

Du växlar till den nya ISE-layouten genom att trycka på <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> för att öppna **kommando-paletten**, skriva `PowerShell` och välja **PowerShell: Aktivera ISE-läge**.

Om du vill ställa in layouten på den ursprungliga layouten öppnar du **kommandot palett**, väljer **POWERSHELL: inaktivera ISE-läge (Återställ till standardvärden)**.

Mer information om hur du anpassar VSCode-layouten till ISE finns i [så här replikerar du ISE-upplevelsen i Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)

> [!NOTE]
> Det finns inga planer på att uppdatera ISE med nya funktioner. ISE är nu en funktion för att avinstallera användare i de senaste versionerna av Windows 10 och Windows Server. Det finns inga planer på att permanent ta bort ISE. PowerShell-teamet och dess partners fokuserar på att förbättra skript upplevelsen i PowerShell-tillägget för Visual Studio Code.

## <a name="next-steps"></a>Efterföljande moment

Följ med kunskapen för att snabbt migrera, [Installera PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) nu!
