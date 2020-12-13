---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa ett konsolgränssnitt
description: Skapa ett konsolgränssnitt
ms.openlocfilehash: 9ea67c43b1ee35b1fbfc553b22a1423419317ca2
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657220"
---
# <a name="how-to-create-a-console-shell"></a>Skapa ett konsolgränssnitt

Windows PowerShell innehåller ett Make-Shell verktyg, även kallat "make-kit", som används för att skapa ett konsol gränssnitt som inte är utöknings Bart. Gränssnitt som skapats med det här nya verktyget kan inte utökas senare via en Windows PowerShell-snapin-modul.

## <a name="syntax"></a>Syntax

Här är den syntax som används för att köra Make-Shell inifrån en-fil.

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

## <a name="parameters"></a>Parameters (Parametrar)

Här är en kort beskrivning av parametrarna för märke-Shell.

> [!CAUTION]
> UNC-sökvägar till sammansättningar stöds inte av skapa-gränssnitt.

|Parameter|Beskrivning|
|---------------|-----------------|
|n.exe|Krävs. Namnet på det gränssnitt som ska skapas. Sökvägen anges som en del av den här parametern.<br /><br /> Med-Shell läggs ". exe" till i det här värdet om det inte anges. **Varning:**  Skapa inte en utdatafil med samma namn som den refererade DLL-filen. Om du gör det skapar Make-Shell-verktyget en. CS-fil med samma namn, vilket skriver över. cs-filen som innehåller käll koden för cmdleten.|
|-namnrymd ns|Krävs. Namn området som ska användas för den härledda [system. Management. Automation. körnings utrymmen. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) -klassen som gör-satsen genererar och kompilerar.|
|-lib-libdirectory1 [, libdirectory2,..]|De kataloger som genomsöks för .NET-sammansättningar, inklusive Windows PowerShell-sammansättningar, sammansättningar som anges av `reference` parametern, sammansättningar som indirekt refereras till av en annan sammansättning och .net-systemets sammansättningar.|
|-referens ca1.dll [, ca2.dll,...]|En kommaavgränsad lista över de sammansättningar som ska ingå i gränssnittet. Dessa sammansättningar innehåller alla cmdlet-och Provider-sammansättningar, samt resurs sammansättningar som ska läsas in. Om den här parametern inte anges skapas ett gränssnitt som bara innehåller de kärn-cmdlets och providers som tillhandahålls av Windows PowerShell.<br /><br /> Sammansättningarna kan anges med hjälp av sin fullständiga sökväg, annars söks de igenom med den sökväg som anges av `lib` parametern.|
|-formatdata fd1.format.ps1XML [, fd2.format.ps1XML,...]|En kommaavgränsad lista med format data som ska tas med i gränssnittet. Om den här parametern inte anges skapas ett gränssnitt som bara innehåller de format data som tillhandahålls av Windows PowerShell.|
|-typedata td1.type.ps1XML [, td2.type.ps1XML,...]|En kommaavgränsad lista med typ data som ska tas med i gränssnittet. Om den här parametern inte anges skapas ett gränssnitt som bara innehåller de typ data som tillhandahålls av Windows PowerShell.|
|-source c1.cs [, c2.cs,...]|Namnet på en fil, som tillhandahålls av Shell-utvecklaren, som innehåller alla käll koder som krävs för att bygga gränssnittet.<br /><br /> Käll kods filen kan innehålla någon av följande käll koder:<br /><br /> – Den Auktoriseringshanteraren-implementering som åsidosätter standard hanteraren för Auktoriseringshanteraren. (Detta kan också anges kompileras till en sammansättning.)<br />– Assembly information Attribute-deklarationer: till exempel AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute och AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|Den typ som innehåller implementeringen av Auktoriseringshanteraren. Detta kan definieras i käll koden eller kompileras till en sammansättning (anges av `reference` parametern). Om den här parametern inte anges används standard säkerhets hanteraren. Värdet ska vara ett fullständigt typnamn, inklusive namn områden.|
|-win32icon i. ico|Ikonen för. exe-filen för gränssnittet. Om detta inte anges kommer gränssnittet att ha den ikon som c#-kompilatorn inkluderar (om det finns några).|
|– initscript p.ps1|Start profilen för gränssnittet. Filen ingår "i befintligt skick"; ingen giltighets kontroll utförs med ett märke.|
|-builtinscript s1.ps1 [, s2.ps1,...]|En lista med inbyggda skript för gränssnittet. Dessa skript identifieras före skript i sökvägen och deras innehåll kan inte ändras när gränssnittet har skapats.<br /><br /> Filerna ingår "i befintligt skick"; ingen giltighets kontroll utförs med ett märke.|
|– resurs resourcefile.txt|Txt-filen som innehåller hjälp-och informations resurser för gränssnittet. Den första resursen heter ShellHelp och innehåller den text som visas om gränssnittet anropas med `help` parametern. Den andra resursen heter ShellBanner och innehåller texten och copyrightinformation som visas när gränssnittet startas i interaktivt läge.<br /><br /> Om den här parametern inte anges eller om dessa resurser inte finns, används en generisk hjälp och banderoll.|
|-cscflags cscFlags|Flaggor som ska skickas till C#-kompilatorn (csc.exe). Dessa skickas genom oförändrade. Om den här parametern innehåller blank steg ska den omges av dubbla citat tecken.|
|-?<br /><br /> – hjälp|Visar Copyright-meddelandet och Make-Shell kommando rads alternativ.|
|– utförlig|Visar detaljerad information medan gränssnittet skapas.|

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
