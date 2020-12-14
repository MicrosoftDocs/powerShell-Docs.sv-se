---
description: '`enum`Instruktionen används för att deklarera en uppräkning. En uppräkning är en distinkt typ som består av en uppsättning namngivna etiketter som kallas Enumerator-lista.'
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Enum
ms.openlocfilehash: 5572a717bbf9b546a30b227b3baf215196c4145d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709678"
---
# <a name="about-enum"></a><span data-ttu-id="b46fb-104">Om Enum</span><span class="sxs-lookup"><span data-stu-id="b46fb-104">About Enum</span></span>

## <a name="short-description"></a><span data-ttu-id="b46fb-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b46fb-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b46fb-106">`enum`Instruktionen används för att deklarera en uppräkning.</span><span class="sxs-lookup"><span data-stu-id="b46fb-106">The `enum` statement is used to declare an enumeration.</span></span> <span data-ttu-id="b46fb-107">En uppräkning är en distinkt typ som består av en uppsättning namngivna etiketter som kallas Enumerator-lista.</span><span class="sxs-lookup"><span data-stu-id="b46fb-107">An enumeration is a distinct type that consists of a set of named labels called the enumerator list.</span></span>

## <a name="long-description"></a><span data-ttu-id="b46fb-108">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b46fb-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="b46fb-109">Med `enum` instruktionen kan du skapa en strikt skriven uppsättning etiketter.</span><span class="sxs-lookup"><span data-stu-id="b46fb-109">The `enum` statement allows you to create a strongly typed set of labels.</span></span> <span data-ttu-id="b46fb-110">Den här uppräkningen kan användas i koden utan att du behöver parsa eller kontrol lera stavnings fel.</span><span class="sxs-lookup"><span data-stu-id="b46fb-110">That enumeration can be used in the code without having to parse or check for spelling errors.</span></span>

<span data-ttu-id="b46fb-111">Uppräkningar visas internt som heltal med start värde noll.</span><span class="sxs-lookup"><span data-stu-id="b46fb-111">Enumerations are internally represented as integers with a starting value of zero.</span></span> <span data-ttu-id="b46fb-112">Den första etiketten i listan är tilldelad värdet noll.</span><span class="sxs-lookup"><span data-stu-id="b46fb-112">The first label in the list is assigned the value zero.</span></span> <span data-ttu-id="b46fb-113">Återstående etiketter tilldelas med efterföljande nummer.</span><span class="sxs-lookup"><span data-stu-id="b46fb-113">The remaining labels are assigned with consecutive numbers.</span></span>

<span data-ttu-id="b46fb-114">I definitionen kan etiketter tilldelas alla heltals värden.</span><span class="sxs-lookup"><span data-stu-id="b46fb-114">In the definition, labels can be given any integer value.</span></span> <span data-ttu-id="b46fb-115">Etiketter utan tilldelade värde tar nästa heltals värde.</span><span class="sxs-lookup"><span data-stu-id="b46fb-115">Labels with no value assigned take the next integer value.</span></span>

## <a name="syntax-basic"></a><span data-ttu-id="b46fb-116">Syntax (Basic)</span><span class="sxs-lookup"><span data-stu-id="b46fb-116">Syntax (basic)</span></span>

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a><span data-ttu-id="b46fb-117">Exempel på användning</span><span class="sxs-lookup"><span data-stu-id="b46fb-117">Usage example</span></span>

<span data-ttu-id="b46fb-118">I följande exempel visas en uppräkning av objekt som kan visas som mediefiler.</span><span class="sxs-lookup"><span data-stu-id="b46fb-118">The following example shows an enumeration of objects that can be seen as media files.</span></span> <span data-ttu-id="b46fb-119">Definitionen tilldelar explicita värden till de underliggande värdena för `music` , `picture` , `video` .</span><span class="sxs-lookup"><span data-stu-id="b46fb-119">The definition assigns explicit values to the underlying values of `music`, `picture`, `video`.</span></span> <span data-ttu-id="b46fb-120">Etiketter direkt efter en explicit tilldelning får nästa heltals värde.</span><span class="sxs-lookup"><span data-stu-id="b46fb-120">Labels immediately following an explicit assignment get the next integer value.</span></span> <span data-ttu-id="b46fb-121">Synonymer kan skapas genom att tilldela samma värde till en annan etikett. Se de konstruerade värdena för: `ogg` , `oga` ,,, eller, `mogg` `jpg` `jpeg` `mpg` `mpeg` .</span><span class="sxs-lookup"><span data-stu-id="b46fb-121">Synonyms can be created by assigning the same value to another label; see the constructed values for: `ogg`, `oga`, `mogg`, or `jpg`, `jpeg`, or `mpg`, `mpeg`.</span></span>

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

<span data-ttu-id="b46fb-122">`GetEnumNames()`Metoden returnerar listan över etiketterna för uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="b46fb-122">The `GetEnumNames()` method returns the list of the labels for the enumeration.</span></span>

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

<span data-ttu-id="b46fb-123">`GetEnumValues()`Metoden returnerar listan över värdena för uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="b46fb-123">The `GetEnumValues()` method returns the list of the values for the enumeration.</span></span>

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

<span data-ttu-id="b46fb-124">**Obs**: GetEnumNames () och GetEnumValues () verkar returnera samma resultat.</span><span class="sxs-lookup"><span data-stu-id="b46fb-124">**Note**: GetEnumNames() and GetEnumValues() seem to return the same results.</span></span>
<span data-ttu-id="b46fb-125">Men internt ändrar PowerShell värdena till etiketter.</span><span class="sxs-lookup"><span data-stu-id="b46fb-125">However, internally, PowerShell is changing values into labels.</span></span> <span data-ttu-id="b46fb-126">Läs listan noggrant och se att `oga` och `mogg` nämns i resultatet "Get Names", men inte under "Get values", som är liknande utdata för `jpg` , `jpeg` och `mpg` `mpeg` .</span><span class="sxs-lookup"><span data-stu-id="b46fb-126">Read the list carefully and you'll notice that `oga` and `mogg` are mentioned under the 'Get Names' results, but not under the 'Get Values' similar output for `jpg`, `jpeg`, and `mpg`, `mpeg`.</span></span>

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

## <a name="enumerations-as-flags"></a><span data-ttu-id="b46fb-127">Uppräkningar som flaggor</span><span class="sxs-lookup"><span data-stu-id="b46fb-127">Enumerations as flags</span></span>

<span data-ttu-id="b46fb-128">Uppräkningar kan definieras som en samling av bit flaggor.</span><span class="sxs-lookup"><span data-stu-id="b46fb-128">Enumerations can be defined as a collection of bit flags.</span></span>
<span data-ttu-id="b46fb-129">Där uppräkningen representerar en eller flera av dessa flaggor som är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="b46fb-129">Where, at any given point the enumeration represents one or more of those flags turned on.</span></span>

<span data-ttu-id="b46fb-130">För uppräkningar när flaggor ska fungera korrekt ska varje etikett ha en potens av två värden.</span><span class="sxs-lookup"><span data-stu-id="b46fb-130">For enumerations as flags to work properly, each label should have a power of two value.</span></span>

## <a name="syntax-flags"></a><span data-ttu-id="b46fb-131">Syntax (flaggor)</span><span class="sxs-lookup"><span data-stu-id="b46fb-131">Syntax (flags)</span></span>

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a><span data-ttu-id="b46fb-132">Exempel på flaggor användning</span><span class="sxs-lookup"><span data-stu-id="b46fb-132">Flags usage example</span></span>

<span data-ttu-id="b46fb-133">I följande exempel skapas *FileAttributes* -uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="b46fb-133">In the following example the *FileAttributes* enumeration is created.</span></span>

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

<span data-ttu-id="b46fb-134">Om du vill testa att en speciell uppsättning har angetts kan du använda den binära jämförelse operatorn `-band` .</span><span class="sxs-lookup"><span data-stu-id="b46fb-134">To test that a specific is set, you can use the binary comparison operator `-band`.</span></span> <span data-ttu-id="b46fb-135">I det här exemplet testar vi för **enheten** och **arkivattributet** i värdet för `$file2` .</span><span class="sxs-lookup"><span data-stu-id="b46fb-135">In this example, we test for the **Device** and the **Archive** attributes in the value of `$file2`.</span></span>

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```

