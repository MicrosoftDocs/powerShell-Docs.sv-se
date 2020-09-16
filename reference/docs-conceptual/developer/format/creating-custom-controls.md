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
