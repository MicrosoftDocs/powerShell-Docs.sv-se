---
title: Läser in och formatering dataexport | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054194"
---
# <a name="loading-and-exporting-formatting-data"></a>Läsa in och exportera formateringsdata

När du har skapat din formatering fil kan behöva du uppdatera formatera data sessionen genom att läsa in dina filer i den aktuella sessionen. (De formatering filer som tillhandahålls av Windows PowerShell har lästs in av snapin-moduler som är registrerade när den aktuella sessionen öppnas.) När formatera data i den aktuella sessionen har uppdaterats använder dessa data för att visa .NET-objekt som är associerade med de vyer som definierats i inlästa formatering filer i Windows PowerShell. Det finns ingen gräns för hur många formatering filer som du kan läsa in i den aktuella sessionen. Du kan exportera formatera data i den aktuella sessionen tillbaka till en formatering fil förutom formatering data uppdateras.

## <a name="loading-format-data"></a>Läser in formatera data

Formatering filer kan läsas in i den aktuella sessionen med hjälp av följande metoder:

- Du kan importera formatering filen till den aktuella sessionen från kommandoraden. Använd den [uppdatering FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet som beskrivs i följande procedur.

- Du kan skapa ett modulmanifest som refererar till filen formatering. Moduler kan du paketera du formatering filer för distribution. Använd den [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet för att skapa manifestet, och [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet för att läsa in modulen i den aktuella sessionen. Läs mer om moduler [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

- Du kan skapa en snapin-modul som refererar till filen formatering. Använd den [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) att referera till filerna formatering. Det är vi rekommenderar att du använder moduler att paketet cmdlet: ar, och alla associerade formaterar och typer av filer för distribution. Läs mer om moduler [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

- Om du anropar kommandon programmässigt, kan du lägga till en formatering filpost inledande sessionens tillstånd av körningsutrymmet där kommandona körs. Mer information om .NET-typ som används för att lägga till filen formatering finns i den [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) klass.

När en formatering fil har lästs in, läggs den till en intern lista att Windows PowerShell använder för att avgöra vilken vy som ska använda när du visar objekt på kommandoraden. Du kan åtkomstgruppen för filen formatering i början av listan, eller du kan lägga till den i slutet av listan. Det är viktigt om du läser in formatering-fil som definierar en vy för ett objekt som har en befintlig vy som definierats, till exempel när du vill ändra hur ett objekt som returneras av en Windows PowerShell core-cmdlet är att att känna till där din formatering fil läggs till i den här listan  visas. Om du läser in en formatering fil som definierar den enda vyn för ett objekt, kan du använda någon av metoderna som beskrivs ovan.  Om du läser in en formatering fil som definierar en annan vy för ett objekt, måste du använda den [uppdatering FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet och Lägg till åtkomstgruppen din fil till början av listan.

## <a name="storing-your-formatting-file"></a>Lagra filen formatering

Det finns inga krav på var din formatering filer lagras på disk. Dock vi rekommenderar att du sparar dem i följande mapp: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Läser in en formatfil med Import-FormatData

1. Store formatering filen till disk.

2. Kör den [uppdatering FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet med någon av följande kommandon.

   För att lägga till formateringen fil först i listan för att använda det här kommandot. Använd det här kommandot om du ändrar hur ett objekt visas.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   För att lägga till formateringen fil i slutet av listan för att använda det här kommandot.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   När du har lagt till en fil med hjälp av den [uppdatering FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, du kan inte ta bort filen från listan över när sessionen är öppet. Du måste stänga sessionen om du vill ta bort filen formatering från listan.

## <a name="exporting-format-data"></a>Format för dataexport

Infoga avsnittet här.
