---
title: Skapa anpassade kontroller | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354791"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="d6ed6-102">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="d6ed6-102">Creating Custom Controls</span></span>

<span data-ttu-id="d6ed6-103">Anpassade kontroller är de mest flexibla komponenterna i en format fil.</span><span class="sxs-lookup"><span data-stu-id="d6ed6-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="d6ed6-104">Till skillnad från tabeller, listor och breda vyer som definierar en formell data struktur, till exempel en tabell med data, anpassade kontroller kan du definiera hur en enskild del av data ska visas.</span><span class="sxs-lookup"><span data-stu-id="d6ed6-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="d6ed6-105">Du kan definiera en gemensam uppsättning anpassade kontroller som är tillgängliga för alla vyer i format filen, du kan definiera anpassade kontroller som är tillgängliga för en speciell vy eller definiera en uppsättning kontroller som är tillgängliga för en grupp med objekt.</span><span class="sxs-lookup"><span data-stu-id="d6ed6-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="d6ed6-106">Exempel på anpassad kontroll</span><span class="sxs-lookup"><span data-stu-id="d6ed6-106">Custom Control Example</span></span>

<span data-ttu-id="d6ed6-107">I följande exempel visas en anpassad kontroll som definieras i filen certificates. format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="d6ed6-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="d6ed6-108">Den här anpassade kontrollen används för att separera objekten [system. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) som visas i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="d6ed6-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d6ed6-109">Se även</span><span class="sxs-lookup"><span data-stu-id="d6ed6-109">See Also</span></span>

[<span data-ttu-id="d6ed6-110">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="d6ed6-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
