---
title: HelpInfo-XML-exempelfil
ms.date: 09/12/2016
ms.openlocfilehash: ec9a2a1afed4f22be00900cbc80b580ff99f8f38
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86953275"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="e30d1-102">HelpInfo-XML-exempelfil</span><span class="sxs-lookup"><span data-stu-id="e30d1-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="e30d1-103">I det här avsnittet visas ett exempel på en välformulerad uppdaterings bar hjälp informations fil, vanligt vis kallad "HelpInfo XML File".</span><span class="sxs-lookup"><span data-stu-id="e30d1-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="e30d1-104">I den här exempel filen ordnas GRÄNSSNITTets kultur element i alfabetisk ordning efter användar gränssnittets kultur namn.</span><span class="sxs-lookup"><span data-stu-id="e30d1-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="e30d1-105">Alfabetisk ordning är en bra metod, men det är inget krav.</span><span class="sxs-lookup"><span data-stu-id="e30d1-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="e30d1-106">HelpInfo-XML-exempelfil</span><span class="sxs-lookup"><span data-stu-id="e30d1-106">HelpInfo XML Sample File</span></span>

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
