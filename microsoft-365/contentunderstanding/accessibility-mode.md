---
title: 'SharePoint 合成辅助功能模式 '
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: Normal
description: 了解如何在 SharePoint Syntex 中培训模型时使用辅助功能模式。
ms.openlocfilehash: 32e5bd132a7a0145f03e4620545d65d1d92ff223
ms.sourcegitcommit: d354727303d9574991b5a0fd298d2c9414e19f6c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/02/2021
ms.locfileid: "50080994"
---
# <a name="sharepoint-syntex-accessibility-mode"></a>SharePoint 合成辅助功能模式

在 [SharePoint 合成](index.md)中，用户可以在使用示例文档时在模型 (、培训、测试) 启用辅助功能模式。 使用辅助功能模式可帮助低视力用户在文档查看器中导航和标记项目时更轻松地使用键盘辅助功能。

这可帮助用户使用键盘在文档查看器中浏览文本，并不仅听到所选值的旁白，还有助于听到操作 (例如标记或删除选定文本) 中的标签，或者用其他示例文档训练模型时预测的标签值。 


![辅助功能模式](../media/content-understanding/accessibility-mode.png)

## <a name="requirements"></a>要求

若要听到旁白的音频，请确保在 Windows 10 系统[](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1)上的"讲述人"设置中打开"讲述人"应用。

![打开"讲述人"](../media/content-understanding/narrator-settings.png)

## <a name="labeling-for-keyboard-users"></a>键盘用户标签

对于使用辅助功能模式的键盘用户，如果要在查看器中标记示例文档中的文本，可以使用以下键：

- Tab：向前移动并选择下一个单词。
- Tab + Shift：向后移动并选择上一个单词。
- Enter： Label or removes a label from the selected word.
- 向前箭头：在所选单词中的单个字符之间向前移动。
- 向后箭头：向后移动选定单词中的单个字符。

> [!NOTE]
> 如果要为单个标签标记多个单词，则需要标记每个单词。


## <a name="narration"></a>旁白

对于使用辅助功能模式的讲述人用户，请使用与键盘用户描述的相同的键盘导航，以在查看器中浏览示例文档。

在示例文档和标签字符串值中导航时，讲述人会向用户提供以下音频提示：

- 当使用键盘在文档查看器中导航时，讲述人音频将说明选定的字符串。
- 在选定的字符串中，"讲述人"音频将在你使用向前或向后箭头选择每个字符时，对字符串中的每个字符进行说明。
- 如果选择已标记的字符串，"讲述人"将声明该值，然后"标记"。  例如，如果标签值为"Contoso"，它将声明"Costoso labeled"。 
- 在培训选项卡中，如果在文档查看器中选择仅预测的字符串，"讲述人"音频将声明值，然后"预测"。 当培训预测文件中与用户标记的值不匹配的值时，会发生此情况。
- 在培训选项卡中，如果在已标记和预测的文档查看器中选择一个字符串，讲述人音频将声明值，然后"标记并预测"。 当培训成功且预测值与用户标签匹配时，将发生这种情况。



在查看器中标记字符串或删除标签后，讲述人音频会警告你退出之前保存更改。

## <a name="see-also"></a>另请参阅

[创建提取程序](create-an-extractor.md)</br>

[创建分类器](create-a-classifier.md)</br>










 


  
  


