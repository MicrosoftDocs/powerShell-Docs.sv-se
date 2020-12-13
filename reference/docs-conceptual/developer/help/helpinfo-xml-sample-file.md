---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo-XML-exempelfil
description: HelpInfo-XML-exempelfil
ms.openlocfilehash: 321793d61ab5df3cccc7c353b6c93f5a7275b533
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647767"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="cd80d-103">HelpInfo-XML-exempelfil</span><span class="sxs-lookup"><span data-stu-id="cd80d-103">HelpInfo XML Sample File</span></span>

<span data-ttu-id="cd80d-104">I det här avsnittet visas ett exempel på en välformulerad uppdaterings bar hjälp informations fil, vanligt vis kallad "HelpInfo XML File".</span><span class="sxs-lookup"><span data-stu-id="cd80d-104">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="cd80d-105">I den här exempel filen ordnas GRÄNSSNITTets kultur element i alfabetisk ordning efter användar gränssnittets kultur namn.</span><span class="sxs-lookup"><span data-stu-id="cd80d-105">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="cd80d-106">Alfabetisk ordning är en bra metod, men det är inget krav.</span><span class="sxs-lookup"><span data-stu-id="cd80d-106">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="cd80d-107">HelpInfo-XML-exempelfil</span><span class="sxs-lookup"><span data-stu-id="cd80d-107">HelpInfo XML Sample File</span></span>

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
