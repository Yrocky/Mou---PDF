# SettingBundle  设置束

## Root.plist

可选类型|简单含义|键和具体含义
----|----|----
Group|分组|键为PSGroupSpecifier，首选项逻辑编组的标题。
Mulit Value|多选|键为PSMultiValueSpecifier，下拉式列表。
Text Field|文本框输入|键为PSTextFieldSpecifier，可编辑的文本字符串。
Toggle Switch|选择开关|键为PSToggleSwitchSpecifier，开关按钮。
Slider|滑动杆|键为PSSliderSpecifier，取值位于特定范围内的滑块。
Title|显示文本|键为PSTitleValueSpecifier，只读文本字符串。
`Child Pane`|子窗格|键为PSChildPaneSpecifier，子首选项页。


**
Item0非常重要，Item0的类型一定是Group，对应的是一个分组表格类型，然后下面的Item都在这个分组表格中，直到遇到下一个Group。
**

**
基本设置`type`：可选类型 ,`Title`:将要显示的名字, `Identifier`:name_preference, `DefaultValue`：默认设置 。设置Identifier是为了通过ObjectForKey来查找数据。
但是indentifier和type是必须添加的，并且identifier不添加是不会显示的
**

##### Text Field

选项|含义
----|----
Text Field is Secure -- 是否为安全文本|如果设置为YES，则内容以圆点符号出现
Autocapitalization Style -- 自动大写。|有四个值: None(无)、Sentences(句子首字母大写)、Words(单词首字母大写)、All Characters(所有字母大写)
Autocorrection Style -- 自动纠正拼写。|如果开启，你输入一个不存在的单词，系统会划红线提示。有三个值：Default(默认)、No Autocorrection(不自动纠正)、Autocorrection(自动纠正)
Keyboard Type -- 键盘样式。|有五个值：Alphabet(字母表，默认)、Numbers and Punctuation(数字和标点符号)、Number Pad(数字面板)、URL(比Alphabet多出了.com等域名后缀)、Email Address(比Alphabet多出了@符合)


##### Toggle Switch

选项|含义
---|---
Value for ON |当开关置为ON时，取得的字符串值
Value for OFF | 当开关置为OFF时，取得的字符串值

##### Slider

选项|含义
---|---
Minimum Value | 最小值，Number类型
Maximum Value | 最大值，Number类型
Min Value Image Filename | 最小值那一端的图片
Max Value Image Filename | 最大值那一端的图片

`Ps.图片大小必须小于30*30，并且要放在Settings.bundle包内(在Finder里显示包内容，然后粘贴)。`

##### Multivalue

选项|含义
-----|----
Values | 值的集合
Titles | 标题的集合，**与值一一对应**

##### `Child Pane`

选项|含义
---|---
Filename | 子plist的文件名

