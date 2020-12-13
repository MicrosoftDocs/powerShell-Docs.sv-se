---
ms.date: 09/12/2016
ms.topic: reference
title: GetProc03 (VB.NET) – kodexempel
description: GetProc03 (VB.NET) – kodexempel
ms.openlocfilehash: fc70496178c85e101b380e68aacd64c8d1f350e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355569"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03 (VB.NET) – kodexempel

Följande kod visar implementeringen av en `Get-Process` cmdlet som kan acceptera pipeline-inmatade. Den här implementeringen definierar en `Name` parameter som accepterar pipeline-indata, hämtar process information från den lokala datorn baserat på de angivna namnen och använder sedan metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka objekt till pipelinen.

## <a name="code-sample"></a>Kod exempel

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
