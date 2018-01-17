---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Windows PowerShell Integrated Scripting Environment ISE
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 66f36371cbb8ad8523aa1e1e3cd791cc692194c9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell® Integrated Scripting Environment (ISE)
I Windows PowerShell Integrated Scripting Environment (ISE) är en av två värdar för Windows PowerShell-motorn och språk. Med det som du kan skriva, köra och testa skript på sätt som inte är tillgängliga i Windows PowerShell-konsolen. I ISE lägger till syntax färgläggning, flikavslutande, IntelliSense, visual felsökning och sammanhangsberoende hjälp.

I ISE kan du köra kommandon i en konsolfönstret, men det stöder också fönster som du kan använda för att visa källkoden för ditt skript och andra verktyg som ansluter till ISE samtidigt. Du kan även öppna flera skript windows på samma gång, vilket är särskilt användbart när du felsöker ett skript som använder funktioner som är definierade i andra skript och moduler.

## <a name="whats-new"></a>Nyheter
Här följer några av de funktioner som har lagts till i de senaste versionerna av PowerShell ISE.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Lades till i PowerShell 3.0 (Windows Server 2012, Windows 8)
**IntelliSense** slutförs automatiskt dina kommandon genom att visa menyer matchande cmdlets, parametrar, parametervärden, filer eller mappar som du anger.

**Kodavsnitt** är korta kodavsnitt som du enkelt infogar i skripten din skrivåtgärder. En samling användbar kodavsnitt ingår i rutan och mer kan du med hjälp av den **ny fragment** cmdlet.

**Tilläggsverktyg** som lägger till funktioner till ISE kan skapas genom att skriva kod som interagerar med det [i Windows PowerShell ISE Scripting Object Model](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md). Dessa verktyg kan visa kontroller i en streckad fönstret eller loggas i bakgrunden. Den **kommandon** tillägget är ett bra exempel och ingår i version 3.0 och senare som visar en lista över tillgängliga kommandon och deras hjälp.

**Starta om Manager och spara automatiskt** Spara automatiskt skripten varannan minut för att hjälpa dig att undvika förlust av ditt arbete vid en krasch eller en oväntad omstart.

**De flesta lista över senast använda** ingår i den öppna menyn att göra det enklare att hämta de filer som du ofta använder.

**Kopplade konsolfönstret**. I tidigare versioner av ISE fanns separat fönster för kommandot och utdata. De nu kombineras till ett enda fönster att flera direkt efterliknar vad som visas i Windows Powershell-konsolen.

**Kommandoradsväxlar**. Flera nya kommandoradsväxlar ger dig större kontroll över hur av ISE fungerar. -NoProfile startar av ISE utan att köra ett skript för profilen. -Help öppnar ett fönster för hjälp med av ISE. -mta startar ISE ”flertrådad inneslutning läget”. Standardvärdet är enkeltrådad.

**Nya funktioner** gör det enklare att skapa och läsa koden:

- **XML-syntax färgläggning**. Redigeraren för ISE färger nu XML-syntaxen på samma sätt som den färger kodsyntax för Windows PowerShell.

- **Klammerparentes matchar**. ISEWindows PowerShell ISE visar matchande klammerparenteser som hjälper dig att kontrollera att du har rätt antal klammerparenteser för att matcha dina öppnas de som. Använd CTRL -\[ att hitta den avslutande klammerparentesen som matchar den inledande klammerparentesen som markören är på.

- **Visa disposition**. Du kan komprimera eller expandera avsnitt i din kod genom att klicka på plustecknet och minustecken i vänster marginal. På så sätt blir det lättare att hitta den kod som du söker i ett skript för lång.

- **Dra och släpp textredigering**. Du kan markera ett block med text och drar den till en annan plats att flytta den. Om du håller ned Ctrl-tangenten medan du drar den markerade texten som du kopierar i stället för att flytta.

- **Parsa fel visas**. Windows PowerShell undersöker skriptet när du skriver. Om det uppstår ett fel visas en röd markering under felaktiga koden. När du hovrar över det angivna felet visas en knappbeskrivning problemet som hittades.

- **Zooma**. Du kan zooma in texten så att den lättare att läsa eller Zooma ut för att ha bättre överblick med hjälp av skjutreglaget i det nedre högra hörnet i fönstret ISE.

- **Omfattande text kopiera och klistra in**. När du kopierar från ISE till Urklipp, teckensnitt, storlek och färginformation för den markerade texten ingår.

- **Blockera markeringen**. Du kan välja ett block-formade segment av text genom att hålla ned ALT-tangenten medan du markerar text i skriptfönstret med musen eller genom att trycka på **Alt + Skift + pil**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Lades till i PowerShell 2.0 (Windows Server 2008 R2, Windows 7)
I ISE introducerades med PowerShell version 2.0.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Krav för att köra Windows PowerShell ISE
I ISE är tillgängliga på alla Windows-datorer som kan köra Windows PowerShell version 2.0 eller senare.
Varje version av Windows och Windows Server innehåller en version av Windows PowerShell och av ISE, men du kan uppgradera till den senaste tillgängliga genom att installera Windows Management Framework.
Sök för att hitta den senaste versionen: [hämtar](http://www.microsoft.com/en-us/search/DownloadResults.aspx?q=%22windows%20management%20framework%22%20PowerShell&sortby=Relevancy~Descending).
Observera att alla poster som är märkta ”Förhandsgranska” är förhandsversionen kod och inte är funktionen som är klar.

> [!NOTE]
> Eftersom Windows PowerShell ISE kräver ett grafiskt användargränssnitt, kan du köra det på alternativet Server Core av Windows Server.

## <a name="see-also"></a>Se även
- [Med hjälp av Windows PowerShell Integrated Scripting Environment](../../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

