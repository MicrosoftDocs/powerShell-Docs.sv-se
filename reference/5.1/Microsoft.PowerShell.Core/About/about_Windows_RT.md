---
description: I artikeln förklaras begränsningar för Windows PowerShell 4,0 på Windows RT 8,1.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_rt?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_RT
ms.openlocfilehash: 323f06a7a0d8253417510503c1011ac02c20179f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271352"
---
# <a name="about-windows-rt"></a>Om Windows RT

## <a name="short-description"></a>KORT BESKRIVNING

I artikeln förklaras begränsningar för Windows PowerShell 4,0 på Windows RT 8,1.

## <a name="long-description"></a>LÅNG BESKRIVNING

Operativ systemet Windows RT 8,1 installeras på datorer och enheter (till exempel Microsoft Surface 2, där det är det operativ system som levereras med datorn) som använder sig av ARM-processorer (Advanced RISC Machine).

Windows PowerShell 4,0 ingår i Windows RT 8,1. Alla cmdletar, providers och moduler, och de flesta skript som har utformats för Windows PowerShell 2,0 och senare versioner körs på Windows RT 8,1 utan ändringar.

Eftersom Windows RT 8,1 inte innehåller alla Windows-funktioner fungerar vissa funktioner i Windows PowerShell annorlunda eller fungerar inte på Windows RT-baserade enheter. I följande lista beskrivs skillnaderna.

- Windows PowerShell ISE ingår inte i och kan inte köras på Windows RT 8,1.
  Windows PowerShell ISE kräver Windows Presentation Foundation, som inte ingår i Windows RT 8,1.

- Windows PowerShell-fjärrkommunikation och WinRM-tjänsten är inaktiverade som standard.
  Kör cmdleten Enable-PSRemoting om du vill aktivera fjärr kommunikation. Du kan också köra cmdleten Set-Service för att ställa in start typen för WinRM-tjänsten på automatisk eller automatisk (fördröjd start).

  Fjärr kommunikation är inaktive rad, du kan använda Windows PowerShell-fjärrkommunikation för att köra kommandon på andra datorer, men andra datorer kan inte köra kommandon på Windows RT-enheten. Även implicit fjärr kommunikation – det vill säga fjärr kommunikation som är inbyggd i en cmdlet eller ett skript, och som inte uttryckligen begärs med tillagda parametrar
  - fungerar inte i Windows PowerShell som körs på Windows RT 8,1.

- Domänanslutna data behandling och Kerberos-autentisering stöds inte på Windows RT 8,1. Du kan inte använda Windows PowerShell för att lägga till eller hantera dessa funktioner.

- Microsoft .NET Framework-klasser som inte stöds i Windows RT 8,1 stöds inte heller av Windows PowerShell på Windows RT 8,1.

- Transaktioner är inte aktiverade på Windows RT 8,1. Transaktions-cmdletar, till exempel start-och transaktions parametrar, t. ex. UseTransaction, fungerar inte som de ska.

- Alla Windows PowerShell-sessioner på Windows RT 8,1-enheter använder språk läget ConstrainedLanguage. ConstrainedLanguage-språkläget är en komponent till UMCI (User Mode Code Integrity). Den tillåter alla Windows-cmdlets och Windows PowerShell-språkelement, men begränsar typer för att säkerställa att användare inte kan använda Windows PowerShell för att kringgå eller bryta mot UMCI skydd.

Mer information om språk läge för ConstrainedLanguage finns i [about_Language_Modes](about_Language_Modes.md).

## <a name="see-also"></a>SE ÄVEN

[about_Language_Modes](about_Language_Modes.md)

[about_Remote](about_Remote.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)
