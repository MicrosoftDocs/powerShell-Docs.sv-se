---
title: Redigera MOF-schemafilen för en hantering av OData-webbtjänsten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65fbac8b-07d0-4513-bc8d-79f1f389be0f
caps.latest.revision: 5
ms.openlocfilehash: 7aadee07b38d2e9d87c5f0c548d13a5cdad1939f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356744"
---
# <a name="authoring-the-mof-schema-file-for-a-management-odata-web-service"></a>Redigera MOF-schemafilen för en Management OData-webbtjänst

Du definierar de resurser som din hantering av OData-webbtjänsten exponerar genom att skapa en MOF-fil som använde det offentliga resurs schemat. Varje resurs definieras som en klass i filen och egenskaper definieras som klass medlemmar. Mer information om det schema som används i MOF-filen finns i [delat resurs schema](./public-resource-schema.md).

## <a name="example-mof-file"></a>Exempel på MOF-fil

Följande fil definierar tjänst-och process resurser. Var och en av dessa resurser motsvarar ett objekt som kan hanteras av en uppsättning Windows PowerShell-cmdlet. Egenskaperna motsvarar parametrar som används av dessa cmdletar.

Var och en av de två resurserna innehåller egenskaper av typen komplex. De komplexa typerna definieras som klasser som har ändrats med `ComplexType`-kvalificeraren.

```csharp

class PswsTest_Service
{
    [Key]      String  ServiceName;
    [Required] String  DisplayName;
    [Required] String  MachineName;
    [Required] String  ServiceType;
    [Required, EmbeddedInstance("PswsTest_DependentService")] String ServicesDependentOn [];
    [Required] Boolean CanPauseAndContinue;
    [Required] Boolean CanShutdown;
    [Required] Boolean CanStop;
    [Required, Etag] String Status;
};

class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required, EmbeddedInstance("PowerShell_PSCredential")] String Credential;
    [Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
    [Required] SInt32 HandleCount;
    [Required] String MachineName;
    [Required] SInt32 MainWindowHandle;
    [Required] String MainWindowTitle;
    [Required] SInt32 NonpagedSystemMemorySize;
    [Required] SInt64 NonpagedSystemMemorySize64;
    [Required] SInt32 PagedMemorySize;
    [Required] SInt64 PagedMemorySize64;
    [Required] SInt32 PagedSystemMemorySize;
    [Required] SInt64 PagedSystemMemorySize64;
    [Required] SInt32 PeakPagedMemorySize;
    [Required] SInt64 PeakPagedMemorySize64;
    [Required] SInt32 PeakWorkingSet;
    [Required] SInt64 PeakWorkingSet64;
    [Required] SInt32 PeakVirtualMemorySize;
    [Required] SInt64 PeakVirtualMemorySize64;
    [Required] SInt32 PrivateMemorySize;
    [Required] SInt64 PrivateMemorySize64;
    [Required] String ProcessName;
    [Required] Boolean Responding;
    [Required] SInt32 SessionId;
    [Required, EmbeddedInstance("PswsTest_ProcessStartInfo")] String StartInfo;
    [Required] SInt32 VirtualMemorySize;
    [Required] SInt64 VirtualMemorySize64;
    [Required] Boolean EnableRaisingEvents;
    [Required] SInt32 WorkingSet;
    [Required] SInt64 WorkingSet64;
};

[ComplexType]
class PswsTest_DependentService
{
    String  ServiceName;
};

[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};

[ComplexType]
class PswsTest_ProcessStartInfo
{
    String Verb;
    String Arguments;
    Boolean CreateNoWindow;
    Boolean RedirectStandardInput;
    Boolean RedirectStandardOutput ;
    Boolean RedirectStandardError;
    [EmbeddedInstance("PswsTest_Encoding")] String StandardErrorEncoding;
    [EmbeddedInstance("PswsTest_Encoding")] String StandardOutputEncoding;
    Boolean UseShellExecute;
    String UserName ;
    [EmbeddedInstance("PswsTest_SecureString")] String Password;
    String Domain;
    Boolean LoadUserProfile;
    String FileName;
    String WorkingDirectory ;
    Boolean ErrorDialog ;
    SInt32 ErrorDialogParentHandle;
    String WindowStyle;
};

[ComplexType]
class PswsTest_FileVersionInfo
{
    String Comments;
    String CompanyName;
    SInt32 FileBuildPart;
    String FileDescription;
    sInt32 FileMajorPart;
    SInt32 FileMinorPart;
    String FileName;
    SInt32 FilePrivatePart;
    String FileVersion;
    String InternalName;
    Boolean IsDebug;
    Boolean IsPatched;
    Boolean IsPrivateBuild;
    Boolean IsPreRelease;
    Boolean IsSpecialBuild;
    String Language;
    String LegalCopyright;
    String LegalTrademarks;
    String OriginalFilename;
    String PrivateBuild;
    SInt32 ProductBuildPart;
    SInt32 ProductMajorPart;
    SInt32 ProductMinorPart;
    String ProductName;
    SInt32 ProductPrivatePart;
    String ProductVersion;
    String SpecialBuild;
};

[ComplexType]
class PswsTest_Encoding
{
    String BodyName;
    String EncodingName;
    String HeaderName;
    String WebName;
    SInt32 WindowsCodePage;
    Boolean IsBrowserDisplay;
    Boolean IsBrowserSave;
    Boolean IsMailNewsDisplay;
    Boolean IsMailNewsSave;
    Boolean IsSingleByte;
    [EmbeddedInstance("PswsTest_EncoderFallback")] String EncoderFallback;
    [EmbeddedInstance("PswsTest_DecoderFallback")] String DecoderFallback;
    Boolean IsReadOnly;
    SInt32 CodePage;
};

[ComplexType]
class PswsTest_EncoderFallback
{
    SInt32 MaxCharCount;
};

[ComplexType]
class PswsTest_DecoderFallback
{
    SInt32 MaxCharCount;
};

[ComplexType]
class PswsTest_SecureString
{
    SInt32 Length;
};

[ComplexType]
class PswsTest_ProcessThread
{
    SInt32 BasePriority;
    SInt32 CurrentPriority;
    SInt32 Id;
    SInt32 IdealProcessor;
    String PriorityLevel;
    SInt32 StartAddress;
    String ThreadState;
    String WaitReason;
    SInt32 ProcessorAffinity;
};

[ComplexType]
class PswsTest_Stream
{
    Boolean CanRead;
    Boolean CanSeek;
    Boolean CanTimeout;
    Boolean CanWrite;
    SInt64 Length;
    SInt64 Position;
    SInt32 ReadTimeout;
    SInt32 WriteTimeout;
};

```

## <a name="see-also"></a>Se även

[Skapa en hantering av OData-webbtjänst](./creating-a-management-odata-web-service.md)

[Offentligt resurs schema](./public-resource-schema.md)