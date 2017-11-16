---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ResourceSet-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9cd9c1b3f58a5862db6c4eea0488423b8dfe7310
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>ResourceSet-metoden i klassen MSFT_DSCLocalConfigurationManager

Direkt anropar den **ange** metoden för en DSC-resurs.

<a name="syntax"></a>Syntax
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
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

*RebootRequired* \[ut\]  
På RETUR, ange den här egenskapen är **SANT** om målnoden måste startas om.

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

 

 



