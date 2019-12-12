---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: ISEFile-objektet
ms.openlocfilehash: ebb5a35f6ea9d93eab633b9f4e6c84e4fddd6ae8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028956"
---
# <a name="the-isefile-object"></a>ISEFile-objektet

Ett **ISEFile** -objekt representerar en fil i Windows POWERSHELL® Ise (Integrated Scripting Environment). Det är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEFile. I det här avsnittet visas dess medlems metoder och medlems egenskaper. Filen **$psISE. CurrentFile** och filerna i samlingen filer på en PowerShell-flik är alla instanser av klassen Microsoft. PowerShell. Host. ISE. ISEFile.

## <a name="methods"></a>Metoder

### <a name="save-saveencoding-"></a>Spara\( \[saveEncoding\] \)

Stöds i Windows PowerShell ISE 2,0 och senare.

Sparar filen på disk.

**\[saveEncoding\]** -valfri [system. text. Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) en valfri tecken kodnings parameter som ska användas för den sparade filen. Standardvärdet är **utf8**.

### <a name="exceptions"></a>Undantag

- **System. io. IOException**: det gick inte att spara filen.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>Spara som\(fil namn, \[saveEncoding\]\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Sparar filen med det angivna fil namnet och kodningen.

**filename** – sträng namnet som ska användas för att spara filen.

**\[saveEncoding\]** -valfri [system. text. Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) en valfri tecken kodnings parameter som ska användas för den sparade filen. Standardvärdet är **utf8**.

### <a name="exceptions"></a>Undantag

- **System. ArgumentNullException**: **fil namns** parametern är null.
- **System. ArgumentException**: **fil namns** parametern är tom.
- **System. io. IOException**: det gick inte att spara filen.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Egenskaper

### <a name="displayname"></a>Visningsnamn

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar den sträng som innehåller visnings namnet för den här filen. Namnet visas på fliken **fil** överst i redigeraren. Förekomsten av en asterisk \(\*\) i slutet av namnet anger att filen har ändringar som inte har sparats.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Redigeringsprogram

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar det [Editor-objekt](The-ISEEditor-Object.md) som används för den angivna filen.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Encoding

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar den ursprungliga fil kodningen. Detta är ett **system. text. Encoding** -objekt.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar strängen som anger den fullständiga sökvägen till den öppna filen.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade booleska egenskapen som returnerar **$True** om filen har sparats efter att den senast ändrades.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som returnerar **$True** om filen aldrig har fått en rubrik.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Se även

- [ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
