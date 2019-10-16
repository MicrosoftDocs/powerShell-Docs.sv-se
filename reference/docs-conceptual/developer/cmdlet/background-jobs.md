---
title: Bakgrunds jobb | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354917"
---
# <a name="background-jobs"></a>Bakgrundsjobb

Cmdlets kan utföra sina åtgärder internt eller som ett*bakgrunds jobb*i Windows PowerShell. När en cmdlet körs som ett bakgrunds jobb utförs arbetet asynkront i sin egen tråd separat från pipeline-tråden som cmdleten använder. När en cmdlet körs som ett bakgrunds jobb i användar perspektivet returnerar kommando tolken omedelbart även om jobbet tar en längre tid att slutföra, och användaren kan fortsätta utan avbrott medan jobbet körs.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Bakgrunds jobb, underordnade jobb och jobb databasen

Jobbobjektet som returneras av de cmdletar som har stöd för bakgrunds jobb definierar jobbet. (Cmdleten [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) returnerar också ett Job-objekt.) Namnet på jobbet, en identifierare som används för att ange jobbet, tillståndsinformation och de underordnade jobben ingår i den här definitionen. Jobbet utför inget arbete. Varje bakgrunds jobb har minst ett underordnat jobb eftersom det underordnade jobbet utför det faktiska arbetet. När du kör en cmdlet så att arbetet utförs som ett bakgrunds jobb måste cmdleten lägga till jobbet och de underordnade jobben till en gemensam lagrings plats, som kallas *jobbets lagrings plats*.

Mer information om hur bakgrunds jobb hanteras på kommando raden finns i följande avsnitt:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Skriva en cmdlet som körs som ett bakgrunds jobb

Om du vill skriva en-cmdlet som kan köras som ett bakgrunds jobb måste du utföra följande uppgifter:

- Definiera en växel parameter för `asJob` så att användaren kan bestämma om cmdleten ska köras som ett bakgrunds jobb.

- Skapa ett objekt som härleds från klassen [system. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) . Objektet kan vara ett anpassat jobb objekt eller ett jobb objekt som tillhandahålls av Windows PowerShell, till exempel ett [system. Management. Automation. Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) -objekt.

- I en post bearbetnings metod lägger du till en `if`-instruktion som identifierar om cmdleten ska köras som ett bakgrunds jobb.

- Implementera jobb klassen för anpassade jobb objekt.

- Returnera lämpliga objekt, beroende på om cmdleten körs som ett bakgrunds jobb.

Ett kod exempel finns i [så här stöder du jobb](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>API: er för bakgrunds jobb

Följande API: er tillhandahålls av Windows PowerShell för att hantera bakgrunds jobb.

[System. Management. Automation. job](/dotnet/api/System.Management.Automation.Job) härleder anpassade jobb objekt. Detta är en abstrakt klass.

[System. Management. Automation. Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) hanterar och ger information om de aktuella aktiva bakgrunds jobben.

[System. Management. Automation. JobState](/dotnet/api/System.Management.Automation.JobState) definierar status för bakgrunds jobbet. Tillstånd är igång, körs och stoppas.

[System. Management. Automation. Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) innehåller information om tillståndet för ett bakgrunds jobb och, om den senaste tillstånds ändringen orsakades av ett fel, varför jobbet skrevs i det aktuella tillståndet.

[System. Management. Automation. Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) innehåller argument för en händelse som aktive ras när ett bakgrunds jobb ändrar tillstånd.

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell-jobb-cmdletar

Följande cmdletar tillhandahålls av Windows PowerShell för att hantera bakgrunds jobb.

[Hämta jobb](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Hämtar bakgrunds jobb i Windows PowerShell som körs i den aktuella sessionen.

[Mottagning – jobb](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Hämtar resultatet av bakgrunds jobben för Windows PowerShell i den aktuella sessionen.

[Ta bort – jobb](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Tar bort ett bakgrunds jobb i Windows PowerShell.

[Start – jobb](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Startar ett bakgrunds jobb i Windows PowerShell.

[Stoppa – jobb](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Stoppar ett bakgrunds jobb i Windows PowerShell.

[Vänta – jobb](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Ignorerar kommando tolken tills en eller flera av de Windows PowerShell-bakgrunds jobb som körs i sessionen är slutförda.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
