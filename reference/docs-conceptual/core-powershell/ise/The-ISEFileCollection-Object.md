---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: 60bf4dae33f3a71c31e7fdbed0f4fd6ab27a8bd1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefilecollection-object"></a>Objektet ISEFileCollection
  Den **ISEFileCollection** objekt är en samling **ISEFile** objekt. Ett exempel är $psISE.CurrentPowerShellTab.Files-samling.

## <a name="methods"></a>Metoder

### <a name="add-fullpath-"></a>Lägg till\( \[fullPath\]\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Skapar och returnerar en ny namnlös fil och lägger till den samlingen. Den **IsUntitled** egenskapen för den nya filen är **$true**.

 **\[fullPath\]**  – valfritt string fullständigt angiven sökväg till filen. Ett undantag genereras om du inkluderar den **fullPath** parametern och en relativ sökväg, eller om du använder ett filnamn i stället för den fullständiga sökvägen.

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a>Ta bort\( filen \[kraft\]\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Tar bort en fil från den aktuella PowerShell-fliken.

 **Filen** -sträng i ISEFile-fil som du vill ta bort från samlingen. Om filen inte har sparats, genereras ett undantag i den här metoden. Använd den **tvinga** växla parametern om du vill framtvinga borttagning av en fil som inte har sparats.

 **\[Framtvinga\]**  -valfritt booleskt om **$true**, ger behörighet att ta bort filen även om den inte har sparats efter senaste användning. Standardvärdet är **$false**.

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Väljer du den fil som anges av den **selectedFile** parameter.

 **selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile i ISEFile-fil som du vill välja.

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a>Se även
- [Objektet ISEFile](The-ISEFile-Object.md) 
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)
