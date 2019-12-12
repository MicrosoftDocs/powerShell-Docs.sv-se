---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Arbeta med registernycklar
ms.openlocfilehash: 18daeaea2ee8917a709fef421d2b316f46bf7f4c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030652"
---
# <a name="working-with-registry-keys"></a>Arbeta med registernycklar

Eftersom register nycklar är objekt på Windows PowerShell-enheter, är det mycket likt att arbeta med filer och mappar. En kritisk skillnad är att varje objekt på en register-baserad Windows PowerShell-enhet är en behållare, precis som en mapp på en fil system enhet. Register poster och deras associerade värden är dock egenskaper för objekten, inte distinkta objekt.

## <a name="listing-all-subkeys-of-a-registry-key"></a>Lista alla under nycklar för en register nyckel

Du kan visa alla objekt direkt i en register nyckel med hjälp av **Get-ChildItem**. Lägg till den valfria **Force** -parametern om du vill visa dolda eller system objekt. Till exempel visar det här kommandot objekten direkt i Windows PowerShell-enheten HKCU:, som motsvarar HKEY_CURRENT_USER registrerings data fil:

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

Det här är nycklarna på den översta nivån som visas under HKEY_CURRENT_USER i Registereditorn (regedit. exe).

Du kan också ange den här register Sök vägen genom att ange namnet på register leverantören följt av " **::** ". Register leverantörens fullständiga namn är **Microsoft. PowerShell. Core\\Registry**, men detta kan kortas ned till bara **registret**. Något av följande kommandon visar innehållet direkt under HKCU:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

De här kommandona visar bara de direkt objekt som finns, ungefär som att använda CMD. Exes **dir** -kommando eller **ls** i ett UNIX-gränssnitt. Om du vill visa tillgängliga objekt måste du ange parametern **rekursivt** . Om du vill visa alla register nycklar i HKCU använder du följande kommando (den här åtgärden kan ta lång tid.):

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** kan utföra komplexa filtrerings funktioner via **sökväg**, **filtrera**, **Inkludera**och **exkludera** parametrar, men dessa parametrar baseras vanligt vis på namn. Du kan utföra komplex filtrering baserat på andra egenskaper för objekt med hjälp av cmdleten **Where-Object** . Följande kommando hittar alla nycklar i HKCU:\\program vara som inte har fler än en under nyckel och också har exakt fyra värden:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>Kopierar nycklar

Kopieringen görs med **Kopiera objekt**. Följande kommando kopierar HKLM:\\program vara\\Microsoft\\Windows\\CurrentVersion och alla dess egenskaper till HKCU:\\, vilket skapar en ny nyckel med namnet "CurrentVersion":

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Om du undersöker den nya nyckeln i Registereditorn eller använder **Get-ChildItem**, ser du att du inte har kopior av de inneslutna under nycklarna på den nya platsen. För att kunna kopiera allt innehåll i en behållare måste du ange parametern **rekursivt** . Om du vill göra föregående kopierings kommando rekursivt använder du följande kommando:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Du kan fortfarande använda andra verktyg som du redan har tillgängligt för att utföra fil Systems kopior. Alla redigerings verktyg för registret, inklusive REG. exe, regini. exe och regedit. exe – och COM-objekt som stöder redigering av registret (till exempel WScript. Shell och WMI: s StdRegProv-klass) kan användas i Windows PowerShell.

## <a name="creating-keys"></a>Skapar nycklar

Det är enklare att skapa nya nycklar i registret än att skapa ett nytt objekt i ett fil system. Eftersom alla register nycklar är behållare behöver du inte ange typ av objekt. du anger bara en explicit sökväg, till exempel:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

Du kan också använda en provider-baserad sökväg för att ange en nyckel:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

## <a name="deleting-keys"></a>Tar bort nycklar

Att ta bort objekt är i princip samma för alla leverantörer. Följande kommandon tar bort objekt tyst:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>Ta bort alla nycklar under en angiven nyckel

Du kan ta bort objekt som finns med hjälp av **Remove-item**, men du uppmanas att bekräfta borttagningen om objektet innehåller något annat. Om vi till exempel försöker ta bort följande HKCU:\\CurrentVersion-under nyckel som vi skapade, ser vi följande:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Om du vill ta bort de objekt som finns utan att ange parametern **-rekursivt** :

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Om du vill ta bort alla objekt i HKCU:\\CurrentVersion, men inte HKCU:\\CurrentVersion, kan du i stället använda:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
