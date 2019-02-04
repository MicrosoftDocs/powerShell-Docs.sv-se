---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Windows PowerShell Integrated Scripting Environment ISE
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: a5fcc8c813349d0b85cc3af29047424fe787d168
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683837"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell® Integrated Scripting Environment (ISE)

I Windows PowerShell Integrated Scripting Environment (ISE) är en av två värdar för Windows PowerShell-motorn och språk. Med det som du kan skriva, köra och testa skript på ett sätt som inte är tillgängliga i Windows PowerShell-konsolen. ISE lägger till syntaxfärgning tabbifyllning, IntelliSense, visual felsökning och sammanhangsberoende hjälp.

ISE kan du köra kommandon i en konsolfönstret, men det stöder även fönster som du kan använda för att visa källkoden för ditt skript och andra verktyg som ansluter till ISE samtidigt. Du kan även öppna flera skript windows på samma gång, vilket är särskilt användbart när du felsöker ett skript som använder funktioner som definierats i andra skript och moduler.

## <a name="whats-new"></a>Nyheter

Här följer några av de funktioner som har lagts till i de senaste versionerna av PowerShell ISE.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Har lagts till i PowerShell 3.0 (Windows Server 2012, Windows 8)

**IntelliSense** slutförs automatiskt dina kommandon genom att visa menyer matchande cmdletar, parametrar, parametervärden, filer eller mappar som du skriver.

**Kodfragment** är korta kodavsnitt som du enkelt infogar i skripten din skrivning. En samling av användbara fragment ingår i rutan och mer kan du med hjälp av den **New-kodfragment** cmdlet.

**Tilläggsverktyg** lägger till funktioner till ISE kan skapas genom att skriva kod som interagerar med [The Windows PowerShell ISE-Skriptobjektmodell](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

Dessa verktyg kan visa kontroller i ett kodfragment med fönster eller loggas i bakgrunden. Den **kommandon** tillägg är ett bra exempel och ingår version 3.0 och senare som visar en lista över tillgängliga kommandon och deras hjälp.

**Starta om Manager och spara automatiskt** Spara automatiskt skripten varannan minut för att undvika förlust av ditt arbete i händelse av en krasch eller en oväntad omstart.

**De flesta nyligen använda listan** ingår nu i den öppna menyn för att göra det enklare att komma till de filer som du använder oftast.

**Sammanfogade konsolfönstret**. I tidigare versioner av ISE fanns det separat fönster för kommandot och utdata. De nu kombineras till ett enda fönster att mer direkt imiterar vad som visas i Windows Powershell-konsolen.

**Kommandoradsväxlar**. Flera nya kommandoradsväxlar ger dig större kontroll över hur ISE fungerar. NoProfile - startar ISE utan att köra ett skript för profilen. -Help öppnas ett hjälpfönster med ISE. -mta startar ISE i ”flertrådad inneslutning läget”. Standardvärdet är entrådiga.

**Nya funktioner i redigeraren** gör det enklare att skapa och läsa din kod:

- **XML-syntaxfärgning**. ISE-redigeraren färger nu XML-syntaxen på samma sätt som den färger syntax för Windows PowerShell-kod.

- **Klammerparentes matchar**. ISEWindows PowerShell ISE visar matchande klammerparenteser som hjälper dig att kontrollera att du har tillräckligt många klammerparenteser för att matcha dina inledande sådana. Använd CTRL -\[ att hitta högerparentesen som matchar den inledande klammerparentesen som markören är på.

- **Beskriver visa**. Du kan minimera eller expandera avsnitt i din kod genom att klicka på plustecknet och minustecken i vänster marginal. Detta gör det lättare att hitta den kod som du söker i ett långt skript.

- **Dra och släpp textredigering**. Du kan markera en textblock och drar den till en annan plats att flytta den. Om du håller ned Ctrl-tangenten medan du drar den markerade texten som du kopierar i stället för flytta.

- **Parsa fel visas**. Windows PowerShell undersöker skriptet när du skriver. Om det uppstår ett fel visas en röd markering under den felaktiga koden. När du hovrar över det angivna felet visar en knappbeskrivning problemet som hittades.

- **Zooma**. Du kan zooma in texten att göra det enklare att läsa eller Zooma ut för att se helheten med hjälp av skjutreglaget i det nedre högra hörnet i ISE-fönstret.

- **Rich text kopiera och klistra in**. När du kopierar från ISE till Urklipp, teckensnitt, storlek och färginformation för den markerade texten ingår.

- **Blockera val av**. Du kan välja ett block formad textavsnitt genom att hålla ned ALT-tangenten medan du markerar text i skriptfönstret med musen eller genom att trycka på **Alt + Skift + pil**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Har lagts till i PowerShell 2.0 (Windows Server 2008 R2, Windows 7)

ISE introducerades med PowerShell v2.0.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Krav för att köra Windows PowerShell ISE

ISE är tillgängliga på alla Windows-datorer som kan köra Windows PowerShell version 2.0 eller senare. Varje version av Windows och Windows Server innehåller en version av Windows PowerShell och ISE, men du kan uppgradera till den senaste tillgängliga genom att installera Windows Management Framework (WMF). Se den [WMF](/powershell/wmf) dokumentationen för mer information.

> [!NOTE]
> Eftersom Windows PowerShell ISE kräver ett grafiskt användargränssnitt, kan du köra den på alternativet Server Core av Windows Server.

## <a name="see-also"></a>Se även

[Syfte för windows power shell ise-skriptobjektmodellen](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)