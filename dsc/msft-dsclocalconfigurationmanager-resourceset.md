---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ResourceSet-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b5f437a123bd38df21f30d11e71d2c3b36bc9f3a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>ResourceSet-metoden för MSFT_DSCLocalConfigurationManager-klassen

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

*ResourceType* \[i\] namnet på resursen ska anropa.

*Modulnamn* \[i\] namnet på den modul som innehåller resursen ska anropa.

*resourceProperty* \[i\] anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive. Använd den [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) för att identifiera egenskaper för resursen och deras typer.

*RebootRequired* \[ut\] på RETUR, ange den här egenskapen är **SANT** om målnoden måste startas om.

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