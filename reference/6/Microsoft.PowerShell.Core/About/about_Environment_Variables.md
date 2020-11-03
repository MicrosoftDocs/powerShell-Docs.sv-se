---
description: Beskriver hur du kommer åt Windows-miljövariabler i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 2a477c9e343be2c4e26096fe1a0a73544b5e91bf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270788"
---
# <a name="about-environment-variables"></a>Om miljövariabler

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver hur du kommer åt Windows-miljövariabler i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Miljövariabler lagrar information om operativ system miljön. Den här informationen innehåller information som till exempel operativ system Sök vägen, antalet processorer som används av operativ systemet och platsen för temporära mappar.

Miljövariabler lagrar data som används av operativ systemet och andra program. `WINDIR`Miljövariabeln innehåller till exempel platsen för Windows installations katalog. Program kan fråga värdet för den här variabeln för att avgöra var Windows-operativsystemfiler finns.

PowerShell kan komma åt och hantera miljövariabler i någon av de operativ system plattformar som stöds. PowerShell-hälsoleverantören fören klar den här processen genom att göra det enkelt att visa och ändra miljövariabler.

Miljövariabler, till skillnad från andra typer av variabler i PowerShell, ärvs av underordnade processer, till exempel lokala bakgrunds jobb och sessioner där modul medlemmar körs. Detta gör miljövariabler bra lämpade för att lagra värden som behövs i både över-och underordnade processer.

## <a name="using-and-changing-environment-variables"></a>Använda och ändra miljövariabler

I Windows kan miljövariabler definieras i tre omfång:

- Datorns (eller systemets) omfång
- Användar omfång
- Process omfång

_Process_ omfånget innehåller de miljövariabler som är tillgängliga i den aktuella processen eller PowerShell-sessionen. Den här listan över variabler ärvs från den överordnade processen och är konstruerad från variablerna i _dator_ -och _användar_ omfång. UNIX-baserade plattformar har bara _process_ omfånget.

Du kan visa och ändra värdena för miljövariabler utan att använda en-cmdlet med hjälp av en variabel syntax med-miljö leverantören. Om du vill visa värdet för en miljö variabel använder du följande syntax:

```
$Env:<variable-name>
```

Om du till exempel vill visa värdet för `WINDIR` miljövariabeln, skriver du följande kommando i PowerShell-kommando tolken:

```powershell
$Env:windir
```

I den här syntaxen visar dollar tecknet ( `$` ) en variabel och enhets namnet ( `Env:` ) anger en miljö variabel följt av variabel namnet ( `windir` ).

När du ändrar miljövariabler i PowerShell påverkar ändringen endast den aktuella sessionen. Detta beteende påminner om `Set` kommandots beteende i Windows Command Shell och `Setenv` kommandot i UNIX-baserade miljöer. Om du vill ändra värden i dator-eller användar omfång måste du använda metoderna i klassen **system. Environment** .

För att göra ändringar i webbprogramsomfattande variabler måste även ha behörighet. Om du försöker ändra ett värde utan tillräcklig behörighet, Miss lyckas kommandot och PowerShell visar ett fel.

Du kan ändra värdena för variabler utan att använda en cmdlet med hjälp av följande syntax:

```powershell
$Env:<variable-name> = "<new-value>"
```

Om du till exempel vill lägga till `;c:\temp` värdet för `Path` miljövariabeln, använder du följande syntax:

```powershell
$Env:Path += ";c:\temp"
```

Kolon () i kommandot på Linux eller MacOS `:` separerar den nya sökvägen från den sökväg som föregår den i listan.

```powershell
$Env:PATH += ":/usr/local/temp"
```

Du kan också använda objekt-cmdletar, till exempel `Set-Item` , `Remove-Item` , och `Copy-Item` för att ändra värdena för miljövariabler. Om du till exempel vill använda `Set-Item` cmdleten för att lägga till `;c:\temp` värdet för `Path` miljövariabeln, använder du följande syntax:

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

I det här kommandot omges värdet av parenteser så att det tolkas som en enhet.

## <a name="environment-variables-that-store-preferences"></a>Miljövariabler som lagrar inställningar

PowerShell-funktioner kan använda miljövariabler för att lagra användar inställningar.
Dessa variabler fungerar som Preference-variabler, men de ärvs av underordnade sessioner av de sessioner som de skapas i. Mer information om Preferences-variabler finns i [about_Preference_Variables](about_Preference_Variables.md).

Miljövariablerna som lagrar inställningarna är:

- PSExecutionPolicyPreference

  Lagrar körnings princip uppsättningen för den aktuella sessionen. Denna miljö variabel finns bara när du anger en körnings princip för en enskild session.
  Du kan göra detta på två olika sätt.

  - Starta en session från kommando raden med hjälp av parametern **ExecutionPolicy** för att ange körnings principen för sessionen.

  - Använd `Set-ExecutionPolicy` cmdleten. Använd omfattnings parametern med värdet "process".

    Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).

- PSModuleAnalysisCachePath

  PowerShell ger kontroll över filen som används för att cachelagra data om moduler och deras cmdlets. Cachen läses vid start vid sökning efter ett kommando och skrivs i en bakgrunds tråd någon gång efter att en modul har importer ATS.

  Standard platsen för cachen är:

  - Windows PowerShell 5,1: `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`
  - PowerShell 6,0 och högre: `$env:LOCALAPPDATA\Microsoft\PowerShell`
  - Standard som inte är Windows: `~/.cache/powershell`

  Standard namnet för cachen är `ModuleAnalysisCache` . När du har flera instanser av PowerShell installerat innehåller fil namnet ett hexadecimalt suffix så att det finns ett unikt fil namn per installation.

  > [!NOTE]
  > Om kommando identifieringen inte fungerar som den ska, till exempel om IntelliSense visar kommandon som inte finns kan du ta bort cachefilen. Cachen återskapas nästa gången du startar PowerShell.

  Om du vill ändra standard platsen för cacheminnet anger du miljövariabeln innan du startar PowerShell. Ändringar av denna miljö variabel påverkar bara underordnade processer. Värdet bör ge en fullständig sökväg (inklusive fil namnet) som PowerShell har behörighet att skapa och skriva filer.

  Om du vill inaktivera filcachen ställer du in det här värdet på en ogiltig plats, till exempel:

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to,
  # on non-Windows you would use `/dev/null`
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  Detta anger sökvägen till **NUL** -enheten. PowerShell kan inte skriva till sökvägen, men inget fel returneras. Du kan se de fel som rapporteras med hjälp av en spårning:

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- PSDisableModuleAnalysisCacheCleanup

  När du skriver ut modulens analys-cache söker PowerShell efter moduler som inte längre finns för att undvika en onödigt stor cache. Ibland är de här kontrollerna inte önskvärda, i så fall kan du inaktivera dem genom att ange miljövariabeln värde till `1` .

  Att ställa in den här miljövariabeln börjar gälla direkt i den aktuella processen.

- PSModulePath

  `$env:PSModulePath`Miljövariabeln innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.

  Som standard är de effektiva platser som `$env:PSModulePath` är tilldelade:

  - Platser i hela systemet: dessa mappar innehåller moduler som levereras med PowerShell. Modulerna lagras på `$PSHOME\Modules` platsen. Detta är också den plats där Windows Management-modulerna är installerade.

  - Användare-installerade moduler: de här är moduler som installeras av användaren.
    `Install-Module` har en **omfattnings** parameter som gör att du kan ange om modulen är installerad för den aktuella användaren eller för alla användare. Mer information finns i [install-module](xref:PowerShellGet.Install-Module).

    - I Windows är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME\Documents\PowerShell\Modules` mappen. Platsen för **allusers** -omfattningen är `$env:ProgramFiles\PowerShell\Modules` .
    - På andra datorer än Windows-system är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME/.local/share/powershell/Modules` mappen. Platsen för **allusers** -omfattningen är `/usr/local/share/powershell/Modules` .

  Dessutom kan installations program som installerar moduler i andra kataloger, till exempel katalogen program filer, lägga till sina platser till värdet `$env:PSModulePath` .

  Mer information finns i [about_PSModulePath](about_PSModulePath.md).

## <a name="managing-environment-variables"></a>Hantera miljövariabler

PowerShell tillhandahåller flera olika metoder för att hantera miljövariabler.

- Miljö leverantören het
- Objekt-cmdletar
- Klassen .NET **system. Environment**
- I Windows, kontroll panelen system

### <a name="using-the-environment-provider"></a>Använda-miljö leverantören

Varje miljö variabel representeras av en instans av klassen **system. Collections. typen DictionaryEntry** . I varje **typen DictionaryEntry** -objekt är namnet på miljövariabeln ord listans nyckel. Värdet för variabeln är värdet för ord listan.

Använd cmdleten för att visa egenskaper och metoder för objektet som representerar en miljö variabel i PowerShell `Get-Member` . Om du till exempel vill visa metoder och egenskaper för alla objekt i `Env:` enheten skriver du:

```powershell
Get-Item -Path Env:* | Get-Member
```

PowerShell-hälsoleverantören ger dig åtkomst till miljövariabler i en PowerShell-enhet ( `Env:` enheten). Den här enheten ser ut ungefär som en fil system enhet. Om du vill gå till `Env:` enheten skriver du:

```powershell
Set-Location Env:
```

Använd innehålls-cmdletar för att hämta eller ange värden för en miljö variabel.

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

Du kan visa miljövariablerna i `Env:` enheten från andra PowerShell-enheter, och du kan gå in på `Env:` enheten för att visa och ändra miljövariablerna.

### <a name="using-item-cmdlets"></a>Använda objekt-cmdletar

När du refererar till en miljö variabel, anger du `Env:` enhetens namn följt av namnet på variabeln. Om du till exempel vill visa värdet för `COMPUTERNAME` miljö variabeln, skriver du:

```powershell
Get-ChildItem Env:Computername
```

Om du vill visa värdena för alla miljövariabler skriver du:

```powershell
Get-ChildItem Env:
```

Eftersom miljövariablerna inte har underordnade objekt är resultatet av `Get-Item` och `Get-ChildItem` samma.

Som standard visar PowerShell miljövariablerna i den ordning som de hämtar dem. Om du vill sortera listan över miljövariabler efter variabel namn, skickar du ut resultatet av ett `Get-ChildItem` kommando till `Sort-Object` cmdleten. Till exempel, från valfri PowerShell-enhet, skriver du:

```powershell
Get-ChildItem Env: | Sort Name
```

Du kan också gå in på `Env:` enheten med hjälp av `Set-Location` cmdleten:

```powershell
Set-Location Env:
```

När du är i `Env:` enheten kan du utelämna `Env:` enhets namnet från sökvägen. Om du till exempel vill visa alla miljövariabler skriver du:

```powershell
PS Env:\> Get-ChildItem
```

Om du vill visa värdet för `COMPUTERNAME` variabeln inifrån `Env:` enheten skriver du:

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a>Spara ändringar i miljövariabler

Om du vill göra en beständig ändring i en miljö variabel i Windows kan du använda system kontroll panelen. Välj **Avancerade systeminställningar**. På fliken **Avancerat** klickar du på **miljö variabel...**. Du kan lägga till eller redigera befintliga miljövariabler i scope för **användare** och **system** (datorer). Windows skriver dessa värden till registret så att de behålls mellan sessioner och omstarter av systemet.

Alternativt kan du lägga till eller ändra miljövariabler i din PowerShell-profil. Den här metoden fungerar för alla versioner av PowerShell på alla plattformar som stöds.

### <a name="using-systemenvironment-methods"></a>Använda system. miljö metoder

Klassen **system. Environment** tillhandahåller **GetEnvironmentVariable** -och **SetEnvironmentVariable** -metoder som gör att du kan ange variabelns omfång.

I följande exempel används metoden **GetEnvironmentVariable** för att hämta dator inställningen för `PSModulePath` och metoden **SetEnvironmentVariable** för att lägga till `C:\Program Files\Fabrikam\Modules` sökvägen till värdet.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

Mer information om metoderna i klassen **system. miljö** finns i [miljö metoder](/dotnet/api/system.environment).

## <a name="see-also"></a>SE ÄVEN

- [Miljö (Provider)](../About/about_Environment_Provider.md)
- [about_Modules](about_Modules.md)
