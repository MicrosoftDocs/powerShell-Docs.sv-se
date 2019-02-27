---
title: Ändra installationssökvägen PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846510"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Ändra installationssökvägen för PSModulePath

Den `PSModulePath` miljövariabeln lagrar sökvägar till platser där modulerna som är installerade på disken. Windows PowerShell använder den här variabeln för att hitta moduler när användaren inte anger den fullständiga sökvägen till en modul. Sökvägarna i den här variabeln genomsöks i den ordning som de visas.

När Windows PowerShell startar `PSModulePath` skapas som en systemmiljövariabel med följande standardvärdet: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Visa PSModulePath variabeln

Visa sökvägarna som anges i den `PSModulePath` variabel, skriver du följande kommando:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Att lägga till platser i variabeln PSModulePath

Använd någon av följande metoder för att lägga till sökvägar till den här variabeln:

- Om du vill lägga till ett tillfälligt värde som är tillgänglig endast för den aktuella sessionen, kör du följande kommando på kommandoraden:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Lägg till följande kommando i en Windows PowerShell-profil för att lägga till ett beständigt värde som är tillgängliga när en session öppnas:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Mer information om profiler finns i [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) i Microsoft TechNet-biblioteket.

- Lägg till en beständig variabel i registret genom att skapa en ny användare-miljövariabel som heter `PSModulePath` med hjälp av redigeraren miljö variabler i den **Systemegenskaper** dialogrutan.

- Lägg till en beständig variabel med ett skript genom att använda den **SetEnvironmentVariable** -metoden i klassen miljö. Till exempel följande skriptet lägger till ”c:\Program\Microsoft Files\Fabrikam\Module sökväg till värdet för miljövariabeln PSModulePath för datorn. Lägg till sökvägen till miljövariabeln användaren PSModulePath, ange målet ”användare”.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Ta bort platser från PSModulePath

Du kan ta bort sökvägar från variabeln med liknande metoder: till exempel `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` tar bort den **c:\ModulePath** sökväg från den aktuella sessionen.

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
