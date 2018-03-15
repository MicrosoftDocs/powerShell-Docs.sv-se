---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Skriv och kör skript i Windows PowerShell ISE"
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 77d8ae81cb03f03b3b5d044e6503bbb23cb5b771
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Skriv och kör skript i Windows PowerShell ISE
Det här avsnittet beskriver hur du skapar, redigerar, kör och spara skript i skriptfönstret.

## <a name="how-to-create-and-run-scripts"></a>Hur du skapar och kör skript
Du kan öppna och redigera filer i Windows PowerShell i skriptfönstret. Specifika filtyper av intresse för Windows PowerShell är skriptfiler (.ps1), skript datafiler (.psd1) och skriptfiler modul (.psm1). De här filtyperna är syntax färgade i Redigeraren för skriptfönster. Andra vanliga filtyper som du kan öppna i skriptfönstret är konfigurationsfiler (.ps1xml), XML-filer och textfiler.

> [!NOTE]
> Windows PowerShell-körningsprincipen avgör om du kan köra skript och ladda konfigurationsfiler och profiler för Windows PowerShell. Körningsprincipen standard begränsad, förhindrar alla skript från att köras och förhindrar att läsa in profiler. Om du vill ändra körningsprincipen för att tillåta profiler för att läsa in och användas [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) och [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### <a name="to-create-a-new-script-file"></a>Skapa en ny skriptfil
I verktygsfältet klickar du på **ny** , eller på den **filen** -menyn klickar du på **ny**. Skapade filen visas i en ny flik filen under aktuell PowerShell-fliken. Kom ihåg att PowerShell-flikar visas endast när det finns fler än en. Som standard skapas en fil av typen skript (.ps1), men den kan sparas med ett nytt namn och filnamnstillägg. Flera filer kan skapas på samma flik i PowerShell.

### <a name="to-open-an-existing-script"></a>Öppna ett befintligt skript
I verktygsfältet klickar du på **öppna**, eller på den **filen** -menyn klickar du på **öppna**. I den **öppna** dialogrutan Välj filen som du vill öppna. Öppna filen visas i en ny flik.

### <a name="to-close-a-script-tab"></a>Stäng fliken ett skript
Klicka på fliken skript på det skript som du vill stänga och gör sedan något av följande:

1. Klicka på den **Stäng** ikon (X) på fliken skript.

2. På den **filen** -menyn klickar du på **Stäng**.

Om filen har ändrats sedan den senast sparades, uppmanas du att spara eller ta bort den.

### <a name="to-display-the-file-path"></a>Så här visar du sökvägen till filen
Peka på filnamnet på fliken Arkiv. Den fullständiga sökvägen till skriptfilen visas i en knappbeskrivning.

### <a name="to-run-a-script"></a>Att köra ett skript
I verktygsfältet klickar du på **kör skriptet**, eller på den **filen** -menyn klickar du på **kör**.

### <a name="to-run-a-portion-of-a-script"></a>Att köra en del av ett skript

1. Välj en del av ett skript i rutan skript.

2. På den **filen** -menyn klickar du på **kör**, eller i verktygsfältet klickar du på **kör**.

### <a name="to-stop-a-running-script"></a>Stoppa ett skript som körs
I verktygsfältet klickar du på **stoppa åtgärden**, tryck på CTRL + BREAK, eller på den **filen** -menyn klickar du på **stoppa åtgärden**. När du trycker på **CTRL + C** fungerar även om vissa text är markerad, vilket innebär **CTRL + C** mappar till kopieringsfunktionen för den markerade texten.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Hur du skriver och redigera texten i skriptfönstret
Använd följande steg om du vill redigera texten i rutan skript. Du kan kopiera, Klipp ut, klistra in, söka och ersätta text. Du kan också ångra och gör om den senaste åtgärden som du nyss utfört. Kortkommandon för att utföra dessa åtgärder är samma som de som används för alla Windows-program.

### <a name="to-enter-text-in-the-script-pane"></a>Ange text i skriptfönstret

1. Flytta markören till skriptfönstret genom att klicka i skriptfönstret eller genom att klicka på **går du till Skriptfönster** i den **visa** menyn.

2. Skapa ett skript. Syntaxen färgläggning och flikavslutande gör du detta en rikare upplevelse i Windows PowerShell ISE.

3. Se [så Använd Flikavslutande i fönstret skript och konsolfönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) mer information om hur du använder funktionen fliken slutförande för att underlätta att skriva.

### <a name="to-find-text-in-the-script-pane"></a>Söka efter text i skriptfönstret

1. Om du vill söka efter text var som helst, trycker du på **CTRL + F** eller på den **redigera** -menyn klickar du på **hitta i skriptet**.

2. Om du vill söka efter text efter markören trycker du på **F3** eller på den **redigera** -menyn klickar du på **Sök nästa i skriptet**.

3. Om du vill söka efter text före markören trycker du på **SKIFT + F3** eller på den **redigera** -menyn klickar du på **Sök föregående i skriptet**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Söka efter och ersätta texten i rutan skript
Tryck på **CTRL + H** eller på den **redigera** -menyn klickar du på **ersätta i skriptet**. Ange både den text som du vill söka efter och den text som du vill ersätta den och tryck sedan på **RETUR**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Gå till en viss textrad i skriptfönstret

1. I rutan skript trycker du på **CTRL + G** eller på den **redigera** -menyn klickar du på **går du till rad**.

2. Ange ett radnummer.

### <a name="to-copy-text-in-the-script-pane"></a>Kopiera text i skriptfönstret

1. Välj den text som du vill kopiera i rutan skript.

2. Tryck på **CTRL + C** i verktygsfältet klickar du på den **kopiera** ikonen, eller på den **redigera** -menyn klickar du på **kopiera**.

### <a name="to-cut-text-in-the-script-pane"></a>Att klippa ut text i skriptfönstret

1. Välj den text som du vill minska i rutan skript.

2. Tryck på **CTRL + X** i verktygsfältet klickar du på den **klipp ut** ikonen, eller på den **redigera** -menyn klickar du på **klipp ut**.

### <a name="to-paste-text-into-the-script-pane"></a>Klistra in texten i rutan skript
Tryck på **CTRL + V** i verktygsfältet klickar du på den **klistra in** ikonen, eller på den **redigera** -menyn klickar du på **klistra in**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Återställa en åtgärd i skriptfönstret
Tryck på **CTRL + Z** i verktygsfältet klickar du på den **ångra** ikonen, eller på den **redigera** -menyn klickar du på **ångra**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Om en åtgärd i skriptfönstret
Tryck på **CTRL + Y** i verktygsfältet klickar du på den **gör om** ikonen, eller på den **redigera** -menyn klickar du på **gör om**.

## <a name="how-to-save-a-script"></a>Så här sparar du ett skript
Använd följande steg för att spara och namnge ett skript. En asterisk visas bredvid namnet på att markera en fil som inte har sparats eftersom den har ändrats. Asterisken försvinner när filen sparas.

### <a name="to-save-a-script"></a>Att spara ett skript
Tryck på **CTRL + S** i verktygsfältet klickar du på den **spara** ikonen, eller på den **filen** -menyn klickar du på **spara**.

### <a name="to-save-and-name-a-script"></a>Spara och namnge ett skript

1. På den **filen** -menyn klickar du på **Spara som**. Den **Spara som** visas dialogrutan.

2. I den **filnamn** anger du ett namn för filen.

3. I den **filformat** väljer du en filtyp. Till exempel i den **filformat** väljer ' œPowerShell skript (\* .ps1)'.

4. Klicka på **Spara**.

### <a name="to-save-a-script-in-ascii-encoding"></a>För att spara ett skript i ASCII-kodning
Som standard sparas Windows PowerShell ISE nya skriptfiler (.ps1), skript datafiler (.psd1) och skriptfiler modul (.psm1) som Unicode (BigEndianUnicode) som standard. Â att spara ett skript i en annan kodning, till exempel ASCII (ANSI), använder den **spara** eller **SaveAs** metoder på det [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) objekt.

Följande kommando sparar ett nytt skript som MyScript.ps1 med ASCII-kodning.

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Följande kommando ersätter den aktuella skriptfilen med en fil med samma namn men med ASCII-kodning.

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Följande kommando hämtar kodning för den aktuella filen.

```
$psise.CurrentFile.encoding
```

Windows PowerShell ISE stöder följande alternativ för kodning: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 och standard. Värdet för alternativet varierar beroende på systemet.

Windows PowerShell ISE inte ändra kodningen av skript som har skapats med andra program, även när du använder spara eller spara som-kommandon i Windows PowerShell ISE.

## <a name="see-also"></a>Se även
- [Utforska Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
