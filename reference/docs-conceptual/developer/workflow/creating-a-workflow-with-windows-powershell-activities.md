---
title: Skapa ett arbets flöde med Windows PowerShell-aktiviteter | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352159"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Skapa ett arbetsflöde med Windows PowerShell-aktiviteter

Du kan skapa ett Windows PowerShell-arbetsflöde genom att välja aktiviteter från Visual Studio-verktygslådan och dra dem till arbetsflödesdesigners fönstret. Information om hur du lägger till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan finns i [lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Följande procedurer beskriver hur du skapar ett arbets flöde som kontrollerar domän status för en grupp av användardefinierade datorer, kopplar dem till en domän om de inte redan är anslutna och sedan kontrollerar statusen igen.

### <a name="setting-up-the-project"></a>Konfigurerar projektet

1. Följ proceduren i [lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) för att skapa ett arbets flödes projekt och lägga till aktiviteterna från sammansättningarna [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) och [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) i verktygs lådan.

2. Lägg till system. Management. Automation, Microsoft. PowerShell. Activities, system. Management, Microsoft. PowerShell. Management. Activities och Microsoft. PowerShell. commands. Management för projektet som referens sammansättningar.

### <a name="adding-activities-to-the-workflow"></a>Lägga till aktiviteter i arbets flödet

1. Lägg till en **sekvens** -aktivitet i arbets flödet.

2. Skapa ett argument med namnet `ComputerName` med en argument typ `String[]`. Det här argumentet representerar namnen på de datorer som ska kontrol leras och anslutas.

3. Skapa ett argument med namnet `DomainCred` av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Det här argumentet representerar domänautentiseringsuppgifter för ett domän konto som har behörighet att ansluta en dator till domänen.

4. Skapa ett argument med namnet `MachineCred` av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Det här argumentet representerar autentiseringsuppgifterna för en administratör på de datorer som ska kontrol leras och anslutas.

5. Lägg till en **ParallelForEach** -aktivitet i **sekvens** -aktiviteten. Ange `comp` och `ComputerName` i text rutorna så att loopen upprepas genom elementen i `ComputerName` matrisen.

6. Lägg till en **sekvens** -aktivitet i bröd texten i **ParallelForEach** -aktiviteten. Ange egenskapen **DisplayName** för sekvensen till `JoinDomain`.

7. Lägg till en **GetWmiObject** -aktivitet i **JoinDomain** -sekvensen.

8. Redigera egenskaperna för **GetWmiObject** -aktiviteten enligt följande.

   |Egenskap|Värde|
   |--------------|-----------|
   |**Lektion**|"Win32_ComputerSystem"|
   |**PSComputerName**|fysiskt|
   |**PSCredential**|MachineCred|

9. Lägg till en **AddComputer** -aktivitet i **JoinDomain** -sekvensen efter **GetWmiObject** -aktiviteten.

10. Redigera egenskaperna för **AddComputer** -aktiviteten enligt följande.

    |Egenskap|Värde|
    |--------------|-----------|
    |**Namnet**|fysiskt|
    |**DomainCredential**|DomainCred|

11. Lägg till en **RestartComputer** -aktivitet i **JoinDomain** -sekvensen efter **AddComputer** -aktiviteten.

12. Redigera egenskaperna för **RestartComputer** -aktiviteten enligt följande.

    |Egenskap|Värde|
    |--------------|-----------|
    |**Namnet**|fysiskt|
    |**Autentiseringsuppgifter**|MachineCred|
    |**Söker**|Microsoft. PowerShell. commands. WaitForServiceTypes. PowerShell|
    |**Inför**|Sant|
    |Vänta|Sant|
    |PSComputerName|{""}|

13. Lägg till en **GetWmiObject** -aktivitet i **JoinDomain** -sekvensen efter **RestartComputer** -aktiviteten. Redigera egenskaperna så att de är samma som föregående **GetWmiObject** -aktivitet.

    När du är färdig med procedurerna bör fönstret arbets flödes design se ut så här.

    ![JoinDomain XAML i Workflow Designer](../media/joindomainworkflow.png)
    ![JoinDomain XAML i arbetsflödesdesignern](../media/joindomainworkflow.png "JoinDomainWorkflow")