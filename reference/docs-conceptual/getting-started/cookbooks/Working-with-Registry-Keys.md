---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Arbeta med registernycklar
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951706"
---
# <a name="working-with-registry-keys"></a>Arbeta med registernycklar

Eftersom registernycklar objekt på Windows PowerShell-enheter kan påminner arbeta med dem mycket om att arbeta med filer och mappar. En kritisk skillnaden är att varje objekt på en registerbaserade Windows PowerShell-enhet är en behållare, precis som en mapp på en filsystemets enhet. Registerposter och deras associerade värden är dock egenskaperna för objekt som inte olika objekt.

### <a name="listing-all-subkeys-of-a-registry-key"></a>Visar en lista över alla undernycklar till en registernyckel

Du kan visa alla objekt direkt i en registernyckel med hjälp av **Get-ChildItem**. Lägga till valfria **kraft** parametern för att visa dolda eller system-objekt. Till exempel detta kommando visar objekten direkt i Windows PowerShell-enhet HKCU:, som motsvarar registreringsdatafilen HKEY_CURRENT_USER:

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

Dessa är de översta nycklarna visas under HKEY_CURRENT_USER i Registereditorn (Regedit.exe).

Du kan också ange den här sökvägen i registret genom att ange register-provider-namn, följt av ”**::**”. Register-provider fullständiga namnet är **Microsoft.PowerShell.Core\\registret**, men detta kan vara förkortas så för att bara **registret**. Något av följande kommandon visar en lista över innehållet direkt under HKCU:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Dessa kommandon listan endast direkt ingående objekt, ungefär som använder Cmd.exe's **DIR** kommando eller **ls** i ett UNIX-gränssnitt. Om du vill visa objekten, måste du ange den **Recurse** parameter. Använd följande kommando (åtgärden kan ta en mycket lång tid). Om du vill visa alla registernycklar i HKCU:

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** kan utföra komplexa filtreringsfunktioner via dess **sökväg**, **Filter**, **inkludera**, och **undanta**parametrar, men de här parametrarna vanligtvis endast baseras på namn. Du kan utföra komplexa filtrering baserat på andra egenskaper för objekt med hjälp av **Where-Object** cmdlet. Följande kommando hittar alla nycklar i HKCU:\\programvara som har fler än en undernycklar och även ha exakt fyra värden:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Kopiera nycklarna

Kopieringen är klar med **Copy-Item**. I följande kopieras HKLM:\\programvara\\Microsoft\\Windows\\CurrentVersion och alla dess egenskaper till HKCU:\\, skapa en ny nyckel med namnet ”CurrentVersion”:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Om du undersöker den här nya nyckeln i Registereditorn eller genom att använda **Get-ChildItem**, ser du att du inte har kopior av undernycklarna som finns på den nya platsen. För att kopiera hela innehållet i en behållare, måste du ange den **Recurse** parameter. Om du vill göra det föregående kopiera kommandot rekursivt använder det här kommandot:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Du kan fortfarande använda andra verktyg som du redan har tillgängliga för att utföra filesystem kopior. Alla verktyg för redigering av registret, inklusive reg.exe regini.exe och regedit.exe—and COM-objekt som stöder redigering av registret (till exempel WScript.Shell och WMI StdRegProv-klassen) kan användas i Windows PowerShell.

### <a name="creating-keys"></a>Skapa nycklar

Skapa nya nycklar i registret är enklare än om du skapar ett nytt objekt i ett filsystem. Eftersom alla registernycklar är behållare, behöver du inte ange vilken typ av objekt; du bara ange en explicit sökväg som:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

Du kan också använda en provider-baserad sökväg för att ange en nyckel:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>Ta bort nycklar

Ta bort objekt är i stort sett densamma för alla leverantörer. Objekt tas bort tyst i följande kommandon:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Ta bort alla nycklar Under en viss nyckel

Du kan ta bort ingående objekt med hjälp av **ta bort objektet**, men du uppmanas att bekräfta borttagningen om artikeln innehåller någonting annat. Om vi försöker ta bort HKCU exempelvis:\\CurrentVersion-undernyckeln vi skapade, vi finns här:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Om du vill ta bort ingående objekt utan att ange den **-Recurse** parameter:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Om du vill ta bort alla objekt i HKCU:\\CurrentVersion men inte HKCU:\\CurrentVersion sig själv kan du istället använda:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```