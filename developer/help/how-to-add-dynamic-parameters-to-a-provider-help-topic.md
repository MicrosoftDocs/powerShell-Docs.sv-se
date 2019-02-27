---
title: Lägga till dynamiska parametrar i ett hjälpavsnitt för providern | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849527"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Lägga till dynamiska parametrar i ett hjälpavsnitt för providers

Det här avsnittet beskrivs hur du fyller i **dynamiska parametrar** delen av ett hjälpavsnitt för providern.

*Dynamiska parametrar* är parametrarna för en cmdlet eller funktion som är tillgängliga endast under angivna villkor.

De dynamiska parametrar som finns dokumenterade i ett hjälpavsnitt för providern är dynamiska parametrar som providern lägger till cmdlet eller funktion när cmdlet eller funktionen används i provider-enheten.

Dynamiska parametrar kan också dokumenterade i anpassade cmdlet-hjälpen för en provider. När du skriver både providern hjälp och anpassade cmdlet-hjälpen för en provider ska inkludera den dynamiska parameter-dokumentationen i båda dokumenten. Mer information om anpassade cmdlet-hjälpen finns i [skriva Windows PowerShell anpassade Cmdlet-hjälp för leverantörer av](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Om en provider inte implementerar några dynamiska parametrar, provider hjälpavsnitt innehåller en tom `DynamicParameters` element.

### <a name="to-add-dynamic-parameters"></a>Att lägga till dynamiska parametrar

1. I den *AssemblyName*.dll-help.xml filen i den `providerHelp` element, lägga till en `DynamicParameters` element. Den `DynamicParameters` element visas efter den `Tasks` elementet och innan den `RelatedLinks` element.

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

   Om leverantören inte implementerar alla dynamiska parametrar, den `DynamicParameters` elementet kan vara tomt.

2. I den `DynamicParameters` element för varje dynamisk parameter, lägga till en `DynamicParameter` element.

   Till exempel:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. I varje `DynamicParameter` element, lägga till en `Name` och `CmdletSupported` element.

   |Elementnamn|Beskrivning|
   |------------------|-----------------|
   |Namn|Anger parameternamnet.|
   |CmdletSupported|Anger de cmdletar som parametern är giltig. Ange en kommaavgränsad lista med cmdlet-namnen.|

   Till exempel följande XML-dokument i `Encoding` dynamisk parameter som filsystem för Windows PowerShell-providern lägger till i den `Add-Content`, `Get-Content`, `Set-Content` cmdletar.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. I varje `DynamicParameter` element, lägga till en `Type` element. Den `Type` element är en behållare för de `Name` element som innehåller .NET-typ av värdet för den dynamiska parametern.

   Visar till exempel följande XML som .NET-typ av den `Encoding` dynamisk parameter är den [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) uppräkning.

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

5. Lägg till den `Description` element som innehåller en kort beskrivning av den dynamiska parametern. När du skriver beskrivningen, Använd riktlinjer föreskrivs för alla cmdlet-parametrarna i [hur du lägger till parameterinformation](./how-to-add-parameter-information.md).

   Följande XML-filen innehåller till exempel en beskrivning av den `Encoding` dynamisk parameter.

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

6. Lägg till den `PossibleValues` elementet och dess underordnade element. De här elementen beskrivs tillsammans värden för den dynamiska parametern. Det här elementet har utformats för uppräknade värden. Om den dynamiska parametern inte tar ett värde, som är fallet med en switchparameter eller går inte att räkna upp värdena, lägga till en tom `PossibleValues` element.

   I följande tabell visas och beskrivs de `PossibleValues` elementet och dess underordnade element.

   |Elementnamn|Beskrivning|
   |------------------|-----------------|
   |PossibleValues|Det här elementet är en behållare. De underordnade elementen beskrivs nedan. Lägg till en `PossibleValues` elementet så att varje hjälpavsnitt för providern. Elementet kan vara tom.|
   |PossibleValue|Det här elementet är en behållare. De underordnade elementen beskrivs nedan. Lägg till en `PossibleValue` element för varje värde i den dynamiska parametern.|
   |Värde|Anger värdenamnet.|
   |Beskrivning|Det här elementet innehåller ett `Para` element. Texten i den `Para` element beskriver värdet med namnet i den `Value` element.|

   Följande XML visar exempelvis en `PossibleValue` elementet i den `Encoding` dynamisk parameter.

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

I följande exempel visas den `DynamicParameters` elementet i den `Encoding` dynamisk parameter.

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