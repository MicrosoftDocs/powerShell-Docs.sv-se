---
title: Så här skapar du en konsolen Shell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845061"
---
# <a name="how-to-create-a-console-shell"></a>Skapa ett konsolgränssnitt

Windows PowerShell ger ett Kontrollera-Shell-verktyg, kallas även i ”Kontrollera-kit”, som används för att skapa ett gränssnitt i konsolen som inte kan utökas. Gränssnitt som skapats med den här nya verktyget kan inte utökas senare via en Windows PowerShell-snapin-modul.

## <a name="syntax"></a>Syntax

Här är den syntax som används för att köra Kontrollera-Shell från inom en gör-fil.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Parametrar

Här är en kort beskrivning av parametrarna för Kontrollera-Shell.

> [!CAUTION]
> UNC-sökvägar till sammansättningar stöds inte av Kontrollera Shell.

|Parameter|Beskrivning|
|---------------|-----------------|
|-ut n.exe|Obligatoriskt. Namnet på gränssnittet för att producera. Sökvägen har angetts som en del av den här parametern.<br /><br /> Kontrollera-shell läggs ”.exe” till det här värdet om det inte har angetts. **Varning:**  Skapa inte en utdatafil med samma namn som refererade DLL-filen. Om du försöker utföra detta skapar verktyget gör-Shell en .cs-fil med samma namn som skrivs .cs-fil med källkoden cmdlet.|
|-namespace ns|Obligatoriskt. Namnområdet som ska användas för den härledda [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) klass som gör-kit genererar och kompilerar.|
|-lib libdirectory1 [, libdirectory2,...]|De kataloger som genomsöks för .NET-sammansättningar, inklusive Windows PowerShell-sammansättningar, sammansättningar som anges av den `reference` parametern, sammansättningar indirekt refereras till av en annan sammansättning och .NET system-sammansättningar.|
|-referera ca1.dll[,ca2.dll,...]|En kommaavgränsad lista över sammansättningar ska ingå i gränssnittet. Dessa sammansättningar innehåller alla cmdlet och providern sammansättningar samt resource sammansättningar som ska läsas. Om den här parametern inte anges, sedan skapas ett gränssnitt som innehåller endast core-cmdlets och providers som tillhandahålls av Windows PowerShell.<br /><br /> Sammansättningarna kan anges med hjälp av deras fullständiga sökväg, annars de söks igenom för att använda sökvägen som angetts av den `lib` parametern.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|En kommaavgränsad lista över Formatdata som ska ingå i gränssnittet. Om den här parametern inte anges, sedan skapas ett gränssnitt med endast de Formatdata som tillhandahålls av Windows PowerShell.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|En kommaavgränsad lista över typ av data som ska ingå i gränssnittet. Om den här parametern inte anges, sedan skapas ett gränssnitt som innehåller bara den typ av data som tillhandahålls av Windows PowerShell.|
|-källa c1.cs [, c2.cs,...]|Namnet på en fil som tillhandahålls av utvecklaren shell, som innehåller källkod som behövs för att skapa gränssnittet.<br /><br /> Källkodsfilen kan innehålla något av följande källkoden:<br /><br /> -Auktorisering manager implementeringen som åsidosätter standard Auktoriseringshanteraren. (Detta kan också anges i en sammansättning.)<br />-Sammansättningen information attributet deklarationer: till exempel AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, och AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|Typen som innehåller auktorisering manager implementering. Det kan definieras i källkoden eller kompileras till en sammansättning (anges av den `reference` parametern). Om den här parametern inte anges används standard-säkerhetshanteraren. Värdet bör vara det fullständiga namnet, inklusive namnområden.|
|-win32icon i.ico|Ikon för .exe-fil för gränssnittet. Om inte anges kommer gränssnittet har ikon med c#-kompilatorn (om sådan finns).|
|-initscript p.ps1|Startprofil för gränssnittet. Filen ingår ”som – är”; Ingen kontroll av giltigheten görs genom att kontrollera-Shell.|
|-builtinscript s1.ps1[,s2.ps1,...]|En lista över inbyggda skript innan Windows-gränssnittet. Dessa skript identifieras innan skript i sökvägen och deras innehåll kan inte ändras när du har skapat i gränssnittet.<br /><br /> Filerna är inkluderade ”som – är”; Ingen kontroll av giltigheten görs genom att kontrollera-Shell.|
|-resurs resourcefile.txt|Txt-fil som innehåller hjälp och banderoll resurser för gränssnittet. Den första resursen heter ShellHelp och innehåller den text som visas om gränssnittet anropas med den `help` parametern. Den andra resursen heter ShellBanner och den innehåller text och copyrightinformation som visas när gränssnittet har startats i interaktivt läge.<br /><br /> Om den här parametern inte anges, eller finns inte dessa resurser, används en allmän hjälp och popup-meddelandet.|
|-cscflags cscFlags|Flaggor som ska skickas till den C# kompilatorn (csc.exe). Dessa skickas via oförändrade. Om den här parametern innehåller blanksteg, bör det omges i dubbla citattecken.|
|-?<br /><br /> -hjälp|Visar meddelandet om upphovsrätt och kontrollera-Shell kommandoradsalternativ.|
|-verbose|Visar detaljerad information medan gränssnittet skapas.|

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)