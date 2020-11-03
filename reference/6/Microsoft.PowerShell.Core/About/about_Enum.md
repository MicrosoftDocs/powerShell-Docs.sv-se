---
description: '`enum`Instruktionen används för att deklarera en uppräkning. En uppräkning är en distinkt typ som består av en uppsättning namngivna etiketter som kallas Enumerator-lista.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Enum
ms.openlocfilehash: 2b363f1d2dfcf45ec69d863a50f5f359ddf8e284
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270789"
---
# <a name="about-enum"></a>Om Enum

## <a name="short-description"></a>KORT BESKRIVNING
`enum`Instruktionen används för att deklarera en uppräkning. En uppräkning är en distinkt typ som består av en uppsättning namngivna etiketter som kallas Enumerator-lista.

## <a name="long-description"></a>LÅNG BESKRIVNING

Med `enum` instruktionen kan du skapa en strikt skriven uppsättning etiketter. Den här uppräkningen kan användas i koden utan att du behöver parsa eller kontrol lera stavnings fel.

Uppräkningar visas internt som heltal med start värde noll. Den första etiketten i listan är tilldelad värdet noll. Återstående etiketter tilldelas med efterföljande nummer.

I definitionen kan etiketter tilldelas alla heltals värden. Etiketter utan tilldelade värde tar nästa heltals värde.

## <a name="syntax-basic"></a>Syntax (Basic)

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a>Exempel på användning

I följande exempel visas en uppräkning av objekt som kan visas som mediefiler. Definitionen tilldelar explicita värden till de underliggande värdena för `music` , `picture` , `video` . Etiketter direkt efter en explicit tilldelning får nästa heltals värde. Synonymer kan skapas genom att tilldela samma värde till en annan etikett. Se de konstruerade värdena för: `ogg` , `oga` ,,, eller, `mogg` `jpg` `jpeg` `mpg` `mpeg` .

```powershell
enum MediaTypes {
    unknown
    music = 10
    mp3
    aac
    ogg = 15
    oga = 15
    mogg = 15
    picture = 20
    jpg
    jpeg = 21
    png
    video = 40
    mpg
    mpeg = 41
    avi
    m4v
}
```

`GetEnumNames()`Metoden returnerar listan över etiketterna för uppräkningen.

```powershell
[MediaTypes].GetEnumNames()
unknown
music
mp3
aac
ogg
oga
mogg
picture
jpg
jpeg
png
video
mpg
mpeg
avi
m4v
```

`GetEnumValues()`Metoden returnerar listan över värdena för uppräkningen.

```powershell
[MediaTypes].GetEnumValues()
unknown
music
mp3
aac
oga
oga
oga
picture
jpeg
jpeg
png
video
mpeg
mpeg
avi
m4v
```

**Obs** : GetEnumNames () och GetEnumValues () verkar returnera samma resultat.
Men internt ändrar PowerShell värdena till etiketter. Läs listan noggrant och se att `oga` och `mogg` nämns i resultatet "Get Names", men inte under "Get values", som är liknande utdata för `jpg` , `jpeg` och `mpg` `mpeg` .

```powershell
[MediaTypes].GetEnumName(15)
oga

[MediaTypes].GetEnumNames() | ForEach-Object {
  "{0,-10} {1}" -f $_,[int]([MediaTypes]::$_)
}
unknown    0
music      10
mp3        11
aac        12
ogg        15
oga        15
mogg       15
picture    20
jpg        21
jpeg       21
png        22
video      40
mpg        41
mpeg       41
avi        42
m4v        43
```

## <a name="enumerations-as-flags"></a>Uppräkningar som flaggor

Uppräkningar kan definieras som en samling av bit flaggor.
Där uppräkningen representerar en eller flera av dessa flaggor som är aktiverade.

För uppräkningar när flaggor ska fungera korrekt ska varje etikett ha en potens av två värden.

## <a name="syntax-flags"></a>Syntax (flaggor)

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a>Exempel på flaggor användning

I följande exempel skapas *FileAttributes* -uppräkningen.

```powershell
[Flags()] enum FileAttributes {
    Archive = 1
    Compressed = 2
    Device = 4
    Directory = 8
    Encrypted = 16
    Hidden = 32
}

[FileAttributes]$file1 = [FileAttributes]::Archive
[FileAttributes]$file1 +=[FileAttributes]::Compressed
[FileAttributes]$file1 +=  [FileAttributes]::Device
"file1 attributes are: $file1"

[FileAttributes]$file2 = [FileAttributes]28 ## => 16 + 8 + 4
"file2 attributes are: $file2"
```

```output
file1 attributes are: Archive, Compressed, Device
file2 attributes are: Device, Directory, Encrypted
```

Om du vill testa att en speciell uppsättning har angetts kan du använda den binära jämförelse operatorn `-band` . I det här exemplet testar vi för **enheten** och **arkivattributet** i värdet för `$file2` .

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```
