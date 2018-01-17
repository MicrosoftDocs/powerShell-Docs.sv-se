---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ResourceGet-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
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


 

 



