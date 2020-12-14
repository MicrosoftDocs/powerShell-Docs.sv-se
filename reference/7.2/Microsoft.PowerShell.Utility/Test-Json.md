---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: a29eab449e567f78d1e54a6716ca91d87aa08405
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709721"
---
# Test-Json

## SAMMANFATTNING
Testar om en sträng är ett giltigt JSON-dokument

## SYNTAX

### __AllParameterSets (standard)
```
Test-Json [-Json] <String> [<CommonParameters>]
```

### SchemaString
```
Test-Json [-Json] <String> [[-Schema] <String>] [<CommonParameters>]
```

### SchemaFile
```
Test-Json [-Json] <String> [-SchemaFile <String>] [<CommonParameters>]
```

## BESKRIVNING

`Test-Json`Cmdleten testar om en sträng är ett giltigt JavaScript Object Notation (JSON)-dokument och kan alternativt verifiera att JSON-dokumentet mot ett angivet schema.

Den verifierade strängen kan sedan användas med `ConvertFrom-Json` cmdleten Convert en JSON-formaterad sträng till ett JSON-objekt, som enkelt hanteras i PowerShell eller skickas till ett annat program eller en webb tjänst som har åtkomst till JSON-ininformation.

Många webbplatser använder JSON i stället för XML för att serialisera data för kommunikation mellan servrar och webbaserade appar.

Den här cmdleten introducerades i PowerShell 6,1

## EXEMPEL

### Exempel 1: testa om ett objekt är giltigt JSON

Det här exemplet testar om Indatasträngen är ett giltigt JSON-dokument.

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### Exempel 2: testa ett objekt mot ett angivet schema

Det här exemplet använder en sträng som innehåller ett JSON-schema och jämför det med en indatasträng.

```powershell
$schema = @'
{
  "definitions": {},
  "$schema": "http://json-schema.org/draft-07/schema#",
  "$id": "http://example.com/root.json",
  "type": "object",
  "title": "The Root Schema",
  "required": [
    "name",
    "age"
  ],
  "properties": {
    "name": {
      "$id": "#/properties/name",
      "type": "string",
      "title": "The Name Schema",
      "default": "",
      "examples": [
        "Ashley"
      ],
      "pattern": "^(.*)$"
    },
    "age": {
      "$id": "#/properties/age",
      "type": "integer",
      "title": "The Age Schema",
      "default": 0,
      "examples": [
        25
      ]
    }
  }
}
'@
"{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
```

```Output
Test-Json : IntegerExpected: #/age
At line:1 char:37
+ "{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
+                                     ~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (:) [Test-Json], Exception
+ FullyQualifiedErrorId : InvalidJsonAgainstSchema,Microsoft.PowerShell.Commands.TestJsonCommand
False
```

I det här exemplet får vi ett fel meddelande eftersom schemat förväntar sig ett heltal för **ålder** , men JSON-inflödet som vi har testat använder ett sträng värde i stället.

Mer information finns i [JSON-schema](https://json-schema.org/).

### Exempel 3: testa ett objekt mot ett schema från en fil

JSON-schemat kan referera till definitioner med hjälp av `$ref` nyckelord. `$ref`Kan matcha en URI som refererar till en annan fil. `SchemaFile`Parametern accepterar en literal sökväg till JSON-schemafilen och tillåter att JSON-filer verifieras mot sådana scheman.

I det här exemplet har vi en `schema.json` fil som refererar till `definitions.json` .

```powershell
PS> Get-Content schema.json

{
  "description":"A person",
  "type":"object",
  "properties":{
    "name":{
      "$ref":"definitions.json#/definitions/name"
    },
    "hobbies":{
      "$ref":"definitions.json#/definitions/hobbies"
    }
  }
}

PS> Get-Content definitions.json

{
  "definitions":{
    "name":{
      "type":"string"
    },
    "hobbies":{
      "type":"array",
      "items":{
        "type":"string"
      }
    }
  }
}

'{"name": "James", "hobbies": [".NET", "Blogging"]}' | Test-Json -SchemaFile 'schema.json'
```

```Output
True
```

Mer information finns i [strukturera ett komplext schema](https://json-schema.org/understanding-json-schema/structuring.html).

## PARAMETRAR

### – JSON

Anger den JSON-sträng som ska kontrol leras. Ange en variabel som innehåller strängen eller Skriv ett kommando eller uttryck som hämtar strängen. Du kan också skicka en sträng till `Test-Json` .

**JSON** -parametern krävs.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Schema

Anger ett schema för att validera JSON-inflödet mot. Om det här alternativet har godkänts `Test-Json` kontrollerar du att JSON-indata överensstämmer med den specifikation som anges av **schema** parametern och returnerar `$True` endast om indata överensstämmer med det angivna schemat.

Mer information finns i [JSON-schema](https://json-schema.org/).

```yaml
Type: System.String
Parameter Sets: SchemaString
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SchemaFile

Anger en schema fil som används för att validera JSON-indata. När den används `Test-Json` returneras `$True` endast om JSON-indata överensstämmer med schemat som definierats i filen som anges av parametern **SchemaFile** .

Mer information finns i [JSON-schema](https://json-schema.org/).

```yaml
Type: System.String
Parameter Sets: SchemaFile
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en JSON-sträng till `Test-Json` .

## UTDATA

### Boolesk

## ANTECKNINGAR

`Test-Json`Cmdleten implementeras med hjälp av [klassen NJsonSchema](https://github.com/RSuter/NJsonSchema).

## RELATERADE LÄNKAR

[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[Ytterligare JSON-schema-information](https://json-schema.org/)

[ConvertTo-Json](ConvertTo-Json.md)

[Anropa-webbegäran](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
