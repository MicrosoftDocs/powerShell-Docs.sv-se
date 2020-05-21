---
title: Så här skapar du ett konsol gränssnitt | Microsoft Docs
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
ms.openlocfilehash: 5ddf312228cb17628400ce8d8a3abbf9c888439e
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560329"
---
# <a name="how-to-create-a-console-shell"></a>Skapa ett konsolgränssnitt

Windows PowerShell tillhandahåller ett verktyg för att ge ett skal, även kallat "make-kit", som används för att skapa ett konsol gränssnitt som inte är utöknings Bart. Gränssnitt som skapats med det här nya verktyget kan inte utökas senare via en Windows PowerShell-snapin-modul.

## <a name="syntax"></a>Syntax

Här är syntaxen som används för att köra kommandot-Shell i en-fil.

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

Här är en kort beskrivning av parametrarna för märke-Shell.

> [!CAUTION]
> UNC-sökvägar till sammansättningar stöds inte av skapa-gränssnitt.

|Parameter|Beskrivning|
|---------------|-----------------|
|-ut n. exe|Krävs. Namnet på det gränssnitt som ska skapas. Sökvägen anges som en del av den här parametern.<br /><br /> Med-Shell läggs ". exe" till i det här värdet om det inte anges. **Varning:**  Skapa inte en utdatafil med samma namn som den refererade DLL-filen. Om du gör det skapas en. CS-fil med samma namn, vilket kommer att skriva över. cs-filen som innehåller käll koden för cmdleten.|
|-namnrymd ns|Krävs. Namn området som ska användas för den härledda [system. Management. Automation. körnings utrymmen. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) -klassen som gör-satsen genererar och kompilerar.|
|-lib-libdirectory1 [, libdirectory2,..]|De kataloger som genomsöks för .NET-sammansättningar, inklusive Windows PowerShell-sammansättningar, sammansättningar som anges av `reference` parametern, sammansättningar som indirekt refereras till av en annan sammansättning och .net-systemets sammansättningar.|
|-referens CA1. dll [, CA2. dll,...]|En kommaavgränsad lista över de sammansättningar som ska ingå i gränssnittet. Dessa sammansättningar innehåller alla cmdlet-och Provider-sammansättningar, samt resurs sammansättningar som ska läsas in. Om den här parametern inte anges skapas ett gränssnitt som bara innehåller de kärn-cmdlets och providers som tillhandahålls av Windows PowerShell.<br /><br /> Sammansättningarna kan anges med hjälp av sin fullständiga sökväg, annars söks de igenom med den sökväg som anges av `lib` parametern.|
|-formatdata FD1. format. ps1xml [, fd2. format. ps1xml,...]|En kommaavgränsad lista med format data som ska tas med i gränssnittet. Om den här parametern inte anges skapas ett gränssnitt som bara innehåller de format data som tillhandahålls av Windows PowerShell.|
|-typedata TD1. Type. ps1xml [, TD2. Type. ps1xml,...]|En kommaavgränsad lista med typ data som ska tas med i gränssnittet. Om den här parametern inte anges skapas ett gränssnitt som bara innehåller de typ data som tillhandahålls av Windows PowerShell.|
|-source c1.cs [, c2.cs,...]|Namnet på en fil, som tillhandahålls av Shell-utvecklaren, som innehåller alla käll koder som krävs för att bygga gränssnittet.<br /><br /> Käll kods filen kan innehålla någon av följande käll koder:<br /><br /> – Den Auktoriseringshanteraren-implementering som åsidosätter standard hanteraren för Auktoriseringshanteraren. (Detta kan också anges kompileras till en sammansättning.)<br />– Assembly information Attribute-deklarationer: till exempel AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute och AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|Den typ som innehåller implementeringen av Auktoriseringshanteraren. Detta kan definieras i käll koden eller kompileras till en sammansättning (anges av `reference` parametern). Om den här parametern inte anges används standard säkerhets hanteraren. Värdet ska vara ett fullständigt typnamn, inklusive namn områden.|
|-win32icon i. ico|Ikonen för. exe-filen för gränssnittet. Om detta inte anges kommer gränssnittet att ha den ikon som c#-kompilatorn inkluderar (om det finns några).|
|-initscript p. ps1|Start profilen för gränssnittet. Filen ingår "i befintligt skick"; ingen giltighets kontroll utförs med ett märke.|
|-builtinscript S1. ps1 [, S2. ps1,...]|En lista med inbyggda skript för gränssnittet. Dessa skript identifieras före skript i sökvägen och deras innehåll kan inte ändras när gränssnittet har skapats.<br /><br /> Filerna ingår "i befintligt skick"; ingen giltighets kontroll utförs med ett märke.|
|-Resource resourcefile. txt|Txt-filen som innehåller hjälp-och informations resurser för gränssnittet. Den första resursen heter ShellHelp och innehåller den text som visas om gränssnittet anropas med `help` parametern. Den andra resursen heter ShellBanner och innehåller texten och copyrightinformation som visas när gränssnittet startas i interaktivt läge.<br /><br /> Om den här parametern inte anges eller om dessa resurser inte finns, används en generisk hjälp och banderoll.|
|-cscflags cscFlags|Flaggor som ska skickas till C#-kompilatorn (CSC. exe). Dessa skickas genom oförändrade. Om den här parametern innehåller blank steg ska den omges av dubbla citat tecken.|
|-?<br /><br /> – hjälp|Visar Copyright-meddelandet och kommando rads alternativen för Shell.|
|– utförlig|Visar detaljerad information medan gränssnittet skapas.|

## <a name="see-also"></a>Se även

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
