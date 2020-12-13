---
ms.date: 07/09/2020
ms.topic: reference
title: Fel och undantag i det utökade typ systemet
description: Fel och undantag i det utökade typ systemet
ms.openlocfilehash: 295c16ad9abb67b0c4967bf32125bfc7ee0a35da
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652476"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a>Fel och undantag i det utökade typ systemet

Fel kan uppstå i ETS vid initiering av typ data och vid åtkomst till en medlem i ett **PSObject** -objekt eller med hjälp av en av verktygs klasserna som **LanguagePrimitives**.

## <a name="runtime-errors"></a>Körnings fel

Med ett undantag, vid data byte, är alla undantag som har utlösts av ETS under körning antingen ett **ExtendedTypeSystemException** -undantag eller ett undantag som härletts från **ExtendedTypeSystemException** -klassen. Detta gör att skript utvecklare kan svälla dessa undantag med hjälp av `Trap` instruktionen i skriptet.

## <a name="errors-getting-member-values"></a>Fel vid hämtning av medlems värden

Alla fel som inträffar när värdet för en ETS-medlem (egenskap, metod eller parameter egenskap) hämtas gör att ett **GetValueException** -eller **GetValueInvocationException** -undantag genereras.
När ETS känner av att ett fel har uppstått ett **GetValueException** -undantag genereras. När den underliggande hämtningen av en refererad medlem känner av att ett fel har uppstått, genereras ett **GetValueInvocationException** -undantag som kan innehålla det inre undantag som orsakade get-anropet.

## <a name="errors-setting-member-values"></a>Fel vid inställning av medlems värden

Alla fel som inträffar när du ställer in värdet för en ETS-egenskap orsakar ett **SetValueException** -eller **SetValueInvocationException** -undantag som ska genereras. När ETS känner av att ett fel har uppstått ett **SetValueException** -undantag genereras. När den underliggande set-egenskapen för en refererad egenskap känner av att ett fel har uppstått, genereras ett **SetValueInvocationException** -undantag som kan innehålla det inre undantag som orsakade det angivna anrops felet.

## <a name="errors-invoking-a-method"></a>Fel vid anrop av en metod

Alla fel som inträffar när en ETS-metod anropas orsakar ett **MethodException** -eller **MethodInvocationException** -undantag. När ETS känner av att ett fel har uppstått ett **MethodException** -undantag genereras. När den refererade metoden känner av att ett fel har uppstått, genereras ett **MethodInvocationException** -undantag som kan innehålla det inre undantag som orsakade anrops felet.

## <a name="casting-errors"></a>Data typs fel

När en ogiltig omvandling görs, genereras en **PSInvalidCastException** . Eftersom detta undantag härleds från **system. InvalidCastException**, kan det inte direkt svällas från skriptet. Tänk på att den entitet som försöker omvandlaren måste figursätta **PSInvalidCastException** i en **PSRuntimeException** för att detta ska kunna svällas av skript. Om ett försök görs att ange värdet för en **PSPropertySet**, **PSMemberSet**, **PSMethodInfo** eller en medlem i **ReadOnlyPSMemberInfoCollection 1**, genereras en **NotSupportedException** .

## <a name="common-runtime-errors"></a>Vanliga körnings fel

Andra vanliga körnings fel som inträffar är av typen **ExtendedTypeSystemException** -undantag utan ytterligare vissa undantags typer.

## <a name="initialization-errors"></a>Initierings fel

Fel kan uppstå vid initiering `types.ps1xml` . Dessa fel visas vanligt vis när PowerShell-körningsmiljön startar. De kan dock också visas när en modul läses in.
