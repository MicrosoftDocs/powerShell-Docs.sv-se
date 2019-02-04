---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med registernycklar
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686952"
---
# <a name="working-with-registry-keys"></a>Arbeta med registernycklar

Eftersom registernycklar finns på Windows PowerShell-enheter, påminner arbeta med dem mycket om att arbeta med filer och mappar. En viktig skillnad är att varje objekt i en registerbaserade Windows PowerShell-enhet är en behållare, precis som en mapp på en filsystemets enhet. Registerposter och deras associerade värden är dock egenskaperna hos objekten inte olika objekt.

### <a name="listing-all-subkeys-of-a-registry-key"></a>Visa en lista över alla undernycklar till en registernyckel

Du kan visa alla objekt direkt i en registernyckel med hjälp av **Get-ChildItem**. Lägg till det valfria **kraft** parameter för att visa dolda eller poster. Till exempel det här kommandot visar objekt direkt i Windows PowerShell-enhet HKCU:, som motsvarar registreringsdatafilen HKEY_CURRENT_USER:

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

Det här är de översta nycklarna som visas under HKEY_CURRENT_USER i Registereditorn (Regedit.exe).

Du kan också ange den här sökvägen i registret genom att ange registret leverantörens namn följt av ”**::**”. Det fullständiga namnet för register-provider är **Microsoft.PowerShell.Core\\registret**, men detta kan vara kortats ned för att bara **registret**. Något av följande kommandon visar en lista över innehållet direkt under HKCU:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

De här kommandona visar endast direkt ingående objekt, ungefär som med Cmd.exe's **DIR** kommando eller **ls** i ett UNIX-gränssnitt. För att visa ingående objekt, måste du ange den **Recurse** parametern. Om du vill visa alla registernycklar i HKCU, använder du följande kommando (den här åtgärden kan ta en mycket lång tid.):

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** kan utföra avancerade filtreringsfunktioner via dess **sökväg**, **Filter**, **inkludera**, och **undanta**parametrar, men de här parametrarna vanligtvis endast baseras på namnet. Du kan utföra komplex filtrering baserat på andra egenskaper för objekt med hjälp av den **Where-Object** cmdlet. Kommandot söker efter alla nycklar i HKCU:\\programvara som har mer än en undernyckel och samtidigt ha exakt fyra värden:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Kopiera nycklar

Kopieringen är klar med **Copy-Item**. I följande kopieras HKLM:\\programvara\\Microsoft\\Windows\\CurrentVersion och alla dess egenskaper så att HKCU:\\, skapa en ny nyckel med namnet ”CurrentVersion”:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Om du granskar den här nya nyckeln i Registereditorn eller genom att använda **Get-ChildItem**, ser du att du inte har kopior av inneslutna undernycklar i den nya platsen. För att kopiera alla innehållet i en behållare, måste du ange den **Recurse** parametern. Om du vill göra det föregående kopiera kommandot rekursivt, använder du det här kommandot:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Du kan fortfarande använda andra verktyg som du redan har tillgängliga för att utföra filsystem kopior. Alla registerredigeringsverktygen – inklusive reg.exe och regini.exe regedit.exe—and COM-objekt som har stöd för redigering av registret (till exempel WScript.Shell och WMI StdRegProv-klassen) kan användas i Windows PowerShell.

### <a name="creating-keys"></a>Hur du skapar nycklar

Skapa nya nycklar i registret är enklare än att skapa ett nytt objekt i ett filsystem. Eftersom alla registernycklar är behållare, behöver du inte ange objekttypen; du bara ange en explicit sökväg, till exempel:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

Du kan också använda en provider-baserad sökväg för att ange en nyckel:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>Ta bort nycklar

Ta bort objekt är i stort sett desamma för alla leverantörer. Följande kommandon raderas tyst objekt:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Ta bort alla nycklar Under en viss nyckel

Du kan ta bort ingående objekt med hjälp av **Remove-Item**, men du kommer att uppmanas att bekräfta borttagningen om objektet innehåller något annat. Exempel: om vi försöker ta bort HKCU:\\CurrentVersion-undernyckeln infogades, ser vi detta:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Om du vill ta bort ingående objekt utan att fråga, ange den **-Recurse** parameter:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Om du vill ta bort alla objekt i HKCU:\\CurrentVersion men inte HKCU:\\CurrentVersion själva, du kan i stället använda:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```