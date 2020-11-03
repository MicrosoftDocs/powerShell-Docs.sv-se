---
description: '`enum`Instruktionen används för att deklarera en uppräkning. En uppräkning är en distinkt typ som består av en uppsättning namngivna etiketter som kallas Enumerator-lista.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Enum
ms.openlocfilehash: 0b1959ba009119769535c3d39231ff8dab9dc5de
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272168"
---
# <a name="about-enum"></a><span data-ttu-id="c4086-105">Om Enum</span><span class="sxs-lookup"><span data-stu-id="c4086-105">About Enum</span></span>

## <a name="short-description"></a><span data-ttu-id="c4086-106">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c4086-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="c4086-107">`enum`Instruktionen används för att deklarera en uppräkning.</span><span class="sxs-lookup"><span data-stu-id="c4086-107">The `enum` statement is used to declare an enumeration.</span></span> <span data-ttu-id="c4086-108">En uppräkning är en distinkt typ som består av en uppsättning namngivna etiketter som kallas Enumerator-lista.</span><span class="sxs-lookup"><span data-stu-id="c4086-108">An enumeration is a distinct type that consists of a set of named labels called the enumerator list.</span></span>

## <a name="long-description"></a><span data-ttu-id="c4086-109">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c4086-109">LONG DESCRIPTION</span></span>

<span data-ttu-id="c4086-110">Med `enum` instruktionen kan du skapa en strikt skriven uppsättning etiketter.</span><span class="sxs-lookup"><span data-stu-id="c4086-110">The `enum` statement allows you to create a strongly typed set of labels.</span></span> <span data-ttu-id="c4086-111">Den här uppräkningen kan användas i koden utan att du behöver parsa eller kontrol lera stavnings fel.</span><span class="sxs-lookup"><span data-stu-id="c4086-111">That enumeration can be used in the code without having to parse or check for spelling errors.</span></span>

<span data-ttu-id="c4086-112">Uppräkningar visas internt som heltal med start värde noll.</span><span class="sxs-lookup"><span data-stu-id="c4086-112">Enumerations are internally represented as integers with a starting value of zero.</span></span> <span data-ttu-id="c4086-113">Den första etiketten i listan är tilldelad värdet noll.</span><span class="sxs-lookup"><span data-stu-id="c4086-113">The first label in the list is assigned the value zero.</span></span> <span data-ttu-id="c4086-114">Återstående etiketter tilldelas med efterföljande nummer.</span><span class="sxs-lookup"><span data-stu-id="c4086-114">The remaining labels are assigned with consecutive numbers.</span></span>

<span data-ttu-id="c4086-115">I definitionen kan etiketter tilldelas alla heltals värden.</span><span class="sxs-lookup"><span data-stu-id="c4086-115">In the definition, labels can be given any integer value.</span></span> <span data-ttu-id="c4086-116">Etiketter utan tilldelade värde tar nästa heltals värde.</span><span class="sxs-lookup"><span data-stu-id="c4086-116">Labels with no value assigned take the next integer value.</span></span>

## <a name="syntax-basic"></a><span data-ttu-id="c4086-117">Syntax (Basic)</span><span class="sxs-lookup"><span data-stu-id="c4086-117">Syntax (basic)</span></span>

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a><span data-ttu-id="c4086-118">Exempel på användning</span><span class="sxs-lookup"><span data-stu-id="c4086-118">Usage example</span></span>

<span data-ttu-id="c4086-119">I följande exempel visas en uppräkning av objekt som kan visas som mediefiler.</span><span class="sxs-lookup"><span data-stu-id="c4086-119">The following example shows an enumeration of objects that can be seen as media files.</span></span> <span data-ttu-id="c4086-120">Definitionen tilldelar explicita värden till de underliggande värdena för `music` , `picture` , `video` .</span><span class="sxs-lookup"><span data-stu-id="c4086-120">The definition assigns explicit values to the underlying values of `music`, `picture`, `video`.</span></span> <span data-ttu-id="c4086-121">Etiketter direkt efter en explicit tilldelning får nästa heltals värde.</span><span class="sxs-lookup"><span data-stu-id="c4086-121">Labels immediately following an explicit assignment get the next integer value.</span></span> <span data-ttu-id="c4086-122">Synonymer kan skapas genom att tilldela samma värde till en annan etikett. Se de konstruerade värdena för: `ogg` , `oga` ,,, eller, `mogg` `jpg` `jpeg` `mpg` `mpeg` .</span><span class="sxs-lookup"><span data-stu-id="c4086-122">Synonyms can be created by assigning the same value to another label; see the constructed values for: `ogg`, `oga`, `mogg`, or `jpg`, `jpeg`, or `mpg`, `mpeg`.</span></span>

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

<span data-ttu-id="c4086-123">`GetEnumNames()`Metoden returnerar listan över etiketterna för uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="c4086-123">The `GetEnumNames()` method returns the list of the labels for the enumeration.</span></span>

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

<span data-ttu-id="c4086-124">`GetEnumValues()`Metoden returnerar listan över värdena för uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="c4086-124">The `GetEnumValues()` method returns the list of the values for the enumeration.</span></span>

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

<span data-ttu-id="c4086-125">**Obs** : GetEnumNames () och GetEnumValues () verkar returnera samma resultat.</span><span class="sxs-lookup"><span data-stu-id="c4086-125">**Note** : GetEnumNames() and GetEnumValues() seem to return the same results.</span></span>
<span data-ttu-id="c4086-126">Men internt ändrar PowerShell värdena till etiketter.</span><span class="sxs-lookup"><span data-stu-id="c4086-126">However, internally, PowerShell is changing values into labels.</span></span> <span data-ttu-id="c4086-127">Läs listan noggrant och se att `oga` och `mogg` nämns i resultatet "Get Names", men inte under "Get values", som är liknande utdata för `jpg` , `jpeg` och `mpg` `mpeg` .</span><span class="sxs-lookup"><span data-stu-id="c4086-127">Read the list carefully and you'll notice that `oga` and `mogg` are mentioned under the 'Get Names' results, but not under the 'Get Values' similar output for `jpg`, `jpeg`, and `mpg`, `mpeg`.</span></span>

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

## <a name="enumerations-as-flags"></a><span data-ttu-id="c4086-128">Uppräkningar som flaggor</span><span class="sxs-lookup"><span data-stu-id="c4086-128">Enumerations as flags</span></span>

<span data-ttu-id="c4086-129">Uppräkningar kan definieras som en samling av bit flaggor.</span><span class="sxs-lookup"><span data-stu-id="c4086-129">Enumerations can be defined as a collection of bit flags.</span></span>
<span data-ttu-id="c4086-130">Där uppräkningen representerar en eller flera av dessa flaggor som är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="c4086-130">Where, at any given point the enumeration represents one or more of those flags turned on.</span></span>

<span data-ttu-id="c4086-131">För uppräkningar när flaggor ska fungera korrekt ska varje etikett ha en potens av två värden.</span><span class="sxs-lookup"><span data-stu-id="c4086-131">For enumerations as flags to work properly, each label should have a power of two value.</span></span>

## <a name="syntax-flags"></a><span data-ttu-id="c4086-132">Syntax (flaggor)</span><span class="sxs-lookup"><span data-stu-id="c4086-132">Syntax (flags)</span></span>

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a><span data-ttu-id="c4086-133">Exempel på flaggor användning</span><span class="sxs-lookup"><span data-stu-id="c4086-133">Flags usage example</span></span>

<span data-ttu-id="c4086-134">I följande exempel skapas *FileAttributes* -uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="c4086-134">In the following example the *FileAttributes* enumeration is created.</span></span>

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

<span data-ttu-id="c4086-135">Om du vill testa att en speciell uppsättning har angetts kan du använda den binära jämförelse operatorn `-band` .</span><span class="sxs-lookup"><span data-stu-id="c4086-135">To test that a specific is set, you can use the binary comparison operator `-band`.</span></span> <span data-ttu-id="c4086-136">I det här exemplet testar vi för **enheten** och **arkivattributet** i värdet för `$file2` .</span><span class="sxs-lookup"><span data-stu-id="c4086-136">In this example, we test for the **Device** and the **Archive** attributes in the value of `$file2`.</span></span>

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```
