---
title: GetProc03 (VB.NET) exempelkoden | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058257"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03 (VB.NET) – kodexempel

Följande kod visar implementeringen av en `Get-Process` cmdlet som kan acceptera pipelined indata. Den här implementeringen definierar en `Name` parameter som accepterar pipeline-indata, hämtar information om från den lokala datorn baserat på angivna namnen och använder sedan den [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metod som utdata-mekanism för att skicka objekt till pipelinen.

## <a name="code-sample"></a>Kodexempel

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->