---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: 79cf0d9a8107cbf843eba5c58e4b4e9ad30ad285
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263415"
---
# <span data-ttu-id="a984d-103">Test-Json</span><span class="sxs-lookup"><span data-stu-id="a984d-103">Test-Json</span></span>

## <span data-ttu-id="a984d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a984d-104">SYNOPSIS</span></span>
<span data-ttu-id="a984d-105">Testar om en sträng är ett giltigt JSON-dokument</span><span class="sxs-lookup"><span data-stu-id="a984d-105">Tests whether a string is a valid JSON document</span></span>

## <span data-ttu-id="a984d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a984d-106">SYNTAX</span></span>

### <span data-ttu-id="a984d-107">__AllParameterSets (standard)</span><span class="sxs-lookup"><span data-stu-id="a984d-107">__AllParameterSets (Default)</span></span>
```
Test-Json [-Json] <String> [<CommonParameters>]
```

### <span data-ttu-id="a984d-108">SchemaString</span><span class="sxs-lookup"><span data-stu-id="a984d-108">SchemaString</span></span>
```
Test-Json [-Json] <String> [[-Schema] <String>] [<CommonParameters>]
```

### <span data-ttu-id="a984d-109">SchemaFile</span><span class="sxs-lookup"><span data-stu-id="a984d-109">SchemaFile</span></span>
```
Test-Json [-Json] <String> [-SchemaFile <String>] [<CommonParameters>]
```

## <span data-ttu-id="a984d-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a984d-110">DESCRIPTION</span></span>

<span data-ttu-id="a984d-111">`Test-Json`Cmdleten testar om en sträng är ett giltigt JavaScript Object Notation (JSON)-dokument och kan alternativt verifiera att JSON-dokumentet mot ett angivet schema.</span><span class="sxs-lookup"><span data-stu-id="a984d-111">The `Test-Json` cmdlet tests whether a string is a valid JavaScript Object Notation (JSON) document and can optionally verify that JSON document against a provided schema.</span></span>

<span data-ttu-id="a984d-112">Den verifierade strängen kan sedan användas med `ConvertFrom-Json` cmdleten Convert en JSON-formaterad sträng till ett JSON-objekt, som enkelt hanteras i PowerShell eller skickas till ett annat program eller en webb tjänst som har åtkomst till JSON-ininformation.</span><span class="sxs-lookup"><span data-stu-id="a984d-112">The verified string can then be used with the `ConvertFrom-Json` cmdlet convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell or sent to another program or web service that access JSON input.</span></span>

<span data-ttu-id="a984d-113">Många webbplatser använder JSON i stället för XML för att serialisera data för kommunikation mellan servrar och webbaserade appar.</span><span class="sxs-lookup"><span data-stu-id="a984d-113">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="a984d-114">Den här cmdleten introducerades i PowerShell 6,1</span><span class="sxs-lookup"><span data-stu-id="a984d-114">This cmdlet was introduced in PowerShell 6.1</span></span>

## <span data-ttu-id="a984d-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a984d-115">EXAMPLES</span></span>

### <span data-ttu-id="a984d-116">Exempel 1: testa om ett objekt är giltigt JSON</span><span class="sxs-lookup"><span data-stu-id="a984d-116">Example 1: Test if an object is valid JSON</span></span>

<span data-ttu-id="a984d-117">Det här exemplet testar om Indatasträngen är ett giltigt JSON-dokument.</span><span class="sxs-lookup"><span data-stu-id="a984d-117">This example tests whether the input string is a valid JSON document.</span></span>

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### <span data-ttu-id="a984d-118">Exempel 2: testa ett objekt mot ett angivet schema</span><span class="sxs-lookup"><span data-stu-id="a984d-118">Example 2: Test an object against a provided schema</span></span>

<span data-ttu-id="a984d-119">Det här exemplet använder en sträng som innehåller ett JSON-schema och jämför det med en indatasträng.</span><span class="sxs-lookup"><span data-stu-id="a984d-119">This example takes a string containing a JSON schema and compares it to an input string.</span></span>

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

<span data-ttu-id="a984d-120">I det här exemplet får vi ett fel meddelande eftersom schemat förväntar sig ett heltal för **ålder** , men JSON-inflödet som vi har testat använder ett sträng värde i stället.</span><span class="sxs-lookup"><span data-stu-id="a984d-120">In this example, we get an error because the schema expects an integer for **age** but the JSON input we tested uses a string value instead.</span></span>

<span data-ttu-id="a984d-121">Mer information finns i [JSON-schema](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="a984d-121">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

### <span data-ttu-id="a984d-122">Exempel 3: testa ett objekt mot ett schema från en fil</span><span class="sxs-lookup"><span data-stu-id="a984d-122">Example 3: Test an object against a schema from file</span></span>

<span data-ttu-id="a984d-123">JSON-schemat kan referera till definitioner med hjälp av `$ref` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a984d-123">JSON schema can reference definitions using `$ref` keyword.</span></span> <span data-ttu-id="a984d-124">`$ref`Kan matcha en URI som refererar till en annan fil.</span><span class="sxs-lookup"><span data-stu-id="a984d-124">The `$ref` can resolve to a URI that references another file.</span></span> <span data-ttu-id="a984d-125">`SchemaFile`Parametern accepterar en literal sökväg till JSON-schemafilen och tillåter att JSON-filer verifieras mot sådana scheman.</span><span class="sxs-lookup"><span data-stu-id="a984d-125">The `SchemaFile` parameter accepts literal path to the JSON schema file and allows JSON files to be validated against such schemas.</span></span>

<span data-ttu-id="a984d-126">I det här exemplet har vi en `schema.json` fil som refererar till `definitions.json` .</span><span class="sxs-lookup"><span data-stu-id="a984d-126">In this example we have `schema.json` file which references `definitions.json`.</span></span>

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

<span data-ttu-id="a984d-127">Mer information finns i [strukturera ett komplext schema](https://json-schema.org/understanding-json-schema/structuring.html).</span><span class="sxs-lookup"><span data-stu-id="a984d-127">For more information, see [Structuring a complex schema](https://json-schema.org/understanding-json-schema/structuring.html).</span></span>

## <span data-ttu-id="a984d-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a984d-128">PARAMETERS</span></span>

### <span data-ttu-id="a984d-129">– JSON</span><span class="sxs-lookup"><span data-stu-id="a984d-129">-Json</span></span>

<span data-ttu-id="a984d-130">Anger den JSON-sträng som ska kontrol leras.</span><span class="sxs-lookup"><span data-stu-id="a984d-130">Specifies the JSON string to test for validity.</span></span> <span data-ttu-id="a984d-131">Ange en variabel som innehåller strängen eller Skriv ett kommando eller uttryck som hämtar strängen.</span><span class="sxs-lookup"><span data-stu-id="a984d-131">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="a984d-132">Du kan också skicka en sträng till `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="a984d-132">You can also pipe a string to `Test-Json`.</span></span>

<span data-ttu-id="a984d-133">**JSON** -parametern krävs.</span><span class="sxs-lookup"><span data-stu-id="a984d-133">The **Json** parameter is required.</span></span>

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

### <span data-ttu-id="a984d-134">– Schema</span><span class="sxs-lookup"><span data-stu-id="a984d-134">-Schema</span></span>

<span data-ttu-id="a984d-135">Anger ett schema för att validera JSON-inflödet mot.</span><span class="sxs-lookup"><span data-stu-id="a984d-135">Specifies a Schema to validate the JSON input against.</span></span> <span data-ttu-id="a984d-136">Om det här alternativet har godkänts `Test-Json` kontrollerar du att JSON-indata överensstämmer med den specifikation som anges av **schema** parametern och returnerar `$True` endast om indata överensstämmer med det angivna schemat.</span><span class="sxs-lookup"><span data-stu-id="a984d-136">If passed `Test-Json` will validate that the Json input conforms to the spec specified by the **Schema** parameter and return `$True` only if the input conforms to the provided Schema.</span></span>

<span data-ttu-id="a984d-137">Mer information finns i [JSON-schema](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="a984d-137">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

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

### <span data-ttu-id="a984d-138">-SchemaFile</span><span class="sxs-lookup"><span data-stu-id="a984d-138">-SchemaFile</span></span>

<span data-ttu-id="a984d-139">Anger en schema fil som används för att validera JSON-indata.</span><span class="sxs-lookup"><span data-stu-id="a984d-139">Specifies a schema file used to validate the JSON input.</span></span> <span data-ttu-id="a984d-140">När den används `Test-Json` returneras `$True` endast om JSON-indata överensstämmer med schemat som definierats i filen som anges av parametern **SchemaFile** .</span><span class="sxs-lookup"><span data-stu-id="a984d-140">When used, the `Test-Json` returns `$True` only if the JSON input conforms to the Schema defined in the file specified by the **SchemaFile** parameter.</span></span>

<span data-ttu-id="a984d-141">Mer information finns i [JSON-schema](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="a984d-141">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

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

### <span data-ttu-id="a984d-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a984d-142">CommonParameters</span></span>

<span data-ttu-id="a984d-143">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a984d-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a984d-144">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a984d-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a984d-145">INDATA</span><span class="sxs-lookup"><span data-stu-id="a984d-145">INPUTS</span></span>

### <span data-ttu-id="a984d-146">System. String</span><span class="sxs-lookup"><span data-stu-id="a984d-146">System.String</span></span>

<span data-ttu-id="a984d-147">Du kan skicka vidare en JSON-sträng till `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="a984d-147">You can pipe a JSON string to `Test-Json`.</span></span>

## <span data-ttu-id="a984d-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a984d-148">OUTPUTS</span></span>

### <span data-ttu-id="a984d-149">Boolesk</span><span class="sxs-lookup"><span data-stu-id="a984d-149">Boolean</span></span>

## <span data-ttu-id="a984d-150">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a984d-150">NOTES</span></span>

<span data-ttu-id="a984d-151">`Test-Json`Cmdleten implementeras med hjälp av [klassen NJsonSchema](https://github.com/RSuter/NJsonSchema).</span><span class="sxs-lookup"><span data-stu-id="a984d-151">The `Test-Json` cmdlet is implemented by using the [NJsonSchema Class](https://github.com/RSuter/NJsonSchema).</span></span>

## <span data-ttu-id="a984d-152">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a984d-152">RELATED LINKS</span></span>

<span data-ttu-id="a984d-153">[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="a984d-153">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="a984d-154">Ytterligare JSON-schema-information</span><span class="sxs-lookup"><span data-stu-id="a984d-154">Additional JSON Schema Details</span></span>](https://json-schema.org/)

[<span data-ttu-id="a984d-155">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="a984d-155">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="a984d-156">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="a984d-156">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="a984d-157">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="a984d-157">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
