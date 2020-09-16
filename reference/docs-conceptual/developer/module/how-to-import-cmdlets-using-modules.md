---
title: Så här importerar du cmdlets med hjälp av moduler | Microsoft Docs
ms.date: 08/28/2019
ms.openlocfilehash: fa8d629c14b06e3f9e9d6151cf09aa6b4acce358
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779377"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Importera cmdlets med hjälp av moduler

I den här artikeln beskrivs hur du importerar cmdletar till en PowerShell-session med hjälp av en binär modul.

> [!NOTE]
> Medlemmar i moduler kan omfatta cmdlets, providrar, functions, variabler, alias och mycket mer. Snapin-moduler kan bara innehålla cmdlets och providers.

## <a name="how-to-load-cmdlets-using-a-module"></a>Så här läser du in cmdletar med hjälp av en modul

1. Skapa en modul som har samma namn som den sammansättnings fil där cmdletarna implementeras. I den här proceduren skapas mappen modul i Windows- `system32` mappen.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. Kontrol lera att `PSModulePath` miljövariabeln innehåller sökvägen till din nya modul-mapp. Som standard har System-mappen redan lagts till i `PSModulePath` miljövariabeln. Om du vill visa `PSModulePath` skriver du: `$env:PSModulePath` .

1. Kopiera cmdlet-sammansättningen till module-mappen.

1. Lägg till en modul för manifest fil ( `.psd1` ) i modulens rotmapp. PowerShell använder modulen manifest för att importera modulen. Mer information finns i [så här skriver du ett manifest för PowerShell-modul](../module/how-to-write-a-powershell-module-manifest.md).

1. Kör följande kommando för att lägga till cmdletarna i sessionen:

   `Import-Module [Module_Name]`

   Den här proceduren kan användas för att testa dina cmdletar. Den lägger till alla cmdletar i sammansättningen till sessionen. Mer information om moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Se även

[Skriva ett PowerShell-modulmanifest](../module/how-to-write-a-powershell-module-manifest.md)

[Importera en PowerShell-modul](../module/importing-a-powershell-module.md)

[Importera-modul](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[Installera moduler](../module/installing-a-powershell-module.md)

[Ändra installationssökvägen för PSModulePath](../module/modifying-the-psmodulepath-installation-path.md)

[Skriva en Windows PowerShell-cmdlet](../cmdlet/cmdlet-overview.md)
