---
ms.date: 03/12/2021
ms.topic: reference
title: Ändra installationssökvägen för PSModulePath
description: Ändra installationssökvägen för PSModulePath
ms.openlocfilehash: 1bea1e8ed20f55352cc9b4270e95cf7f0f7e2faa
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412911"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Ändra installationssökvägen för PSModulePath

`PSModulePath`Miljövariabeln lagrar Sök vägarna till platserna för de moduler som är installerade på disk. PowerShell använder den här variabeln för att hitta moduler när användaren inte anger den fullständiga sökvägen till en modul. Sök vägarna i den här variabeln genomsöks i den ordning som de visas.

När PowerShell startar `PSModulePath` skapas som en system miljö variabel med följande standardvärde: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` i Windows och `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` på Linux eller Mac, och `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` för Windows PowerShell.

> [!NOTE]
> Den användarspecifika **CurrentUser** -platsen är `WindowsPowerShell\Modules` mappen som finns på **dokument** platsen i din användar profil. Den angivna sökvägen till platsen varierar efter Windows-version och om du använder mappomdirigering. Som standard är den platsen i Windows 10 `$HOME\Documents\WindowsPowerShell\Modules` .

## <a name="to-view-the-psmodulepath-variable"></a>Så här visar du variabeln PSModulePath

Om du vill visa Sök vägarna som anges i `PSModulePath` variabeln, skriver du följande kommando:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Lägga till platser i PSModulePath-variabeln

Använd någon av följande metoder för att lägga till sökvägar till den här variabeln:

- Om du vill lägga till ett tillfälligt värde som bara är tillgängligt för den aktuella sessionen kör du följande kommando på kommando raden:

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- Om du vill lägga till ett permanent värde som är tillgängligt när en session öppnas, lägger du till kommandot ovan i en PowerShell-profil fil ( `$PROFILE` ) >

  Mer information om profiler finns [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).

- Om du vill lägga till en beständig variabel i registret skapar du en ny användar miljö variabel som kallas `PSModulePath` med hjälp av miljövariabler-redigeraren i dialog rutan **system egenskaper** .

- Om du vill lägga till en beständig variabel med hjälp av ett skript, använder du .net-metoden [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) i klassen [system. Environment](/dotnet/api/system.environment) . Följande skript lägger till exempel till `C:\Program Files\Fabrikam\Module` sökvägen till värdet för `PSModulePath` miljö variabeln för datorn. Om du vill lägga till sökvägen till användar `PSModulePath` miljö variabeln anger du målet till "användare".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

Du kan också ange `PSModulePath` värdena i `powershell.config.json` konfigurations filen. Mer information finns i [about_PowerShell_Config](/powershell/module/microsoft.powershell.core/about/about_powershell_config#psmodulepath).

## <a name="to-remove-locations-from-the-psmodulepath"></a>Ta bort platser från PSModulePath

Du kan ta bort sökvägar från variabeln med liknande metoder: till exempel `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"`
tar bort **c:\ModulePath** -sökvägen från den aktuella sessionen.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-modul](./writing-a-windows-powershell-module.md)

[about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules)
