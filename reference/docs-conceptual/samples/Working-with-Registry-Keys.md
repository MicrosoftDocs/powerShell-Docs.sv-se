---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Arbeta med registernycklar
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736853"
---
# <a name="working-with-registry-keys"></a>Arbeta med registernycklar

Eftersom register nycklar är objekt på PowerShell-enheter, är det mycket likt att arbeta med filer och mappar. En kritisk skillnad är att varje objekt på en register-baserad PowerShell-enhet är en behållare, precis som en mapp på en fil system enhet. Register poster och deras associerade värden är dock egenskaper för objekten, inte distinkta objekt.

## <a name="listing-all-subkeys-of-a-registry-key"></a>Lista alla under nycklar för en register nyckel

Du kan visa alla objekt direkt i en register nyckel med hjälp `Get-ChildItem`av. Lägg till den valfria **Force** -parametern om du vill visa dolda eller system objekt. Detta kommando visar till exempel objekten direkt i PowerShell-enheten `HKCU:`, som motsvarar `HKEY_CURRENT_USER` registrerings data filen:

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

Det här är nycklarna på den översta nivån som `HKEY_CURRENT_USER` visas under i Registereditorn (regedit. exe).

Du kan också ange den här register Sök vägen genom att ange namnet på registrerings leverantören följt `::`av. Register leverantörens fullständiga namn är `Microsoft.PowerShell.Core\Registry`, men detta kan kortas ned till bara. `Registry` Något av följande kommandon visar innehållet direkt under `HKCU:`.

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Kommandona visar bara de objekt som finns direkt, ungefär som `DIR` att använda i **cmd. exe** eller `ls` i ett UNIX-gränssnitt. Om du vill visa tillgängliga objekt måste du ange parametern **rekursivt** . Om du vill visa alla register `HKCU:`nycklar i använder du följande kommando.

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

`Get-ChildItem`kan utföra komplexa filtrerings funktioner med hjälp av **sökvägen**, **filtrera**, **Inkludera**och **exkludera** parametrar, men dessa parametrar baseras vanligt vis endast på namn. Du kan utföra komplex filtrering baserat på andra egenskaper för objekt med hjälp av `Where-Object` cmdleten. Följande kommando hittar alla nycklar i `HKCU:\Software` som inte har fler än en under nyckel och har även exakt fyra värden:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>Kopierar nycklar

Kopieringen görs med `Copy-Item`. I följande exempel kopieras `CurrentVersion` under nyckeln för `HKLM:\SOFTWARE\Microsoft\Windows\` och alla dess egenskaper till. `HKCU:\`

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

Om du undersöker den nya nyckeln i Registereditorn eller använder `Get-ChildItem`kan du se att du inte har kopior av de inneslutna under nycklarna på den nya platsen. För att kunna kopiera allt innehåll i en behållare måste du ange parametern **rekursivt** . Om du vill göra föregående kopierings kommando rekursivt använder du följande kommando:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

Du kan fortfarande använda andra verktyg som du redan har tillgängligt för att utföra fil Systems kopior. Alla redigerings verktyg för registret, inklusive **reg. exe**, **regini. exe**, **regedit. exe**och com-objekt som stöder redigering av registret, till exempel **wscript. Shell** och WMI: s **StdRegProv** -klass kan användas i Windows PowerShell.

## <a name="creating-keys"></a>Skapar nycklar

Det är enklare att skapa nya nycklar i registret än att skapa ett nytt objekt i ett fil system. Eftersom alla register nycklar är behållare behöver du inte ange typ av objekt. du anger bara en explicit sökväg, till exempel:

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

Du kan också använda en provider-baserad sökväg för att ange en nyckel:

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a>Tar bort nycklar

Att ta bort objekt är i princip samma för alla leverantörer. Följande kommandon tar bort objekt tyst:

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>Ta bort alla nycklar under en angiven nyckel

Du kan ta bort de objekt som `Remove-Item`finns med, men du uppmanas att bekräfta borttagningen om objektet innehåller något annat. Om vi till exempel försöker ta bort `HKCU:\CurrentVersion` under nyckeln som vi skapade, ser vi följande:

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Om du vill ta bort de objekt som finns utan att du behöver göra det anger du parametern **rekursivt** :

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Om du vill ta bort alla objekt inom `HKCU:\CurrentVersion` men inte `HKCU:\CurrentVersion` själv, kan du istället använda:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
