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
# <a name="creating-custom-controls"></a>Skapa anpassade kontroller

Anpassade kontroller är de mest flexibla komponenterna i en formatering fil. Till skillnad från tabellen, lista och många vyer som definierar en formell strukturen för data, till exempel en tabell med data, kan anpassade kontroller du definiera hur en del av data ska visas. Du kan definiera en gemensam uppsättning anpassade kontroller som är tillgängliga för alla vyer i filen formatering, kan du definiera anpassade kontroller som är tillgängliga för en specifik vy eller du kan definiera en uppsättning kontroller som är tillgängliga för en grupp med objekt.

## <a name="custom-control-example"></a>Den anpassade kontrollen som exempel

I följande exempel visas en anpassad kontroll som definieras i filen Certificates.Format.ps1xml. Den anpassade kontrollen som används för att avgränsa de [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objekt som ska visas i en tabellvy.

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

## <a name="see-also"></a>Se även

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
