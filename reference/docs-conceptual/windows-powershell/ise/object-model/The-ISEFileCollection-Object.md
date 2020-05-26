---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEFileCollection-objektet
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810668"
---
# <a name="the-isefilecollection-object"></a>ISEFileCollection-objektet

**ISEFileCollection** -objektet är en samling av **ISEFile** -objekt. Ett exempel är `$psISE.CurrentPowerShellTab.Files` samlingen.

## <a name="methods"></a>Metoder

### <a name="add-fullpath-"></a>Lägg till \( \[ fullpath \]\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Skapar och returnerar en ny namnlös fil och lägger till den i samlingen. **IsUntitled** -egenskapen för den nyligen skapade filen är `$true` .

** \[ Fullpath \] ** – valfri sträng som är den fullständigt angivna sökvägen till filen. Ett undantag skapas om du inkluderar parametern **fullpath** och en relativ sökväg, eller om du använder ett fil namn i stället för den fullständiga sökvägen.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Ta bort \( fil, \[ tvinga \]\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Tar bort en angiven fil från den aktuella PowerShell-fliken.

**Filsträng filen ISEFile** som du vill ta bort från samlingen. Om filen inte har sparats, genererar den här metoden ett undantag. Använd parametern **Framtvinga** växel för att tvinga borttagning av en fil som inte sparats.

** \[ \] Tvingande** -valfria booleska om det är inställt på `$true` , ger behörighet att ta bort filen även om den inte har sparats efter den senaste användningen. Standardvärdet är `$false`.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile \( selectedFile\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Väljer den fil som anges av parametern **SelectedFile** .

**SelectedFile** -Microsoft. PowerShell. Host. ISE. ISEFile den ISEFile-fil som du vill välja.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Se även

- [ISEFile-objektet](The-ISEFile-Object.md)
- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
