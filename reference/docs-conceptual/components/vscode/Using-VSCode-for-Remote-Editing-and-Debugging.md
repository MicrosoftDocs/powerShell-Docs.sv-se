---
title: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
description: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086686"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Använda Visual Studio Code för att fjärredigera och fjärrfelsöka

För dig som har erfarenhet av ISE, du kanske kommer ihåg att du kan köra `psedit file.ps1` från integrerad konsol för att öppna filer – lokal eller fjärransluten - Högerklicka i ISE.

Den här funktionen är även tillgängliga i PowerShell-tillägget för VSCode eftersom det har visat sig. Den här guiden visar hur du gör den.

## <a name="prerequisites"></a>Förutsättningar

Den här guiden förutsätter att du har:

- en fjärransluten resurs (t.ex.: en virtuell dator, en behållare) att du har åtkomst till
- PowerShell som körs på den och värddatorn
- VSCode och PowerShell-tillägget för VSCode

Den här funktionen fungerar i Windows PowerShell och PowerShell Core.

Den här funktionen fungerar även när du ansluter till en fjärrdator via WinRM, PowerShell Direct eller SSH. Om du vill använda SSH, men använder Windows, Kolla in den [Win32-versionen av SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>Kom så går vi

I det här avsnittet kan gå jag igenom remote redigering och felsökning från min MacBook Pro för en Ubuntu-VM som körs i Azure. Jag kan inte använda Windows, men **processen är identiska**.

### <a name="local-file-editing-with-open-editorfile"></a>Lokal fil Redigera med öppen EditorFile

Med PowerShell-tillägget för VSCode igång och integrerad PowerShell-konsolen öppnas, vi kan skriva `Open-EditorFile foo.ps1` eller `psedit foo.ps1` att öppna lokala foo.ps1 fil direkt i redigeraren.

![Öppna EditorFile foo.ps1 arbetar lokalt](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 måste redan finnas.

Därifrån kan vi:

lägga till brytpunkter fästmarginalen ![att lägga till brytpunkt om du vill fästmarginalen](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

och tryck på F5 för att felsöka PowerShell-skriptet.
![Felsökning av lokal PowerShell-skriptet](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

När du felsöker, kan du interagera med Felsökningskonsolen, Kolla in variabler i området till vänster och de andra vanliga felsökningsverktyg.

### <a name="remote-file-editing-with-open-editorfile"></a>Fjärrfil Redigera med öppen EditorFile

Nu ska vi gå in fjärrfil redigering och felsökning. Stegen är nästan desamma finns det bara en sak som vi behöver göra först - ange våra PowerShell-session till fjärrservern.

Det finns en cmdlet för att göra detta. Den kallas `Enter-PSSession`.

Watered ned förklaring av cmdlet: en är:

- `Enter-PSSession -ComputerName foo` startar en session via WinRM
- `Enter-PSSession -ContainerId foo` och `Enter-PSSession -VmId foo` starta en session via PowerShell Direct
- `Enter-PSSession -HostName foo` startar en session via SSH

Mer information om `Enter-PSSession`, Kolla in dokumenten [här](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Jag kommer att använda SSH för fjärrkörning eftersom jag från macOS för en Ubuntu-VM i Azure.

Först i konsolen integrerad vi köra våra Enter-PSSession. Du vet att du befinner dig i sessionen eftersom `[something]` visas till vänster om din fråga.

![Anropet till Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

Därifrån kan göra vi de exakta stegen som om vi redigerade ett lokalt skript.

1. Kör `Open-EditorFile test.ps1` eller `psedit test.ps1` att öppna fjärransluten `test.ps1` filen ![öppen-EditorFile test.ps1-fil](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Redigera filen/set-brytpunkter ![Redigera och ange brytpunkter](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Starta felsökning (F5) fjärrfilen

![Felsökning fjärrfilen](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Det är allt det! Vi hoppas att den här guiden hjälpt Rensa upp frågor om remote felsökning och redigera PowerShell i VSCode.

Om du har problem kan passa på att öppna problem [på GitHub-lagringsplatsen](http://github.com/powershell/vscode-powershell).
