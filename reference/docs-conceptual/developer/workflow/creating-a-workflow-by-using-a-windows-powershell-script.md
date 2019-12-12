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
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356646"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript

Du kan skapa ett arbets flöde genom att skriva ett Windows PowerShell-skript. Om du vill skapa ett arbets flöde använder du arbets flödets nyckelord följt av ett namn för arbets flödet före bröd texten i skriptet. Till exempel:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Du hittar arbets flödet på samma sätt som med andra Windows PowerShell-kommandon.

## <a name="implementing-parallel-and-sequence"></a>Implementera parallell och sekvens

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) stöder körning av aktiviteter parallellt. Om du vill implementera den här funktionen i ett Windows PowerShell-skript använder du nyckelordet `parallel` framför ett skript block. Du kan också använda `foreach -parallel` konstruktion för att iterera genom en samling objekt parallellt. Om du vill köra en grupp med aktiviteter i nummerordning i ett parallellt block, omger du den gruppen med aktiviteter i ett-skript block och föregår blocket med nyckelordet Sequence.

## <a name="joining-computers-to-a-domain"></a>Ansluta datorer till en domän

Följande skript skapar ett arbets flöde som kontrollerar domän status för en grupp med användardefinierade datorer, kopplar dem till en domän om de inte redan är anslutna och kontrollerar sedan statusen igen. Det här är en skript version av XAML-arbetsflödet som beskrivs i [skapa ett arbets flöde med Windows PowerShell-aktiviteter](./creating-a-workflow-with-windows-powershell-activities.md).

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