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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844851"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="688cb-102">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="688cb-102">Creating Custom Controls</span></span>

<span data-ttu-id="688cb-103">Anpassade kontroller är de mest flexibla komponenterna i en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="688cb-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="688cb-104">Till skillnad från tabellen, lista och många vyer som definierar en formell strukturen för data, till exempel en tabell med data, kan anpassade kontroller du definiera hur en del av data ska visas.</span><span class="sxs-lookup"><span data-stu-id="688cb-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="688cb-105">Du kan definiera en gemensam uppsättning anpassade kontroller som är tillgängliga för alla vyer i filen formatering, kan du definiera anpassade kontroller som är tillgängliga för en specifik vy eller du kan definiera en uppsättning kontroller som är tillgängliga för en grupp med objekt.</span><span class="sxs-lookup"><span data-stu-id="688cb-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="688cb-106">Den anpassade kontrollen som exempel</span><span class="sxs-lookup"><span data-stu-id="688cb-106">Custom Control Example</span></span>

<span data-ttu-id="688cb-107">I följande exempel visas en anpassad kontroll som definieras i filen Certificates.Format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="688cb-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="688cb-108">Den anpassade kontrollen som används för att avgränsa de [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objekt som ska visas i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="688cb-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="688cb-109">Se även</span><span class="sxs-lookup"><span data-stu-id="688cb-109">See Also</span></span>

[<span data-ttu-id="688cb-110">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="688cb-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
