---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Installera Windows PowerShell 2.0-motorn
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: ff6c2b52b8948472ace3ee35cd4c6aa2dbf46c25
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="installing-the-windows-powershell-20-engine"></a>Installera Windows PowerShell 2.0-motorn
Det här avsnittet beskriver hur du installerar Windows PowerShell 2.0-motorn.

Windows PowerShell 3.0 är avsedd att vara bakåtkompatibla med Windows PowerShell 2.0. Kör oförändrad i Windows PowerShell 3.0 och 4.0 för Windows PowerShell cmdlets, providers, snapin-moduler, moduler och skript som är skrivna för Windows PowerShell 2.0. Men på grund av en ändring i principen runtime aktivering i Microsoft .NET Framework 4, Windows PowerShell värden program som har skrivits för Windows PowerShell 2.0 och kompileras med Runtime CLR (Common Language) 2.0 kan inte köras utan ändringar i senare versioner av Windows PowerShell som kompileras med CLR-4.0.

För att bibehålla kompatibilitet med kommandon och värd-program som påverkas av ändringarna är motorer för Windows PowerShell 2.0, Windows PowerShell 3.0 och Windows PowerShell 4.0 avsedd att köras sida vid sida. Motorn för Windows PowerShell 2.0 ingår också i Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 och Windows Management Framework 3.0. Windows PowerShell 2.0-motorn är avsedd att användas endast när ett befintligt skript eller värdprogrammet kan inte köras eftersom den inte är kompatibel med Windows PowerShell 3.0, Windows PowerShell 4.0 eller Microsoft .NET Framework 4. Sådana fall förväntas vara sällsynt.

Windows PowerShell 2.0-motorn är en valfri funktion i Windows Server 2012 R2, Windows 8.1, Windows® 8 och Windows Server® 2012. I tidigare versioner av Windows när du installerar Windows Management Framework 3.0 ersätter installationen av Windows PowerShell 3.0 Windows PowerShell 2.0-installationen i installationskatalogen för Windows PowerShell. Windows PowerShell 2.0-motorn är dock kvar.

Information om hur du startar Windows PowerShell 2.0-motorn finns [starta Windows PowerShell 2.0 motorn](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>På Windows 8.1 och Windows 8
På Windows 8.1 och Windows 8, är Windows PowerShell 2.0-motorn-funktionen aktiverad som standard. Men för att använda den måste du aktivera alternativet för Microsoft .NET Framework 3.5, där det krävs. Det här avsnittet beskriver även hur du kan aktivera eller inaktivera funktionen Windows PowerShell 2.0-motorn.

#### <a name="to-turn-on-net-framework-35"></a>Aktivera .NET Framework 3.5

1. På den **starta** skriver **Windows-funktioner**.

2. På den **appar** klickar du på **inställningar**, och klicka sedan på **aktivera Windows-funktioner på eller stänga av**.

3. I den **Windowsfunktioner** klickar du på **.NET Framework 3.5 (omfattar .NET 2.0 och 3.0** att välja den.

    När du väljer **.NET Framework 3.5 (omfattar .NET 2.0 och 3.0**, rutan fylls att endast en del av funktionen har valts. Detta är tillräckliga för Windows PowerShell 2.0-motorn.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Att aktivera eller inaktivera Windows PowerShell 2.0-motorn

1. På den **starta** skriver **Windows-funktioner**.

2. På den **appar** klickar du på **inställningar**, och klicka sedan på **aktivera Windows-funktioner på eller stänga av**.

3. I den **Windows-funktioner** , expandera den **Windows PowerShell 2.0** och klicka på **Windows PowerShell 2.0-motorn** om du vill markera eller avmarkera den.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>På Windows Server 2012 R2 och Windows Server 2012
Använd följande procedurer för att lägga till Windows PowerShell 2.0-motorn och Microsoft .NET Framework 3.5 funktioner. Windows PowerShell 2.0-motorn kräver Microsoft .NET Framework 2.0.50727 minst. Detta krav uppfylls genom att Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>Att lägga till funktionen .NET Framework 3.5

1. I **Serverhanteraren**, från den **hantera** väljer du **Lägg till roller och funktioner**.

    Eller i **Serverhanteraren**, klickar du på **alla servrar**, högerklicka på ett servernamn och väljer sedan **Lägg till roller och funktioner**.

2. På den **installationstyp** väljer **rollbaserad eller funktionsbaserad installation**.

3. På den **funktioner** expanderar den **funktioner i .NET Framework 3.5** och välj **.NET Framework 3.5 (omfattar .NET 2.0 och 3.0)**.

    Andra alternativ under den noden krävs inte för Windows PowerShell 2.0-motorn.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Att lägga till funktionen Windows PowerShell 2.0-motorn

- I **Serverhanteraren**, från den **hantera** väljer du **Lägg till roller och funktioner**.

    Eller **Serverhanteraren**, klickar du på **alla servrar**, högerklicka på ett servernamn och väljer sedan **Lägg till roller och funktioner**.

- På den **installationstyp** väljer **rollbaserad eller funktionsbaserad installation**.

- På den **funktioner** expanderar den **Windows PowerShell (installerad)** och välj **Windows PowerShell 2.0-motorn**.

Information om hur du startar Windows PowerShell 2.0-motorn finns [starta Windows PowerShell 2.0 motorn](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>I tidigare versioner
Den [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) paket som installerar Windows PowerShell 4.0 på Windows 7, Windows Server 2008 R2 och Windows Server 2012 innehåller Windows PowerShell 2.0-motorn. Windows PowerShell 2.0-motorn är aktiverad och redo att använda, om det behövs utan ytterligare information, installation eller konfiguration.

Windows Management Framework 3.0-paketet som installerar Windows PowerShell 3.0 på Windows 7, Windows Server 2008 R2 och Windows Server 2008, innehåller Windows PowerShell 2.0-motorn. Windows PowerShell 2.0-motorn är aktiverad och redo att använda, om det behövs utan ytterligare information, installation eller konfiguration.

## <a name="see-also"></a>Se även
- [Systemkrav för Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Installera Windows PowerShell](Installing-Windows-PowerShell.md)
- [Starta Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Starta Windows PowerShell 2.0-motorn](Starting-the-Windows-PowerShell-2.0-Engine.md)

