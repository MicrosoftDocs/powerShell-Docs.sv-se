---
title: Installerar ett PowerShell-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082200"
---
# <a name="installing-a-powershell-module"></a>Installera en PowerShell-modul

När du har skapat din PowerShell-modulen, kommer troligen du att installera modulen på ett system, så att du eller andra kan använda den. Generellt sett består detta bara modulen filerna kopieras (.psm1, eller binära sammansättningen, modulmanifestet, och andra tillhörande filer) till en katalog på datorn. För ett mycket små projekt, och detta kan vara lika enkelt som att kopiera och klistra in filerna med Windows Explorer till en fjärransluten dator. men för större lösningar kan du använda en mer avancerad installationsprocess. Oavsett hur du får din modul till systemet, kan PowerShell använda flera olika tekniker som låter användarna hitta och använda dina moduler. (Mer information finns i [importera en PowerShell-modul](./importing-a-powershell-module.md).) Största problemet för installation därför se till att PowerShell kommer att kunna hitta din modul.

Det här avsnittet består av följande underavsnitt:

- Regler för att installera moduler

- Var du vill installera moduler

- Installera flera versioner av en modul

- Hantering av kommandot namnet står i konflikt

## <a name="rules-for-installing-modules"></a>Regler för att installera moduler

Följande information gäller alla moduler, inklusive moduler som du skapar för användning, moduler som du får från andra parter och moduler som du distribuerar till andra.

### <a name="install-modules-in-psmodulepath"></a>Installera moduler i PSModulePath

När det är möjligt, installera alla moduler i en sökväg som anges i den **PSModulePath** miljövariabeln eller Lägg till modulen sökvägen till den **PSModulePath** miljövariabelvärdet.

Den **PSModulePath** miljövariabeln ($Env: PSModulePath) innehåller platserna för Windows PowerShell-moduler. Cmdlet: ar är beroende av värdet för den här miljövariabeln för att hitta moduler.

Som standard den **PSModulePath** miljövariabelvärdet innehåller följande system och användaren modulen kataloger, men du kan lägga till och redigera värdet.

- $PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Den här platsen är reserverad för moduler som medföljer Windows. Installera inte moduler till den här platsen.

- $Home\Documents\WindowsPowerShell\Modules (% UserProfile%\Documents\WindowsPowerShell\Modules)

- $Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)

  Att hämta värdet för den **PSModulePath** miljövariabeln, använda någon av följande kommandon.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Att lägga till en modulsökväg till värdet för den **PSModulePath** miljövariabeln värde, använder du följande kommandoformat. Det här formatet använder den **SetEnvironmentVariable** -metoden för den **System.Environment** klassen för att göra en ändring av sessionen oberoende den **PSModulePath** miljö variabeln.

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > När du har lagt till sökvägen till **PSModulePath**, bör du skicka meddelandet miljö om ändringen. Sänder ändringen kan andra program, till exempel i gränssnittet och att välja ändringen. Om du vill skicka ändringen har din kod för installation av produkten skicka en **uppdaterats** med `lParam` anger till strängen ”miljö”. Se till att skicka meddelandet när modulen installationen koden har uppdaterats **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Använd rätt modul katalognamn

En ”välformulerad” modul är en modul som lagras i en mapp med samma namn som det grundläggande namnet på minst en fil i modulkatalogen. Om en modul inte är korrekt formaterad, känner Windows PowerShell inte igen det som en modul.

”Huvudnamnet” för en fil är namn utan filnamnstillägget. I en giltig modul, måste namnet på den katalog som innehåller filerna som modulen matcha det grundläggande namnet på minst en fil i modulen.

Till exempel i Fabrikam exempelmodulen den katalog som innehåller filerna som modulen heter ”Fabrikam” och minst en fil har det grundläggande namnet ”Fabrikam”. I det här fallet har både Fabrikam.psd1 och Fabrikam.dll det grundläggande namnet ”Fabrikam”.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Effekten av felaktig Installation

Om modulen är inte korrekt formaterad och dess plats ingår inte i värdet för den **PSModulePath** miljövariabeln, identifiering av grundläggande funktioner i Windows PowerShell, exempelvis följande, fungerar inte.

- Modulen automatisk inläsning-funktionen kan inte importera modulen automatiskt.

- Den `ListAvailable` -parametern för den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet kan inte hitta modulen.

- Den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet kan inte hitta modulen. Du måste ange den fullständiga sökvägen till rot-filen för modulen eller modulen manifestfilen om du vill importera modulen.

  Ytterligare funktioner, till exempel följande, fungerar inte om inte modulen har importerats till sessionen. I rätt moduler i den **PSModulePath** miljövariabeln, dessa funktioner fungerar även om modulen inte importeras till sessionen.

- Den [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet kan inte hitta kommandon i modulen.

- Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets kan inte uppdatera eller spara hjälp för modulen.

- Den [visningskommandot](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet: Det går inte att hitta och visa kommandon i modulen.

  Kommandona i modulen saknas från den `Show-Command` fönster i Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>Var du vill installera moduler

Det här avsnittet beskrivs var i filsystemet för att installera Windows PowerShell-moduler. Platsen är beroende av hur modulen ska användas.

### <a name="installing-modules-for-a-specific-user"></a>Installera moduler för en viss användare

Om du skapar en egen modul eller få en modul från en annan part, till exempel en community-webbplatsen för Windows PowerShell, och du vill att modulen ska vara tillgängliga för ditt konto endast, installera modulen i katalogen användarspecifika moduler.

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

Katalogen användarspecifika moduler läggs till i värdet för den **PSModulePath** miljövariabeln som standard.

### <a name="installing-modules-for-all-users-in-program-files"></a>Installera moduler för alla användare i program

Om du vill att en modul ska vara tillgängliga för alla användarkonton på datorn, installera modulen på platsen för programmet.

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> Plats för programfiler läggs till värdet för miljövariabeln PSModulePath som standard i Windows PowerShell 4.0 och senare. För tidigare versioner av Windows PowerShell kan du manuellt skapa programfiler plats ((%ProgramFiles%\WindowsPowerShell\Modules) och lägga till den här sökvägen i miljövariabeln PSModulePath enligt beskrivningen ovan.

### <a name="installing-modules-in-a-product-directory"></a>Installerar moduler i en produktkatalog

Om du ska distribuera modulen till andra parter använda standardplatsen för programfiler som beskrivs ovan, eller skapa egna företagsspecifik eller produktspecifik underkatalog i katalogen % ProgramFiles %.

Fabrikam-tekniker, ett fiktivt företag, levereras till exempel en Windows PowerShell-modul för sina Fabrikam Manager-produkten. Sina modulen installer skapar en underkatalog moduler i underkatalogen Fabrikam Manager produkten.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Om du vill aktivera Windows PowerShell-modulen identifiering funktioner att hitta modulen Fabrikam Fabrikam modulen installationsprogrammet lägger till modulen platsen till värdet för den **PSModulePath** miljövariabeln.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Installerar moduler i katalogen med vanliga

Om en modul används av flera komponenter i en produkt eller genom att flera versioner av en produkt, installera modulen i en modul-specifika underkatalog i underkatalogen %ProgramFiles%\Common Files\Modules.

I följande exempel installeras Fabrikam-modulen i en underkatalog för Fabrikam i underkatalogen %ProgramFiles%\Common Files\Modules. Observera att varje modul finns i en egen underkatalog i underkatalogen moduler.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

Sedan kan installationsprogrammet säkerställer värdet för den **PSModulePath** miljövariabeln innehåller sökvägen i underkatalogen moduler vanliga filer.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Installera flera versioner av en modul

Använd följande procedur för att installera flera versioner av samma modul.

1. Skapa en katalog för varje version av modulen. Inkludera versionsnumret i katalognamnet.

2. Skapa ett modulmanifest för varje version av modulen. I värdet för den **ModuleVersion** nyckeln i manifestet, ange versionsnummer för modulen. Spara manifestfilen (.psd1) i katalogen versionsspecifika för modulen.

3. Lägg till sökvägen till rotmappen modulen till värdet för den **PSModulePath** miljövariabeln, som visas i följande exempel.

Om du vill importera en viss version av modulen, slutanvändaren kan använda den `MinimumVersion` eller `RequiredVersion` parametrarna för den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Till exempel om modulen Fabrikam är tillgängliga i version 8.0 och 9.0, kan katalogstruktur för Fabrikam-modulen likna följande.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

Installationsprogrammet lägger till båda modulernas sökvägar till den **PSModulePath** miljövariabelvärdet.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

När dessa steg har slutförts, den **ListAvailable** -parametern för den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet hämtar båda Fabrikam-moduler. Om du vill importera en viss modul, Använd den `MinimumVersion` eller `RequiredVersion` parametrarna för den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Om båda moduler importeras till samma session, och moduler innehåller cmdletar och arbetsflöden med samma namn, gäller de cmdletar som importeras senast i sessionen.

## <a name="handling-command-name-conflicts"></a>Hantering av kommandot namnet står i konflikt

Namnkonflikter i kommandot kan inträffa när de kommandon som en modul exporterar har samma namn som kommandon i sessionen.

När en session innehåller två kommandon som har samma namn, kör Windows PowerShell kommandotypen som företräde. När en session innehåller två kommandon som har samma namn och samma typ, kör Windows PowerShell-kommandot som har lagts till i sessionen senast. Om du vill köra ett kommando som inte körs som standard, kan användare kvalificera sig kommandonamnet med modulens namn.

Om sessionen innehåller till exempel en `Get-Date` funktion och `Get-Date` Windows PowerShell-cmdleten körs funktionen som standard. För att köra cmdlet: en, måste du börja kommandot med modulens namn, till exempel:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

För att förhindra namnkonflikter modulskapare kan använda den **DefaultCommandPrefix** exportera nyckeln i modulmanifestet att ange ett substantivprefix för alla kommandon från modulen.

Användare kan använda den **Prefix** -parametern för den `Import-Module` cmdlet för att använda en annan prefix. Värdet för den **prefixet** parametern har företräde framför värdet för den **DefaultCommandPrefix** nyckel.

## <a name="see-also"></a>Se även

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Skriva ett Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
