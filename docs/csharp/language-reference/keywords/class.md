---
title: "class (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- class_CSharpKeyword
- class
dev_langs:
- CSharp
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 02491e64813f84d031debdca09161d88aab1b94c
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

---
# <a name="class-c-reference"></a>類別 (C# 參考)
使用 `class` 關鍵字宣告類別，如下列範例所示︰  
  
```  
      class TestClass  
{  
    // Methods, properties, fields, events, delegates   
    // and nested classes go here.  
}  
```  
  
## <a name="remarks"></a>備註  
 僅允許在 C# 中使用單一繼承。 換句話說，類別可以只從一個基底類別繼承實作。 不過，類別可以實作多個介面。 下表顯示類別繼承和介面實作範例︰  
  
|繼承|範例|  
|-----------------|-------------|  
|無|`class ClassA { }`|  
|Single|`class DerivedClass: BaseClass { }`|  
|無，實作兩個介面|`class ImplClass: IFace1, IFace2 { }`|  
|單一，實作一個介面|`class ImplDerivedClass: BaseClass, IFace1 { }`|  
  
 直接在命名空間內宣告的類別 (未巢狀在其他類別內) 可以是 [public](../../../csharp/language-reference/keywords/public.md) 或 [internal](../../../csharp/language-reference/keywords/internal.md)。 類別預設為 `internal`。  
  
 類別成員 (包括巢狀類別) 可以是 [public](../../../csharp/language-reference/keywords/public.md)、`protected internal`、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 [private](../../../csharp/language-reference/keywords/private.md)。 成員預設為 [private](../../../csharp/language-reference/keywords/private.md)。  
  
 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 您可以宣告具有型別參數的泛型類別。 如需詳細資訊，請參閱[泛型類別](../../../csharp/programming-guide/generics/generic-classes.md)。  
  
 類別可以包含下列成員的宣告︰  
  
-   [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [常數](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)  

-   [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [索引子](../../../csharp/programming-guide/indexers/index.md)  
  
-   [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [事件](../../../csharp/programming-guide/events/index.md)  
  
-   [委派](../../../csharp/programming-guide/delegates/index.md)  
  
-   [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [介面](../../../csharp/programming-guide/interfaces/index.md)  
  
-   [結構](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何宣告類別欄位、建構函式和方法。 它也會示範物件具現化和列印執行個體資料。 在此範例中，宣告兩個類別：`Child` 類別，其中包含兩個私用欄位 (`name` 和 `age`) 和兩個公用方法。 第二個類別 `StringTest` 是用來包含 `Main`。  
  
 [!code-cs[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]  
  
## <a name="comments"></a>註解  
 請注意，在上述範例中，只能透過 `Child` 類別的公用方法來存取私用欄位 (`name` 和 `age`)。 例如，您無法使用如下的陳述式，從 `Main` 方法列印子系的名稱︰  
  
```  
Console.Write(child1.name);   // Error  
```  
  
 只有在 `Main` 已是類別的成員時，才能從 `Main` 存取 `Child` 的 private 成員。  
  
 類型已宣告在存取修飾詞未預設為 `private` 的類別內，因此，如果已移除關鍵字，則此範例中的資料成員仍然會是 `private`。  
  
 最後，請注意，針對使用預設建構函式建立的物件 (`child3`)，age 欄位預設已初始化為零。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [參考型別](../../../csharp/language-reference/keywords/reference-types.md)

