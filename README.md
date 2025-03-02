# speedpingjiao #
#### 这是什么：

哈尔滨工程大学教务系统评教脚本

#### 如何使用：

请按照以下步骤操作：

##### 1.打开浏览器并进入你需要自动填写的页面。

##### 2.按下 F12 键打开开发者工具。

##### 3.选择“控制台”选项卡。

##### 4.将下面代码粘贴到控制台中并按下 Enter 键。

#### 代码在哪里

```javascript
// 获取所有的选择题组
const questionGroups = document.querySelectorAll('.wjtxRadioButton');

// 遍历每个选择题组
questionGroups.forEach(group => {
  // 获取该组中的所有选项
  const options = group.querySelectorAll('.jqx-radiobutton-input');

  // 遍历选项，找到第一个选项并模拟点击
  options.forEach(option => {
    const text = option.nextElementSibling.textContent.trim();
    if (text.startsWith('A.')) {
      option.click();
    }
  });
});

console.log('所有选择题的第一项已被勾选');

// 获取所有的文本框
const textboxes = document.querySelectorAll('input[type="text"], textarea');

// 遍历每个文本框并填写“示例文本”
textboxes.forEach(textbox => {
  textbox.value = '示例文本';
  
  // 创建并触发输入事件
  const inputEvent = new Event('input', { bubbles: true });
  const changeEvent = new Event('change', { bubbles: true });
  
  // 使用 setTimeout 延迟触发事件
  setTimeout(() => {
    textbox.dispatchEvent(inputEvent);
    textbox.dispatchEvent(changeEvent);
  }, 100);
});

console.log('所有文本框已填写“示例文本”并触发了输入和变更事件');

```

请将其中的 textbox.value = '示例文本'; 中的示例文本替换为评教的文字内容，例如

教师通过对课本的独到深入的讲解，达到了很好的教学效果，能结合多种教学手段，使学生对知识的掌握更深刻。教学内容重点突出，教学目的十分明确，教师具有极高的专业技能。

#### 我懒怎么办？

我为你提供一个范例

```javascript
// 获取所有的选择题组
const questionGroups = document.querySelectorAll('.wjtxRadioButton');

// 遍历每个选择题组
questionGroups.forEach(group => {
  // 获取该组中的所有选项
  const options = group.querySelectorAll('.jqx-radiobutton-input');

  // 遍历选项，找到第一个选项并模拟点击
  options.forEach(option => {
    const text = option.nextElementSibling.textContent.trim();
    if (text.startsWith('A.')) {
      option.click();
    }
  });
});

console.log('所有选择题的第一项已被勾选');

// 获取所有的文本框
const textboxes = document.querySelectorAll('input[type="text"], textarea');

// 遍历每个文本框并填写“示例文本”
textboxes.forEach(textbox => {
  textbox.value = '教师通过对课本的独到深入的讲解，达到了很好的教学效果，能结合多种教学手段，使学生对知识的掌握更深刻。教学内容重点突出，教学目的十分明确，教师具有极高的专业技能。';
  
  // 创建并触发输入事件
  const inputEvent = new Event('input', { bubbles: true });
  const changeEvent = new Event('change', { bubbles: true });
  
  // 使用 setTimeout 延迟触发事件
  setTimeout(() => {
    textbox.dispatchEvent(inputEvent);
    textbox.dispatchEvent(changeEvent);
  }, 100);
});

console.log('所有文本框已填写“示例文本”并触发了输入和变更事件');

```

