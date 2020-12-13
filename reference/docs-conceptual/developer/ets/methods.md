---
ms.date: 07/09/2020
ms.topic: reference
title: System klass metoder för utökad typ
description: System klass metoder för utökad typ
ms.openlocfilehash: b53604a36e0a0c3587f345262e8f274e3a2c4859
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660389"
---
# <a name="ets-class-methods"></a>ETS klass metoder

ETS-metoder är medlemmar som kan ta argument, kan returnera resultat och får inte visas till vänster i ett uttryck. Metoderna som är tillgängliga i ETS inkluderar Code, Windows PowerShell och skript metoder.

> [!NOTE]
> Från skript används metoder för att använda samma syntax som andra medlemmar som har tillsatsen parentes i slutet av metod namnet.

## <a name="code-methods"></a>Kod metoder

En kod metod är en utökad medlem som definieras i ett CLR-språk. Den innehåller liknande funktioner som en metod som definierats i ett bas objekt. en kod metod kan dock läggas till dynamiskt i ett **PSObject** -objekt. För att en kod metod ska bli tillgänglig måste en utvecklare skriva egenskapen i vissa CLR-språk, kompilera och leverera den resulterande sammansättningen. Den här sammansättningen måste vara tillgänglig i körnings utrymme där kod metoden önskas. Tänk på att implementeringen av en kod metod måste vara tråd säker. Åtkomst till dessa metoder görs genom [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) -objekt som tillhandahåller följande offentliga metoder och egenskaper.

- `PSCodeMethod.Copy` metod: gör en exakt kopia av **PSCodeMethod** -objektet.
- `PSCodeMethod.Invoke(System.Object[])` metod: anropar den underliggande kod metoden.
- `PSCodeMethod.ToString` metod: konverterar **PSCodeMethod** -objektet till en sträng.
- `PSCodeMethod.CodeReference` egenskap: hämtar den underliggande metoden som kod metoden baseras på.
- **PSMemberInfo. IsInstance** -egenskap: hämtar ett **booleskt** värde som anger medlemmens källa.
- **PSCodeMethod. MemberType** -egenskap: hämtar en **PSMemberTypes. CodeMethod** -uppräknings konstant som identifierar den här metoden som en kod metod.
- **PSMemberInfo.name** -egenskap: hämtar namnet på den underliggande kod metoden.
- **PSCodeMethod. OverloadDefinitions** -egenskap: hämtar en definition av alla överlagringar av den underliggande kod metoden.
- **PSCodeMethod. TypeNameOfValue** -egenskap: hämtar det fullständiga namnet på kod metoden.
- **PSMemberInfo. Value** -egenskap: hämtar **PSCodeMethod** -objektet.

## <a name="windows-powershell-methods"></a>Windows PowerShell-metoder

En PowerShell-metod är en CLR-metod som definierats för bas objektet eller som kan nås via ett kort. Åtkomst till dessa metoder görs genom **PSMethod** -objekt som tillhandahåller följande offentliga metoder och egenskaper.

- `PSMethod.Copy` metod: gör en exakt kopia av **PSMethod** -objektet.
- `PSMethod.Invoke(System.Object[])` metod: anropar den underliggande metoden.
- `PSMethod.ToString` metod: konverterar **PSMethod** -objektet till en sträng.
- **PSMemberInfo. IsInstance** -egenskap: hämtar ett **booleskt** värde som anger medlemmens källa.
- **PSMethod. MemberType** -egenskap: hämtar en **PSMemberTypes. Method** Enumeration-konstant som identifierar den här metoden som en PowerShell-metod.
- **PSMemberInfo.name** -egenskap: hämtar namnet på den underliggande metoden.
- **PSMethod. OverloadDefinitions** -egenskap: hämtar definitionerna för alla överlagringar av den underliggande metoden.
- **PSMethod. TypeNameOfValue** -egenskap: hämtar ETS-typen för den här metoden.
- **PSMemberInfo. Value** -egenskap: hämtar **PSMethod** -objektet.

## <a name="script-methods"></a>Skript metoder

En skript metod är en utökad medlem som definieras i PowerShell-språket. Den innehåller liknande funktioner som en metod som definierats i ett bas objekt. en skript metod kan dock läggas till dynamiskt i ett **PSObject** -objekt. Åtkomst till dessa metoder görs genom [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) -objekt som tillhandahåller följande offentliga metoder och egenskaper.

- `PSScriptMethod.Copy` metod: gör en exakt kopia av **PSScriptMethod** -objektet.
- `PSScriptMethod.Invoke(System.Object[])` metod: anropar den underliggande skript metoden.
- `PSScriptMethod.ToString` metod: konverterar **PSScriptMethod** -objektet till en sträng.
- **PSMemberInfo. IsInstance** -egenskap: hämtar ett **booleskt** värde som anger medlemmens källa.
- **PSScriptMethod. MemberType** -egenskap: hämtar en **PSMemberTypes. ScriptMethod** -uppräknings konstant som identifierar den här metoden som en skript metod.
- **PSMemberInfo.name** -egenskap: hämtar namnet på den underliggande kod metoden.
- **PSScriptMethod. OverloadDefinitions** -egenskap: hämtar definitionerna för alla överlagringar av den underliggande skript metoden.
- **PSScriptMethod. TypeNameOfValue** -egenskap: hämtar ETS-typen för den här metoden.
- **PSScriptMethod. skript** egenskap: hämtar det skript som används för att anropa metoden.
- **PSMemberInfo. Value** -egenskap: hämtar **PSScriptMethod** -objektet.
