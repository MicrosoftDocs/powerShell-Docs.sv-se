---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Anropa DSC-resursmetoder direkt
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685678"
---
# <a name="calling-dsc-resource-methods-directly"></a>Anropa DSC-resursmetoder direkt

>Gäller för: Windows PowerShell 5.0

Du kan använda den [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet för att direkt anropar funktioner eller metoder för en DSC-resurs (den **Get-TargetResource**, **Set-TargetResource**, och  **Test-TargetResource** funktioner i en MOF-baserad resurs eller **hämta**, **ange**, och **Test** metoder för en MOF-baserade resurs).
Detta kan användas med tredje part som vill använda DSC-resurser, eller som ett bra verktyg när du utvecklar resurser.

Denna cmdlet används vanligtvis i kombination med en egenskap för metaconfiguration `refreshMode = 'Disabled'`, men du kan använda oavsett vad **refreshMode** är inställd på.

När du anropar den **Invoke-DscResource** kan du ange vilken metod eller funktion som ska anropas med hjälp av den **metoden** parametern. Du anger egenskaperna för resursen genom att skicka en hash-tabell som värde för den **egenskapen** parametern.

Här följer några exempel på att anropa-resursmetoder direkt:

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

>**Obs:** Anropa direkt sammansatta resursmetoder stöds inte. I stället anropa de underliggande resurserna som utgör den sammansatta resursen.

## <a name="see-also"></a>Se även
- [Skriva en anpassad DSC-resurs med MOF](../resources/authoringResourceMOF.md)
- [Skriva en anpassad DSC-resurs med PowerShell-klasser](../resources/authoringResourceClass.md)
- [Felsök DSC-resurser](../troubleshooting/debugResource.md)