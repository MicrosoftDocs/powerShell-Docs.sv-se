---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: 2e3d49700adb8115bf24ae505fbb00c14a774f15
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263145"
---
# <span data-ttu-id="6cdeb-103">Test-Json</span><span class="sxs-lookup"><span data-stu-id="6cdeb-103">Test-Json</span></span>

## <span data-ttu-id="6cdeb-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6cdeb-104">SYNOPSIS</span></span>
<span data-ttu-id="6cdeb-105">Testar om en sträng är ett giltigt JSON-dokument</span><span class="sxs-lookup"><span data-stu-id="6cdeb-105">Tests whether a string is a valid JSON document</span></span>

## <span data-ttu-id="6cdeb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6cdeb-106">SYNTAX</span></span>

```
Test-Json [-Json] <string> [[-Schema] <string>] [<CommonParameters>]
```

## <span data-ttu-id="6cdeb-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6cdeb-107">DESCRIPTION</span></span>

<span data-ttu-id="6cdeb-108">`Test-Json`Cmdleten testar om en sträng är ett giltigt JavaScript Object Notation (JSON)-dokument och kan alternativt verifiera att JSON-dokumentet mot ett angivet schema.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-108">The `Test-Json` cmdlet tests whether a string is a valid JavaScript Object Notation (JSON) document and can optionally verify that JSON document against a provided schema.</span></span>

<span data-ttu-id="6cdeb-109">Den verifierade strängen kan sedan användas med `ConvertFrom-Json` cmdleten Convert en JSON-formaterad sträng till ett JSON-objekt, som enkelt hanteras i PowerShell eller skickas till ett annat program eller en webb tjänst som har åtkomst till JSON-ininformation.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-109">The verified string can then be used with the `ConvertFrom-Json` cmdlet convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell or sent to another program or web service that access JSON input.</span></span>

<span data-ttu-id="6cdeb-110">Många webbplatser använder JSON i stället för XML för att serialisera data för kommunikation mellan servrar och webbaserade appar.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-110">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="6cdeb-111">Den här cmdleten introducerades i PowerShell 6,1</span><span class="sxs-lookup"><span data-stu-id="6cdeb-111">This cmdlet was introduced in PowerShell 6.1</span></span>

## <span data-ttu-id="6cdeb-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6cdeb-112">EXAMPLES</span></span>

### <span data-ttu-id="6cdeb-113">Exempel 1: testa om ett objekt är giltigt JSON</span><span class="sxs-lookup"><span data-stu-id="6cdeb-113">Example 1: Test if an object is valid JSON</span></span>

<span data-ttu-id="6cdeb-114">Det här exemplet testar om Indatasträngen är ett giltigt JSON-dokument.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-114">This example tests whether the input string is a valid JSON document.</span></span>

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### <span data-ttu-id="6cdeb-115">Exempel 2: testa ett objekt mot ett angivet schema</span><span class="sxs-lookup"><span data-stu-id="6cdeb-115">Example 2: Test an object against a provided schema</span></span>

<span data-ttu-id="6cdeb-116">Det här exemplet använder en sträng som innehåller ett JSON-schema och jämför det med en indatasträng.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-116">This example takes a string containing a JSON schema and compares it to an input string.</span></span>

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

<span data-ttu-id="6cdeb-117">I det här exemplet får vi ett fel meddelande eftersom schemat förväntar sig ett heltal för **ålder** , men JSON-inflödet som vi har testat använder ett sträng värde i stället.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-117">In this example, we get an error because the schema expects an integer for **age** but the JSON input we tested uses a string value instead.</span></span>

<span data-ttu-id="6cdeb-118">Mer information finns i [JSON-schema](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="6cdeb-118">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

## <span data-ttu-id="6cdeb-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6cdeb-119">PARAMETERS</span></span>

### <span data-ttu-id="6cdeb-120">– JSON</span><span class="sxs-lookup"><span data-stu-id="6cdeb-120">-Json</span></span>

<span data-ttu-id="6cdeb-121">Anger den JSON-sträng som ska kontrol leras.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-121">Specifies the JSON string to test for validity.</span></span> <span data-ttu-id="6cdeb-122">Ange en variabel som innehåller strängen eller Skriv ett kommando eller uttryck som hämtar strängen.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-122">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="6cdeb-123">Du kan också skicka en sträng till `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="6cdeb-123">You can also pipe a string to `Test-Json`.</span></span>

<span data-ttu-id="6cdeb-124">**JSON** -parametern krävs.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-124">The **Json** parameter is required.</span></span>

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

### <span data-ttu-id="6cdeb-125">– Schema</span><span class="sxs-lookup"><span data-stu-id="6cdeb-125">-Schema</span></span>

<span data-ttu-id="6cdeb-126">Anger ett schema för att validera JSON-inflödet mot.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-126">Specifies a Schema to validate the JSON input against.</span></span> <span data-ttu-id="6cdeb-127">Om det här alternativet har godkänts `Test-Json` kontrollerar du att JSON-indata överensstämmer med den specifikation som anges av **schema** parametern och returnerar `$True` endast om indata överensstämmer med det angivna schemat.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-127">If passed `Test-Json` will validate that the Json input conforms to the spec specified by the **Schema** parameter and return `$True` only if the input conforms to the provided Schema.</span></span>

<span data-ttu-id="6cdeb-128">Mer information finns i [JSON-schema](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="6cdeb-128">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6cdeb-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6cdeb-129">CommonParameters</span></span>

<span data-ttu-id="6cdeb-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6cdeb-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6cdeb-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6cdeb-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6cdeb-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="6cdeb-132">INPUTS</span></span>

### <span data-ttu-id="6cdeb-133">System. String</span><span class="sxs-lookup"><span data-stu-id="6cdeb-133">System.String</span></span>

<span data-ttu-id="6cdeb-134">Du kan skicka vidare en JSON-sträng till `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="6cdeb-134">You can pipe a JSON string to `Test-Json`.</span></span>

## <span data-ttu-id="6cdeb-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6cdeb-135">OUTPUTS</span></span>

### <span data-ttu-id="6cdeb-136">Boolesk</span><span class="sxs-lookup"><span data-stu-id="6cdeb-136">Boolean</span></span>

## <span data-ttu-id="6cdeb-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6cdeb-137">NOTES</span></span>

<span data-ttu-id="6cdeb-138">`Test-Json`Cmdleten implementeras med hjälp av [klassen NJsonSchema](https://github.com/RSuter/NJsonSchema).</span><span class="sxs-lookup"><span data-stu-id="6cdeb-138">The `Test-Json` cmdlet is implemented by using the [NJsonSchema Class](https://github.com/RSuter/NJsonSchema).</span></span>

## <span data-ttu-id="6cdeb-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6cdeb-139">RELATED LINKS</span></span>

<span data-ttu-id="6cdeb-140">[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="6cdeb-140">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="6cdeb-141">Ytterligare JSON-schema-information</span><span class="sxs-lookup"><span data-stu-id="6cdeb-141">Additional JSON Schema Details</span></span>](https://json-schema.org/)

[<span data-ttu-id="6cdeb-142">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="6cdeb-142">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="6cdeb-143">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="6cdeb-143">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="6cdeb-144">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="6cdeb-144">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
