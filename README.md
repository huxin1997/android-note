# 基础控件

## TextView

1、基本布局

```xml
<TextView
    android:id="@+id/tv_title"
    android:layout_width="match_parent"
    android:text="这是一段文字"
    android:layout_height="wrap_content" />
```

2、属性

1 对齐

**android:gravity="center" <!-- 控件内对齐 -->**

常用：center 居中
​	 center_horizontal 水平居中
​	 center_vertical 垂直居中
​	 left 左对齐
​	 rigth 右对齐
​	 top 顶部对齐
​	 bottom 底部对齐
​	 start 左对齐的替代形式
​	 end 右对齐的替代形式


![](G:\移动互联\解题\Annotation 2019-01-02 144952.jpg)

2 显示文字

**android:text="这是一段文字" <!-- 显示基础文字 -->**

**android:hint="这是一段默认文字" <!-- 显示默认文字 -->**

```xml
 <TextView
        android:id="@+id/tv_title"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="这是一段文字"
        android:hint="这是一段默认文字"
        />
```

![](G:\移动互联\解题\Annotation 2019-01-02 152137.jpg)

3 颜色

**android:textColor="#EA5246" <!--字体颜色-->**

4 字体样式

**android:textStyle="bold|italic" <!--字体加粗并斜体-->**

**android:textSize="22sp" <!--字体大小-->**

5 背景

**android:background="#ddd" <!--背景颜色可以是个drawable-->**

**android:background="@drawable/border"**

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <stroke android:color="#f00" android:width="1dp"></stroke>
    <solid android:color="#96ff96"></solid>
    <corners android:radius="5dp"></corners>
</shape>
```

6 格式

**android:singleLine="true" 或者android:maxLines="1" 设置一行显示**

**android:ellipsize="" 溢出显示方式**

可以有5种值：

| Constant | Value | Description  |
| -------- | ----- | ------------ |
| end      | 3     | 省略结束     |
| marquee  | 4     | 跑！马！灯！ |
| middle   | 2     | 省略中间     |
| none     | 0     | 默认         |
| start    | 1     | 省略开头     |

最常见是省略后面的文字和跑马灯



## EditText
1 基本布局

```xml
<EditText
    android:id="@+id/et_input"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:inputType="text"
    android:hint="这是个输入框"
    />
```

![1546425557527](1546425557527.png)

大多数方法和TextView相同

inputType 输入类型：

https://developer.android.google.cn/reference/android/R.styleable#TextView_inputType

几个常用：

- number 数字（只能输数字时可以用，比如允许输入1-999可以设置输入类型为数字并限制长度为3，这样在代码中就只需做非空和非0判断）
- text 文本
- textPassword 文本密码
- numberPassword 数字密码
- phone 号码

点击全选文字

```java
android:selectAllOnFocus="true" //点击时全选文字
```

2 代码

大部分相同，获取文字时注意类型！

**获取输入文本：getText()** 返回是个`Editable`对象，toString()即可返回正常文本

**代码输入文本：setText()**

​	

## ImageView

该控件具有设置图片两个属性，**src** 和  **background**  

- src指内容 ，background 指背景
- background 会拉伸，src 根据图片大小填充
- src 和 background 可以同时使用
- 代码设置图片

- android:adjustViewBounds="true" 缩放跟随宽高等比缩放
- android:maxHeight="" 最大的高度
- android:maxWidth="" 最大的宽度

第一个属性如果在宽高不对等的情况下，会优先缩放到最小的那一个值，其他部分留白。

有个专门属性控制缩放：

**android:scaleType**

| Constant     | Value | Description                                                |
| ------------ | ----- | ---------------------------------------------------------- |
| center       | 5     | 居中显示，不做任何缩放                                     |
| centerCrop   | 6     | 拉伸缩放，直到覆盖整个控件大小，并居中，可能图像出现不完整 |
| centerInside | 7     | 缩放，确保图像显示完整，居中显示                           |
| fitCenter    | 3     | 中心缩放，对齐中心                                         |
| fitEnd       | 4     | 局右缩放，对齐右边                                         |
| fitStart     | 2     | 局左缩放，对齐左边                                         |
| fitXY        | 1     | 拉伸缩放，填充宽高                                         |
| matrix       | 0     | 对齐左上角，不做缩放                                       |

当添加了上面这个属性后，adjustViewBounds属性无效！



## Button

1 基本布局

```xml
<Button
    android:id="@+id/btn_one_button"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Button"
    />
```

text中的英文字符都会强制变为大写

Button 继承自TextView，所以TextView有的属性，Button也有。

2 代码

设置点击事件

```java
btnOneB.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {
        ...
    }
});
```





## RadioButton 

该控件和RadioGroup 配合使用常用方法如下

- getChildCount()  
- getChildAt(i)
- isChecked() 

```java
RadioGroup sexGroup = findViewById(R.id.sexGroup);
sexGroup.setOnCheckedChangeListener((group, checkedId) ->{
	RadioButton radioButton = findViewById(checkedId);
	Toast.makeText(this, "你选择的是"+radioButton.getText(), Toast.LENGTH_SHORT).show();
  });
```



![1546417839052](./img/radiobutton.png)



## CheckBox 

- setOnCheckedChangeListener()

  1 布局

  与RadioButton继承关系一样，同样可以使用Button或TextView的所有属性

  ```xml
  <CheckBox
      android:id="@+id/cb_check_one"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:text="选我第一份"
      />
  ```

  这个就不能结合RadioGroup的事件来使用了，最好是在一堆多选框中使用LinearLayout包含使用。

  2 代码

  继承自Button和TextView，所以方法都类似，主要使用一个Getter和一个状态改变事件

  ```java
  checkBoxOne.isChecked();//是否被勾选
  ```

  ```java
  checkBoxOne.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
      @Override
      public void onCheckedChanged(CompoundButton compoundButton, boolean b) {
          ...
      }
  });
  /*
  	第一个事件发生的按钮，第二个参数是否被勾选
  */
  ```



## ToggleButton & Switch

- textOn
- textOff
- setOnCheckedChangeListener()

1 布局

还是和上面的RadioButton、CheckBox一样.

```xml
<ToggleButton
    android:id="@+id/tb_switch"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:disabledAlpha="1.0"
    android:textOn="我开着"
    android:textOff="我关着"
    />
```

两个属性：textOn和textOff分别代表激活时显示的字和没激活的字，此时设置text属性就没有用了。这两个属性代替了text属性。所以一定要设置。

另外可以设置drawable背景，在状态不同时改变背景。

android:disabledAlpha 按钮在禁用时的透明度

2 代码

按钮状态改变事件

```java
tbSwitch.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
    @Override
    public void onCheckedChanged(CompoundButton compoundButton, boolean b) {
        if(b){
            Toast.makeText(MainActivity.this, "开关：on", Toast.LENGTH_SHORT).show();
        }else {
            Toast.makeText(MainActivity.this, "开关：off",Toast.LENGTH_SHORT).show();
        }
    }
});
```

设置按钮状态

```java
tbSwitch.setChecked(true);
```



## ProgressBar

显示类型需要通过Style来设置。

## SeekBar

- thumb 设置进度标识样式

- Drawable 属性


## RatingBar 

- isIndicator 是否仅作演示
- NumStarts 数量
- Rating 评分值 浮点型
- StepSize 增加的量
- OnRatingBarChangeListener

## ScrollBar 

- fullSroll ()  :ScrollView.**FOCUS_DOWN** ,ScrollView.**FOCUS_UP**
- android:**scrollbarThumbVertical** 设置滑块图片

## Adapter

![adpater](./img/adapter_hierarchy.jpg)

**ArrayAdapter**

> 支持泛型操作，最简单的adapter

​	当需要设置选择类型时候，必须设置ListView的setChoiceMode

```java
listView.setChoiceMode(AbsListView.CHOICE_MODE_MULTIPLE);
```

![](.\img\listView_setchoiceMode.jpg)

**SimpleAdapter**

> 具有良好的扩展性,使用List<Map<String,?>> 结构存放数据。

**BaseAdapter**

> 抽象基类，需要自定义adapter通常继承它。

- convertView
- viewHolder
- inflate

## ListView

listView 复用原理：每一个item显示时都需要调用adapter的getView方法一次，此方法传入一个convertView参数，返回一个将会显示view对象，如果当item数量非常多时，若在在为每一个item都创建一个view对象，会造成内存开销过大。LayoutInflater.inflater()从XML读取属于IO操作也会造成耗时，必将影响性能。

​	android提供了一个叫做**Recycler**的构件，当滚动时超出屏幕上面的item将会被缓存到Recycler中，对应将会显示区域的下方生成一个Item，同时调用getView方法将Recycler中的item作为convertView参数传递到方法中去。所有重用convertView会提升性能。

​	![](.\img\recycler.jpg)

### issue

​	如果使用了recycler缓存机制，新加载的item由于是复用之间隐藏的item将会出现控件属性还是之间item的，造成状态混乱。

​	![](F:\资料文档\笔记\Android笔记\img\listview_checkbox.gif)

常用属性：

```xml
<ListView
        android:id="@+id/lv_1"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:divider="@android:color/holo_blue_bright"
        android:dividerHeight="2dp"/>
```

divider：列表项之间绘制的可绘制的颜色。

dividerHeight：divider的高度。

预览图如下：

![546657356751](.\img\listview_review.png)

使用xml配置ListView的数据

entries：填充res里的values里已经配置好的固定数据

```xml
<ListView
    android:id="@+id/lv_0"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:entries="@array/listview_data"/>
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string-array name="listview_data">
        <item>这是xml配置的数据01</item>
        <item>这是xml配置的数据012</item>
        <item>这是xml配置的数据013</item>
        <item>这是xml配置的数据014</item>
        <item>这是xml配置的数据015</item>
        <item>这是xml配置的数据016</item>
        <item>这是xml配置的数据017</item>
        <item>这是xml配置的数据018</item>
    </string-array>
</resources>
```

运行结果如下：

![1546658930283](C:\Users\baikunlong\AppData\Roaming\Typora\typora-user-images\1546658930283.png)



## Layout

1. layout继承关系
2. LinearLayout

   - 常用控件属性

     - Orientaion

     - gravity

     - layout_gravity

     - layout_width

     - layout_height

     - background

     - weight
   - Divider
     - divider
     - showDividers
     - dividersPadding 
3. 布局方式练习 代码方式显示
4. RelativeLayout
   - 控件属性

#### LinearLayout

![linearLayout](.\img\linearlayout_inher.jpg)

LinearLayout是一个控件容器，用于将容器内的子元素按照指定的方向(水平或者垂直)线性排列。LinearLayout 继承自ViewGroup，呈线性显示它的子元素，水平排列一行或者垂直显示一列Views。

##### **orientation**

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
   android:layout_width="match_parent"
   android:layout_height="match_parent"
   android:orientation="vertical">
 </LinearLayout>
```

​	通知设置 `android:orientaion` 属性设置 水平( **horizontal **)显示和垂直(**vertical**)显示。





![](F:\资料文档\笔记\Android笔记\img\vertical.jpg)

​				

​						![](F:\资料文档\笔记\Android笔记\img\horizontal.jpg)



##### layout_width & layout_height

该属性值分为四种

- wrap_content
- match_parent
- ~~fill_parent~~
- 固定值 dp



##### gravity (容器里子控件的对齐方向） 

常用7种属性值

- Top 上
- Bottom 下
- Left 左
- Right 右
- center 水平垂直居中
- center_horizontal 水平居中
- center_vertical 垂直居中

##### ****layout_gravity

控件在父容器的对其方式



##### weight(布局权重）

用于线性布局种的控件分配剩余空间比例权重。

![](F:\资料文档\笔记\Android笔记\img\weight.jpg)













##### 嵌套使用	

![](F:\资料文档\笔记\Android笔记\img\qiantao.jpg)

##### Margin & padding

![](F:\资料文档\笔记\Android笔记\img\margin_padding.jpg)



##### Divider 

- divider
- showDividers
- dividerPadding





##### 练习

![](F:\资料文档\笔记\Android笔记\img\login.jpg)



#### RelativeLayout

![](F:\资料文档\笔记\Android笔记\img\relative_layout.jpg)

##### 梅花布局

![

](F:\资料文档\笔记\Android笔记\img\meihua.jpg)

## Spinner

```xml
<Spinner
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:spinnerMode="dialog" <--dropdown-->
    android:entries="@array/tool">
</Spinner>
```



## ExpandableListView

- **ExpandableAdapter** 存放group以及group的子元素

- **android:childDivider**：指定各组内子类表项之间的分隔条，图片不会完全显示， 分离子列表项的是一条直线

- **android:childIndicator**：显示在子列表旁边的Drawable对象，可以是一个图像

- **android:groupIndicator**：显示在组列表旁边的Drawable对象，可以是一个图像




## ProgressDialog的

```java
ProgressDialog progressDialog = ProgressDialog.show(this, "提示", "加载中...");
ProgressDialog progressDialog = new ProgressDialog(this);
```

第一种的方式不能更改progress样式。	



## 事件处理的5种方式

- 内部类形式
- 外部类形式
- Activity本身作为事件监听器类
- 匿名内部类形式
- 直接绑定到标签

## Handler

> Handler 发送消息(Message) 到消息队列中(MessageQueue) ，Looper 通过无限循环的方式不断向消息队列中获取新添加的消息 然后交给 Handler ，最终消息回到 Handler 中被处理
>
>

#### 耗时 - 线程安全

#### 线程生命周期

#### MainThread & WorkerThread

#### ANR

#### Message

- obj
- what

#### MessageQueue （消息队列）

- 容器
- 添加 queue.enqueueMessage(msg, uptimeMillis)
- 消费



#### Looper

![](![img](https://images0.cnblogs.com/blog/234895/201308/19093258-aa3efb1164ba4959a55cb9b3369b98e0.x-png))

线程分为主线程(主线程又叫UI线程，只能有一个主线程）和子线程（可以有多个）Handler只能在主线程里运行 
handler是Android给我们提供用来更新UI的一套机制，也是一套消息处理机制，我们可以发消息，也可以通过它 处理消息。 谷歌采用了只允许在主线程更新UI。

- 子线程中修改UI，耗时操作，网络操作，handler修改UI
- runOnUiThread()
- handler.post()
- handler.sendMessage()
- handler.sendEmptyMessage()
- loop()
- 



mHandler



1. 演示ANR (耗时操作)
2. 线程安全
3. Handler
4. handler常用使用方式
5. Looper Message MessageQueue
6. 练习







##### Hnadler 常用方法

1. sendMessage(msg)  
2. sendEmptyMessageDelayed(what , 0)
3. sendEmptyMessage(what)
4. post(runnable)





##### Activity 方法

runOnUIThread







