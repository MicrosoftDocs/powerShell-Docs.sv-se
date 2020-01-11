---
title: Skapa ett arbets flöde med hjälp av ett Windows PowerShell-skript | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5720200ce32f114cd4965d961b9e2804bd154b2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870854"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript

Du kan skapa ett arbets flöde genom att skriva ett Windows PowerShell-skript. Om du vill skapa ett arbets flöde använder du arbets flödets nyckelord följt av ett namn för arbets flödet före bröd texten i skriptet. Ett exempel:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Du hittar arbets flödet på samma sätt som med andra Windows PowerShell-kommandon.

## <a name="implementing-parallel-and-sequence"></a>Implementera parallell och sekvens

[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) stöder körning av aktiviteter parallellt. Om du vill implementera den här funktionen i ett Windows PowerShell-skript använder du nyckelordet `parallel` framför ett skript block. Du kan också använda `foreach -parallel` konstruktion för att iterera genom en samling objekt parallellt. Om du vill köra en grupp med aktiviteter i nummerordning i ett parallellt block, omger du den gruppen med aktiviteter i ett-skript block och föregår blocket med nyckelordet Sequence.

## <a name="joining-computers-to-a-domain"></a>Ansluta datorer till en domän

Följande skript skapar ett arbets flöde som kontrollerar domän status för en grupp med användardefinierade datorer, kopplar dem till en domän om de inte redan är anslutna och kontrollerar sedan statusen igen.
Det här är en skript version av XAML-arbetsflödet som beskrivs i [skapa ett arbets flöde med Windows PowerShell-aktiviteter](./creating-a-workflow-with-windows-powershell-activities.md).

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```