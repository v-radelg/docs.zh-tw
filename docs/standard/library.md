---
title: .NET Standard | Microsoft Docs
description: "了解什麼是 .NET Standard、其版本及所支援的 .NET 平台。"
keywords: .NET Standard, PCL, .NET
author: richlander
ms.author: mairaw
ms.date: 03/17/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.translationtype: Machine Translation
ms.sourcegitcommit: a580e33f756bfb5eb96daeb9decb4acfe3ef2f52
ms.openlocfilehash: 970c70af2d8e5524e022f38d1ad93697a62985f8
ms.contentlocale: zh-tw
ms.lasthandoff: 05/11/2017

---

# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) 是計劃在所有 .NET 執行階段提供的正式 .NET API 規格。 .NET Standard 背後的動機是在 .NET 生態系統中建立更高的一致性。 [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) 會繼續建立 .NET 執行階段行為的一致性，但沒有 .NET 程式庫實作之 .NET 基底類別庫 (BCL) 的類似規格。 

.NET Standard 支援下列重要案例： 

- 定義一致的 BCL API 集合，以供所有 .NET 平台實作，而不論工作負載為何。
- 可讓開發人員使用這組相同的 API，產生可跨 .NET 執行階段使用的可攜式程式庫。
- 減少因 .NET API 而必須對共用原始程式碼進行的條件式編譯，並在順利的情況下完全排除，僅適用於 OS API。

不同的 .NET 執行階段會實作特定版本的 .NET Standard。 每個 .NET 執行階段版本會宣佈它所支援的最高 .NET Standard 版本，此聲明表示它也會支援舊版。 例如，.NET Framework 4.6 會實作 .NET Standard 1.3，這意謂著它會公開 .NET Standard 1.0 到 1.3 版中定義的所有 API。 同樣地，.NET Framework 4.6.1 會實作 .NET Standard 1.5，而 .NET Core 1.0 會實作 .NET Standard 1.6。

## <a name="net-platforms-support"></a>.NET 平台支援

下表列出所有 .NET Standard 版本和支援的平台：

[!INCLUDE [net-standard-table](../includes/net-standard-table.md)]

若要尋找可作為您目標的最新 .NET Standard 版本，請執行下列操作：
1. 尋找指出要作為您執行位置之 .NET 平台的資料列。
2. 在該資料列中，由左到右尋找指出您版本的資料行。
3. 資料行標題會指出您目標所支援的 .NET Standard 版本 (而所有較舊的 .NET Standard 版本也都會支援它)。
4. 針對您想要作為目標的每個平台重複此程序。 如果您有多個目標平台，應該從中挑選最舊的版本。 例如，如果您想要在 .NET Framework 4.5 和 .NET Core 1.0 上執行，則可以使用的最新 .NET Standard 版本是 .NET Standard 1.1。

### <a name="which-net-standard-version-to-target"></a>要以哪個 .NET Standard 版本作為目標

選擇 .NET Standard 版本時，您應該考量下列取捨：

- 版本越新，可供您使用的 API 就越多。
- 版本越舊，可實作它的平台就越多。

一般而言，建議您儘可能以「最舊的」.NET Standard 版本為目標。 因此，在您找到可作為目標的最新 .NET Standard 版本之後，請依照下列步驟操作：
1. 以次舊的 .NET Standard 版本為目標並建置您的專案。
2. 如果您的專案建置成功，便重複步驟 1。 否則，請將目標重新設定為次新版本，這會是您應該使用的版本。

### <a name="net-standard-versioning-rules"></a>.NET Standard 版本控制規則

有兩個主要的版本控制規則：

- 累加：.NET Standard 版本就邏輯而言是同心圓：較新的版本會包含來自較舊版本的所有 API。 版本之間並沒有任何重大變更。
- 不可變。 .NET Standard 在交付後，版本便已凍結。 新 API 將先在特定的 .NET 平台 (例如 .NET Core) 提供。 如果 .NET Standard 審查委員會認為應該在所有平台都提供新的 API，就會在新的 .NET Standard 版本中新增這些 API。

## <a name="comparison-to-portable-class-libraries"></a>與可攜式類別庫的比較

您可以將 .NET Standard 視為新一代的[可攜式類別庫 (PCL)](https://msdn.microsoft.com/library/gg597391.aspx)。 .NET Standard 可透過策劃標準 BCL，進而在 .NET 執行階段之間建立更高的一致性，來改進建立可攜式程式庫的體驗。 以 .NET Standard 為目標的程式庫是 PCL 或「.NET Standard 型 PCL」。 現有的 PCL 是「設定檔型 PCL」。

.NET Standard 和 PCL 設定檔是為了類似的目的而建立，但也有幾點重要的不同之處。

相似之處：

- 定義可用於二進位字碼共用的 API。

不同之處：

- .NET Standard 是一組經過策劃的 API，而 PCL 設定檔則是由現有平台的交集所定義。
- .NET Standard 是以線性方式控制版本，而 PCL 設定檔則不是。
- PCL 設定檔代表 Microsoft 平台，而 .NET Standard 則無從驗證平台。

## <a name="specification"></a>規格

.NET Standard 規格是一組標準化的 API。 此規格是由 .NET 執行階段實作者所維護，具體而言即 Microsoft (包括 .NET Framework、.NET Core 和 Mono) 和 Unity。 透過 [GitHub](https://github.com/dotnet/standard) 建立新的 .NET Standard 版本時，會使用公開回饋程序。

### <a name="official-artifacts"></a>正式成品

正式規格是一組定義 API 的 .cs 檔案，這些 API 是標準的一部分。 每個[元件](https://github.com/dotnet/corefx/tree/master/src)的 [ref 目錄](https://github.com/dotnet/corefx/tree/master/src/System.Runtime/ref)會定義 .NET Standard API。 雖然參考成品位於 [CoreFX 儲存機制](https://github.com/dotnet/corefx)，但不是 .NET Core 的特定成品。

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) 中繼套件 ([原始程式碼](https://github.com/dotnet/standard/blob/master/netstandard/pkg/NETStandard.Library.dependencies.props)) 描述定義 (部分) 一個或多個 .NET 標準程式庫版本的程式庫集合。

System.Runtime 等指定元件描述：

- .NET Standard 的組件 (僅限其範圍)。
- 適用於該範圍的多個 .NET Standard 版本。

為了更方便閱讀及支援特定開發人員案例 (例如使用編譯器)，已提供衍生成品。

- [Markdown 中的 API 清單](https://github.com/dotnet/standard/tree/master/docs/versions)
- 以 [NuGet 套件](../core/packages.md)散發並由 [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) 中繼套件參考的參考組件。

### <a name="package-representation"></a>封裝表示

.NET Standard 參考組件的主要散發工具是 [NuGet 套件](../core/packages.md)。 您可以根據每個 .NET 執行階段，以各種適當的方式來提供實作。

NuGet 套件是以一個或多個[架構](frameworks.md)為目標。 .NET Standard 套件是以 ".NET Standard" 架構為目標。 您可以使用 `netstandard` [Compact TFM](frameworks.md) (例如 `netstandard1.4`) 將 .NET 標準程式庫設為目標。 要在多個執行階段上執行的程式庫應以此架構為目標。 

`NETStandard.Library` 中繼套件會參考定義 .NET Standard 的一組完整 NuGet 套件。  若要將 `netstandard` 設為目標，最常見方式是參考這個中繼套件。 它描述大約 40 種定義 .NET Standard 的 .NET 程式庫和相關 API，並提供其存取權。 您可以參考目標為 `netstandard` 的其他套件，以存取其他 API。 

### <a name="versioning"></a>版本控制

此規格不是單一的，而是一組以累加方式擴充並以線性方式控制版本的 API。 此標準的第一個版本會建立一組基準 API。 後續版本會新增 API，並繼承舊版所定義的 API。 沒有任何既定的佈建可從標準中移除 API。

.NET Standard 並不是任何一個 .NET 執行階段專屬的，也不符合任何這些執行階段的版本配置。

加入任何執行階段 (例如 .NET Framework、.NET Core 和 Mono) 的 API 都可視為要加入規格的候選項目，尤其是如果本質上要作為基礎的 API。 新的 [.NET Standard 版本](https://github.com/dotnet/standard/blob/master/docs/versions.md)是根據 .NET 執行階段版本所建立，可讓您以來自 .NET Standard PCL 的新 API 為目標。 如需版本控制機制的詳細資訊，請參閱 [.NET Core 版本控制](../core/versions/index.md)。

.NET Standard 版本控制對於使用至關重要。 指定 .NET Standard 版本之後，您可以使用以相同版本或更舊版本為目標的程式庫。 下列方法描述使用 .NET Standard PCL (專門用於 .NET Standard 目標設定) 的工作流程。

- 選取要用於 PCL 的 .NET Standard 版本。
- 使用相依於相同 .NET Standard 版本或更舊版本的程式庫。
- 如果您發現有程式庫相依於更新的 .NET Standard 版本，就需要採用該相同的版本，或決定不要使用該程式庫。

### <a name="pcl-compatibility"></a>PCL 相容性

.NET Standard 與 PCL 設定檔子集相容。 .NET Standard Library 1.0、1.1 和 1.2 會各自與一組 PCL 設定檔重疊。 建立此重疊的原因有兩個：

- 可讓 .NET Standard 型 PCL 參考設定檔型 PCL。
- 可將設定檔型 PCL 封裝成 .NET Standard 型 PCL。

[Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet 套件提供設定檔型 PCL 相容性。 參考包含設定檔型 PCL 的 NuGet 套件時需要此相依性。

封裝成 `netstandard` 的設定檔型 PCL，會比一般封裝的設定檔型 PCL 更容易使用。 現有的使用者可以使用 `netstandard` 封裝。

您會看到與 .NET Standard 相容的 PCL 設定檔集合： 

| PCL 設定檔 | .NET Standard | PCL 平台
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4.5、Windows 8
| Profile31   | 1.0           | Windows 8.1、Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1、Windows Phone 8.1
| Profile44   | 1.2           | .NET Framework 4.5.1、Windows 8.1
| Profile49   | 1.0           | .NET Framework 4.5、Windows Phone Silverlight 8
| Profile78   | 1.0           | .NET Framework 4.5、Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8.1、Windows Phone Silverlight 8.1
| Profile111  | 1.1           | .NET Framework 4.5、Windows 8, Windows Phone 8.1
| Profile151  | 1.2           | .NET Framework 4.5.1、Windows 8.1、Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1、Windows Phone 8.1、Windows Phone Silverlight 8.1
| Profile259  | 1.0           | .NET Framework 4.5、Windows 8、Windows Phone 8.1、Windows Phone Silverlight 8


## <a name="targeting-net-standard"></a>以 .NET Standard 為目標

您可以搭配使用 `netstandard` 架構和 NETStandard.Library 中繼套件，來[建置 .NET 標準程式庫](../core/tutorials/libraries.md)。 您可以查看[使用 .NET Core 工具將 .NET Standard 設為目標](../core/packages.md)的範例。

## <a name="see-also"></a>請參閱
[.NET Standard 版本](https://github.com/dotnet/standard/blob/master/docs/versions.md)

