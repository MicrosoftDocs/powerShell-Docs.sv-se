---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Installera Windows PowerShell 2.0-motorn
ms.openlocfilehash: ca0e83209324b28bd41f65ced61bfe9003d98553
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810066"
---
# <a name="installing-the-windows-powershell-20-engine"></a>Installera Windows PowerShell 2.0-motorn

Det här avsnittet beskriver hur du installerar Windows PowerShell 2,0-motorn.

Windows PowerShell 3,0 är avsett att vara bakåtkompatibla med Windows PowerShell 2,0. Cmdlets, providers, snapin-moduler, moduler och skript som skrivits för Windows PowerShell 2,0 körs oförändrade i Windows PowerShell 3,0 och Windows PowerShell 4,0. Men på grund av en ändring i aktiverings principen för körning i Microsoft .NET Framework 4 kan Windows PowerShell-värdprogram som skrivits för Windows PowerShell 2,0 och kompileras med CLR (Common Language Runtime) 2,0 inte köras utan ändringar i senare versioner av Windows PowerShell, som kompileras med CLR 4,0.

För att upprätthålla bakåtkompatibilitet med kommandon och värd program som påverkas av dessa ändringar, är Windows PowerShell 2,0, Windows PowerShell 3,0 och Windows PowerShell 4,0-motorer utformade för att köras sida vid sida. Windows PowerShell 2,0-motorn ingår också i Windows Server 2012 R2, Windows 8,1, Windows 8, Windows Server 2012 och Windows Management Framework 3,0. Windows PowerShell 2,0-motorn är avsedd att användas endast när ett befintligt skript eller värd program inte kan köras eftersom det är inkompatibelt med Windows PowerShell 3,0, Windows PowerShell 4,0 eller Microsoft .NET Framework 4. Sådana fall förväntas vara ovanliga.

Windows PowerShell 2,0-motorn är en valfri funktion i Windows Server 2012 R2, Windows 8,1, Windows® 8 och Windows Server® 2012. När du installerar Windows Management Framework 3,0 i tidigare versioner av Windows ersätter installationen av Windows PowerShell 3,0 fullständigt Windows PowerShell 2,0-installationen i installations katalogen för Windows PowerShell. Windows PowerShell 2,0-motorn behålls dock.

Information om hur du startar Windows PowerShell 2,0-motorn finns i [Starta Windows PowerShell 2,0-motorn](../Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>På Windows 8,1 och Windows 8

På Windows 8,1 och Windows 8 är Windows PowerShell 2,0-motorn aktiverat som standard.
Men om du vill använda det måste du aktivera alternativet för Microsoft .NET Framework 3,5 som krävs. Det här avsnittet beskriver också hur du aktiverar och inaktiverar motor funktionen i Windows PowerShell 2,0.

#### <a name="to-turn-on-net-framework-35"></a>Aktivera .NET Framework 3,5

1. Skriv **Windows-funktioner**på **Start** skärmen.
2. I fältet **appar** klickar du på **Inställningar**och sedan på **Aktivera eller inaktivera Windows-funktioner**.
3. I rutan **Windows-funktioner** klickar du på **.NET Framework 3,5 (omfattar .net 2,0 och 3,0** för att välja den.

   När du väljer **.NET Framework 3,5 (inklusive .net 2,0 och 3,0**) fyller rutan för att indikera att endast en del av funktionen är markerad. Detta räcker dock för Windows PowerShell 2,0-motorn.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Aktivera och inaktivera Windows PowerShell 2,0-motorn

1. Skriv **Windows-funktioner**på **Start** skärmen.

2. I fältet **appar** klickar du på **Inställningar**och sedan på **Aktivera eller inaktivera Windows-funktioner**.

3. I rutan **Windows-funktioner** expanderar du noden **Windows PowerShell 2,0** och klickar på **Windows PowerShell 2,0-motor** rutan för att markera eller avmarkera den.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>På Windows Server 2012 R2 och Windows Server 2012

Använd följande procedurer för att lägga till Windows PowerShell 2,0-motorn och Microsoft .NET Framework 3,5-funktioner. Windows PowerShell 2,0-motorn kräver minst Microsoft .NET Framework-2.0.50727. Detta krav uppfylls av Microsoft .NET Framework 3,5.

#### <a name="to-add-the-net-framework-35-feature"></a>Lägga till .NET Framework 3,5-funktionen

1. I **Serverhanteraren**väljer du **Lägg till roller och funktioner**i menyn **Hantera** .

    Du kan också klicka på **alla servrar**i **Serverhanteraren**, högerklicka på ett server namn och sedan välja **Lägg till roller och funktioner**.

2. På sidan **Installations typ** väljer du **rollbaserad eller funktions baserad installation**.

3. På sidan **funktioner** expanderar du noden **.net 3,5 Framework-funktioner** och väljer **.NET Framework 3,5 (inklusive .NET 2,0 och 3,0)**.

   De andra alternativen under noden krävs inte för Windows PowerShell 2,0-motorn.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Lägga till Windows PowerShell 2,0-motor funktionen

- I **Serverhanteraren**väljer du **Lägg till roller och funktioner**i menyn **Hantera** .

  Eller **Serverhanteraren**, klickar du på **alla servrar**, högerklickar på ett server namn och väljer sedan **Lägg till roller och funktioner**.

- På sidan **Installations typ** väljer du **rollbaserad eller funktions baserad installation**.

- På sidan **funktioner** expanderar du noden **Windows PowerShell (installerad)** och väljer **Windows PowerShell 2,0-motor**.

Information om hur du startar Windows PowerShell 2,0-motorn finns i [Starta Windows PowerShell 2,0-motorn](../Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>I tidigare system

[Windows Management Framework 4,0](https://go.microsoft.com/fwlink/?LinkID=293881) -paketet som installerar windows PowerShell 4,0 på Windows 7, windows Server 2008 R2 och windows Server 2012 innehåller windows PowerShell 2,0-motorn. Windows PowerShell 2,0-motorn är aktive rad och redo att användas, om det behövs, utan ytterligare installation, konfiguration eller konfiguration.

Windows Management Framework 3,0-paketet som installerar Windows PowerShell 3,0 på Windows 7, Windows Server 2008 R2 och Windows Server 2008 innehåller Windows PowerShell 2,0-motorn. Windows PowerShell 2,0-motorn är aktive rad och redo att användas, om det behövs, utan ytterligare installation, konfiguration eller konfiguration.

## <a name="see-also"></a>Se även

- [Windows PowerShell-systemkrav](Windows-PowerShell-System-Requirements.md)
- [Installera Windows PowerShell](Installing-Windows-PowerShell.md)
- [Starta Windows Powershell](/previous-versions/ms714415(v=vs.85))
- [Starta Windows PowerShell 2.0-motorn](../Starting-the-Windows-PowerShell-2.0-Engine.md)
