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
# <a name="associating-management-odata-entities"></a><span data-ttu-id="ff7f3-102">Associera Management OData-entiteter</span><span class="sxs-lookup"><span data-stu-id="ff7f3-102">Associating Management OData Entities</span></span>

<span data-ttu-id="ff7f3-103">Ofta är det praktiskt att skapa en koppling mellan två olika Management OData-entiteter.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="ff7f3-104">Exempelvis en Management OData-tjänst kan ha entiteter som hanterar en förteckning över produkter som är uppdelade i kategorier och definiera entiteterna `Product` och `Category`.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="ff7f3-105">Genom att associera dessa två entiteter kan hämta en klient information om alla produkter i en kategori med en enskild begäran till webbtjänsten.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="ff7f3-106">Ett exempel som visar hur du skapar kopplingar mellan entiteter kan ladda ned [Association exempel](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="ff7f3-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="ff7f3-107">Skapa kopplingen i schemat resursfil</span><span class="sxs-lookup"><span data-stu-id="ff7f3-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="ff7f3-108">Följande MOF definierar två entiteter.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-108">The following MOF defines two entities.</span></span> <span data-ttu-id="ff7f3-109">Vi skapar en association mellan dem.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-109">We will create an association between them.</span></span>

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

<span data-ttu-id="ff7f3-110">Den `Category` klassen definierar en egenskap som är en matris med namnen på de produkter som tillhör den kategorin.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="ff7f3-111">Om du vill associera två entiteter, måste du definiera en klass med den `Association` attribut i resursen schemat MOF-filen för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="ff7f3-112">Klassen måste definiera två entiteter som är associerade, kallas `ends` av kopplingen.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="ff7f3-113">I följande exempel visas en definition av en klass som definierar en association mellan entiteter kategori och produkter.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="ff7f3-114">Du måste också ändra deklaration av produkter-egenskap i klassen kategori.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="ff7f3-115">Du använder den `AssociationClass` nyckelord att ange att egenskapen är ena änden av kopplingen.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="ff7f3-116">Egenskapen måste också definieras som en referens till en separat entitet i stället för en matris med strängar.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="ff7f3-117">Du kan göra detta med hjälp av den `ref` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="ff7f3-118">I följande exempel visar egenskapen definitionen för kopplingen.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="ff7f3-119">Slutligen måste du deklarera den andra änden av kopplingen genom att lägga till en egenskapsdefinition till den `Product` klass.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="ff7f3-120">Det här är en referens till antingen en matris eller till en enda entitet.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="ff7f3-121">Förutsatt att varje produkt tillhör endast en kategori, är definitionen på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="ff7f3-122">De egenskaper som representerar två ändar av associationen kallas navigeringsegenskaper.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="ff7f3-123">Steg för att associera entiteter i schemat resursfil</span><span class="sxs-lookup"><span data-stu-id="ff7f3-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="ff7f3-124">Definiera associationen som en klass genom att använda den `Association` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="ff7f3-125">Definiera ändar av kopplingen genom att använda nyckelordet Associeringsklass måste anges för programmets egenskaper för associerade entiteter.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="ff7f3-126">Skapa kopplingen i resursen mappning XML-fil</span><span class="sxs-lookup"><span data-stu-id="ff7f3-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="ff7f3-127">Det finns tre olika fall att tänka på när du mappar en koppling i resursen mappning XML-fil.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="ff7f3-128">Bestämma hur du associerar entiteter i mappningsfilen resurs</span><span class="sxs-lookup"><span data-stu-id="ff7f3-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="ff7f3-129">Om navigeringsegenskapen finns i den underliggande.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="ff7f3-130">.NET framework-typ och den egenskapen innehåller främmande nycklar krävs ingen explicit mappning.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="ff7f3-131">Om navigeringsegenskapen inte finns i den underliggande typen för .NET Framework, måste du ange en cmdlet som hämtar listan över nycklarna för de kopplade instanserna.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="ff7f3-132">Du gör detta genom att lägga till en `Association` element kapslat under den `CmdletImplementation` elementet efter de element som definierar den `cmdlets` för andra CRUD-kommandon.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

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

- <span data-ttu-id="ff7f3-133">Om navigeringsegenskapen finns i den underliggande typen för .NET Framework, men den innehåller objektinstanser i stället för sekundärnycklar så måste du skapa en cmdlet (genom att skriva en Windows PowerShell-funktion eller ett skript) att hämta sekundärnycklar.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="ff7f3-134">Du anger sedan cmdleten i mappningsfilen resurs.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="ff7f3-135">Skript för att hämta nycklarna skulle se ut så här.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="ff7f3-136">Och XML-koden i mappningsfilen resursen skulle se ut så här.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-136">And the XML in the resource mapping file would look like the following.</span></span>

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

- <span data-ttu-id="ff7f3-137">Förutom att ange en cmdlet för att hämta associerade entiteter kan ange du även cmdletar för att lägga till och ta bort referenser från samlingen.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="ff7f3-138">Följande exempel förutsätter att cmdlet: Lägg till ProductToCategory och ta bort ProductFromCategory finns (de kan också definieras i skript eller funktioner som i föregående exempel).</span><span class="sxs-lookup"><span data-stu-id="ff7f3-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

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

## <a name="querying-associated-entities"></a><span data-ttu-id="ff7f3-139">Fråga associerade entiteter</span><span class="sxs-lookup"><span data-stu-id="ff7f3-139">Querying associated entities</span></span>

<span data-ttu-id="ff7f3-140">Klienten kan hämta en lista över de instanser som är associerade med en entitet genom att skapa specifika frågor.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="ff7f3-141">Konstruera frågor för associerade entiteter</span><span class="sxs-lookup"><span data-stu-id="ff7f3-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="ff7f3-142">En klient kan begära information om en kategori utan att hämta dess relaterade produkter.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="ff7f3-143">Till exempel följande begäran hämtar information om den `food` kategori.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="ff7f3-144">Att hämta associerade produkter i kategorin (men inte information om kategorin, klienten anger navigeringsegenskapen i begäran.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="ff7f3-145">Använd för att hämta endast URL: er av produkter, den `$links` kvalificerare i begäran.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="ff7f3-146">Klienten kan få både kategori-information och dess tillhörande produkter med hjälp av den `$expand` kvalificerare.</span><span class="sxs-lookup"><span data-stu-id="ff7f3-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="ff7f3-147">Se även</span><span class="sxs-lookup"><span data-stu-id="ff7f3-147">See Also</span></span>

[<span data-ttu-id="ff7f3-148">Skapa en webbtjänst för Management OData IIS-tillägget</span><span class="sxs-lookup"><span data-stu-id="ff7f3-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)