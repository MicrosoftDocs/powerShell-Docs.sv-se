---
title: GetProc02 (VB.NET) exempelkoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 4ec63ed32bd2906f5b027523aa0f253b51a5d873
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301336"
---
# <a name="getproc02-vbnet-sample-code"></a>GetProc02 (VB.NET) – kodexempel

Följande kod visar implementeringen av en `Get-Process` cmdlet som accepterar kommandoradsverktyget indata. Observera att den här implementeringen definierar en `Name` parametern så att kommandoraden indata och använder den [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) metod som utdata-mekanism för att skicka utdata objekt till den pipeline.

## <a name="code-sample"></a>Kodexempel

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
