---
title: Skapa ett arbetsflöde med Windows PowerShell aktiviteter | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055435"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Skapa ett arbetsflöde med Windows PowerShell-aktiviteter

Du kan skapa ett Windows PowerShell-arbetsflöde genom att välja aktiviteter i verktygslådan för Visual Studio och dra dem till Workflow Designer-fönstret. Information om att lägga till Windows PowerShell-aktiviteter i verktygslådan för Visual Studio finns i [att lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Följande procedurer beskriver hur du skapar ett arbetsflöde som kontrollerar domänen för en grupp användardefinierade datorer och kopplar dem till en domän om de inte redan är ansluten och kontrollerar status igen.

### <a name="setting-up-the-project"></a>Konfigurera projektet

1. Följ proceduren i [att lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) att skapa ett arbetsflöde-projekt och lägga till aktiviteter från den [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) och [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) sammansättningar i verktygslådan.

2. Lägg till System.Management.Automation, Microsoft.PowerShell.Activities, av System.Management, Microsoft.PowerShell.Management.Activities och Microsoft.PowerShell.Commands.Management om projektet som referenssammansättningar.

### <a name="adding-activities-to-the-workflow"></a>Att lägga till aktiviteter i arbetsflödet

1. Lägg till en **sekvens** aktivitet i arbetsflödet.

2. Skapa ett argument som heter `ComputerName` med ett argument av typen `String[]`. Det här argumentet representerar namnen på datorerna för att kontrollera och ansluta till.

3. Skapa ett argument som heter `DomainCred` av typen [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Det här argumentet representerar domänautentiseringsuppgifter för ett domänkonto som har behörighet att ansluta en dator till domänen.

4. Skapa ett argument som heter `MachineCred` av typen [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Det här argumentet representerar autentiseringsuppgifter för administratör på datorerna för att kontrollera och ansluta till.

5. Lägg till en **ParallelForEach** aktivitet i den **sekvens** aktivitet. Ange `comp` och `ComputerName` i textrutor så att loopen upprepas elementen i den `ComputerName` matris.

6. Lägg till en **sekvens** aktivitet och i brödtexten för den **ParallelForEach** aktivitet. Ange den **DisplayName** egenskapen för aktivitetssekvensen ska `JoinDomain`.

7. Lägg till en **GetWmiObject** aktivitet för att den **JoinDomain** sekvens.

8. Redigera egenskaperna för den **GetWmiObject** aktivitet på följande sätt.

   |Egenskap|Värde|
   |--------------|-----------|
   |**Klass**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. Lägg till en **AddComputer** aktivitet för att den **JoinDomain** aktivitetssekvensen efter den **GetWmiObject** aktivitet.

10. Redigera egenskaperna för den **AddComputer** aktivitet på följande sätt.

    |Egenskap|Värde|
    |--------------|-----------|
    |**Datornamn**|{comp}|
    |**DomainCredential**|DomainCred|

11. Lägg till en **RestartComputer** aktivitet för att den **JoinDomain** aktivitetssekvensen efter den **AddComputer** aktivitet.

12. Redigera egenskaperna för den **RestartComputer** aktivitet på följande sätt.

    |Egenskap|Värde|
    |--------------|-----------|
    |**Datornamn**|{comp}|
    |**Autentiseringsuppgifter**|MachineCred|
    |**för**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|Sant|
    |Vänta|Sant|
    |PSComputerName|{""}|

13. Lägg till en **GetWmiObject** aktivitet för att den **JoinDomain** aktivitetssekvensen efter den **RestartComputer** aktivitet. Redigera dess egenskaper för att vara samma som föregående **GetWmiObject** aktivitet.

    När du är klar med följande arbetsflöde design-fönstret bör se ut så här.

    ![JoinDomain XAML i arbetsflödesdesigner](../media/joindomainworkflow.png)
    ![JoinDomain XAML i arbetsflödesdesigner](../media/joindomainworkflow.png "JoinDomainWorkflow")