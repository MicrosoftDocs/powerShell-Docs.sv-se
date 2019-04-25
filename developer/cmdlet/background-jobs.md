---
title: Bakgrundsjobb | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068697"
---
# <a name="background-jobs"></a>Bakgrundsjobb

Cmdlet: ar kan utföra sina åtgärder internt eller som ett Windows PowerShell*bakgrundsjobbet*. När en cmdlet körs i bakgrunden på arbetet utförs asynkront i en egen separat från den pipeline-tråden med hjälp av cmdlet: en tråd. Ur användare när en cmdlet körs i bakgrunden, returnerar Kommandotolken omedelbart även om jobbet tar längre tid att slutföra och användaren kan fortsätta utan avbrott medan jobbet körs.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Bakgrundsjobb, underordnade jobb och jobbet databasen

Objektet som returneras av cmdlet: ar som stöder bakgrundsjobb definierar jobbet. (Den [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet även returnerar ett jobbobjekt.) Namnet på jobbet, en identifierare som används för att ange jobbet, tillståndsinformationen och det underordnade jobbet ingår i den här definitionen. Jobbet utför inte någon av arbetet. Varje bakgrundsjobbet har minst ett underordnat jobb eftersom underordnat jobb utför det faktiska arbetet. När du kör en cmdlet så att arbetet utförs i bakgrunden, cmdlet: en måste lägga till jobbet och det underordnade jobbet till en gemensam databas, kallas de *jobbet databasen*.

Mer information om hur bakgrundsjobb hanteras på kommandoraden finns i följande:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Skriva en Cmdlet som körs i bakgrunden

Om du vill skriva en cmdlet som kan köras i bakgrunden, måste du utföra följande uppgifter:

- Definiera en `asJob` växla parametern så att användaren kan välja om du vill köra cmdleten i bakgrunden.

- Skapa ett objekt som härleds från den [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) klass. Det här objektet kan vara en anpassad jobbobjektet eller ett jobbobjekt som tillhandahålls av Windows PowerShell, till exempel en [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objekt.

- I en post bearbetning av-metoden lägger du till en `if` -instruktion som identifierar om cmdleten ska köras i bakgrunden.

- Implementera klassen jobb för anpassade jobbobjekt.

- Returnera de lämpliga objekt, beroende på om cmdleten körs i bakgrunden.

Finns ett kodexempel i [så Support jobb](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>Bakgrund jobbrelaterade API: er

Följande API: er tillhandahålls av Windows PowerShell för att hantera bakgrundsjobb.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) härleds anpassade jobbobjekt. Det här är en abstrakt klass.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) hanterar och ger information om de aktuella aktiva bakgrundsjobb.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definierar tillståndet för bakgrundsjobbet. Tillstånd är igång, körs och stoppad.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) innehåller information om tillståndet för ett bakgrundsjobb och, om det senaste tillståndet ändrar orsakades av ett fel, orsak som jobbet har angett det aktuella tillståndet.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) ger argumenten för en händelse som utlöses när ett bakgrundsjobb ändrar tillstånd.

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell-Job-Cmdlets

Följande cmdletar tillhandahålls av Windows PowerShell för att hantera bakgrundsjobb.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Hämtar Windows PowerShell-bakgrundsjobb som körs i den aktuella sessionen.

[Ta emot jobb](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Hämtar resultaten av Windows PowerShell-bakgrundsjobb i den aktuella sessionen.

[Ta bort jobb](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Tar bort ett Windows PowerShell-bakgrundsjobb.

[Starta jobb](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Startar ett Windows PowerShell-bakgrundsjobb.

[Stoppa jobb](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Stoppar ett Windows PowerShell-bakgrundsjobb.

[Wait-jobb](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Undertrycker Kommandotolken förrän en eller alla av Windows PowerShell-bakgrundsjobb som körs i sessionen har slutförts.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
