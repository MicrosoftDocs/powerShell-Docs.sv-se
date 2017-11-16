---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>PerformRequiredConfigurationChecks-metoden i klassen MSFT_DSCLocalConfigurationManager

Startar en konsekvenskontroll med Schemaläggaren.

<a name="syntax"></a>Syntax
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a>Parametrar
----------

*Flaggorna* \[i\]  
En bitmask som anger vilken typ av kontroll av att köra. Följande värden är giltiga och kan kombineras med hjälp av en bitvis **eller** igen:

|Värde |Beskrivning |
|:--- |:---|
|**1** | En normal konsekvenskontroll. |
|**2** | En förlängning av en konsekvenskontroll efter en omstart. Det här värdet får inte kombineras med andra värden. |
|**4** | Konfigurationen ska dras från hämtningsservern som anges i metakonfigurationen för noden. Det här värdet alltid ska kombineras med **1**, för ett värde för **5**. |
|**8** | Skicka status till rapportservern. |

## <a name="return-value"></a>Returvärde
------------

Returnerar noll på lyckade; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Se även


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



