# 基础控件

## TextView

测试

## ImageView

该控件具有设置图片两个属性，**src** 和  **background**  

- src指内容 ，background 指背景
- background 会拉伸，src 根据图片大小填充
- src 和 background 可以同时使用
- 代码设置图片

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


## ToggleButton & Switch

- textOn
- textOff
- setOnCheckedChangeListener()

## 2019/01/06-Switch-开关

#### 基本布局

```java
<Switch
    android:id="@+id/s_button"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:showText="true"
    android:textOn="关闭"
    android:textOff="打开"
    />

<Switch
    android:id="@+id/s_buttona"
    android:layout_marginTop="40dp"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:thumb="@drawable/switch_thumb_on"
    android:track="@drawable/switch_track_on"
    android:textColor="#ff0000"
    android:textSize="20sp"
    android:textOn="@string/on"
    android:textOff="@string/off"
    android:switchMinWidth="80dp"
    />
```

#### 属性

- **android:showText：**设置on/off的时候是否显示文字,boolean
- **android:splitTrack：**是否设置一个间隙，让滑块与底部图片分隔,boolean
- **android:switchMinWidth：**设置开关的最小宽度
- **android:switchPadding：**设置滑块内文字的间隔
- **android:textOff：**按钮没有被选中时显示的文字
- **android:textOn：**按钮被选中时显示的文字
- **android:textStyle：**文字风格，粗体，斜体写划线那些
- **android:track：**底部的图片
- **android:thumb：**滑块的图片

#### 代码

```
public class SwitchActivity extends AppCompatActivity {

    Switch s_button,s_buttona;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_switch);
        s_button= (Switch) findViewById(R.id.s_button);
        s_buttona= (Switch) findViewById(R.id.s_buttona);

        s_buttona.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
                if(isChecked){
                    Toast.makeText(SwitchActivity.this, "1111打开了", Toast.LENGTH_SHORT).show();
                    return;
                }
                Toast.makeText(SwitchActivity.this, "1111关闭了", Toast.LENGTH_SHORT).show();
            }
        });

        s_button.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
                if(isChecked){
                    Toast.makeText(SwitchActivity.this, "打开了", Toast.LENGTH_SHORT).show();
                    return;
                }
                Toast.makeText(SwitchActivity.this, "关闭了", Toast.LENGTH_SHORT).show();
            }
        });
    }
}

//可能常用方法。
s_buttona.setChecked(true); 参数为true或false    是否默认打开。
s_buttona.getTextOff();
s_buttona.getTextOn();
s_buttona.setTextOn();
s_buttona.setTextOff();
```

#### 事件

```
s_buttona.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
    @Override
    public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
    }
});
```

#### 补充

//自定义样式。

滑块的自定义样式。

```
<selector xmlns:android="http://schemas.android.com/apk/res/android">
<item
    android:state_pressed="false">
    <shape>
        <size android:height="40dp" android:width="40dp"></size>
        <solid android:color="#ff0000"></solid>
    </shape>
</item>
    <item android:state_pressed="true">
        <shape>
            <size android:height="40dp" android:width="40dp"></size>
            <solid android:color="#ffff00"></solid>
        </shape>
    </item>
</selector>
```

背景的自定义样式。

```
<selector xmlns:android="http://schemas.android.com/apk/res/android">
<item android:state_checked="false" >
    <shape>
        <size android:height="40dp" android:width="40dp"></size>
        <solid android:color="#0000ff"></solid>
    </shape>
</item>
    <item android:state_checked="true" >
        <shape>
            <size android:height="40dp" android:width="40dp"></size>
            <solid android:color="#0000ff"></solid>
        </shape>
    </item>
</selector>
```

## 2019/01/06-ProgressBar-进度条

#### 基本布局

```
<LinearLayout android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    xmlns:android="http://schemas.android.com/apk/res/android">
    <ProgressBar
        android:id="@+id/pb_show"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:max="100"
        style="@style/Widget.AppCompat.ProgressBar.Horizontal"
        />
    <ProgressBar
        android:id="@+id/pb_showBase"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:max="100"
        style="@style/Base.Widget.AppCompat.ProgressBar.Horizontal"
        />
    <ProgressBar
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        style="@android:style/Widget.ProgressBar.Small"
        />
    <ProgressBar
        android:id="@+id/pb_showy"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        style="@android:style/Widget.ProgressBar.Horizontal"
        android:max="100"
        />
    <ProgressBar
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        style="@android:style/Widget.ProgressBar.Inverse"
        />
    <ProgressBar
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        style="@android:style/Widget.ProgressBar.Large"
        />
    <ProgressBar
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        style="@style/Widget.AppCompat.ProgressBar.Horizontal"
        android:indeterminateDuration="5"
        android:indeterminate="true"
        />
    <ProgressBar
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        style="@style/Widget.AppCompat.ProgressBar.Horizontal"
        android:indeterminate="true"
        />
    <ProgressBar
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        style="@android:style/Widget.ProgressBar.Horizontal"
        android:indeterminate="true"
        />
    <ProgressBar
        android:id="@+id/pb_zshow"
        android:layout_width="match_parent"
        android:layout_height="40dp"
        style="@android:style/Widget.ProgressBar.Horizontal"
        android:progressDrawable="@drawable/progressbar_z1"
        android:max="100"
        android:progress="10"
        />
</LinearLayout>
```

#### 属性

- android:**max**：进度条的最大值
- android:**progress**：进度条已完成进度值
- android:**progressDrawable**：设置轨道对应的Drawable对象
- android:**indeterminate**：如果设置成true，则进度条不精确显示进度
- android:**indeterminateDrawable**：设置不显示进度的进度条的Drawable对象
- android:**indeterminateDuration**：设置不精确显示进度的持续时间
- android:**secondaryProgress**：二级进度条，类似于视频播放的一条是当前播放进度，一条是缓冲进度，前者通过progress属性进行设置！

#### 代码

```
public class ProgressBarActivity extends AppCompatActivity {
    ProgressBar pb_show,pb_showBase,pb_showy,pb_zshow;
    int i=1;

    Handler handler=new Handler(){
        @Override
        public void handleMessage(Message msg) {
                if (msg.what==1){
                pb_show.setProgress(i);
                pb_showBase.setProgress(i);
                pb_showy.setProgress(i);
                pb_zshow.setProgress(i++);
                pb_zshow.setSecondaryProgress(i+new Random().nextInt(10));
            }
        }
    };

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_progress_bar);
        pb_show= (ProgressBar) findViewById(R.id.pb_show);
        pb_showBase= (ProgressBar) findViewById(R.id.pb_showBase);
        pb_showy= (ProgressBar) findViewById(R.id.pb_showy);
        pb_zshow= (ProgressBar) findViewById(R.id.pb_zshow);
        final Timer timer =new Timer();
    TimerTask timerTask = new TimerTask() {
        @Override
        public void run() {
            if(i>100){
                timer.cancel();
            }
            Message message = new Message();
            message.what = 1;
            handler.sendMessage(message);
        }
    };
    timer.schedule(timerTask,0, 500);
    }
}
```

#### 事件

#### 补充

由于样式比较多，在布局中将大多数的样式用了一遍。

下面是自定义样式。

```
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">

    <item android:id="@android:id/background">
        <shape>
            <solid android:color="#0000ff"></solid>
        </shape>
    </item>
    <item
        android:id="@android:id/secondaryProgress"
        >
        <clip>
        <shape>
            <solid android:color="#ff0000"></solid>
        </shape>
        </clip>
    </item>
    <item android:id="@android:id/progress">
        <clip>
        <shape>
            <solid android:color="#00ffff"></solid>
        </shape>
        </clip>
    </item>
</layer-list>
```



## 2019/01/06-SeekBar-拖动条

  #### 基本布局

  ```
  <LinearLayout android:layout_width="match_parent"
      android:layout_height="match_parent"
      android:orientation="vertical"
      xmlns:android="http://schemas.android.com/apk/res/android">
  
      <SeekBar
          android:id="@+id/sb_change"
          android:layout_width="match_parent"
          android:layout_height="wrap_content"
          android:max="100"
          />
      <SeekBar
          android:id="@+id/sb_changea"
          android:layout_width="match_parent"
          android:layout_height="wrap_content"
          android:thumb="@mipmap/ic_launcher"
          android:background="@color/colorAccent"
          android:maxHeight="20dp"
          android:max="100"
          />
      <SeekBar
          android:id="@+id/sb_changeb"
          android:layout_width="match_parent"
          android:layout_height="wrap_content"
          android:thumb="@mipmap/ic_launcher"
          android:progressDrawable="@drawable/seekbar_style"
          android:secondaryProgress="52"
          android:maxHeight="30dp"
          android:max="100"
          />
  
  </LinearLayout>
  ```

#### 属性

  **android:max**="100" //滑动条的最大值

  **android:progress**="60" //滑动条的当前值

  **android:secondaryProgress**="70" //二级滑动条的进度

  **android:thumb** = "@mipmap/sb_icon" //滑块的drawable

  #### 代码

  ```
  public class SeekBarActivity extends AppCompatActivity {
  
      SeekBar sb_change;
  
      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_seek_bar);
          sb_change= (SeekBar) findViewById(R.id.sb_change);
          sb_change.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
              @Override
     public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
       Toast.makeText(SeekBarActivity.this, "值发生改变。"+fromUser+" "+progress+" ", Toast.LENGTH_SHORT).show();
              }
  
              @Override
              public void onStartTrackingTouch(SeekBar seekBar) {
         Toast.makeText(SeekBarActivity.this, "开始滑动了", Toast.LENGTH_SHORT).show();
              }
  
              @Override
              public void onStopTrackingTouch(SeekBar seekBar) {
         Toast.makeText(SeekBarActivity.this, "停止滑动了", Toast.LENGTH_SHORT).show();
              }
          });
      }
  }
  ```

  #### 事件

  ```
  说明：
  onProgressChanged：进度发生改变时会触发
  onStartTrackingTouch：按住SeekBar时会触发
  onStopTrackingTouch：放开SeekBar时触发
  
  sb_change.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
      @Override
      public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
  
      }
  
      @Override
      public void onStartTrackingTouch(SeekBar seekBar) {
       
      }
  
      @Override
      public void onStopTrackingTouch(SeekBar seekBar) {
         
      }
  });
  ```

  #### 补充

  自定义样式。

  ```
  <layer-list xmlns:android="http://schemas.android.com/apk/res/android">
  <item android:id="@android:id/background"
      >
      <shape>
          <solid android:color="#0fff00"></solid>
      </shape>
  </item>
      <item android:id="@android:id/secondaryProgress"
          >
          <clip>
          <shape>
              <solid android:color="#f00f00"></solid>
          </shape>
          </clip>
      </item>
      <item
          android:id="@android:id/progress"
          >
          <clip>
              <shape>
                  <solid android:color="#0ffefa"></solid>
              </shape>
          </clip>
      </item>
  </layer-list>
  ```


## 2019/01/06-RatingBar-星级评分条

  #### 基本布局

  ```
  <LinearLayout android:layout_width="match_parent"
      android:layout_height="match_parent"
      android:orientation="vertical"
      android:gravity="center"
      xmlns:android="http://schemas.android.com/apk/res/android">
      <RatingBar
          android:id="@+id/rb_show"
          android:layout_width="match_parent"
          android:layout_height="wrap_content"
          android:isIndicator="true"
          android:numStars="5"
          android:rating="1.5"
          android:stepSize="0.1"
          />
      <RatingBar
          style="@style/Base.Widget.AppCompat.RatingBar.Indicator"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:numStars="5"
          android:rating="1.5"
          android:stepSize="0.1"
          />
      <RatingBar
      style="@style/Widget.AppCompat.RatingBar.Small"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:numStars="5"
      android:rating="1.5"
      android:stepSize="0.1"
          android:layout_margin="20dp"
      />
      <RatingBar
          style="@android:style/Widget.RatingBar"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:numStars="5"
          android:rating="1.5"
          android:stepSize="0.1"
          />
      <RatingBar
          style="@android:style/Widget.Holo.RatingBar"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:numStars="5"
          android:rating="1.5"
          android:stepSize="0.1"
          />
      <RatingBar
          android:id="@+id/rb_rgbs"
          android:layout_width="200dp"
          android:layout_height="40dp"
          android:progressDrawable="@drawable/retingbar_style_testa"
          android:numStars="5"
          android:rating="1.5"
          android:stepSize="0.1"
          />
  </LinearLayout>
  ```

  #### 属性

  **android:isIndicator**：是否用作指示，用户无法更改，默认false
  **android:numStars**：显示多少个星星，必须为整数
  **android:rating**：默认评分值，必须为浮点数
  **android:stepSize：** 评分每次增加的值，必须为浮点数

  #### 代码

  ```
  public class RatingBarActivity extends AppCompatActivity {
  
      RatingBar rb_show,rb_rgbs;
  
      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_rating_bar);
          rb_rgbs= (RatingBar) findViewById(R.id.rb_rgbs);
          rb_show= (RatingBar) findViewById(R.id.rb_show);
          rb_show.setOnRatingBarChangeListener(new RatingBar.OnRatingBarChangeListener() {
              @Override
    public void onRatingChanged(RatingBar ratingBar, float rating, boolean fromUser) {
                  Toast.makeText(RatingBarActivity.this, "结果："+rating+" "+fromUser, Toast.LENGTH_SHORT).show();
              }
          });
          rb_rgbs.setOnRatingBarChangeListener(new RatingBar.OnRatingBarChangeListener() {
              @Override
    public void onRatingChanged(RatingBar ratingBar, float rating, boolean fromUser) {
                  Toast.makeText(RatingBarActivity.this, "RGB值："+rating+" "+fromUser, Toast.LENGTH_SHORT).show();
              }
          });
      }
  }
  ```

  #### 事件

  ```
  rb_show.setOnRatingBarChangeListener(new RatingBar.OnRatingBarChangeListener() {
      @Override
      public void onRatingChanged(RatingBar ratingBar, float rating, boolean fromUser) {
          
      }
  });
  ```

  #### 补充

  自定义样式。

  ```
  <layer-list xmlns:android="http://schemas.android.com/apk/res/android">
  
      <item
          android:id="@android:id/background"
          >
          <selector>
              <item android:state_pressed="true">
                  <shape>
                      <solid android:color="#aa5f55"></solid>
                  </shape>
              </item>
              <item android:state_pressed="false">
                  <shape>
                      <solid android:color="#aa88ff"></solid>
                  </shape>
              </item>
          </selector>
      </item>
      <item
          android:id="@android:id/secondaryProgress"
          >
          <clip>
              <shape>
                  <solid android:color="#ff0000"></solid>
              </shape>
          </clip>
      </item>
      <item
          android:id="@android:id/progress"
          >
          <clip>
              <selector>
                  <item android:state_pressed="true">
                      <shape>
                          <solid android:color="#0000ff"></solid>
                      </shape>
                  </item>
                  <item android:state_pressed="false">
                  <shape>
                      <solid android:color="#00ff00"></solid>
                  </shape>
              </item>
              </selector>
          </clip>
      </item>
  </layer-list>
  ```


## 2019/01/06-ScrollView-滚动条

  #### 基本布局

  ```
  特别注意里面只能有一个布局，如果里面直接放了一个Button那么button里面就不能放控件了，一般ScrollView里面放的都是一个布局，这样在子布局里面还能放很多其他布局。
  一般用法：
  <ScrollView
      android:layout_width="match_parent"
      android:scrollbarThumbVertical="@drawable/scrollview_style_test"
      android:layout_height="match_parent">
      	<LinearLayout
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:orientation="vertical">
          
      	</LinearLayout>
      </ScrollView>
  ```

  #### 属性

  **垂直**方向滑块：android:**scrollbarThumbVertical**
  **水平**方向滑块：android:**scrollbarThumbHorizontal**

  隐藏滑块：android:scrollbars="none"



  我们可以直接利用ScrollView给我们提供的:**fullScroll()方法**：

  scrollView.fullScroll(ScrollView.**FOCUS_DOWN**);滚动到底部

  scrollView.fullScroll(ScrollView.**FOCUS_UP**);滚动到顶部

  scrollview.setVerticalScrollBarEnabled(false);隐藏滑块

  #### 代码

  ```
  这是菜鸟教程的button用法。
  public class MainActivity extends AppCompatActivity implements View.OnClickListener {
      private Button btn_down;
      private Button btn_up;
      private ScrollView scrollView;
      private TextView txt_show;
  
      @Override
      public void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_main);
          bindViews();
      }
      private void bindViews() {
          btn_down = (Button) findViewById(R.id.btn_down);
          btn_up = (Button) findViewById(R.id.btn_up);
          scrollView = (ScrollView) findViewById(R.id.scrollView);
          txt_show = (TextView) findViewById(R.id.txt_show);
          btn_down.setOnClickListener(this);
          btn_up.setOnClickListener(this);
  
          StringBuilder sb = new StringBuilder();
          for (int i = 1; i <= 100; i++) {
              sb.append("呵呵 * " + i + "\n");
          }
          txt_show.setText(sb.toString());
  
      }
  
      @Override
      public void onClick(View v) {
          switch (v.getId()) {
              case R.id.btn_down:
                  scrollView.fullScroll(ScrollView.FOCUS_DOWN);
                  break;
              case R.id.btn_up:
                  scrollView.fullScroll(ScrollView.FOCUS_UP);
                  break;
          }
      }
  }
  ```

## 2019/01/06-DatePicker-日期选择器

#### 基本布局
```
<LinearLayout android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    xmlns:android="http://schemas.android.com/apk/res/android">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="horizontal"
        >
        <DatePicker
            android:id="@+id/dp_show"
            style="@android:style/Widget.Holo.DatePicker"
            android:layout_width="wrap_content"
            android:layout_weight="1"
            android:layout_height="wrap_content"
            android:spinnersShown="true"
            android:endYear="2099"
            >
        </DatePicker>
<View
​    android:layout_width="1dp"
​    android:layout_height="match_parent"
​    android:background="#ff0000"
​    >
</View>
​        <DatePicker
​            android:id="@+id/dp_showa"
​            android:layout_weight="1"
​            style="@android:style/Widget.DatePicker"
​            android:layout_width="wrap_content"
​            android:layout_height="wrap_content"
​            android:spinnersShown="true"
​            android:endYear="2099"
​            >
​        </DatePicker>
​    </LinearLayout>
</LinearLayout>
```

#### 属性

- **android:calendarTextColor** ： 日历列表的文本的颜色
- **android:calendarViewShown**：是否显示日历视图
- **android:datePickerMode**：组件外观，可选值:spinner，calendar 前者效果如下，默认效果是后者 ![img](http://www.runoob.com/wp-content/uploads/2015/08/47223691.jpg)
- **android:dayOfWeekBackground**：顶部星期几的背景颜色
- **android:dayOfWeekTextAppearance**：顶部星期几的文字颜色
- **android:endYear**：去年(内容)比如2010
- **android:firstDayOfWeek**：设置日历列表以星期几开头
- **android:headerBackground**：整个头部的背景颜色
- **android:headerDayOfMonthTextAppearance**：头部日期字体的颜色
- **android:headerMonthTextAppearance**：头部月份的字体颜色
- **android:headerYearTextAppearance**：头部年的字体颜色
- **android:maxDate**：最大日期显示在这个日历视图mm / dd / yyyy格式
- **android:minDate**：最小日期显示在这个日历视图mm / dd / yyyy格式
- **android:spinnersShown**：是否显示spinner
- **android:startYear**：设置第一年(内容)，比如19940年
- **android:yearListItemTextAppearance**：列表的文本出现在列表中。
- **android:yearListSelectorColor**：年列表选择的颜色

#### 代码

```
public class DatePickerActivity extends AppCompatActivity {

    DatePicker dp_show,dp_showa;
    
    @SuppressLint("NewApi")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_date_picker);
        dp_show= (DatePicker) findViewById(R.id.dp_show);
        dp_showa= (DatePicker) findViewById(R.id.dp_showa);
        Calendar calendar=new GregorianCalendar();
            dp_show.init(calendar.get(Calendar.YEAR), calendar.get(Calendar.MONTH),calendar.get(Calendar.DAY_OF_MONTH), new DatePicker.OnDateChangedListener() {
                @Override
                public void onDateChanged(DatePicker view, int year, int monthOfYear, int dayOfMonth) {
                    Toast.makeText(DatePickerActivity.this, "您选择的日期是："+year+"年"+monthOfYear+1+"月"+dayOfMonth+"日", Toast.LENGTH_SHORT).show();
                }
            });
        dp_showa.init(calendar.get(Calendar.YEAR), calendar.get(Calendar.MONTH),calendar.get(Calendar.DAY_OF_MONTH), new DatePicker.OnDateChangedListener() {
            @Override
            public void onDateChanged(DatePicker view, int year, int monthOfYear, int dayOfMonth) {
                Toast.makeText(DatePickerActivity.this, "A您选择的日期是："+year+"年"+monthOfYear+1+"月"+dayOfMonth+"日", Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

#### 事件

```
注意一定要调用init不然会报错，在init中设置事件。
dp_showa.init(calendar.get(Calendar.YEAR), calendar.get(Calendar.MONTH),calendar.get(Calendar.DAY_OF_MONTH), new DatePicker.OnDateChangedListener() {
​    @Override
​    public void onDateChanged(DatePicker view, int year, int monthOfYear, int dayOfMonth) {
​        Toast.makeText(DatePickerActivity.this, "A您选择的日期是："+year+"年"+monthOfYear+1+"月"+dayOfMonth+"日", Toast.LENGTH_SHORT).show();
​    }
});
```

#### 补充

在初始化时间的时候要自己先new一个Calendar对象然后通过calendar.get(Calendar.YEAR)来获取当前年份，月份和天数也是相同的方法。

在设置事件监听中月份是以0开头的。



## 2019/01/06-TimePicker-时间选择器

#### 基本布局

```
<LinearLayout xmlns:tools="http://schemas.android.com/tools"
​    android:layout_width="match_parent"
​    android:layout_height="match_parent"
​    android:orientation="vertical"
​    android:gravity="center"
​    xmlns:android="http://schemas.android.com/apk/res/android">

    <TimePicker
        android:id="@+id/tp_show"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">
    
    </TimePicker>
    <TimePicker
        style="@android:style/Widget.Material.TimePicker"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        tools:targetApi="lollipop" />
</LinearLayout>
```

#### 属性

android:timePickerMode：组件外观，同样可选值为:spinner和clock(默认)

#### 代码

```
public class TimePickerActivity extends AppCompatActivity {

    TimePicker tp_show;
    
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_time_picker);
        tp_show= (TimePicker) findViewById(R.id.tp_show);
        tp_show.setOnTimeChangedListener(new TimePicker.OnTimeChangedListener() {
            @Override
            public void onTimeChanged(TimePicker view, int hourOfDay, int minute) {
                Toast.makeText(TimePickerActivity.this, "您选择的日期是："+hourOfDay+"时"+minute+"分", Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

#### 事件

```
tp_show.setOnTimeChangedListener(new TimePicker.OnTimeChangedListener() {
​    @Override
​    public void onTimeChanged(TimePicker view, int hourOfDay, int minute) {
​    }
});

```

#### 补充

TimePicker不需要初始化，只有DatePicker需要初始化。

## 2019/01/06-CalendarView-日历视图

#### 基本布局

```
<LinearLayout android:layout_width="match_parent"
​    android:layout_height="match_parent"
​    android:gravity="center"
​    android:orientation="horizontal"
​    xmlns:android="http://schemas.android.com/apk/res/android">
​    <CalendarView
​        android:id="@+id/cv_date"
​        android:layout_width="wrap_content"
​        android:layout_height="wrap_content">
​    </CalendarView>
​    <CalendarView
​        android:id="@+id/cv_dateb"
​        style="@android:style/Widget.Holo.CalendarView"
​        android:layout_width="300dp"
​        android:layout_height="300sp">
​    </CalendarView>
</LinearLayout>

```

#### 属性

- **android:firstDayOfWeek**：设置一个星期的第一天
- **android:maxDate** ：最大的日期显示在这个日历视图mm / dd / yyyy格式
- **android:minDate**：最小的日期显示在这个日历视图mm / dd / yyyy格式
- **android:weekDayTextAppearance**：工作日的文本出现在日历标题缩写

#### 代码

```
public class CalendarActivity extends AppCompatActivity {

    CalendarView cv_date;
    
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_calendar);
        cv_date= (CalendarView) findViewById(R.id.cv_date);
        cv_date.setOnDateChangeListener(new CalendarView.OnDateChangeListener() {
            @Override
            public void onSelectedDayChange(@NonNull CalendarView view, int year, int month, int dayOfMonth) {
                Toast.makeText(CalendarActivity.this, "您选择的是："+year+"年"+month+1+"月"+dayOfMonth+"日", Toast.LENGTH_SHORT).show();
            }
        });
    }
}

```

#### 事件

```
cv_date.setOnDateChangeListener(new CalendarView.OnDateChangeListener() {
​    @Override
​    public void onSelectedDayChange(@NonNull CalendarView view, int year, int month, int dayOfMonth) {
​    }
});

```

#### 补充

## Adapter

![adpater](./img/adapter_hierarchy.jpg)

**ArrayAdapter**

> 支持泛型操作，最简单的adapter

​	当需要设置选择类型时候，必须设置ListView的setChoiceMode

​```java
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

##### orientation

​```xml
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

- ExpandableAdapter 存放group以及group的子元素

## ProgressDialog

```java
ProgressDialog progressDialog = ProgressDialog.show(this, "提示", "加载中...");
ProgressDialog progressDialog = new ProgressDialog(this);
```

第一种的方式不能更改progress样式。	



## 事件处理的5种方式

- 内部类形式

```
btn_transaction_b.setOnClickListener(new MyListener());
```


```
在Activity中写子类
public class MyListener implements View.OnClickListener {

    @Override
    public void onClick(View v) {
        Toast.makeText(transaction5Activity.this, "我是内部类", Toast.LENGTH_SHORT).show();
    }
}
```

- 外部类形式

```
btn_transaction_c.setOnClickListener(new MyExternalListenner(transaction5Activity.this));
```

```
在新的类继承事件
public class MyExternalListenner implements View.OnClickListener {

    private Context context;

    public MyExternalListenner(Context context) {
        this.context=context;
    }

    @Override
    public void onClick(View v) {
        Toast.makeText(context, "我是外部类", Toast.LENGTH_SHORT).show();
    }
}
```



- Activity本身作为事件监听器类

```
public class transaction5Activity extends AppCompatActivity implements View.OnClickListener {
@Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
		btn_transaction_d.setOnClickListener(this);
}

    @Override
    public void onClick(View v) {
        switch (v.getId()){
            case R.id.btn_transaction_d:
 Toast.makeText(this, "我是transaction5Activity实现的接口", Toast.LENGTH_SHORT).show();
                break;
        }

    }
 }
```

- 匿名内部类形式

```
btn_transaction_a.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        Toast.makeText(transaction5Activity.this, "我是匿名类", Toast.LENGTH_SHORT).show();
    }
});
```

- 直接绑定到标签

```
直接在activity中写一个方法，注意要传一个view在方法中，不然要报错，在xml中配置onClick为方法名。
public void setBtn_transaction_e(View v){
    Toast.makeText(transaction5Activity.this, "第五种直接写方法", Toast.LENGTH_SHORT).show();
};

    <Button
        android:id="@+id/btn_transaction_e"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:onClick="setBtn_transaction_e"
        android:text="第5种"
        />
```



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



## BroadcasetReceiver广播

安卓四大组件之一

#### 广播继承使用

```
public class MyBroadcastReceiver extends BroadcastReceiver {
    String net="android.net.conn.CONNECTIVITY_CHANGE";
    String message="caidonglun.sendMessage";

    @Override
    public void onReceive(Context context, Intent intent) {

        if (net.equals(intent.getAction())){
            Toast.makeText(context, "网络发生改变。"+intent.getAction(), Toast.LENGTH_SHORT).show();
        }else if (ConnectivityManager.CONNECTIVITY_ACTION.equals(intent.getAction())){
            Toast.makeText(context, "收到消息", Toast.LENGTH_SHORT).show();
        }
    }
}
```



#### 注册方式

![](./img\broadcastReceiver_dong_tai_zhu_ce.jpg)

![](.\\img\broadcastReceiver_jing_tai_zhu_ce.jpg)

##### 静态注册详细配置

```
<receiver android:name=".MyBroadcastReceiver">
    <intent-filter android:priority="10">
        下面这行为自定义action
         <action android:name="caidonglun.sendMessage"></action> 
         监听网络变化
         <action android:name="android.net.conn.CONNECTIVITY_CHANGE"></action> 
    </intent-filter>
</receiver>
```

##### 动态注册详细代码

```
        MyBroadcastReceiver myBroadcastReceiver=new MyBroadcastReceiver();
        IntentFilter intentFilter=new IntentFilter();
//        文本也可以。
        String action = "android.net.conn.CONNECTIVITY_CHANGE";
//        使用该类的常量即可。
        intentFilter.addAction(ConnectivityManager.CONNECTIVITY_ACTION);
        intentFilter.addAction("caidonglun.sendMessage");
        registerReceiver(myBroadcastReceiver,intentFilter);
```

##### 动态注册为本地广播

```
LocalBroadcastManager instance = LocalBroadcastManager.getInstance(BroadcastReceiverCActivity.this);
IntentFilter intentFilter=new IntentFilter();
        intentFilter.addAction("dongdongdongdong");
        intentFilter.addAction(ConnectivityManager.CONNECTIVITY_ACTION);
        MyBroadcastD receiver = new MyBroadcastD();
        instance.registerReceiver(receiver,intentFilter);
```

#### 发送广播

![](.\\img\send_or_order_broadcaset.jpg)

常用方法和配置：

```
sendBroadcast(intent);无序广播
sendOrderedBroadcast(intent,null);有序广播，有序广播可以通过abortBroadcast();阻断继续传播。
<intent-filter android:priority="2"> 静态注册设置优先级，数字越大，优先级越高。
</intent-filter>
intentFilter.setPriority(2);动态注册设置优先级，数字越大，优先级越高。
```

![](.\\img\send_broadcast.jpg)

```
通过intent来发送广播，也能绑定数据在里面，通过Bundle或者intent.putExtra()来保存。
Intent intent=new Intent("caidonglun.sendMessage");
Bundle bundle=new Bundle();
bundle.putString("message","我是sendBroadcast");
bundle.putBoolean("isTrue",false);
intent.putExtras(bundle);
sendBroadcast(intent);
```

