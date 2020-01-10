---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISEFileCollection-objektet
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736223"
---
# <a name="the-isefilecollection-object"></a>ISEFileCollection-objektet

**ISEFileCollection** -objektet är en samling av **ISEFile** -objekt. Ett exempel är den `$psISE.CurrentPowerShellTab.Files` samlingen.

## <a name="methods"></a>Metoder

### <a name="add-fullpath-"></a>Lägg till\( \[FullPath\] \)

Stöds i Windows PowerShell ISE 2,0 och senare.

Skapar och returnerar en ny namnlös fil och lägger till den i samlingen. **IsUntitled** -egenskapen för den nyligen skapade filen är `$true`.

**\[FullPath\]** – valfri sträng som anger filens fullständiga sökväg. Ett undantag skapas om du inkluderar parametern **fullpath** och en relativ sökväg, eller om du använder ett fil namn i stället för den fullständiga sökvägen.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Ta bort\(-filen \[tvinga\] \)

Stöds i Windows PowerShell ISE 2,0 och senare.

Tar bort en angiven fil från den aktuella PowerShell-fliken.

**Filsträng filen ISEFile** som du vill ta bort från samlingen. Om filen inte har sparats, genererar den här metoden ett undantag. Använd parametern **Framtvinga** växel för att tvinga borttagning av en fil som inte sparats.

**\[tvinga\]** -valfria booleska om värdet är `$true`ger behörighet att ta bort filen även om den inte har sparats efter den senaste användningen. Standardvärdet är `$false`.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

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
- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
