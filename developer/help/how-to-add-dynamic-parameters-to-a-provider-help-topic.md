---
title: Så här lägger du till dynamiska parametrar till en leverantörs hjälp avsnitt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737587"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Lägga till dynamiska parametrar i ett hjälpavsnitt för providers

I det här avsnittet beskrivs hur du fyller i avsnittet **dynamiska parametrar** i en providers hjälp avsnitt.

*Dynamiska parametrar* är parametrar för en cmdlet eller funktion som endast är tillgängliga under angivna villkor.

De dynamiska parametrar som dokumenteras i ett hjälp avsnitt om providern är de dynamiska parametrar som providern lägger till i cmdleten eller funktionen när-cmdleten eller-funktionen används i leverantörs enheten.

Dynamiska parametrar kan också dokumenteras i anpassad cmdlet-hjälp för en provider. När du skriver både hjälpen för Provider och anpassad cmdlet-hjälp för en provider, inkluderar du den dynamiska parameter dokumentationen i båda dokumenten. Mer information om anpassad cmdlet-hjälp finns i [skriva Windows PowerShell anpassad cmdlet-hjälp för providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Om en provider inte implementerar några dynamiska parametrar innehåller leverantörens hjälp avsnitt ett tomt `DynamicParameters` element.

### <a name="to-add-dynamic-parameters"></a>Lägga till dynamiska parametrar

1. I `providerHelp` filen *AssemblyName*. dll-Help. xml i-elementet lägger du till ett `DynamicParameters` -element. Elementet ska visas `Tasks` efter elementet och före `RelatedLinks` elementet. `DynamicParameters`

   Till exempel:

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   Om providern inte implementerar några dynamiska parametrar `DynamicParameters` kan elementet vara tomt.

2. I elementet `DynamicParameters` lägger du till ett `DynamicParameter` -element för varje dynamisk parameter.

   Till exempel:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. I varje `DynamicParameter` element lägger du till `Name` ett `CmdletSupported` och-element.

   |Elementnamn|Beskrivning|
   |------------------|-----------------|
   |Namn|Anger parameter namnet.|
   |CmdletSupported|Anger cmdletarna där parametern är giltig. Ange en kommaavgränsad lista med cmdlet-namn.|

   Till exempel innehåller följande XML-filer den `Encoding` dynamiska parametern som Windows PowerShell-filleverantören lägger till `Add-Content`i `Get-Content` `Set-Content` cmdletarna.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. I varje `DynamicParameter` element lägger du till `Type` ett-element. Elementet är en behållare för det `Name` element som innehåller .net-typen för den dynamiska parameterns värde. `Type`

   Till exempel visar följande XML att .net-typen för den `Encoding` dynamiska parametern är [Microsoft. PowerShell. commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -uppräkningen.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. Lägg till `Description` elementet, som innehåller en kort beskrivning av den dynamiska parametern. När du skriver beskrivningen använder du rikt linjerna för alla cmdlet-parametrar i [så här lägger du till parameter information](./how-to-add-parameter-information.md).

   Till exempel innehåller följande XML en beskrivning av den `Encoding` dynamiska parametern.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. Lägg till `PossibleValues` elementet och dess underordnade element. Tillsammans beskriver de här elementen värdena för den dynamiska parametern. Det här elementet är utformat för uppräknade värden. Om den dynamiska parametern inte tar ett värde, t. ex. är fallet med en växlings parameter, eller om värdena inte kan räknas upp, lägger du `PossibleValues` till ett tomt element.

   I följande tabell visas och beskrivs `PossibleValues` elementet och dess underordnade element.

   |Elementnamn|Beskrivning|
   |------------------|-----------------|
   |PossibleValues|Det här elementet är en behållare. De underordnade elementen beskrivs nedan. Lägg till `PossibleValues` ett element i varje leverantörs hjälp avsnitt. Elementet kan vara tomt.|
   |PossibleValue|Det här elementet är en behållare. De underordnade elementen beskrivs nedan. Lägg till `PossibleValue` ett-element för varje värde för den dynamiska parametern.|
   |Värde|Anger värde namnet.|
   |Beskrivning|Det här elementet innehåller `Para` ett-element. Texten i `Para` elementet beskriver det värde som namnges `Value` i elementet.|

   I följande XML visas till exempel ett `PossibleValue` element i den `Encoding` dynamiska parametern.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>Exempel

I följande exempel visas `DynamicParameters` elementet i den `Encoding` dynamiska parametern.

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```