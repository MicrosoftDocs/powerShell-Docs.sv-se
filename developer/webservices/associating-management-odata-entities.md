---
title: Associera Management OData-entiteter | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850192"
---
# <a name="associating-management-odata-entities"></a>Associera Management OData-entiteter

Ofta är det praktiskt att skapa en koppling mellan två olika Management OData-entiteter. Exempelvis en Management OData-tjänst kan ha entiteter som hanterar en förteckning över produkter som är uppdelade i kategorier och definiera entiteterna `Product` och `Category`. Genom att associera dessa två entiteter kan hämta en klient information om alla produkter i en kategori med en enskild begäran till webbtjänsten.

Ett exempel som visar hur du skapar kopplingar mellan entiteter kan ladda ned [Association exempel](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Skapa kopplingen i schemat resursfil

Följande MOF definierar två entiteter. Vi skapar en association mellan dem.

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

Den `Category` klassen definierar en egenskap som är en matris med namnen på de produkter som tillhör den kategorin.

Om du vill associera två entiteter, måste du definiera en klass med den `Association` attribut i resursen schemat MOF-filen för tjänsten. Klassen måste definiera två entiteter som är associerade, kallas `ends` av kopplingen. I följande exempel visas en definition av en klass som definierar en association mellan entiteter kategori och produkter.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Du måste också ändra deklaration av produkter-egenskap i klassen kategori. Du använder den `AssociationClass` nyckelord att ange att egenskapen är ena änden av kopplingen. Egenskapen måste också definieras som en referens till en separat entitet i stället för en matris med strängar. Du kan göra detta med hjälp av den `ref` nyckelord. I följande exempel visar egenskapen definitionen för kopplingen.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Slutligen måste du deklarera den andra änden av kopplingen genom att lägga till en egenskapsdefinition till den `Product` klass. Det här är en referens till antingen en matris eller till en enda entitet. Förutsatt att varje produkt tillhör endast en kategori, är definitionen på följande sätt.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

De egenskaper som representerar två ändar av associationen kallas navigeringsegenskaper.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Steg för att associera entiteter i schemat resursfil

- Definiera associationen som en klass genom att använda den `Association` nyckelord.

- Definiera ändar av kopplingen genom att använda nyckelordet Associeringsklass måste anges för programmets egenskaper för associerade entiteter.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Skapa kopplingen i resursen mappning XML-fil

Det finns tre olika fall att tänka på när du mappar en koppling i resursen mappning XML-fil.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Bestämma hur du associerar entiteter i mappningsfilen resurs

- Om navigeringsegenskapen finns i den underliggande. .NET framework-typ och den egenskapen innehåller främmande nycklar krävs ingen explicit mappning.

- Om navigeringsegenskapen inte finns i den underliggande typen för .NET Framework, måste du ange en cmdlet som hämtar listan över nycklarna för de kopplade instanserna. Du gör detta genom att lägga till en `Association` element kapslat under den `CmdletImplementation` elementet efter de element som definierar den `cmdlets` för andra CRUD-kommandon.

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- Om navigeringsegenskapen finns i den underliggande typen för .NET Framework, men den innehåller objektinstanser i stället för sekundärnycklar så måste du skapa en cmdlet (genom att skriva en Windows PowerShell-funktion eller ett skript) att hämta sekundärnycklar. Du anger sedan cmdleten i mappningsfilen resurs. Skript för att hämta nycklarna skulle se ut så här.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  Och XML-koden i mappningsfilen resursen skulle se ut så här.

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- Förutom att ange en cmdlet för att hämta associerade entiteter kan ange du även cmdletar för att lägga till och ta bort referenser från samlingen. Följande exempel förutsätter att cmdlet: Lägg till ProductToCategory och ta bort ProductFromCategory finns (de kan också definieras i skript eller funktioner som i föregående exempel).

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a>Fråga associerade entiteter

Klienten kan hämta en lista över de instanser som är associerade med en entitet genom att skapa specifika frågor.

#### <a name="constructing-queries-for-associated-entities"></a>Konstruera frågor för associerade entiteter

- En klient kan begära information om en kategori utan att hämta dess relaterade produkter. Till exempel följande begäran hämtar information om den `food` kategori.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Att hämta associerade produkter i kategorin (men inte information om kategorin, klienten anger navigeringsegenskapen i begäran.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Använd för att hämta endast URL: er av produkter, den `$links` kvalificerare i begäran.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- Klienten kan få både kategori-information och dess tillhörande produkter med hjälp av den `$expand` kvalificerare.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Se även

[Skapa en webbtjänst för Management OData IIS-tillägget](./creating-a-management-odata-web-service.md)