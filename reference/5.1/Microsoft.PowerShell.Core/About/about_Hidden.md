---
description: Beskriver det dolda nyckelordet, som döljer klass medlemmar från standard Get-Member resultat.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hidden?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hidden
ms.openlocfilehash: 641ebdc942186db90a23f4c784a0f1b3c295cae9
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273249"
---
# <a name="about_hidden"></a><span data-ttu-id="2f790-104">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="2f790-104">about_Hidden</span></span>

## <a name="short-description"></a><span data-ttu-id="2f790-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2f790-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2f790-106">Beskriver det dolda nyckelordet, som döljer klass medlemmar från standard Get-Member resultat.</span><span class="sxs-lookup"><span data-stu-id="2f790-106">Describes the Hidden keyword, which hides class members from default Get-Member results.</span></span>

## <a name="long-description"></a><span data-ttu-id="2f790-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2f790-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="2f790-108">När du använder det dolda nyckelordet i ett skript döljer du medlemmar i en klass som standard.</span><span class="sxs-lookup"><span data-stu-id="2f790-108">When you use the Hidden keyword in a script, you hide the members of a class by default.</span></span> <span data-ttu-id="2f790-109">Det dolda nyckelordet kan dölja egenskaper, metoder (inklusive konstruktorer, händelser, alias egenskaper och andra medlems typer, inklusive statiska medlemmar, från standard resultaten av Get-Member-cmdleten och från IntelliSense-och TABB-slutförande-resultat.</span><span class="sxs-lookup"><span data-stu-id="2f790-109">The Hidden keyword can hide properties, methods (including constructors, events, alias properties, and other member types, including static members, from the default results of the Get-Member cmdlet, and from IntelliSense and tab completion results.</span></span> <span data-ttu-id="2f790-110">Om du vill visa medlemmar som du har dolt med nyckelordet dold lägger du till parametern-Force i ett Get-Member-kommando.</span><span class="sxs-lookup"><span data-stu-id="2f790-110">To display members that you have hidden with the Hidden keyword, add the -Force parameter to a Get-Member command.</span></span>

<span data-ttu-id="2f790-111">Dolda medlemmar visas inte med hjälp av tabb-slutförande eller IntelliSense, om inte slut för ande sker i den klass som definierar den dolda medlemmen.</span><span class="sxs-lookup"><span data-stu-id="2f790-111">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="2f790-112">Ett nytt attribut, system. Management. Automation. HiddenAttribute, har lagts till, så att C- \# koden kan ha samma semantik i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f790-112">A new attribute, System.Management.Automation.HiddenAttribute, has been added, so that C\# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="2f790-113">Nyckelordet Hidden är användbart för att skapa egenskaper och metoder i en klass som du inte nödvändigt vis vill att andra användare av klassen ska kunna se eller redigera.</span><span class="sxs-lookup"><span data-stu-id="2f790-113">The Hidden keyword is useful for creating properties and methods within a class that you do not necessarily want other users of the class to see, or readily be able to edit.</span></span>

<span data-ttu-id="2f790-114">Nyckelordet dold har ingen påverkan på hur du kan visa eller ändra medlemmar i en klass.</span><span class="sxs-lookup"><span data-stu-id="2f790-114">The Hidden keyword has no effect on how you can view or make changes to members of a class.</span></span> <span data-ttu-id="2f790-115">Precis som alla språk nyckelord i PowerShell är dolt inte Skift läges känsligt och dolda medlemmar är fortfarande offentliga.</span><span class="sxs-lookup"><span data-stu-id="2f790-115">Like all language keywords in PowerShell, Hidden is not case-sensitive, and hidden members are still public.</span></span>

<span data-ttu-id="2f790-116">Dolt, tillsammans med anpassade klasser, introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="2f790-116">Hidden, along with custom classes, was introduced in PowerShell 5.0.</span></span>

## <a name="example"></a><span data-ttu-id="2f790-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2f790-117">EXAMPLE</span></span>

<span data-ttu-id="2f790-118">I följande exempel visas hur du använder det dolda nyckelordet i en klass definition.</span><span class="sxs-lookup"><span data-stu-id="2f790-118">The following example shows how to use the Hidden keyword in a class definition.</span></span> <span data-ttu-id="2f790-119">Klass metoden för bilen, enheten har en egenskap, inga ändringar, som inte behöver visas eller ändras (det är bara antalet gånger som enheten anropas i klassen Car, ett mått som inte är viktigt för användare av klassen, till exempel när du köper en bil, så fråga inte säljaren om hur många enheter bilen har tagits.</span><span class="sxs-lookup"><span data-stu-id="2f790-119">The Car class method, Drive, has a property, rides, that does not need to be viewed or changed (it merely tallies the number of times that Drive is called on the Car class, a metric that is not important to users of the class; consider, for example, that when you are buying a car, you do not ask the seller on how many drives the car has been taken.</span></span>

<span data-ttu-id="2f790-120">Eftersom det är lite behov av användare av klassen att ändra den här egenskapen kan vi dölja egenskapen från Get-Member och automatiska kompletterings resultat med hjälp av nyckelordet Hidden.</span><span class="sxs-lookup"><span data-stu-id="2f790-120">Because there is little need for users of the class to change this property, we can hide the property from Get-Member and automatic completion results by using the Hidden keyword.</span></span>

<span data-ttu-id="2f790-121">Lägg till det dolda nyckelordet genom att ange det på samma instruktions rad som egenskapen och dess datatyp.</span><span class="sxs-lookup"><span data-stu-id="2f790-121">Add the Hidden keyword by entering it on the same statement line as the property and its data type.</span></span> <span data-ttu-id="2f790-122">Även om nyckelordet kan vara i vilken ordning som helst på den här raden, blir det enklare för dig att identifiera alla medlemmar som du har dolt när du startar instruktionen med det dolda nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="2f790-122">Although the keyword can be in any order on this line, starting the statement with the Hidden keyword makes it easier for you later to identify all members that you have hidden.</span></span>

```powershell
class Car
{
   # Properties
   [String] $Color
   [String] $ModelYear
   [int] $Distance

   # Method
   [int] Drive ([int]$miles)
   {
      $this.Distance += $miles
      $this.rides++
      return $this.Distance
   }

   # Hidden property of the Drive method
    hidden [int] $rides = 0
}
```

<span data-ttu-id="2f790-123">Skapa nu en ny instans av klassen Car och spara den i en variabel, \$ TestCar.</span><span class="sxs-lookup"><span data-stu-id="2f790-123">Now, create a new instance of the Car class, and save it in a variable, \$TestCar.</span></span>

```powershell
$TestCar = [Car]::new()
```

<span data-ttu-id="2f790-124">När du har skapat den nya instansen tar du med innehållet i variabeln $TestCar för att få medlem.</span><span class="sxs-lookup"><span data-stu-id="2f790-124">After you create the new instance, pipe the contents of the $TestCar variable to Get-Member.</span></span> <span data-ttu-id="2f790-125">Observera att egenskapen Overrides inte är bland de medlemmar som anges i Get-Member kommando resultat.</span><span class="sxs-lookup"><span data-stu-id="2f790-125">Observe that the rides property is not among the members listed in the Get-Member command results.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member

   TypeName: Car

Name        MemberType Definition
----        ---------- ----------
Drive       Method     int Drive(int miles)
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
ToString    Method     string ToString()
Color       Property   string Color {get;set;}
Distance    Property   int Distance {get;set;}
ModelYear   Property   string ModelYear {get;set;}

```

<span data-ttu-id="2f790-126">Prova nu att köra Get-Member igen, men Lägg till parametern-Force i den här tiden.</span><span class="sxs-lookup"><span data-stu-id="2f790-126">Now, try running Get-Member again, but this time, add the -Force parameter.</span></span>
<span data-ttu-id="2f790-127">Observera att resultaten innehåller egenskapen Hidden-åsidosättningar bland andra medlemmar som är dolda som standard.</span><span class="sxs-lookup"><span data-stu-id="2f790-127">Note that the results contain the hidden rides property, among other members that are hidden by default.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member -Force

   TypeName: Car

Name          MemberType   Definition
----          ----------   ----------
pstypenames   CodeProperty System.Collections.ObjectModel.Collection`1
psadapted     MemberSet    psadapted {Color, ModelYear, Distance,
psbase        MemberSet    psbase {Color, ModelYear, Distance,...
psextended    MemberSet    psextended {}
psobject      MemberSet    psobject {BaseObject, Members,...
Drive         Method       int Drive(int miles)
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
get_Color     Method       string get_Color()
get_Distance  Method       int get_Distance()
get_ModelYear Method       string get_ModelYear()
get_rides     Method       int get_rides()
set_Color     Method       void set_Color(string )
set_Distance  Method       void set_Distance(int )
set_ModelYear Method       void set_ModelYear(string )
set_rides     Method       void set_rides(int )
ToString      Method       string ToString()
Color         Property     string Color {get;set;}
Distance      Property     int Distance {get;set;}
ModelYear     Property     string ModelYear {get;set;}
rides         Property     int rides {get;set;}

```

## <a name="see-also"></a><span data-ttu-id="2f790-128">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="2f790-128">SEE ALSO</span></span>

[<span data-ttu-id="2f790-129">about_Classes</span><span class="sxs-lookup"><span data-stu-id="2f790-129">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="2f790-130">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="2f790-130">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="2f790-131">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="2f790-131">about_Wildcards</span></span>](about_Wildcards.md)

[<span data-ttu-id="2f790-132">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="2f790-132">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
