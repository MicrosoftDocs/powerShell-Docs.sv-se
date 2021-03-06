---
ms.date: 12/31/2019
title: ISEFile-objektet
description: Ett ISEFile-objekt representerar en fil i Windows PowerShell ISE.
ms.openlocfilehash: b5ea70219787f254fe85d728518cbc4746c00250
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391501"
---
# <a name="the-isefile-object"></a>ISEFile-objektet

Ett **ISEFile** -objekt representerar en fil i Windows PowerShell ISE (Integrated Scripting Environment). Det är en instans av klassen **Microsoft. PowerShell. Host. ISE. ISEFile** . I det här avsnittet visas dess medlems metoder och medlems egenskaper. `$psISE.CurrentFile`Filerna och filerna i samlingen filer på en PowerShell-flik är alla instanser av klassen * * * * Microsoft. PowerShell. Host. ISE. ISEFile * *.

## <a name="methods"></a>Metoder

### <a name="save-saveencoding-"></a>Spara \( \[ saveEncoding \]\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Sparar filen på disk.

`[saveEncoding]` – valfri [system. text. Encoding](/dotnet/api/system.text.encoding) en valfri tecken kodnings parameter som ska användas för den sparade filen. Standardvärdet är **utf8**.

### <a name="exceptions"></a>Undantag

- **System. io. IOException** : det gick inte att spara filen.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>Spara som \( fil namn, \[ saveEncoding\]\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Sparar filen med det angivna fil namnet och kodningen.

**filename** – sträng namnet som ska användas för att spara filen.

`[saveEncoding]` – valfri [system. text. Encoding](/dotnet/api/system.text.encoding) en valfri tecken kodnings parameter som ska användas för den sparade filen. Standardvärdet är **utf8**.

### <a name="exceptions"></a>Undantag

- **System. ArgumentNullException** : **fil namns** parametern är null.
- **System. ArgumentException** : **fil namns** parametern är tom.
- **System. io. IOException** : det gick inte att spara filen.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Egenskaper

### <a name="displayname"></a>DisplayName

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar den sträng som innehåller visnings namnet för den här filen. Namnet visas på fliken **fil** överst i redigeraren. Förekomsten av en asterisk `(*)` i slutet av namnet anger att filen har ändringar som inte har sparats.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Redigerare

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar det [Editor-objekt](The-ISEEditor-Object.md) som används för den angivna filen.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Kodning

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

Den skrivskyddade booleska egenskapen som returnerar `$true` om filen har sparats efter att den senast ändrades.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som returnerar `$true` om filen aldrig har fått en rubrik.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Se även

- [ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
