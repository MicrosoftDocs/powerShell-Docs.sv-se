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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352887"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Ändra installationssökvägen för PSModulePath

Miljövariabeln `PSModulePath` lagrar Sök vägarna till platserna för de moduler som är installerade på disk. Windows PowerShell använder den här variabeln för att hitta moduler när användaren inte anger den fullständiga sökvägen till en modul. Sök vägarna i den här variabeln genomsöks i den ordning som de visas.

När Windows PowerShell startar skapas `PSModulePath` som en system miljö variabel med följande standardvärde: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Så här visar du variabeln PSModulePath

Om du vill visa Sök vägarna som anges i variabeln `PSModulePath` skriver du följande kommando:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Lägga till platser i PSModulePath-variabeln

Använd någon av följande metoder för att lägga till sökvägar till den här variabeln:

- Om du vill lägga till ett tillfälligt värde som bara är tillgängligt för den aktuella sessionen kör du följande kommando på kommando raden:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Lägg till ett beständigt värde som är tillgängligt när en session öppnas genom att lägga till följande kommando i en Windows PowerShell-profil:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Mer information om profiler finns i [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) i Microsoft TechNet-biblioteket.

- Om du vill lägga till en beständig variabel i registret skapar du en ny användar miljö variabel som kallas `PSModulePath` med hjälp av miljövariabler-redigeraren i dialog rutan **system egenskaper** .

- Om du vill lägga till en beständig variabel med hjälp av ett skript, använder du metoden **SetEnvironmentVariable** i miljö klassen. Följande skript lägger till exempel till "C:\Program Files\Fabrikam\Module sökväg till värdet för PSModulePath-miljövariabeln för datorn. Om du vill lägga till sökvägen till PSModulePath-miljövariabeln anger du målet till "användare".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Ta bort platser från PSModulePath

Du kan ta bort sökvägar från variabeln med liknande metoder: `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` tar till exempel bort **c:\ModulePath** -sökvägen från den aktuella sessionen.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
