---
ms.date: 09/12/2016
ms.topic: reference
title: GetProc03 (VB.NET) – kodexempel
description: GetProc03 (VB.NET) – kodexempel
ms.openlocfilehash: 6d51c3bf65ccb37811acce0ab5f59daaac91118b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657209"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03 (VB.NET) – kodexempel

Följande kod visar implementeringen av en `Get-Process` cmdlet som kan acceptera pipeline-inmatade. Den här implementeringen definierar en `Name` parameter som accepterar pipeline-indata, hämtar process information från den lokala datorn baserat på de angivna namnen och använder sedan metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka objekt till pipelinen.

## <a name="code-sample"></a>Kod exempel

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
