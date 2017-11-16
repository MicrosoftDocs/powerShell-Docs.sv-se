---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a>Objektet ISEFile
  En **ISEFile** -objektet representerar en fil i Windows PowerShell® Integrated Scripting Environment (ISE). Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEFile. Det här avsnittet visar dess medlem metoder och egenskaper. Den **$psISE.CurrentFile** och filerna i samlingen filer i en PowerShell-flik är alla instanser av klassen Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Metoder

### <a name="save-saveencoding-"></a>Spara\( \[saveEncoding\]\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Filen sparas till disk.

 **\[saveEncoding\]**  – valfritt [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) ett valfritt tecken kodning parameter som ska användas för den sparade filen. Standardvärdet är **UTF8**.

 **Undantag**
 -   **System.IO.IOException**: Det gick inte att spara filen.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filnamn, \[saveEncoding\]\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Kodning och sparar filen med det angivna filnamnet.

 **filnamn** -String-namn som används för att spara filen.

 **\[saveEncoding\]**  – valfritt [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) ett valfritt tecken kodning parameter som ska användas för den sparade filen. Standardvärdet är **UTF8**.

 **Undantag**
 -   **System.ArgumentNullException**: den **filename** -parametern är null.

- **System.ArgumentException**: den **filename** parameter är tom.

- **System.IO.IOException**: Det gick inte att spara filen.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a>Egenskaper

### <a name="displayname"></a>Visningsnamn
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Den skrivskyddade egenskapen som hämtar den sträng som innehåller namnet på den här filen. Namnet visas på den **filen** fliken överst i redigeraren. Förekomsten av en asterisk \( \* \) anger att filen har ändringar som inte har sparats i slutet av namnet.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a>Redigeraren
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Skrivskyddad egenskap som hämtar den [editor-objekt](The-ISEEditor-Object.md) som används för den angivna filen.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a>Kodning
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade egenskapen som hämtar ursprungliga Filkodning. Det här är en **System.Text.Encoding** objekt.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a>FullPath
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade egenskapen som hämtar den sträng som anger den fullständiga sökvägen till den öppna filen.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a>IsSaved
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade boolesk egenskap returnerar **$true** om filen har sparats när den senast ändrades.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a>IsUntitled
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Skrivskyddad egenskap som returnerar **$true** om filen har aldrig tilldelats en rubrik.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a>Se även
- [ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)
