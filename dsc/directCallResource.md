---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Anropa DSC-resursmetoder direkt
ms.openlocfilehash: 3ec3a3a8da615f45f3fdd28b1c1e46e312507ed5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="calling-dsc-resource-methods-directly"></a>Anropa DSC-resursmetoder direkt

>Gäller för: Windows PowerShell 5.0

Du kan använda den [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) för att anropa direkt funktioner eller metoder för en DSC-resurs (den **Get-TargetResource**, **Set TargetResource**, och  **Test-TargetResource** funktioner för en MOF-baserade resurs eller **hämta**, **ange**, och **Test** metoder för en klass-baserade resurs).
Detta kan användas med tredje part som vill använda DSC-resurser, eller som ett bra verktyg när du arbetar med resurser.

Den här cmdleten används vanligtvis i kombination med en egenskap för metakonfigurationen `refreshMode = 'Disabled'`, men du kan använda oavsett vad **refreshMode** är inställd på.

När du anropar den **Invoke-DscResource** kan du ange vilken metod eller en funktion som ska anropas med hjälp av den **metoden** parameter. Du kan ange egenskaper för resursen genom att skicka en hash-tabell som värde för den **egenskapen** parameter.

Följande är exempel på direkt anropar resurs metoder:

## <a name="ensure-a-file-is-present"></a>Se till att det finns en fil

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Testa att det finns en fil

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>Hämta innehållet i filen

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Obs:** direkt anropar sammansatta resurs metoder inte stöds. I stället anropa de underliggande resurserna som utgör sammansatta resursen.

## <a name="see-also"></a>Se även
- [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md)
- [Skriva en anpassad DSC-resurs med PowerShell-klasser](authoringResourceClass.md)
- [Felsök DSC-resurser](debugResource.md)