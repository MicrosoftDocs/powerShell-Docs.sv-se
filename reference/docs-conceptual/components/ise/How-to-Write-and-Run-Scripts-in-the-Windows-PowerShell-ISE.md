---
ms.date: 08/14/2018
keywords: PowerShell cmdlet
title: Skriv och kör skript i Windows PowerShell ISE
ms.openlocfilehash: 4a08d7d206d103dcb398964d7ce75bea1e76559a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028968"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Skriv och kör skript i Windows PowerShell ISE

Den här artikeln beskriver hur du skapa, redigera, köra och spara skript i skriptfönstret.

## <a name="how-to-create-and-run-scripts"></a>Hur du skapar och kör skript

Du kan öppna och redigera Windows PowerShell-filer i skriptfönstret. Specifika filtyper intressanta i Windows PowerShell är skriptfiler (.ps1), skriptfiler data (.psd1) och modulen skriptfiler (.psm1). De här filtyperna är färgade i skriptfönstret redigeraren syntax. Andra vanliga filtyper som du kan öppna i skriptfönstret är konfigurationsfiler (.ps1xml), XML-filer och textfiler.

> [!NOTE]
> Windows PowerShell-körningsprincipen avgör om du kan köra skript och läsa in Windows PowerShell-profiler och konfigurationsfiler. Standardprincipen för körning begränsad, förhindrar alla skript från att köras och förhindrar inläsning av profiler. Om du vill ändra körningsprincipen för att tillåta profiler att läsa in och används, se [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) och [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).

### <a name="to-create-a-new-script-file"></a>Du skapar en ny skriptfil

I verktygsfältet klickar du på **New**, eller på den **filen** -menyn klickar du på **New**. Den skapade filen visas i en ny flik i filen under den aktuella PowerShell-fliken. Kom ihåg att PowerShell-flikar visas bara när det finns fler än en. Som standard skapas en fil av typen skript (.ps1), men den kan sparas med ett nytt namn och tillägg. Flera skriptfiler kan skapas i samma PowerShell-flik.

### <a name="to-open-an-existing-script"></a>Öppna ett befintligt skript

I verktygsfältet klickar du på **öppna**, eller på den **filen** -menyn klickar du på **öppna**. I den **öppna** dialogrutan väljer du den fil du vill öppna. Öppna filen visas i en ny flik.

### <a name="to-close-a-script-tab"></a>Stäng fliken ett skript

Klickar du på den **Stäng** ikonen (X) av fliken fil som du vill stänga eller Välj den **filen** menyn och klickar på **Stäng**.

Om filen har ändrats sedan den senast sparades, uppmanas du att spara eller ta bort den.

### <a name="to-display-the-file-path"></a>Att visa sökvägen till filen

På fliken Arkiv, pekar du på namnet på filen. Den fullständiga sökvägen till skriptfilen visas i en knappbeskrivning.

### <a name="to-run-a-script"></a>Att köra ett skript

I verktygsfältet klickar du på **kör skript**, eller på den **filen** -menyn klickar du på **kör**.

### <a name="to-run-a-portion-of-a-script"></a>Att köra en del av ett skript

1. I skriptfönstret, väljer du en del av ett skript.
2. På den **filen** -menyn klickar du på **kör**, eller i verktygsfältet klickar du på **kör**.

### <a name="to-stop-a-running-script"></a>Stoppa en som kör skript

Det finns flera sätt att sluta köra skriptet.

- Klicka på **stoppa åtgärden** i verktygsfältet
- Tryck på CTRL + BREAK
- Välj den **filen** menyn och klickar på **stoppa åtgärden**.

Att trycka på **CTRL + C** fungerar även om inte text är markerad kan i så fall **CTRL + C** mappar till kopieringsfunktionen för den markerade texten.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Hur du skriver och redigerar text i skriptfönstret

Du kan kopiera, klippa ut, klistra in, söka och ersätta text i skriptfönstret. Du kan också ångra och gör om den senaste åtgärden som du precis har utfört. Kortkommandon för dessa åtgärder är samma kortkommandon som används för alla Windows-program.

### <a name="to-enter-text-in-the-script-pane"></a>Ange text i skriptfönstret

1. Flytta markören till skriptfönstret genom att klicka i skriptfönstret eller genom att klicka på **går du till skriptfönstret** i den **visa** menyn.
2. Skapa ett skript. Syntaxfärgning och tabbifyllning ger en rikare redigering upplevelse i Windows PowerShell ISE.
3. Se [så Använd Tabbifyllning i skriptfönstret och konsolfönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) mer information om hur du använder funktionen fliken slutförande för enklare att skriva.

### <a name="to-find-text-in-the-script-pane"></a>Söka efter text i skriptfönstret

1. Du kan hitta text var som helst genom att trycka på **CTRL + F** eller på den **redigera** -menyn klickar du på **hitta i skriptet**.
2. Om du vill hitta text efter markören, trycker du på **F3** eller på den **redigera** -menyn klickar du på **Sök nästa i skriptet**.
3. Om du vill hitta text före markören, trycker du på **SKIFT + F3** eller på den **redigera** -menyn klickar du på **Sök föregående i skriptet**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Söka efter och ersätta texten i skriptfönstret

Tryck på **CTRL + H** eller på den **redigera** -menyn klickar du på **ersättas i skriptet**. Ange den text som du vill att hitta och ersättningstexten, tryck på **RETUR**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Gå till en viss rad med text i skriptfönstret

1. I skriptfönstret, trycker du på **CTRL + G** eller på den **redigera** -menyn klickar du på **går du till rad**.

2. Ange ett radnummer.

### <a name="to-copy-text-in-the-script-pane"></a>Kopiera text i skriptfönstret

1. I skriptfönstret, väljer du den text som du vill kopiera.

2. Tryck på **CTRL + C** i verktygsfältet klickar du på den **kopia** ikonen eller på den **redigera** -menyn klickar du på **kopia**.

### <a name="to-cut-text-in-the-script-pane"></a>Att klippa ut text i skriptfönstret

1. I skriptfönstret, väljer du den text som du vill minska.
2. Tryck på **CTRL + X** i verktygsfältet klickar du på den **klipp ut** ikon, eller på den **redigera** -menyn klickar du på **klipp ut**.

### <a name="to-paste-text-into-the-script-pane"></a>Klistra in text i skriptfönstret

Tryck på **CTRL + V** i verktygsfältet klickar du på den **klistra in** ikon, eller på den **redigera** -menyn klickar du på **klistra in**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Ångra en åtgärd i skriptfönstret

Tryck på **CTRL + Z** i verktygsfältet klickar du på den **ångra** ikon, eller på den **redigera** -menyn klickar du på **ångra**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Att göra om en åtgärd i skriptfönstret

Tryck på **CTRL + Y** i verktygsfältet klickar du på den **gör om** ikon, eller på den **redigera** -menyn klickar du på **gör om**.

## <a name="how-to-save-a-script"></a>Hur du sparar ett skript

En asterisk visas bredvid namnet på skriptet för att markera en fil som inte har sparats sedan det ändrades. Asterisken försvinner när filen sparas.

### <a name="to-save-a-script"></a>Spara ett skript

Tryck på **CTRL + S** i verktygsfältet klickar du på den **spara** ikonen eller på den **filen** -menyn klickar du på **spara**.

### <a name="to-save-and-name-a-script"></a>Spara och namnge ett skript

1. På den **filen** -menyn klickar du på **Spara som**. Den **Spara som** dialogrutan visas.
2. I den **filnamn** anger du ett namn för filen.
3. I den **filformat** väljer du en viss filtyp. Till exempel i den **filformat** väljer ”PowerShell-skript (\*.ps1)”.
4. Klicka på **Spara**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Spara ett skript i ASCII-kodning

Som standard sparar Windows PowerShell ISE nya skriptfiler (.ps1), skriptfiler data (.psd1) och modulen skriptfiler (.psm1) som Unicode (BigEndianUnicode) som standard. Â vill spara ett skript i en annan kodning, till exempel ASCII (ANSI), använder den **spara** eller **spara** metoder på det [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) objekt.

Följande kommando sparar ett nytt skript som MyScript.ps1 med ASCII-kodning.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Följande kommando ersätter den aktuella skriptfilen med en fil med samma namn men med ASCII-kod.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Följande kommando hämtar kodning av den aktuella filen.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE stöder följande kodningsalternativ: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 och standard. Värdet för standardalternativet varierar beroende på systemet.

Windows PowerShell ISE inte ändra kodningen skriptfiler när du använder spara eller spara som kommandon.

## <a name="see-also"></a>Se även

- [Utforska Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
