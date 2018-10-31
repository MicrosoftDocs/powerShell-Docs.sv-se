---
ms.date: 09/10/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Hantera API-nycklar
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002521"
---
# <a name="managing-api-keys"></a>Hantera API-nycklar

PowerShell-galleriet kan du skapa flera API-nycklar för att stödja flera olika publicera krav. En API-nyckel kan tillämpa på ett eller flera paket, ger specifika rättigheter och har ett utgångsdatum.

> [!IMPORTANT]
> Användare som publicerats i PowerShell-galleriet innan introduktionen av begränsade API-nycklar har en ”fullständig åtkomst API key”. Nycklar för fullständig åtkomst har inte säkerhetsförbättringar som är inbyggda i begränsade API-nycklar. Fullständig åtkomstnycklarna aldrig upphör att gälla och gäller för allt som ägs av användaren. Om du tar bort den här nyckeln kan inte återskapas.

Följande bild visar de tillgängliga alternativen när du skapar en begränsade API-nyckel.

![Skapa API-nycklar](../../Images/PSGallery_KeyScoped.png)

I det här exemplet skapade vi en API-nyckel med namnet **AzureRMDataFactory**. Värdet för nyckeln kan användas för att skicka paket med namn som börjar med ”AzureRM.DataFactory” och är giltig i 365 dagar. Det här är ett vanligt scenario när olika team inom samma organisation arbetar med olika paket. Medlemmar i teamet har en nyckel som ger behörighet för det specifika paket som de arbetar på.
Värdet för förfallotid förhindrar användning av inaktuella eller glömda nycklar.

## <a name="using-glob-patterns"></a>Med hjälp av BLOB-mönster

Om du arbetar med flera paket kan använda du globbing mönster så att de matchar flera paket som en grupp. API-nyckel behörigheter gäller för alla nya paket som matchar mönstret BLOB. Till exempel det föregående exemplet används en **BLOB mönstret** värdet för ”AzureRM.DataFactory*”. Du kan skicka ett paket med namnet ”AzureRm.DataFactoryV2.Netcore” med hjälp av den här nyckeln eftersom paketet matchar mönstret BLOB.

## <a name="create-api-keys-securely"></a>Skapa API-nycklar på ett säkert sätt

För säkerhet, ett nyligen skapade nyckelvärde visas aldrig på skärmen och är endast tillgänglig med knappen Kopiera enligt nedan.

![Hämta nya API-nyckelvärdet](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> Du kan bara kopiera API-nyckelvärdet omedelbart efter att skapa eller uppdatera den. Den visas inte och kommer inte att komma åt igen när sidan uppdateras. Om du förlorar nyckelvärdet kan du använda återskapa och kopiera nyckeln när den har återskapats.

## <a name="key-permissions-and-expiration"></a>Nyckelns behörigheter och upphör att gälla

Begränsade API-nycklar kan tilldela någon av följande behörigheter:

- Skicka nya paket
- Skicka ny eller uppdatera paket
- Ta bort paket

Alla nya nycklar har en giltighetstid. Värdet för förfallotid mäts i dagar. De möjliga värdena för förfallodatum är:

- 1 dag
- 90 dagar
- 180 dagar
- 270 dagar
- 365 dagar (standard)

De här inställningarna kan inte ändras när nyckeln har skapats. Du kan inte skapa en ny nyckel med upphör aldrig att gälla.

## <a name="editing-and-deleting-existing-api-keys"></a>Redigera och ta bort befintliga API-nycklar

Du kan ändra vissa inställningar för en befintlig nyckel. Som vi nämnde tidigare kan kan inte du ändra säkerhetsomfattningen för en befintlig API-nyckel eller ändra förfallodatum. Ändringsbart alternativ visas på följande skärmbild:

![Hämta nya API-nyckelvärdet](../../Images/PSGallery_EditAPIKey.png)

Om du vill ändra de paket som styrs av en nyckel, kan du välja enskilda paket i listan eller ändra BLOB-mönster.

Klicka på **återskapa** skapar ett nytt nyckelvärde. Precis som när du först skapade nyckeln, måste du **kopia** nyckelvärdet omedelbart när du har uppdaterat den. Den **kopia** alternativet är inte tillgängligt när du lämnar den här sidan.

Klicka på **ta bort** visas en bekräftelse. När en nyckel har tagits bort, blir det inte kan användas.

## <a name="key-expiration"></a>Utgångsdatum för nyckel

Tio dagar före förfallodatum, skickar PowerShell-galleriet ett e-postmeddelande med varning kontoinnehavaren av API-nyckeln. Efter förfallodatumet kan nyckeln inte användas. Ett varningsmeddelande visas överst på sidan API nyckelhantering som visar vilka nycklar är inte längre giltig. Du kan generera ett nytt nyckelvärde.
