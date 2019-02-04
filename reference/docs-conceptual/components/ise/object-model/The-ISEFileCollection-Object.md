---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISEFileCollection-objektet
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684600"
---
# <a name="the-isefilecollection-object"></a>ISEFileCollection-objektet

Den **ISEFileCollection** objekt är en samling **ISEFile** objekt. Ett exempel är $psISE.CurrentPowerShellTab.Files-samling.

## <a name="methods"></a>Metoder

### <a name="add-fullpath-"></a>Lägg till\( \[fullPath\] \)

Stöds i Windows PowerShell ISE 2.0 och senare.

Skapar och returnerar en ny namnlös fil och lägger till den i samlingen. Den **IsUntitled** egenskapen för den nyligen skapade filen är **$true**.

**\[fullPath\]**  – valfritt sträng fullständigt angivna sökvägen till filen. Ett undantag genereras om du inkluderar den **fullPath** parameter och en relativ sökväg, eller om du använder ett filnamn i stället för den fullständiga sökvägen.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Ta bort\( filen \[kraft\] \)

Stöds i Windows PowerShell ISE 2.0 och senare.

Tar bort en angiven fil från den aktuella PowerShell-fliken.

**Filen** -sträng The ISEFile-fil som du vill ta bort från samlingen. Om filen inte har sparats, utlöser ett undantag i den här metoden. Använd den **tvinga** växla parametern om du vill framtvinga borttagning av en ej sparade filer.

**\[Framtvinga\]**  -valfritt booleskt om **$true**, ger behörighet att ta bort filen även om det inte har sparats efter senaste användning. Standardvärdet är **$false**.

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

Stöds i Windows PowerShell ISE 2.0 och senare.

Väljer den fil som anges av den **selectedFile** parametern.

**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile-fil som du vill välja.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Se även

- [The ISEFile Object](The-ISEFile-Object.md)
- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)