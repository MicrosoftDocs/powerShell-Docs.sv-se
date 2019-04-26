---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085362"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="d742b-102">Extrahera och parsa strukturerade objekt från sträng</span><span class="sxs-lookup"><span data-stu-id="d742b-102">Extract and Parse Structured Objects out of String</span></span>

<span data-ttu-id="d742b-103">Det skapar också ytterligare några funktioner för den `ConvertFrom-String` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="d742b-103">This also introduces some additional functionality for the `ConvertFrom-String` cmdlet:</span></span>

- <span data-ttu-id="d742b-104">Tar bort egenskapen utsträckning text som standard.</span><span class="sxs-lookup"><span data-stu-id="d742b-104">Removes the extent text property by default.</span></span> <span data-ttu-id="d742b-105">Du kan inkludera den med parametern - IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="d742b-105">You can include it with the -IncludeExtent parameter.</span></span>

- <span data-ttu-id="d742b-106">Många learning algoritmen felkorrigeringar från MVP och community-feedback.</span><span class="sxs-lookup"><span data-stu-id="d742b-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

- <span data-ttu-id="d742b-107">En ny parameter - UpdateTemplate att spara resultatet av Inlärningsalgoritmen till en kommentar i mallfilen.</span><span class="sxs-lookup"><span data-stu-id="d742b-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="d742b-108">Detta gör learning bearbeta (långsammaste scenen) en engångskostnad.</span><span class="sxs-lookup"><span data-stu-id="d742b-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="d742b-109">Kör Convert-sträng med en mall som innehåller kodade Inlärningsalgoritmen är nu nästan omedelbart.</span><span class="sxs-lookup"><span data-stu-id="d742b-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="d742b-110">Extrahera och parsa strukturerade objekt från sträng innehåll</span><span class="sxs-lookup"><span data-stu-id="d742b-110">Extract and parse structured objects out of string content</span></span>

<span data-ttu-id="d742b-111">I samarbete med [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), en ny `ConvertFrom-String` cmdlet har lagts till.</span><span class="sxs-lookup"><span data-stu-id="d742b-111">In collaboration with [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), a new `ConvertFrom-String` cmdlet has been added.</span></span>

<span data-ttu-id="d742b-112">Den här cmdleten stöder två lägen: basic avgränsade parsning och automatiskt genererad exempel-drivna parsning.</span><span class="sxs-lookup"><span data-stu-id="d742b-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="d742b-113">Avgränsad parsning, som standard delar upp inmatningen vid blanksteg och tilldelar egenskapsnamn till grupperna.</span><span class="sxs-lookup"><span data-stu-id="d742b-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="d742b-114">Du kan anpassa avgränsaren:</span><span class="sxs-lookup"><span data-stu-id="d742b-114">You can customize the delimiter:</span></span>

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

<span data-ttu-id="d742b-115">Cmdleten stöder också automatiskt genererade exempel-drivna parsning baserat på den [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) undersöka arbete i [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span><span class="sxs-lookup"><span data-stu-id="d742b-115">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) research work in [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span></span>

<span data-ttu-id="d742b-116">Överväg ett textbaserat adressboken för att komma igång:</span><span class="sxs-lookup"><span data-stu-id="d742b-116">To get started, consider a text-based address book:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA
```

<span data-ttu-id="d742b-117">Kopiera några exempel till en fil som du vill använda som din mall:</span><span class="sxs-lookup"><span data-stu-id="d742b-117">Copy a few examples into a file, which you will use as your template:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

<span data-ttu-id="d742b-118">Placera klammerparenteser-data som du vill extrahera, ger den ett namn som du gör.</span><span class="sxs-lookup"><span data-stu-id="d742b-118">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="d742b-119">Eftersom den **namn** egenskapen (och dess associerade andra egenskaper) kan visas flera gånger, använda en asterisk (\*) att indikera att detta resulterar i flera poster (i stället för att extrahera en mängd egenskaper till en post):</span><span class="sxs-lookup"><span data-stu-id="d742b-119">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

<span data-ttu-id="d742b-120">Från den här uppsättningen med exempel `ConvertFrom-String` nu automatiskt extrahera objektbaserad utdata från indatafilerna med liknande struktur.</span><span class="sxs-lookup"><span data-stu-id="d742b-120">From this set of examples, `ConvertFrom-String` can now automatically extract object-based output from input files with similar structure.</span></span>

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

<span data-ttu-id="d742b-121">Att göra ytterligare datamanipulering extraherad text i **ExtentText** egenskapen fångar rå text från vilket posten extraheras.</span><span class="sxs-lookup"><span data-stu-id="d742b-121">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="d742b-122">Lämna feedback om den här funktionen eller för att dela innehåll som du har problem med skriva exempel, e-postmeddelande <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="d742b-122">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>