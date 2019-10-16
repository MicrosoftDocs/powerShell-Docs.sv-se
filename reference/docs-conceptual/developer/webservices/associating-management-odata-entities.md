---
title: Associera hantering OData-entiteter | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352285"
---
# <a name="associating-management-odata-entities"></a>Associera Management OData-entiteter

Det är ofta användbart att skapa en association mellan två olika hanterings-OData-entiteter. En hantering av OData-tjänster kan till exempel ha entiteter som hanterar en katalog med produkter som är ordnade i kategorier och definierar entiteterna `Product` och `Category`. Genom att associera dessa två entiteter kan en klient hämta information om alla produkter i en kategori med en enskild begäran till webb tjänsten.

Ett exempel som visar hur du skapar kopplingar mellan entiteter kan hämtas i [associerings exemplet](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Skapa associationen i resurs schema filen

Följande MOF definierar två entiteter. Vi kommer att skapa en koppling mellan dem.

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

Klassen `Category` definierar en egenskap som är en matris med namnen på de produkter som tillhör den kategorin.

För att associera två entiteter måste du definiera en klass med attributet `Association` i MOF-filen för resurs scheman för tjänsten. Klassen måste definiera de två entiteter som ska associeras, så kallade `ends` i associationen. I följande exempel visas en definition av en klass som definierar en association mellan kategori-och produkt enheterna.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Du måste också ändra deklarationen för egenskapen Products i klassen Category. Du använder nyckelordet `AssociationClass` för att ange att egenskapen är en ände av associationen. Egenskapen måste också definieras som en referens till en separat entitet, snarare än en sträng mat ris. Du gör detta med hjälp av nyckelordet `ref`. I följande exempel visas egenskaps definitionen för associationen.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Slutligen måste du deklarera den andra änden av associationen genom att lägga till en egenskaps definition i klassen `Product`. Detta är en referens till antingen en matris eller en enskild entitet. Om du antar att varje produkt endast tillhör en kategori skulle definitionen vara följande.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Egenskaperna som representerar kopplingens två ändar kallas för navigerings egenskaper.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Steg för att associera entiteter i resurs schema filen

- Definiera associationen som en klass med hjälp av nyckelordet `Association`.

- Definiera slutet av associationen genom att använda nyckelordet AssociationClass för att kvalificera egenskaperna för de associerade entiteterna.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Skapa associationen i XML-filen för resurs mappning

Det finns tre olika fall att tänka på när du mappar en Association i XML-filen för resurs mappning.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Bestämma hur du vill associera entiteter i resurs mappnings filen

- Om navigerings egenskapen finns i den underliggande. .NET Framework typ och egenskapen innehåller sekundär nycklar, krävs ingen explicit mappning.

- Om navigerings egenskapen inte finns i den underliggande .NET Framework typen, måste du ange en cmdlet som hämtar listan över nycklar för de associerade instanserna. Du gör detta genom att lägga till ett `Association`-element kapslat under elementet `CmdletImplementation`, och följa de element som definierar `cmdlets` för de andra CRUD-kommandona.

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

- Om navigerings egenskapen finns i den underliggande .NET Framework typen, men den innehåller objekt instanser i stället för externa nycklar, måste du skapa en cmdlet (genom att skriva en Windows PowerShell-funktion eller ett skript) för att hämta sekundär nycklarna. Sedan anger du denna cmdlet i resurs mappnings filen. Skriptet för att hämta nycklarna skulle till exempel se ut så här.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  XML-koden i resurs mappnings filen ser ut ungefär så här.

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

- Förutom att ange en cmdlet för att hämta associerade entiteter kan du också ange cmdlets för att lägga till och ta bort referenser från samlingen. I följande exempel förutsätts att cmdletarna Add-ProductToCategory och Remove-ProductFromCategory finns (de kan också definieras i ett skript eller en funktion som i föregående exempel).

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

## <a name="querying-associated-entities"></a>Frågar efter associerade entiteter

Klienten kan hämta en lista över instanser som är associerade med en entitet genom att skapa vissa frågor.

#### <a name="constructing-queries-for-associated-entities"></a>Skapa frågor för associerade entiteter

- En klient kan begära information om en kategori utan att hämta tillhör ande produkter. Följande förfrågan hämtar till exempel information om kategorin `food`.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  För att hämta de associerade produkterna i kategorin (men inte information om själva kategorin, anger klienten navigerings egenskapen i begäran.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Om du bara vill hämta URL: er för produkterna använder du kvalificeraren `$links` i begäran.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- Klienten kan hämta både kategori information och tillhör ande produkter med hjälp av `$expand`-kvalificeraren.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Se även

[Skapa en webb tjänst för OData IIS-tillägg för hantering](./creating-a-management-odata-web-service.md)