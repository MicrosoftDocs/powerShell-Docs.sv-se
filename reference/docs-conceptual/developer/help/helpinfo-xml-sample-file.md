---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo-XML-exempelfil
description: HelpInfo-XML-exempelfil
ms.openlocfilehash: 321793d61ab5df3cccc7c353b6c93f5a7275b533
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647767"
---
# <a name="helpinfo-xml-sample-file"></a>HelpInfo-XML-exempelfil

I det här avsnittet visas ett exempel på en välformulerad uppdaterings bar hjälp informations fil, vanligt vis kallad "HelpInfo XML File". I den här exempel filen ordnas GRÄNSSNITTets kultur element i alfabetisk ordning efter användar gränssnittets kultur namn. Alfabetisk ordning är en bra metod, men det är inget krav.

## <a name="helpinfo-xml-sample-file"></a>HelpInfo-XML-exempelfil

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>https://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```
