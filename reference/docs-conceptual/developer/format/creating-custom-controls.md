---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa anpassade kontroller
description: Skapa anpassade kontroller
ms.openlocfilehash: 78d8cc2970b2b3e493bef25d78404ba1be195bb1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668056"
---
# <a name="creating-custom-controls"></a>Skapa anpassade kontroller

Anpassade kontroller är de mest flexibla komponenterna i en format fil. Till skillnad från tabeller, listor och breda vyer som definierar en formell data struktur, till exempel en tabell med data, anpassade kontroller kan du definiera hur en enskild del av data ska visas. Du kan definiera en gemensam uppsättning anpassade kontroller som är tillgängliga för alla vyer i format filen, du kan definiera anpassade kontroller som är tillgängliga för en speciell vy eller definiera en uppsättning kontroller som är tillgängliga för en grupp med objekt.

## <a name="custom-control-example"></a>Exempel på anpassad kontroll

I följande exempel visas en anpassad kontroll som definieras i Certificates.Format.ps1XML-filen. Den här anpassade kontrollen används för att separera objekten [system. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) som visas i en tabellvy.

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

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
