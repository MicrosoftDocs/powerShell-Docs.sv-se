---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Hantera API-nycklar
ms.openlocfilehash: 0f44a080415f1acf13680771b6e9db5b805f8f45
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278328"
---
# <a name="managing-api-keys"></a>Hantera API-nycklar

PowerShell-galleriet har stöd för att skapa flera API-nycklar som stöder ett antal publicerings krav. En API-nyckel kan gälla för ett eller flera paket, ger vissa behörigheter och har ett förfallo datum.

> [!IMPORTANT]
> Användare som har publicerat till PowerShell-galleriet innan införandet av API-nycklar för omfattningar kommer att ha en "fullständig åtkomst-API-nyckel". De fullständiga åtkomst nycklarna har inte de säkerhets förbättringar som är inbyggda i omfånget API-nycklar. De fullständiga åtkomst nycklarna upphör aldrig att gälla och gäller allt som ägs av användaren. Om du tar bort den här nyckeln kan den inte återskapas.

Följande bild visar de alternativ som är tillgängliga när du skapar en omfångs-API-nyckel.

![Skapar API-nycklar](media/creating-APIkeys/PSGallery_KeyScoped.png)

I det här exemplet har vi skapat en API-nyckel med namnet **AzureRMDataFactory**. Detta nyckel värde kan användas för att skicka paket med namn som börjar med "AzureRM. DataFactory" och som är giltiga i 365 dagar. Detta är ett typiskt scenario när olika team inom samma organisation arbetar med olika paket. Medlemmarna i teamet har en nyckel som ger dem behörighet för det aktuella paketet som de arbetar med.
Värdet för förfallo datum förhindrar att inaktuella eller bortglömt nycklar används.

## <a name="using-glob-patterns"></a>Använda BLOB mönster

Om du arbetar med flera paket kan du använda globbing mönster för att matcha flera paket som en grupp. API-nyckelns behörigheter gäller för alla nya paket som matchar BLOB-mönstret. Exemplet ovan använder till exempel ett BLOB- **Pattern** -värde för ' AzureRM. DataFactory * '. Du kan skicka ett paket med namnet "AzureRm. DataFactoryV2. NetCore" med hjälp av den här nyckeln eftersom paketet matchar BLOB-mönstret.

## <a name="create-api-keys-securely"></a>Skapa API-nycklar på ett säkert sätt

För säkerhet visas ett nytt nyckel värde aldrig på skärmen och är bara tillgängligt med kopierings knappen, som du ser nedan.

![Hämtar nytt API-nyckel värde](media/creating-APIkeys/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> Du kan bara kopiera API-nyckelvärdet direkt efter att du har skapat eller uppdaterat det. Den kommer inte att visas och kommer inte att vara tillgänglig igen när sidan har uppdaterats. Om du förlorar nyckelvärdet måste du använda återskapa och kopiera nyckeln när den har återskapats.

## <a name="key-permissions-and-expiration"></a>Nyckel behörigheter och förfallo datum

Begränsade API-nycklar kan tilldela någon av följande behörigheter:

- Skicka nya paket
- Skicka nya eller uppdatera paket
- Lista paket

Varje ny nyckel har ett förfallo datum. Värdet för förfallo datum mäts i dagar. De möjliga värdena för förfallo datum är:

- 1 dag
- 90 dagar
- 180 dagar
- 270 dagar
- 365 dagar (standard)

De här inställningarna kan inte ändras när nyckeln har skapats. Du kan inte skapa en ny nyckel som aldrig upphör att gälla.

## <a name="editing-and-deleting-existing-api-keys"></a>Redigera och ta bort befintliga API-nycklar

Du kan ändra vissa inställningar för en befintlig nyckel. Som tidigare nämnts kan du inte ändra säkerhets omfattningen för en befintlig API-nyckel eller ändra förfallo datumet. De ändrings bara alternativen visas på följande skärm bild:

![Hämtar nytt API-nyckel värde](media/creating-APIkeys/PSGallery_EditAPIKey.png)

Om du vill ändra de paket som styrs av en nyckel kan du välja enskilda paket i listan eller ändra BLOB-mönstret.

Om du klickar på **Återskapa** skapas ett nytt nyckel värde. Precis som när du skapade nyckeln första gången måste du **Kopiera** nyckelvärdet direkt efter att det har uppdaterats. **Kopierings** alternativet är inte tillgängligt när du lämnar den här sidan.

Om du klickar på **ta bort** visas ett bekräftelse meddelande. När en nyckel har tagits bort går den inte att använda.

## <a name="key-expiration"></a>Nyckel förfallo datum

Tio dagar innan förfallo tiden skickar PowerShell-galleriet en varning via e-post till konto innehavaren av API-nyckeln. Efter förfallo datum är nyckeln oanvändbar. Ett varnings meddelande visas längst upp på sidan API-nyckel hantering som visar vilka nycklar som inte längre är giltiga. Du kan generera ett nytt nyckel värde.
