---
ms.date: 07/09/2020
ms.topic: reference
title: Typ konverterare för utökat typ system
description: Typ konverterare för utökat typ system
ms.openlocfilehash: 0774e9eaae1187162b3d55cc45b902f7411a1f18
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648438"
---
# <a name="ets-type-converters"></a>ETS-typkonverterare

ETS använder två grundläggande typer av typ konverterare när ett anrop görs till `LanguagePrimitives.ConvertTo(System.Object, System.Type)` metoden. När den här metoden anropas försöker PowerShell utföra typ konverteringen med dess standard språk konverterare för PowerShell eller en anpassad konverterare. Om PowerShell inte kan utföra konverteringen, utlöses ett **PSInvalidCastException** -undantag.

## <a name="standard-windows-powershell-language-converters"></a>Standard språk konverterare för Windows PowerShell

Dessa standard konverteringar kontrol leras före eventuella anpassade konverteringar och kan inte åsidosättas. I följande tabell visas de typ konverteringar som utförs av PowerShell när `ConvertTo(System.Object, System.Type)` metoden anropas. Tänk på att referenser till parametrarna **valueToConvert** och **resultType** refererar till parametrarna för- `ConvertTo(System.Object,System.Type)` metoden.

| Från (valueToConvert) |  Till (resultType)  |                                                                               Returer                                                                               |
| --------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Null                  | Sträng            | ""                                                                                                                                                                  |
| Null                  | Char              | ' \ 0 '                                                                                                                                                                |
| Null                  | Numeriskt           | `0` av den typ som anges i parametern **resultType** .                                                                                                          |
| Null                  | Boolesk           | Resultat av anrop till `IsTrue(System.Object)(Null)` metoden.                                                                                                        |
| Null                  | PSObject          | Nytt objekt av typen **PSObject**.                                                                                                                                    |
| Null                  | Ej värde-typ    | Ha.                                                                                                                                                               |
| Null                  | Nullable &lt; T&gt; | Ha.                                                                                                                                                               |
| Härledd klass         | Basklass        | **valueToConvert**                                                                                                                                                  |
| Helst              | Void              | **AutomationNull. Value**                                                                                                                                            |
| Helst              | Sträng            | Anrops `ToString` funktion.                                                                                                                                         |
| Helst              | Boolesk           | `IsTrue(System.Object) (valueToConvert)`                                                                                                                            |
| Helst              | PSObject          | Resultat av anrop till `AsPSObject(System.Object) (valueToConvert)` metoden.                                                                                         |
| Helst              | XML-dokument      | Konverterar **valueToConvert** till sträng och anropar sedan **XMLDocument** -konstruktorn.                                                                                      |
| Matris                 | Matris             | Försöker konvertera varje element i matrisen.                                                                                                                      |
| Singleton             | Matris             | `Array[0]` lika med **valueToConvert** som konverteras till matrisens element typ.                                                                            |
| IDictionary           | Hash-tabell        | Resultat av anrop till hash-hash (valueToConvert).                                                                                                                       |
| Sträng                | Char []            | `valueToConvert.ToCharArray`                                                                                                                                        |
| Sträng                | Verifiering             | Resultat från anrop till `Regx(valueToConvert)` .                                                                                                                          |
| Sträng                | Typ              | Returnerar rätt typ med **valueToConvert** -parametern för att söka i **RunspaceConfiguration. sammansättningar**.                                                 |
| Sträng                | Numeriskt           | Om **valueToConvert** är "" returneras `0` av **resultType**. Annars används kulturen "kultur invariant" för att skapa ett numeriskt värde.                       |
| Integer               | System. Enum       | Konverterar heltalet till konstanten om heltalet definieras av uppräkningen. Om heltalet inte är definierat genereras ett **PSInvalidCastException** -undantag. |

## <a name="custom-conversions"></a>Anpassade konverteringar

Om PowerShell inte kan konvertera typen med hjälp av en standard språk konverterare för PowerShell, söker den efter anpassade konverterare. PowerShell söker efter flera typer av anpassade konverterare i den ordning som beskrivs i det här avsnittet. Tänk på att referenser till parametrarna **valueToConvert** och **resultType** refererar till parametrarna för- `ConvertTo(System.Object, System.Type)` metoden. Om en anpassad konverterare genererar ett undantag görs inget ytterligare försök att konvertera objektet och undantaget är omslutet i ett **PSInvalidCastException** -undantag som sedan utlöses.

## <a name="powershell-type-converter"></a>PowerShell-typ konverterare

PowerShell-typ konverterare används för att konvertera en enskild typ eller en typ av typ, till exempel alla typer som härleds från klassen **system. Enum** . Om du vill skapa en PowerShell-typ konverterare måste du implementera en PSTypeConverter-klass och associera den implementeringen med mål klassen. Det finns två sätt att associera PowerShell-typ konverteraren till dess målklass.

- Genom typ konfigurations filen
- Genom att använda attributet **TypeConverterAttribute** i mål klassen

PowerShell-typs konverterare, härledda från den abstrakta klassen [PSTypeConverter](/dotnet/api/system.management.automation.pstypeconverter) , tillhandahåller metoder för att konvertera ett objekt till en speciell typ eller från en speciell typ. Om parametern **valueToConvert** innehåller ett objekt som har en PowerShell-typ konverterare kopplad, anropar PowerShell den `PSTypeConverter.ConvertTo(System.Object, System.Type,System.IFormatProvider, System.Boolean)`
metoden för den associerade konverteraren för att konvertera objektet till den typ som anges av **resultType** -parametern. Om **resultType** -parametern refererar till en typ som har en PowerShell-typ konverterare kopplad till den, anropar PowerShell `PSTypeConverter.ConvertFrom(System.Object,System.Type, System.IFormatProvider, System.Boolean)`
metoden för den associerade konverteraren för att konvertera objektet från den typ som anges av parametern **resultType** .

## <a name="system-type-converter"></a>Konverterare för system typ

System typs konverterare används för att konvertera en speciell målklass. Den här typen av konverterare kan inte användas för att konvertera en klass familj. Om du vill skapa en system typs konverterare måste du implementera en [TypeConverter](/dotnet/api/system.management.automation.runspaces.typedata.typeconverter#System_Management_Automation_Runspaces_TypeData_TypeConverter) -klass och associera den implementeringen med mål klassen. Det finns två sätt att associera system typs konverteraren med dess målklass.

- Genom typ konfigurations filen
- Genom att använda attributet TypeConverterAttribute i mål klassen

## <a name="parse-converter"></a>Parsa konverterare

Om parametern **valueToConvert** är en sträng och objekt typen för **resultType** -parametern har en `Parse` -metod, `Parse` anropas metoden för att konvertera strängen.

## <a name="constructor-converter"></a>Konstruktor konverterare

Om objekt typen för **resultType** -parametern har en konstruktor som har en enda parameter som är av samma typ som objektet för parametern **valueToConvert** , anropas den här konstruktorn.

## <a name="implicit-cast-operator-converter"></a>Konverterare för implicit omvandling

Om parametern **valueToConvert** har en implicit omvandlings operator som konverterar till **resultType**, anropas dess omvandlings operator. Om **resultType** -parametern har en implicit omvandlings operator som konverterar från **valueToConvert**, anropas dess omvandlings operator.

## <a name="explicit-cast-operator-converter"></a>Konverterare för explicit Cast-operator

Om parametern **valueToConvert** har en explicit omvandlings operator som konverterar till **resultType**, anropas dess omvandlings operator. Om **resultType** -parametern har en explicit omvandlings operator som konverterar från **valueToConvert**, anropas dess omvandlings operator.
