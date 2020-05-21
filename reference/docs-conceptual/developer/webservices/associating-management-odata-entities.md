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
ms.openlocfilehash: 4849735bf412497f5590b109c67760b6a197cb2b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561741"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="6acb9-102">Associera Management OData-entiteter</span><span class="sxs-lookup"><span data-stu-id="6acb9-102">Associating Management OData Entities</span></span>

<span data-ttu-id="6acb9-103">Det är ofta användbart att skapa en association mellan två olika hanterings-OData-entiteter.</span><span class="sxs-lookup"><span data-stu-id="6acb9-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="6acb9-104">En hantering av OData-tjänster kan till exempel ha entiteter som hanterar en katalog med produkter som är ordnade i kategorier och definierar entiteterna `Product` och `Category` .</span><span class="sxs-lookup"><span data-stu-id="6acb9-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="6acb9-105">Genom att associera dessa två entiteter kan en klient hämta information om alla produkter i en kategori med en enskild begäran till webb tjänsten.</span><span class="sxs-lookup"><span data-stu-id="6acb9-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="6acb9-106">Ett exempel som visar hur du skapar kopplingar mellan entiteter kan hämtas i [associerings exemplet](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="6acb9-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="6acb9-107">Skapa associationen i resurs schema filen</span><span class="sxs-lookup"><span data-stu-id="6acb9-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="6acb9-108">Följande MOF definierar två entiteter.</span><span class="sxs-lookup"><span data-stu-id="6acb9-108">The following MOF defines two entities.</span></span> <span data-ttu-id="6acb9-109">Vi kommer att skapa en koppling mellan dem.</span><span class="sxs-lookup"><span data-stu-id="6acb9-109">We will create an association between them.</span></span>

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

<span data-ttu-id="6acb9-110">`Category`Klassen definierar en egenskap som är en matris med namnen på de produkter som tillhör den kategorin.</span><span class="sxs-lookup"><span data-stu-id="6acb9-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="6acb9-111">För att associera två entiteter måste du definiera en klass med `Association` attributet i MOF-filen för resurs scheman för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="6acb9-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="6acb9-112">Klassen måste definiera de två entiteter som ska associeras, anropas `ends` för associationen.</span><span class="sxs-lookup"><span data-stu-id="6acb9-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="6acb9-113">I följande exempel visas en definition av en klass som definierar en association mellan kategori-och produkt enheterna.</span><span class="sxs-lookup"><span data-stu-id="6acb9-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="6acb9-114">Du måste också ändra deklarationen för egenskapen Products i klassen Category.</span><span class="sxs-lookup"><span data-stu-id="6acb9-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="6acb9-115">Du kan använda `AssociationClass` nyckelordet för att ange att egenskapen är en ände av associationen.</span><span class="sxs-lookup"><span data-stu-id="6acb9-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="6acb9-116">Egenskapen måste också definieras som en referens till en separat entitet, snarare än en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="6acb9-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="6acb9-117">Du gör detta med hjälp av `ref` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="6acb9-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="6acb9-118">I följande exempel visas egenskaps definitionen för associationen.</span><span class="sxs-lookup"><span data-stu-id="6acb9-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="6acb9-119">Slutligen måste du deklarera den andra änden av associationen genom att lägga till en egenskaps definition i `Product` klassen.</span><span class="sxs-lookup"><span data-stu-id="6acb9-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="6acb9-120">Detta är en referens till antingen en matris eller en enskild entitet.</span><span class="sxs-lookup"><span data-stu-id="6acb9-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="6acb9-121">Om du antar att varje produkt endast tillhör en kategori skulle definitionen vara följande.</span><span class="sxs-lookup"><span data-stu-id="6acb9-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="6acb9-122">Egenskaperna som representerar kopplingens två ändar kallas för navigerings egenskaper.</span><span class="sxs-lookup"><span data-stu-id="6acb9-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="6acb9-123">Steg för att associera entiteter i resurs schema filen</span><span class="sxs-lookup"><span data-stu-id="6acb9-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="6acb9-124">Definiera associationen som en klass med hjälp av `Association` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="6acb9-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="6acb9-125">Definiera slutet av associationen genom att använda nyckelordet AssociationClass för att kvalificera egenskaperna för de associerade entiteterna.</span><span class="sxs-lookup"><span data-stu-id="6acb9-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="6acb9-126">Skapa associationen i XML-filen för resurs mappning</span><span class="sxs-lookup"><span data-stu-id="6acb9-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="6acb9-127">Det finns tre olika fall att tänka på när du mappar en Association i XML-filen för resurs mappning.</span><span class="sxs-lookup"><span data-stu-id="6acb9-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="6acb9-128">Bestämma hur du vill associera entiteter i resurs mappnings filen</span><span class="sxs-lookup"><span data-stu-id="6acb9-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="6acb9-129">Om navigerings egenskapen finns i den underliggande.</span><span class="sxs-lookup"><span data-stu-id="6acb9-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="6acb9-130">.NET Framework typ och egenskapen innehåller sekundär nycklar, krävs ingen explicit mappning.</span><span class="sxs-lookup"><span data-stu-id="6acb9-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="6acb9-131">Om navigerings egenskapen inte finns i den underliggande .NET Framework typen, måste du ange en cmdlet som hämtar listan över nycklar för de associerade instanserna.</span><span class="sxs-lookup"><span data-stu-id="6acb9-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="6acb9-132">Du gör detta genom att lägga till ett `Association` element som är kapslat under `CmdletImplementation` elementet, efter de element som definierar `cmdlets` för de andra CRUD-kommandona.</span><span class="sxs-lookup"><span data-stu-id="6acb9-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

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

- <span data-ttu-id="6acb9-133">Om navigerings egenskapen finns i den underliggande .NET Framework typen, men den innehåller objekt instanser i stället för externa nycklar, måste du skapa en cmdlet (genom att skriva en Windows PowerShell-funktion eller ett skript) för att hämta sekundär nycklarna.</span><span class="sxs-lookup"><span data-stu-id="6acb9-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="6acb9-134">Sedan anger du denna cmdlet i resurs mappnings filen.</span><span class="sxs-lookup"><span data-stu-id="6acb9-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="6acb9-135">Skriptet för att hämta nycklarna skulle till exempel se ut så här.</span><span class="sxs-lookup"><span data-stu-id="6acb9-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="6acb9-136">XML-koden i resurs mappnings filen ser ut ungefär så här.</span><span class="sxs-lookup"><span data-stu-id="6acb9-136">And the XML in the resource mapping file would look like the following.</span></span>

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

- <span data-ttu-id="6acb9-137">Förutom att ange en cmdlet för att hämta associerade entiteter kan du också ange cmdlets för att lägga till och ta bort referenser från samlingen.</span><span class="sxs-lookup"><span data-stu-id="6acb9-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="6acb9-138">I följande exempel förutsätts att cmdletarna Add-ProductToCategory och Remove-ProductFromCategory finns (de kan också definieras i ett skript eller en funktion som i föregående exempel).</span><span class="sxs-lookup"><span data-stu-id="6acb9-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

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

## <a name="querying-associated-entities"></a><span data-ttu-id="6acb9-139">Frågar efter associerade entiteter</span><span class="sxs-lookup"><span data-stu-id="6acb9-139">Querying associated entities</span></span>

<span data-ttu-id="6acb9-140">Klienten kan hämta en lista över instanser som är associerade med en entitet genom att skapa vissa frågor.</span><span class="sxs-lookup"><span data-stu-id="6acb9-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="6acb9-141">Skapa frågor för associerade entiteter</span><span class="sxs-lookup"><span data-stu-id="6acb9-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="6acb9-142">En klient kan begära information om en kategori utan att hämta tillhör ande produkter.</span><span class="sxs-lookup"><span data-stu-id="6acb9-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="6acb9-143">Följande förfrågan hämtar till exempel information om `food` kategorin.</span><span class="sxs-lookup"><span data-stu-id="6acb9-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="6acb9-144">För att hämta de associerade produkterna i kategorin (men inte information om själva kategorin, anger klienten navigerings egenskapen i begäran.</span><span class="sxs-lookup"><span data-stu-id="6acb9-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="6acb9-145">Om du bara vill hämta URL: er för produkterna använder du `$links` kvalificeraren i begäran.</span><span class="sxs-lookup"><span data-stu-id="6acb9-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="6acb9-146">Klienten kan hämta både kategori information och tillhör ande produkter genom att använda `$expand` kvalificeraren.</span><span class="sxs-lookup"><span data-stu-id="6acb9-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="6acb9-147">Se även</span><span class="sxs-lookup"><span data-stu-id="6acb9-147">See Also</span></span>

[<span data-ttu-id="6acb9-148">Skapa en webb tjänst för OData IIS-tillägg för hantering</span><span class="sxs-lookup"><span data-stu-id="6acb9-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)
