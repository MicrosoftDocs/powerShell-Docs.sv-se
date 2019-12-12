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
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353307"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Lägga till dynamiska parametrar i ett hjälpavsnitt för providers

I det här avsnittet beskrivs hur du fyller i avsnittet **dynamiska parametrar** i en providers hjälp avsnitt.

*Dynamiska parametrar* är parametrar för en cmdlet eller funktion som endast är tillgängliga under angivna villkor.

De dynamiska parametrar som dokumenteras i ett hjälp avsnitt om providern är de dynamiska parametrar som providern lägger till i cmdleten eller funktionen när-cmdleten eller-funktionen används i leverantörs enheten.

Dynamiska parametrar kan också dokumenteras i anpassad cmdlet-hjälp för en provider. När du skriver både hjälpen för Provider och anpassad cmdlet-hjälp för en provider, inkluderar du den dynamiska parameter dokumentationen i båda dokumenten.

Om en provider inte implementerar några dynamiska parametrar innehåller hjälp avsnittet Provider ett tomt `DynamicParameters`-element.

### <a name="to-add-dynamic-parameters"></a>Lägga till dynamiska parametrar

1. Lägg till ett `DynamicParameters`-element i `providerHelp`-elementet i filen *AssemblyName*. dll-Help. xml. `DynamicParameters`-elementet ska visas efter `Tasks`-elementet och före `RelatedLinks`-elementet.

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

   Om providern inte implementerar några dynamiska parametrar kan `DynamicParameters`-elementet vara tomt.

2. Lägg till ett `DynamicParameter`-element för varje dynamisk parameter i `DynamicParameters`-elementet.

   Till exempel:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. I varje `DynamicParameter`-element lägger du till ett `Name`-och `CmdletSupported`-element.

   |Elementnamn|Beskrivning|
   |------------------|-----------------|
   |Namn|Anger parameter namnet.|
   |CmdletSupported|Anger cmdletarna där parametern är giltig. Ange en kommaavgränsad lista med cmdlet-namn.|

   Till exempel är följande XML-dokument `Encoding` dynamiska parametern som Windows PowerShell-providern lägger till i `Add-Content``Get-Content``Set-Content` cmdlets.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. I varje `DynamicParameter`-element lägger du till ett `Type`-element. `Type`-elementet är en behållare för det `Name`-element som innehåller .NET-typen för den dynamiska parameterns värde.

   Följande XML visar till exempel att .NET-typen för parametern `Encoding` Dynamic är [Microsoft. PowerShell. commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -uppräkning.

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

5. Lägg till `Description`-elementet som innehåller en kort beskrivning av den dynamiska parametern. När du skriver beskrivningen använder du rikt linjerna för alla cmdlet-parametrar i [så här lägger du till parameter information](./how-to-add-parameter-information.md).

   Följande XML innehåller till exempel en beskrivning av parametern `Encoding` Dynamic.

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

6. Lägg till `PossibleValues`-elementet och dess underordnade element. Tillsammans beskriver de här elementen värdena för den dynamiska parametern. Det här elementet är utformat för uppräknade värden. Om den dynamiska parametern inte tar ett värde, t. ex. är fallet med en växlings parameter, eller om värdena inte kan räknas upp, lägger du till ett tomt `PossibleValues`-element.

   I följande tabell visas och beskrivs `PossibleValues`-elementet och dess underordnade element.

   |Elementnamn|Beskrivning|
   |------------------|-----------------|
   |PossibleValues|Det här elementet är en behållare. De underordnade elementen beskrivs nedan. Lägg till ett `PossibleValues`-element i varje leverantörs hjälp avsnitt. Elementet kan vara tomt.|
   |PossibleValue|Det här elementet är en behållare. De underordnade elementen beskrivs nedan. Lägg till ett `PossibleValue`-element för varje värde för den dynamiska parametern.|
   |Värde|Anger värde namnet.|
   |Beskrivning|Det här elementet innehåller ett `Para`-element. Texten i `Para`-elementet beskriver det värde som namnges i `Value`-elementet.|

   Följande XML visar till exempel ett `PossibleValue`-element i parametern `Encoding` dynamisk.

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

I följande exempel visas `DynamicParameters`-elementet i parametern `Encoding` dynamisk.

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