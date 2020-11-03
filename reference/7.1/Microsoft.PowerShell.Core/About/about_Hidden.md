---
description: Beskriver det dolda nyckelordet, som döljer klass medlemmar från standard Get-Member resultat.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hidden?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hidden
ms.openlocfilehash: 7a8646f1b88da9b42ef26ccdf1d27eaa7042abd7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270194"
---
# <a name="about_hidden"></a>about_Hidden

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver det dolda nyckelordet, som döljer klass medlemmar från standard Get-Member resultat.

## <a name="long-description"></a>LÅNG BESKRIVNING

När du använder det dolda nyckelordet i ett skript döljer du medlemmar i en klass som standard. Det dolda nyckelordet kan dölja egenskaper, metoder (inklusive konstruktorer, händelser, alias egenskaper och andra medlems typer, inklusive statiska medlemmar, från standard resultaten av Get-Member-cmdleten och från IntelliSense-och TABB-slutförande-resultat. Om du vill visa medlemmar som du har dolt med nyckelordet dold lägger du till parametern-Force i ett Get-Member-kommando.

Dolda medlemmar visas inte med hjälp av tabb-slutförande eller IntelliSense, om inte slut för ande sker i den klass som definierar den dolda medlemmen.

Ett nytt attribut, system. Management. Automation. HiddenAttribute, har lagts till, så att C- \# koden kan ha samma semantik i PowerShell.

Nyckelordet Hidden är användbart för att skapa egenskaper och metoder i en klass som du inte nödvändigt vis vill att andra användare av klassen ska kunna se eller redigera.

Nyckelordet dold har ingen påverkan på hur du kan visa eller ändra medlemmar i en klass. Precis som alla språk nyckelord i PowerShell är dolt inte Skift läges känsligt och dolda medlemmar är fortfarande offentliga.

Dolt, tillsammans med anpassade klasser, introducerades i PowerShell 5,0.

## <a name="example"></a>EXEMPEL

I följande exempel visas hur du använder det dolda nyckelordet i en klass definition. Klass metoden för bilen, enheten har en egenskap, inga ändringar, som inte behöver visas eller ändras (det är bara antalet gånger som enheten anropas i klassen Car, ett mått som inte är viktigt för användare av klassen, till exempel när du köper en bil, så fråga inte säljaren om hur många enheter bilen har tagits.

Eftersom det är lite behov av användare av klassen att ändra den här egenskapen kan vi dölja egenskapen från Get-Member och automatiska kompletterings resultat med hjälp av nyckelordet Hidden.

Lägg till det dolda nyckelordet genom att ange det på samma instruktions rad som egenskapen och dess datatyp. Även om nyckelordet kan vara i vilken ordning som helst på den här raden, blir det enklare för dig att identifiera alla medlemmar som du har dolt när du startar instruktionen med det dolda nyckelordet.

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

Skapa nu en ny instans av klassen Car och spara den i en variabel, \$ TestCar.

```powershell
$TestCar = [Car]::new()
```

När du har skapat den nya instansen tar du med innehållet i variabeln $TestCar för att få medlem. Observera att egenskapen Overrides inte är bland de medlemmar som anges i Get-Member kommando resultat.

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

Prova nu att köra Get-Member igen, men Lägg till parametern-Force i den här tiden.
Observera att resultaten innehåller egenskapen Hidden-åsidosättningar bland andra medlemmar som är dolda som standard.

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

## <a name="see-also"></a>SE ÄVEN

[about_Classes](about_Classes.md)

[about_Language_Keywords](about_Language_Keywords.md)

[about_Wildcards](about_Wildcards.md)

[Hämta medlem](xref:Microsoft.PowerShell.Utility.Get-Member)

