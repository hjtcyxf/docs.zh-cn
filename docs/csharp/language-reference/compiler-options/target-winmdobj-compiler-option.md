---
title: "/target:winmdobj（C# 编译器选项） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:winmdobj（C# 编译器选项）
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

如果使用 **\/target:winmdobj** 编译器选项，则编译器会创建一个中间 .winmdobj 文件，您可以将这个文件转换为 Windows 运行时二进制 \(.winmd\) 文件。  之后，除了托管语言程序外，JavaScript 和 C\+\+ 程序也可以使用该 .winmd 文件。  
  
## 语法  
  
```  
/target:winmdobj  
```  
  
## 备注  
 **winmdobj** 设置会向编译器发出信号，表示需要中间模块。  作为响应，Visual Studio 会将 C\# 类库编译为 .winmdobj 文件。  随后，.winmdobj 文件可作为可作为 <xref:Microsoft.Build.Tasks.WinMDExp> 导出工具的输入，生成 Windows 元数据 \(.winmd\) 文件。  .winmd 文件既包含原始库的代码，也包括 JavaScript（或 C\+\+）以及 Windows 运行时使用的 WinMD 元数据的代码。  
  
 使用 **\/target:winmdobj** 编译器选项所编译的文件，只能用作 WimMDExp 导出工具的输入；不能直接引用 .winmdobj 文件自身。  
  
 除非使用 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 选项，否则输出文件的名称采用第一个输入文件的名称。  不需要使用 [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) 方法。  
  
 如果在命令提示符处指定 \/target:winmdobj 选项，则在指定下一个 **\/out** 或 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 选项之前，会使用所有文件来创建 Windows 程序。  
  
### 在 Visual Studio IDE 中为 Windows 应用商店应用程序设置此编译器选项  
  
1.  在**“解决方案资源管理器”**中，打开项目的快捷菜单，然后选择**“属性”**。  
  
2.  选择**“应用程序”**选项卡。  
  
3.  在**“输出类型”**列表中，选择**“WinMD 文件”**。  
  
     **“WinMD 文件”**选项只能用于 [!INCLUDE[win8_appname_long](../../../csharp/language-reference/compiler-options/includes/win8_appname_long_md.md)] 应用模板。  
  
 有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## 示例  
 以下命令将 `filename.cs` 编译为一个中间 .winmdobj 文件。  
  
```  
csc /target:winmdobj filename.cs  
```  
  
## 请参阅  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)