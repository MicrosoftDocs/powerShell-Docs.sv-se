---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Anropa DSC-resursmetoder direkt
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942253"
---
# <a name="calling-dsc-resource-methods-directly"></a>Anropa DSC-resursmetoder direkt

>Gäller för: Windows PowerShell 5,0

Du kan använda cmdleten [Invoke-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) för att direkt anropa funktioner eller metoder för en DSC-resurs (funktionen **Get-TargetResource**, **set-TargetResource**och **test-TargetResource** i en MOF-baserad resurs, eller **Get**-, **set**-och **test** metoder för en klass-baserad resurs).
Detta kan användas av tredje part som vill använda DSC-resurser eller som ett användbart verktyg när du utvecklar resurser.

Denna cmdlet används vanligt vis i kombination med en metaconfiguration- `refreshMode = 'Disabled'`egenskap, men den kan användas oavsett vad **refreshMode** är inställt på.

När du anropar cmdleten **Invoke-dscresource Keyword Supports** anger du vilken metod eller funktion som ska anropas med hjälp av **metod** parametern. Du anger egenskaperna för resursen genom att skicka en hash-egenskap som värde för **egenskaps** parametern.

Följande är exempel på anrop av resurs metoder direkt:

## <a name="ensure-a-file-is-present"></a>Se till att det finns en fil

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Testa att en fil finns

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

>**Obs:** Det finns inte stöd för direkt anrop av sammansatta resurs metoder. Anropa i stället metoderna för de underliggande resurserna som utgör den sammansatta resursen.

## <a name="see-also"></a>Se även
- [Skriva en anpassad DSC-resurs med MOF](../resources/authoringResourceMOF.md)
- [Skriva en anpassad DSC-resurs med PowerShell-klasser](../resources/authoringResourceClass.md)
- [Felsök DSC-resurser](../troubleshooting/debugResource.md)