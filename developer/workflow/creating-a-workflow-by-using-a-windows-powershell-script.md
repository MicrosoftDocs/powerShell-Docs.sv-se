---
title: Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844746"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript

Du kan skapa ett arbetsflöde genom att skriva ett Windows PowerShell-skript. Använd nyckelord för arbetsflöde följt av ett namn för arbetsflödet innan innehållet i skriptet för att skapa ett arbetsflöde. Till exempel:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Du hittar arbetsflödet i på samma sätt som andra Windows PowerShell-kommando.

## <a name="implementing-parallel-and-sequence"></a>Implementera parallell- och

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) stöder körning av aktiviteter parallellt. För att implementera den här funktionen i ett Windows PowerShell-skript, använda den `parallel` nyckelordet framför ett skriptblock. Du kan också använda den `foreach -parallel` konstruktion att gå igenom en uppsättning objekt parallellt. Ange den gruppen med aktiviteter inom ett skriptblock och föregå blocket med nyckelordet sekvens för att köra en grupp med aktiviteter i sekventiell ordning inom en parallell block.

## <a name="joining-computers-to-a-domain"></a>Ansluta datorer till en domän

Följande skript skapar ett arbetsflöde som kontrollerar domänen för en grupp användardefinierade datorer och kopplar dem till en domän om de inte redan är ansluten och kontrollerar status igen. Det här är en skriptversion av XAML-arbetsflödet som beskrivs i [skapar ett arbetsflöde med Windows PowerShell aktiviteter](./creating-a-workflow-with-windows-powershell-activities.md).

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