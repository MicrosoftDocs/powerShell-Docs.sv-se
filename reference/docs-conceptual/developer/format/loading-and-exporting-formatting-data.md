---
title: Läsa in och exportera formatering av data | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b449b280ccee561679d58f2f2a8b467c83150766
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781128"
---
# <a name="loading-and-exporting-formatting-data"></a>Läsa in och exportera formateringsdata

När du har skapat format filen måste du uppdatera format data från sessionen genom att läsa in filerna i den aktuella sessionen. (De filer som tillhandahålls av Windows PowerShell läses in med snapin-moduler som registreras när den aktuella sessionen öppnas.) När format data för den aktuella sessionen har uppdaterats använder Windows PowerShell dessa data för att visa de .NET-objekt som är associerade med de vyer som definierats i de inlästa filerna. Det finns ingen gräns för hur många filer som kan läsas in i den aktuella sessionen. Förutom att uppdatera formateringen kan du exportera format data i den aktuella sessionen tillbaka till en fil med formatering.

## <a name="loading-format-data"></a>Läser in format data

Att formatera filer kan läsas in i den aktuella sessionen med hjälp av följande metoder:

- Du kan importera formaterings filen till den aktuella sessionen från kommando raden. Använd cmdleten [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) enligt beskrivningen i följande procedur.

- Du kan skapa ett modul-manifest som refererar till format filen. Med moduler kan du paketera filer som ska formateras för distribution. Använd cmdleten [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) för att skapa manifestet och cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) för att läsa in modulen i den aktuella sessionen. Mer information om moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

- Du kan skapa en snapin-modul som refererar till format filen. Använd formatet [system. Management. Automation. PSSnapIn. format](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) för att referera till dina filer. Vi rekommenderar starkt att du använder moduler för att paketera cmdlets och alla associerade format och typer av filer för distribution. Mer information om moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

- Om du anropar kommandon program mässigt kan du lägga till en post i det första sessionstillståndet för körnings utrymme där kommandona körs. Mer information om .NET-typen som används för att lägga till format filen finns i [system. Management. Automation. körnings utrymmen. Sessionstateformatentry? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) -klass.

När en fil läses in, läggs den till i en intern lista som Windows PowerShell använder för att avgöra vilken vy som ska användas när objekt visas på kommando raden. Du kan lägga formaterings filen till början av listan eller lägga till den i slutet av listan. Att veta var format filen läggs till i listan är viktig om du läser in format filen som definierar en vy för ett objekt som har en befintlig vy definierad, till exempel när du vill ändra hur ett objekt som returneras av en Windows PowerShell Core-cmdlet visas. Om du läser in en formateringsinformation som definierar den enda vyn för ett objekt, kan du använda någon av de metoder som beskrivs ovan.  Om du läser in en formateringsinformation som definierar en annan vy för ett objekt måste du använda cmdleten [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) och lägga din fil till början av listan.

## <a name="storing-your-formatting-file"></a>Spara format filen

Det finns inget krav på var filerna lagras på disk. Det rekommenderas dock starkt att du lagrar dem i följande mapp: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Läsa in en format fil med hjälp av import-FormatData

1. Lagra format filen på disk.

2. Kör cmdleten [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) med något av följande kommandon.

   Använd det här kommandot för att lägga till format filen överst i listan. Använd det här kommandot om du ändrar hur ett objekt visas.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Använd det här kommandot för att lägga till format filen i slutet av listan.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   När du har lagt till en fil med hjälp av [Update-FormatData-](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdleten kan du inte ta bort filen från listan medan sessionen är öppen. Du måste stänga sessionen för att ta bort formateringen från listan.

## <a name="exporting-format-data"></a>Exportera format data

Infoga avsnittet här.
