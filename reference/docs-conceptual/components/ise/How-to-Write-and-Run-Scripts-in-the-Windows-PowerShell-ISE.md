---
ms.date: 01/02/2020
keywords: PowerShell, cmdlet
title: Skriv och kör skript i Windows PowerShell ISE
ms.openlocfilehash: 2e3122a3b436ba878d2c5f9d72d4f9e024d4d031
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "79406981"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Skriv och kör skript i Windows PowerShell ISE

Den här artikeln beskriver hur du skapar, redigerar, kör och sparar skript i fönstret skript.

## <a name="how-to-create-and-run-scripts"></a>Så här skapar och kör du skript

Du kan öppna och redigera Windows PowerShell-filer i skript fönstret. Specifika filtyper av intresse i Windows PowerShell är skriptfiler (`.ps1`), skript data filer (`.psd1`) och skriptfiler (`.psm1`). Dessa filtyper är syntax som är färgade i redigerings fönstret för skript. Andra vanliga filtyper som du kan öppna i skript fönstret är konfigurationsfiler (`.ps1xml`), XML-filer och textfiler.

> [!NOTE]
> Windows PowerShell-körnings principen avgör om du kan köra skript och läsa in Windows PowerShell-profiler och konfigurationsfiler. Standard körnings principen, som är begränsad, förhindrar att alla skript körs och förhindrar inläsning av profiler. Om du vill ändra körnings principen så att profiler kan läsas in och användas, se [set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) och [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).

### <a name="to-create-a-new-script-file"></a>Så här skapar du en ny skript fil

I verktygsfältet klickar du på **nytt**eller på **nytt**på **Arkiv** -menyn. Den skapade filen visas på fliken ny fil på fliken aktuell PowerShell. kom ihåg att PowerShell-flikarna bara visas när det finns fler än en. Som standard skapas en fil av typen script`.ps1`(), men den kan sparas med ett nytt namn och tillägg. Du kan skapa flera skriptfiler på samma PowerShell-flik.

### <a name="to-open-an-existing-script"></a>Öppna ett befintligt skript

Klicka på **Öppna**i verktygsfältet, eller klicka på **Öppna**på **Arkiv** -menyn. I dialog rutan **Öppna** väljer du den fil som du vill öppna. Den öppna filen visas på en ny flik.

### <a name="to-close-a-script-tab"></a>Stänga en skript-flik

Klicka på ikonen **Stäng** (**X**) på fliken Arkiv som du vill stänga eller Välj menyn **Arkiv** och klicka på **Stäng**.

Om filen har ändrats sedan den senast sparades uppmanas du att spara eller ta bort den.

### <a name="to-display-the-file-path"></a>Så här visar du sökvägen till filen

Peka på fil namnet på fliken fil. Den fullständigt kvalificerade sökvägen till skript filen visas i en knapp beskrivning.

### <a name="to-run-a-script"></a>Köra ett skript

I verktygsfältet klickar du på **Kör skript**eller på **Arkiv** -menyn och sedan på **Kör**.

### <a name="to-run-a-portion-of-a-script"></a>Köra en del av ett skript

1. I fönstret skript väljer du en del av ett skript.
2. På **Arkiv** -menyn klickar du på **Kör markering**eller på verktygsfältet klickar du på **Kör markering**.

### <a name="to-stop-a-running-script"></a>Stoppa ett skript som körs

Det finns flera sätt att stoppa ett skript som körs.

- Klicka på **stoppa åtgärd** i verktygsfältet
- Tryck på <kbd>CTRL</kbd>+<kbd>Break</kbd>
- Välj menyn **Arkiv** och klicka på **stoppa åtgärd**.

Att trycka på <kbd>CTRL</kbd>+<kbd>c</kbd> fungerar även om inte någon text är markerad, i vilket fall <kbd>CTRL</kbd>+<kbd>C</kbd> mappar till kopierings funktionen för den markerade texten.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Skriva och redigera text i skript fönstret

Du kan kopiera, klippa ut, klistra in, söka och ersätta text i skript fönstret. Du kan också ångra och göra om den senaste åtgärden som du nyss utförde. Kortkommandona för dessa åtgärder är samma kortkommandon som används för alla Windows-program.

### <a name="to-enter-text-in-the-script-pane"></a>Ange text i skript fönstret

1. Flytta markören till skript fönstret genom att klicka någonstans i skript fönstret eller genom att klicka på **gå till skript fönstret** i menyn **Visa** .
2. Skapa ett skript. Syntax färgning och TABB-ifyllnad ger en mer omfattande redigerings upplevelse i Windows PowerShell ISE.
3. Mer information om hur du använder funktionen för slut för ande av flikar finns [i skript fönstret och konsol fönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) .

### <a name="to-find-text-in-the-script-pane"></a>Hitta text i skript fönstret

1. Om du vill söka efter text var som helst, trycker du på <kbd>CTRL</kbd>+<kbd>F</kbd> eller på **Redigera** -menyn och klickar på **Sök i skript**.
2. Om du vill hitta text efter markören trycker du på <kbd>F3</kbd> eller på menyn **Redigera** klickar du på **Sök nästa i skript**.
3. Om du vill söka efter text före markören trycker du på <kbd>SKIFT</kbd>+<kbd>F3</kbd> eller på **Redigera** -menyn och klickar på **Sök föregående i skript**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Söka efter och ersätta text i skript fönstret

Tryck på <kbd>CTRL</kbd>+<kbd>H</kbd> eller på **Redigera** -menyn, klicka på **Ersätt i skript**. Ange den text som du vill söka efter och ersättnings texten och tryck sedan på <kbd>RETUR</kbd>.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>För att gå till en viss textrad i skript fönstret

1. Tryck på <kbd>CTRL +</kbd>+<kbd>G</kbd> i rutan skript och klicka på **gå till rad**på **Redigera** -menyn.

2. Ange ett rad nummer.

### <a name="to-copy-text-in-the-script-pane"></a>Kopiera text i skript fönstret

1. I rutan skript väljer du den text som du vill kopiera.

2. Tryck på <kbd>CTRL</kbd>+<kbd>C</kbd> eller, i verktygsfältet, klicka på **Kopiera** -ikonen eller på **Redigera** -menyn och klicka på **Kopiera**.

### <a name="to-cut-text-in-the-script-pane"></a>Klippa ut text i skript fönstret

1. I rutan skript väljer du den text som du vill klippa ut.
2. Tryck på <kbd>CTRL</kbd>+<kbd>X</kbd> eller, i verktygsfältet, klicka på **Klipp ut** -ikonen eller på **Redigera** -menyn och klicka på **Klipp ut**.

### <a name="to-paste-text-into-the-script-pane"></a>Klistra in text i skript fönstret

Tryck på <kbd>CTRL</kbd>+<kbd>V</kbd> eller, i verktygsfältet, klicka på ikonen **Klistra in** eller på **Redigera** -menyn och klicka på **Klistra in**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Ångra en åtgärd i skript fönstret

Tryck på <kbd>CTRL</kbd>+<kbd>Z</kbd> eller, i verktygsfältet, klicka på ikonen **Ångra** eller på **Redigera** -menyn och klicka på **Ångra**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Göra om en åtgärd i skript fönstret

Tryck på <kbd>CTRL</kbd>+<kbd>Y</kbd> eller, i verktygsfältet, klicka på ikonen **gör** om eller på **Redigera** -menyn och klicka på **gör**om.

## <a name="how-to-save-a-script"></a>Så här sparar du ett skript

En asterisk visas bredvid skript namnet för att markera en fil som inte har sparats sedan den ändrades. Asterisken försvinner när filen sparas.

### <a name="to-save-a-script"></a>Så här sparar du ett skript

Tryck på <kbd>CTRL</kbd>+<kbd>S</kbd> eller, i verktygsfältet, klicka på ikonen **Spara** eller på **Arkiv** -menyn och sedan på **Spara**.

### <a name="to-save-and-name-a-script"></a>Spara och namnge ett skript

1. Klicka på **Spara som** på **Arkiv**-menyn. Dialog rutan **Spara som** visas.
2. Ange ett namn på filen i rutan **fil namn** .
3. I rutan fil **format** väljer du en filtyp. I rutan **fil format** väljer du exempelvis PowerShell-skript (`*.ps1`).
4. Klicka på **Spara**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Så här sparar du ett skript i ASCII-kodning

Som standard sparar Windows PowerShell ISE nya skriptfiler (`.ps1`), skriptfiler`.psd1`() och skript-filer (`.psm1`) som Unicode (BigEndianUnicode) som standard. Om du vill spara ett skript i en annan kodning, till exempel ASCII (ANSI), använder du metoderna **Save** eller **savee** som på objektet [$psISE. CurrentFile](object-model/the-ise-object-model-hierarchy.md) .

Följande kommando sparar ett nytt skript som skript. ps1 med ASCII-kodning.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Följande kommando ersätter den aktuella skript filen med en fil med samma namn, men med ASCII-kodning.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Följande kommando hämtar kodningen för den aktuella filen.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE stöder följande kodnings alternativ: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 och default. Värdet för standard alternativet varierar i systemet.

Windows PowerShell ISE ändrar inte kodningen för skriptfiler när du använder Spara-eller Spara som-kommandon.

## <a name="see-also"></a>Se även

- [Utforska Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
