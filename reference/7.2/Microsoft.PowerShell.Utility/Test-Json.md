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
# <span data-ttu-id="59f72-102">Test-Json</span><span class="sxs-lookup"><span data-stu-id="59f72-102">Test-Json</span></span>

## <span data-ttu-id="59f72-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="59f72-103">SYNOPSIS</span></span>
<span data-ttu-id="59f72-104">Testar om en sträng är ett giltigt JSON-dokument</span><span class="sxs-lookup"><span data-stu-id="59f72-104">Tests whether a string is a valid JSON document</span></span>

## <span data-ttu-id="59f72-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="59f72-105">SYNTAX</span></span>

### <span data-ttu-id="59f72-106">__AllParameterSets (standard)</span><span class="sxs-lookup"><span data-stu-id="59f72-106">__AllParameterSets (Default)</span></span>
```
Test-Json [-Json] <String> [<CommonParameters>]
```

### <span data-ttu-id="59f72-107">SchemaString</span><span class="sxs-lookup"><span data-stu-id="59f72-107">SchemaString</span></span>
```
Test-Json [-Json] <String> [[-Schema] <String>] [<CommonParameters>]
```

### <span data-ttu-id="59f72-108">SchemaFile</span><span class="sxs-lookup"><span data-stu-id="59f72-108">SchemaFile</span></span>
```
Test-Json [-Json] <String> [-SchemaFile <String>] [<CommonParameters>]
```

## <span data-ttu-id="59f72-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="59f72-109">DESCRIPTION</span></span>

<span data-ttu-id="59f72-110">`Test-Json`Cmdleten testar om en sträng är ett giltigt JavaScript Object Notation (JSON)-dokument och kan alternativt verifiera att JSON-dokumentet mot ett angivet schema.</span><span class="sxs-lookup"><span data-stu-id="59f72-110">The `Test-Json` cmdlet tests whether a string is a valid JavaScript Object Notation (JSON) document and can optionally verify that JSON document against a provided schema.</span></span>

<span data-ttu-id="59f72-111">Den verifierade strängen kan sedan användas med `ConvertFrom-Json` cmdleten Convert en JSON-formaterad sträng till ett JSON-objekt, som enkelt hanteras i PowerShell eller skickas till ett annat program eller en webb tjänst som har åtkomst till JSON-ininformation.</span><span class="sxs-lookup"><span data-stu-id="59f72-111">The verified string can then be used with the `ConvertFrom-Json` cmdlet convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell or sent to another program or web service that access JSON input.</span></span>

<span data-ttu-id="59f72-112">Många webbplatser använder JSON i stället för XML för att serialisera data för kommunikation mellan servrar och webbaserade appar.</span><span class="sxs-lookup"><span data-stu-id="59f72-112">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="59f72-113">Den här cmdleten introducerades i PowerShell 6,1</span><span class="sxs-lookup"><span data-stu-id="59f72-113">This cmdlet was introduced in PowerShell 6.1</span></span>

## <span data-ttu-id="59f72-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="59f72-114">EXAMPLES</span></span>

### <span data-ttu-id="59f72-115">Exempel 1: testa om ett objekt är giltigt JSON</span><span class="sxs-lookup"><span data-stu-id="59f72-115">Example 1: Test if an object is valid JSON</span></span>

<span data-ttu-id="59f72-116">Det här exemplet testar om Indatasträngen är ett giltigt JSON-dokument.</span><span class="sxs-lookup"><span data-stu-id="59f72-116">This example tests whether the input string is a valid JSON document.</span></span>

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### <span data-ttu-id="59f72-117">Exempel 2: testa ett objekt mot ett angivet schema</span><span class="sxs-lookup"><span data-stu-id="59f72-117">Example 2: Test an object against a provided schema</span></span>

<span data-ttu-id="59f72-118">Det här exemplet använder en sträng som innehåller ett JSON-schema och jämför det med en indatasträng.</span><span class="sxs-lookup"><span data-stu-id="59f72-118">This example takes a string containing a JSON schema and compares it to an input string.</span></span>

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

<span data-ttu-id="59f72-119">I det här exemplet får vi ett fel meddelande eftersom schemat förväntar sig ett heltal för **ålder** , men JSON-inflödet som vi har testat använder ett sträng värde i stället.</span><span class="sxs-lookup"><span data-stu-id="59f72-119">In this example, we get an error because the schema expects an integer for **age** but the JSON input we tested uses a string value instead.</span></span>

<span data-ttu-id="59f72-120">Mer information finns i [JSON-schema](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="59f72-120">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

### <span data-ttu-id="59f72-121">Exempel 3: testa ett objekt mot ett schema från en fil</span><span class="sxs-lookup"><span data-stu-id="59f72-121">Example 3: Test an object against a schema from file</span></span>

<span data-ttu-id="59f72-122">JSON-schemat kan referera till definitioner med hjälp av `$ref` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="59f72-122">JSON schema can reference definitions using `$ref` keyword.</span></span> <span data-ttu-id="59f72-123">`$ref`Kan matcha en URI som refererar till en annan fil.</span><span class="sxs-lookup"><span data-stu-id="59f72-123">The `$ref` can resolve to a URI that references another file.</span></span> <span data-ttu-id="59f72-124">`SchemaFile`Parametern accepterar en literal sökväg till JSON-schemafilen och tillåter att JSON-filer verifieras mot sådana scheman.</span><span class="sxs-lookup"><span data-stu-id="59f72-124">The `SchemaFile` parameter accepts literal path to the JSON schema file and allows JSON files to be validated against such schemas.</span></span>

<span data-ttu-id="59f72-125">I det här exemplet har vi en `schema.json` fil som refererar till `definitions.json` .</span><span class="sxs-lookup"><span data-stu-id="59f72-125">In this example we have `schema.json` file which references `definitions.json`.</span></span>

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

<span data-ttu-id="59f72-126">Mer information finns i [strukturera ett komplext schema](https://json-schema.org/understanding-json-schema/structuring.html).</span><span class="sxs-lookup"><span data-stu-id="59f72-126">For more information, see [Structuring a complex schema](https://json-schema.org/understanding-json-schema/structuring.html).</span></span>

## <span data-ttu-id="59f72-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="59f72-127">PARAMETERS</span></span>

### <span data-ttu-id="59f72-128">– JSON</span><span class="sxs-lookup"><span data-stu-id="59f72-128">-Json</span></span>

<span data-ttu-id="59f72-129">Anger den JSON-sträng som ska kontrol leras.</span><span class="sxs-lookup"><span data-stu-id="59f72-129">Specifies the JSON string to test for validity.</span></span> <span data-ttu-id="59f72-130">Ange en variabel som innehåller strängen eller Skriv ett kommando eller uttryck som hämtar strängen.</span><span class="sxs-lookup"><span data-stu-id="59f72-130">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="59f72-131">Du kan också skicka en sträng till `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="59f72-131">You can also pipe a string to `Test-Json`.</span></span>

<span data-ttu-id="59f72-132">**JSON** -parametern krävs.</span><span class="sxs-lookup"><span data-stu-id="59f72-132">The **Json** parameter is required.</span></span>

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

### <span data-ttu-id="59f72-133">– Schema</span><span class="sxs-lookup"><span data-stu-id="59f72-133">-Schema</span></span>

<span data-ttu-id="59f72-134">Anger ett schema för att validera JSON-inflödet mot.</span><span class="sxs-lookup"><span data-stu-id="59f72-134">Specifies a Schema to validate the JSON input against.</span></span> <span data-ttu-id="59f72-135">Om det här alternativet har godkänts `Test-Json` kontrollerar du att JSON-indata överensstämmer med den specifikation som anges av **schema** parametern och returnerar `$True` endast om indata överensstämmer med det angivna schemat.</span><span class="sxs-lookup"><span data-stu-id="59f72-135">If passed `Test-Json` will validate that the Json input conforms to the spec specified by the **Schema** parameter and return `$True` only if the input conforms to the provided Schema.</span></span>

<span data-ttu-id="59f72-136">Mer information finns i [JSON-schema](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="59f72-136">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

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

### <span data-ttu-id="59f72-137">-SchemaFile</span><span class="sxs-lookup"><span data-stu-id="59f72-137">-SchemaFile</span></span>

<span data-ttu-id="59f72-138">Anger en schema fil som används för att validera JSON-indata.</span><span class="sxs-lookup"><span data-stu-id="59f72-138">Specifies a schema file used to validate the JSON input.</span></span> <span data-ttu-id="59f72-139">När den används `Test-Json` returneras `$True` endast om JSON-indata överensstämmer med schemat som definierats i filen som anges av parametern **SchemaFile** .</span><span class="sxs-lookup"><span data-stu-id="59f72-139">When used, the `Test-Json` returns `$True` only if the JSON input conforms to the Schema defined in the file specified by the **SchemaFile** parameter.</span></span>

<span data-ttu-id="59f72-140">Mer information finns i [JSON-schema](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="59f72-140">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

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

### <span data-ttu-id="59f72-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="59f72-141">CommonParameters</span></span>

<span data-ttu-id="59f72-142">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="59f72-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="59f72-143">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="59f72-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="59f72-144">INDATA</span><span class="sxs-lookup"><span data-stu-id="59f72-144">INPUTS</span></span>

### <span data-ttu-id="59f72-145">System. String</span><span class="sxs-lookup"><span data-stu-id="59f72-145">System.String</span></span>

<span data-ttu-id="59f72-146">Du kan skicka vidare en JSON-sträng till `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="59f72-146">You can pipe a JSON string to `Test-Json`.</span></span>

## <span data-ttu-id="59f72-147">UTDATA</span><span class="sxs-lookup"><span data-stu-id="59f72-147">OUTPUTS</span></span>

### <span data-ttu-id="59f72-148">Boolesk</span><span class="sxs-lookup"><span data-stu-id="59f72-148">Boolean</span></span>

## <span data-ttu-id="59f72-149">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="59f72-149">NOTES</span></span>

<span data-ttu-id="59f72-150">`Test-Json`Cmdleten implementeras med hjälp av [klassen NJsonSchema](https://github.com/RSuter/NJsonSchema).</span><span class="sxs-lookup"><span data-stu-id="59f72-150">The `Test-Json` cmdlet is implemented by using the [NJsonSchema Class](https://github.com/RSuter/NJsonSchema).</span></span>

## <span data-ttu-id="59f72-151">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="59f72-151">RELATED LINKS</span></span>

<span data-ttu-id="59f72-152">[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="59f72-152">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="59f72-153">Ytterligare JSON-schema-information</span><span class="sxs-lookup"><span data-stu-id="59f72-153">Additional JSON Schema Details</span></span>](https://json-schema.org/)

[<span data-ttu-id="59f72-154">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="59f72-154">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="59f72-155">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="59f72-155">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="59f72-156">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="59f72-156">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
