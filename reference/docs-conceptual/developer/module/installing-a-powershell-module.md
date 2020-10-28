---
ms.date: 09/13/2016
ms.topic: reference
title: Installera en PowerShell-modul
description: Installera en PowerShell-modul
ms.openlocfilehash: 3c7a4413168934ca4de1912c9615a6ae0fc45788
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645344"
---
# <a name="installing-a-powershell-module"></a>Installera en PowerShell-modul

När du har skapat din PowerShell-modul vill du förmodligen installera modulen i ett system, så att du eller andra kan använda den. Detta består vanligt vis av att kopiera modulblad (IE,. psm1 eller binär sammansättning, modulens manifest och andra tillhör ande filer) till en katalog på den datorn. För ett mycket litet projekt kan detta vara lika enkelt som att kopiera och klistra in filerna med Utforskaren på en enskild fjärrdator. men för större lösningar kanske du vill använda en mer avancerad installations process. Oavsett hur du hämtar modulen till systemet, kan PowerShell använda ett antal tekniker som gör det möjligt för användarna att hitta och använda dina moduler. Därför säkerställer det huvudsakliga problemet för installationen att PowerShell kan hitta modulen. Mer information finns i [Importera en PowerShell-modul](./importing-a-powershell-module.md).

## <a name="rules-for-installing-modules"></a>Regler för att installera moduler

Följande information gäller alla moduler, inklusive moduler som du skapar för din egen användning, moduler som du hämtar från andra parter och moduler som du distribuerar till andra.

### <a name="install-modules-in-psmodulepath"></a>Installera moduler i PSModulePath

När det är möjligt kan du installera alla moduler i en sökväg som anges i **PSModulePath** -miljövariabeln eller lägga till modulens sökväg i variabeln **PSModulePath** Environment.

**PSModulePath** -miljövariabeln ($env:P smodulepath) innehåller platserna för Windows PowerShell-moduler. -Cmdletar är beroende av värdet för den här miljövariabeln för att hitta moduler.

Som standard innehåller variabeln **PSModulePath** följande kataloger för system-och användar moduler, men du kan lägga till och redigera värdet.

- `$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Den här platsen är reserverad för moduler som levereras med Windows. Installera inte moduler på den här platsen.

- `$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)

  Använd något av följande kommandon för att hämta värdet för **PSModulePath** -miljövariabeln.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Om du vill lägga till en modul Sök väg till värdet för **PSModulePath** -miljövariabeln värde, använder du följande kommando format. I det här formatet används **SetEnvironmentVariable** -metoden i klassen **system. Environment** för att göra en sessions oberoende ändring i miljövariabeln **PSModulePath** .

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > När du har lagt till sökvägen till **PSModulePath** bör du sända ett miljö meddelande om ändringen. Genom att sända ändringen kan andra program, till exempel gränssnittet, Hämta ändringen. Om du vill sända ändringen ska du be din produkt installations kod att skicka ett **WM_SETTINGCHANGE** meddelande med `lParam` inställningen "miljö". Se till att skicka meddelandet efter att modulens installations kod har uppdaterats **PSModulePath** .

### <a name="use-the-correct-module-directory-name"></a>Använd rätt katalog namn för modul

En välformulerad modul är en modul som lagras i en katalog som har samma namn som grund namnet på minst en fil i modul katalogen. Om en modul inte är korrekt utformad känner Windows PowerShell inte igen som en modul.

"Grund namnet" i en fil är namnet utan fil namns tillägget. I en välformulerad modul måste namnet på den katalog som innehåller module-filerna matcha bas namnet för minst en fil i modulen.

I exempel Fabrikam-modulen är katalogen som innehåller filerna namnet "Fabrikam" och minst en fil har bas namnet "Fabrikam". I det här fallet måste både Fabrikam.psd1 och Fabrikam.dll ha "Fabrikam"-bas namnet.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Påverkan av felaktig installation

Om modulen inte är korrekt utformad och dess plats inte ingår i värdet för **PSModulePath** -miljövariabeln, så fungerar inte grundläggande identifierings funktioner i Windows PowerShell, till exempel följande.

- Funktionen för automatisk inläsning av modulen kan inte automatiskt importera modulen.

- `ListAvailable`Parametern för cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) kan inte hitta modulen.

- Cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) kan inte hitta modulen. Om du vill importera modulen måste du ange den fullständiga sökvägen till rot modul filen eller manifest filen för modulen.

  Ytterligare funktioner, till exempel följande, fungerar inte om modulen inte importeras till sessionen. I välformulerade moduler i **PSModulePath** -miljövariabeln fungerar dessa funktioner även när modulen inte importeras till sessionen.

- Cmdleten [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) kan inte hitta kommandon i modulen.

- Cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) kan inte uppdatera eller spara hjälp för modulen.

- Cmdleten [show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) kan inte hitta och Visa kommandon i modulen.

  Kommandona i modulen saknas i `Show-Command` fönstret i Windows POWERSHELL Ise (Integrated Scripting Environment).

## <a name="where-to-install-modules"></a>Installera moduler

I det här avsnittet beskrivs var i fil systemet det ska gå att installera Windows PowerShell-moduler. Platsen beror på hur modulen används.

### <a name="installing-modules-for-a-specific-user"></a>Installera moduler för en speciell användare

Om du skapar en egen modul eller hämtar en modul från en annan part, till exempel en Windows PowerShell Community-webbplats, och du vill att modulen bara ska vara tillgänglig för ditt användar konto, installerar du modulen i din användarspecifika katalog.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

Katalogen med användarspecifika moduler läggs till i värdet för miljövariabeln **PSModulePath** som standard.

### <a name="installing-modules-for-all-users-in-program-files"></a>Installera moduler för alla användare i programfiler

Om du vill att en modul ska vara tillgänglig för alla användar konton på datorn installerar du modulen på platsen program fil.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> Platsen för program filer läggs till i värdet för PSModulePath-miljövariabeln som standard i Windows PowerShell 4,0 och senare. För tidigare versioner av Windows PowerShell kan du manuellt skapa platsen för programfiler (%ProgramFiles%\WindowsPowerShell\Modules) och lägga till den här sökvägen till PSModulePath-miljövariabeln enligt beskrivningen ovan.

### <a name="installing-modules-in-a-product-directory"></a>Installera moduler i en produkt katalog

Om du distribuerar modulen till andra parter använder du standard platsen för programfiler som beskrivs ovan eller skapar en egen företagsspecifik eller produktspecifik under katalog till katalogen% ProgramFiles%.

Exempelvis levererar Fabrikam Technologies, ett fiktivt företag, en Windows PowerShell-modul för sin Fabrikam Manager-produkt. Installations programmet för modulen skapar en underkatalog för moduler i under katalogen Fabrikam Manager-produkt.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Om du vill aktivera identifierings funktionerna i Windows PowerShell-modulen för att hitta Fabrikam-modulen lägger du till modulen i värdet för **PSModulePath** -miljövariabeln i installations programmet för Fabrikam-modulen.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Installera moduler i Common Files-katalogen

Om en modul används av flera komponenter i en produkt eller flera versioner av en produkt, installerar du modulen i en modul-Specific-underkatalogen i under katalogen%ProgramFiles%\Common Files\Modules.

I följande exempel installeras modulen Fabrikam i en Fabrikam-under katalog i under `%ProgramFiles%\Common Files\Modules` katalogen. Observera att varje modul finns i en egen under katalog i under katalogen moduler.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

Installations programmet säkerställer sedan att värdet för **PSModulePath** -miljövariabeln innehåller sökvägen till under katalogen vanliga filer för moduler.

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

Om du vill installera flera versioner av samma modul använder du följande procedur.

1. Skapa en katalog för varje version av modulen. Inkludera versions numret i katalog namnet.
2. Skapa ett modul manifest för varje version av modulen. I värdet för nyckeln **ModuleVersion** i manifestet anger du versions numret för modulen. Spara manifest filen (. psd1) i den versions bara katalogen för modulen.
3. Lägg till rotmappen för modulen rot i värdet för **PSModulePath** -miljövariabeln, som visas i följande exempel.

Om du vill importera en viss version av modulen kan slutanvändaren använda `MinimumVersion` `RequiredVersion` parametrarna eller för cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Om till exempel Fabrikam-modulen är tillgänglig i versionerna 8,0 och 9,0 kan katalog strukturen Fabrikam likna följande.

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

Installations programmet lägger till båda modulens sökvägar i **PSModulePath** -miljövariabeln-värde.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

När de här stegen är klara, hämtar parametern **ListAvailable** för cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) båda fabriks modulerna. Om du vill importera en viss modul använder `MinimumVersion` du `RequiredVersion` parametrarna eller för cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Om båda modulerna importeras till samma session och modulerna innehåller cmdlets med samma namn, gäller cmdletarna som importeras sist i sessionen.

## <a name="handling-command-name-conflicts"></a>Hantera kommando namns konflikter

Kommando namns konflikter kan uppstå när kommandon som en modul exporterar har samma namn som kommandon i användarens session.

När en session innehåller två kommandon som har samma namn, kör Windows PowerShell den kommando typ som har företräde. När en session innehåller två kommandon som har samma namn och samma typ, kör Windows PowerShell kommandot som har lagts till i sessionen senast. Om du vill köra ett kommando som inte körs som standard kan användare kvalificera sig med kommandots namn med namnet på modulen.

Om sessionen t. ex. innehåller en `Get-Date` funktion och `Get-Date` cmdleten körs funktionen som standard i Windows PowerShell. Om du vill köra cmdleten, Inled kommandot med namnet på modulen, till exempel:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

För att förhindra namn konflikter kan modulen författare använda **DefaultCommandPrefix** -nyckeln i modulen manifest för att ange ett substantiv-prefix för alla kommandon som exporteras från modulen.

Användare kan använda parametern **prefix** för `Import-Module` cmdleten för att använda ett alternativt prefix. Värdet för parametern **prefix** har företräde framför värdet för **DefaultCommandPrefix** -nyckeln.

## <a name="see-also"></a>Se även

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Skriva en Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
