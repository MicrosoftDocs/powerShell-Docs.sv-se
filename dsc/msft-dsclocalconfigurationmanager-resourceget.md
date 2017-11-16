---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ResourceGet-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7d8b185c49778253dcb4e983ad948775c4cb0842
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>ResourceGet-metoden i klassen MSFT_DSCLocalConfigurationManager

Direkt anropar den **hämta** metoden för en DSC-resurs.

<a name="syntax"></a>Syntax
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a>Parametrar
----------

*ResourceType* \[i\]  
Namnet på resursen ska anropa.

*Modulnamn* \[i\]  
Namnet på den modul som innehåller resursen ska anropa.

*resourceProperty* \[i\]  
Anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive. Använd den [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) för att identifiera egenskaper för resursen och deras typer.

*konfigurationer* \[ut\]  
Innehåller en inbäddad instans av konfigurationerna på return.

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


 

 



