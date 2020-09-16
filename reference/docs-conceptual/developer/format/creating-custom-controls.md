---
title: Skapa anpassade kontroller | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c36fa9b778e01501a3c88f735cdefdfbb04411a0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786126"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="6fe4c-102">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="6fe4c-102">Creating Custom Controls</span></span>

<span data-ttu-id="6fe4c-103">Anpassade kontroller är de mest flexibla komponenterna i en format fil.</span><span class="sxs-lookup"><span data-stu-id="6fe4c-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="6fe4c-104">Till skillnad från tabeller, listor och breda vyer som definierar en formell data struktur, till exempel en tabell med data, anpassade kontroller kan du definiera hur en enskild del av data ska visas.</span><span class="sxs-lookup"><span data-stu-id="6fe4c-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="6fe4c-105">Du kan definiera en gemensam uppsättning anpassade kontroller som är tillgängliga för alla vyer i format filen, du kan definiera anpassade kontroller som är tillgängliga för en speciell vy eller definiera en uppsättning kontroller som är tillgängliga för en grupp med objekt.</span><span class="sxs-lookup"><span data-stu-id="6fe4c-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="6fe4c-106">Exempel på anpassad kontroll</span><span class="sxs-lookup"><span data-stu-id="6fe4c-106">Custom Control Example</span></span>

<span data-ttu-id="6fe4c-107">I följande exempel visas en anpassad kontroll som definieras i Certificates.Format.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="6fe4c-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="6fe4c-108">Den här anpassade kontrollen används för att separera objekten [system. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) som visas i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="6fe4c-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a><span data-ttu-id="6fe4c-109">Se även</span><span class="sxs-lookup"><span data-stu-id="6fe4c-109">See Also</span></span>

[<span data-ttu-id="6fe4c-110">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="6fe4c-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
