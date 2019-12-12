---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISEFileCollection-objektet
ms.openlocfilehash: 96db51ee921cc0fa34803091d563bc6e118643b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030528"
---
# <a name="the-isefilecollection-object"></a>ISEFileCollection-objektet

**ISEFileCollection** -objektet är en samling av **ISEFile** -objekt. Ett exempel är samlingen $psISE. CurrentPowerShellTab. files.

## <a name="methods"></a>Metoder

### <a name="add-fullpath-"></a>Lägg till\( \[fullPath\] \)

Stöds i Windows PowerShell ISE 2,0 och senare.

Skapar och returnerar en ny namnlös fil och lägger till den i samlingen. **IsUntitled** -egenskapen för den nyligen skapade filen är **$True**.

**\[fullPath\]** – valfri sträng som anger filens fullständiga sökväg. Ett undantag skapas om du inkluderar parametern **fullPath** och en relativ sökväg, eller om du använder ett fil namn i stället för den fullständiga sökvägen.

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

**\[tvinga\]** -valfria booleska om värdet är **$True**ger behörighet att ta bort filen även om den inte har sparats efter den senaste användningen. Standardvärdet är **$false**.

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

Väljer den fil som anges av parametern **selectedFile** .

**selectedFile** -Microsoft. PowerShell. Host. ISE. ISEFile den ISEFile-fil som du vill välja.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Se även

- [ISEFile-objektet](The-ISEFile-Object.md)
- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
