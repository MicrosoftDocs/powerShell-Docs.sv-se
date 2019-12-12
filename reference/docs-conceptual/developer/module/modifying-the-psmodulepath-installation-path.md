---
title: Ändra installations Sök vägen för PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953848"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Ändra installationssökvägen för PSModulePath

I miljövariabeln `PSModulePath` lagras Sök vägarna till platserna för de moduler som är installerade på disk. PowerShell använder den här variabeln för att hitta moduler när användaren inte anger den fullständiga sökvägen till en modul. Sök vägarna i den här variabeln genomsöks i den ordning som de visas.

När PowerShell startar skapas `PSModulePath` som en system miljö variabel med följande standardvärde: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` eller `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` för Windows PowerShell.

## <a name="to-view-the-psmodulepath-variable"></a>Så här visar du variabeln PSModulePath

Om du vill visa de sökvägar som anges i variabeln `PSModulePath` anger du följande kommando:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Lägga till platser i PSModulePath-variabeln

Använd någon av följande metoder för att lägga till sökvägar till den här variabeln:

- Om du vill lägga till ett tillfälligt värde som bara är tillgängligt för den aktuella sessionen kör du följande kommando på kommando raden:

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- Om du vill lägga till ett permanent värde som är tillgängligt när en session öppnas, lägger du till kommandot ovan i en PowerShell-profil fil (`$PROFILE`) >

  Mer information om profiler finns [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).

- Om du vill lägga till en beständig variabel i registret skapar du en ny användar miljö variabel som kallas `PSModulePath` med hjälp av miljövariabler-redigeraren i dialog rutan **system egenskaper** .

- Om du vill lägga till en beständig variabel med hjälp av ett skript, använder du .net-metoden [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) i klassen [system. Environment](https://docs.microsoft.com/dotnet/api/system.environment) . Följande skript lägger till exempel till `C:\Program Files\Fabrikam\Module` sökvägen till värdet i `PSModulePath` miljövariabeln för datorn. Om du vill lägga till sökvägen till användar `PSModulePath`-miljövariabeln anger du målet till "användare".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Ta bort platser från PSModulePath

Du kan ta bort sökvägar från variabeln med liknande metoder: `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` tar till exempel bort **c:\ModulePath** -sökvägen från den aktuella sessionen.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
