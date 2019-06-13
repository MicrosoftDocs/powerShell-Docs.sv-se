---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Installera Windows PowerShell 2.0-motorn
ms.openlocfilehash: a2b78755e7e44e2523baee5477fadc94eab485b1
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030961"
---
# <a name="installing-the-windows-powershell-20-engine"></a>Installera Windows PowerShell 2.0-motorn
Det här avsnittet beskriver hur du installerar Windows PowerShell 2.0-motorn.

Windows PowerShell 3.0 är avsett att vara bakåtkompatibla med Windows PowerShell 2.0. Cmdlet: ar, leverantörer, snapin-moduler, moduler och skript som har skrivits för Windows PowerShell 2.0 kör oförändrad i Windows PowerShell 3.0 och Windows PowerShell 4.0. Men på grund av en ändring i principen runtime aktivering i Microsoft .NET Framework 4, Windows PowerShell-värd program som har skrivits för Windows PowerShell 2.0 och kompileras med Runtime CLR (Common Language) 2.0 kan inte köras utan ändringar i senare versioner av Windows PowerShell som kompileras med CLR 4.0.

Windows PowerShell 2.0, Windows PowerShell 3.0 och Windows PowerShell 4.0 motorerna är avsedda att köras sida-vid-sida för att bibehålla kompatibilitet med kommandon och värd-program som påverkas av ändringarna. Windows PowerShell 2.0-motorn ingår också i Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 och Windows Management Framework 3.0. Windows PowerShell 2.0-motorn är avsedd att användas endast när ett befintligt skript eller värdprogrammet kan inte köras eftersom det är inte kompatibel med Windows PowerShell 3.0, Windows PowerShell 4.0 eller Microsoft .NET Framework 4. Sådana fall förväntas vara sällsynt.

Windows PowerShell 2.0-motorn är en valfri funktion i Windows Server 2012 R2, Windows 8.1, Windows® 8 och Windows Server® 2012. I tidigare versioner av Windows när du installerar Windows Management Framework 3.0 ersätter installationen av Windows PowerShell 3.0 helt Windows PowerShell 2.0-installation i Windows PowerShell-installationskatalogen. Windows PowerShell 2.0-motorn är dock kvar.

Information om hur du startar Windows PowerShell 2.0-motorn finns i [starta Windows PowerShell 2.0-motorn](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>På Windows 8.1 och Windows 8
På Windows 8.1 och Windows 8, Windows PowerShell 2.0-motorn funktionen är aktiverad som standard. Men om du vill använda den måste aktivera alternativet för Microsoft .NET Framework 3.5, som krävs. Det här avsnittet beskriver också hur du kan aktivera eller inaktivera funktionen Windows PowerShell 2.0-motorn.

#### <a name="to-turn-on-net-framework-35"></a>Aktivera .NET Framework 3.5

1. På den **starta** skärmen, Skriv **Windows-funktioner**.

2. På den **appar** klickar du på **inställningar**, och klicka sedan på **aktivera Windows-funktioner på eller av**.

3. I den **Windows-funktioner** klickar du på **.NET Framework 3.5 (inklusive.NET 2.0 och 3.0** att välja den.

    När du väljer **.NET Framework 3.5 (inklusive.NET 2.0 och 3.0**, rutan fylls att endast en del av funktionen har valts. Men räcker detta för Windows PowerShell 2.0-motorn.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Inaktivera Windows PowerShell 2.0-motorn på

1. På den **starta** skärmen, Skriv **Windows-funktioner**.

2. På den **appar** klickar du på **inställningar**, och klicka sedan på **aktivera Windows-funktioner på eller av**.

3. I den **Windows-funktioner** , expandera den **Windows PowerShell 2.0** noden och klicka på den **Windows PowerShell 2.0-motorn** om du vill markera eller avmarkera den.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>På Windows Server 2012 R2 och Windows Server 2012
Använd följande procedurer för att lägga till Windows PowerShell 2.0-motorn och Microsoft .NET Framework 3.5 funktioner. Windows PowerShell 2.0-motorn kräver Microsoft .NET Framework 2.0.50727 minst. Detta krav uppfylls genom att Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>Att lägga till funktionen .NET Framework 3.5

1. I **Serverhanteraren**, från den **hantera** menyn och välj **Lägg till roller och funktioner**.

    Eller i **Serverhanteraren**, klickar du på **alla servrar**, högerklicka på ett servernamn och välj sedan **Lägg till roller och funktioner**.

2. På den **installationstyp** väljer **rollbaserad eller funktionsbaserad installation**.

3. På den **funktioner** expanderar den **funktioner i .NET 3.5 Framework** noden och väljer **.NET Framework 3.5 (omfattar .NET 2.0 och 3.0)** .

    De andra alternativen under den noden krävs inte för Windows PowerShell 2.0-motorn.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Att lägga till funktionen Windows PowerShell 2.0-motorn

- I **Serverhanteraren**, från den **hantera** menyn och välj **Lägg till roller och funktioner**.

    Eller **Serverhanteraren**, klickar du på **alla servrar**, högerklicka på ett servernamn och välj sedan **Lägg till roller och funktioner**.

- På den **installationstyp** väljer **rollbaserad eller funktionsbaserad installation**.

- På den **funktioner** expanderar den **Windows PowerShell (installerad)** noden och väljer **Windows PowerShell 2.0-motorn**.

Information om hur du startar Windows PowerShell 2.0-motorn finns i [starta Windows PowerShell 2.0-motorn](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>I tidigare versioner
Den [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) paketet som installerar Windows PowerShell 4.0 på Windows 7, Windows Server 2008 R2 och Windows Server 2012 innehåller Windows PowerShell 2.0-motorn. Windows PowerShell 2.0-motorn är aktiverad och redo att använda, om det behövs utan ytterligare information, installation eller konfiguration.

Paketet Windows Management Framework 3.0 som installerar Windows PowerShell 3.0 på Windows 7, Windows Server 2008 R2 och Windows Server 2008, innehåller Windows PowerShell 2.0-motorn. Windows PowerShell 2.0-motorn är aktiverad och redo att använda, om det behövs utan ytterligare information, installation eller konfiguration.

## <a name="see-also"></a>Se även
- [Windows PowerShell-systemkrav](Windows-PowerShell-System-Requirements.md)
- [Installera Windows PowerShell](Installing-Windows-PowerShell.md)
- [Starta Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Starta Windows PowerShell 2.0-motorn](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)
