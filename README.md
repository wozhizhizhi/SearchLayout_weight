# SearchLayout_weight
- ![image01.jpg](https://github.com/wozhizhizhi/SearchLayout_weight/blob/master/image/image01.jpg)

- 一款历史搜索记录功能自定义搜索框(可自定义)
- 使用简单高度自定义
## 步骤1：导入控件库
- root build.gradle写入
```
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```

- Gradle引入依赖 build.Gradle
```
dependencies {
	        compile 'com.github.wozhizhizhi:SearchLayout_weight:v1.0'
	}
```
## 步骤2：设置搜索框
-  在XML文件中进行设置 activity_search.xml
```
<com.aji.searchlayoutview.SearchView
        android:id="@+id/search_view"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:textSizeSearch="5dp"
        app:textColorSearch="#9b9b9b"
        app:textHintSearch="请输入查询的关键字"
        app:searchBlockHeight="150"
        app:searchBlockColor="#ffffff"
        />
```
## 步骤3：代码使用
```
public class MainActivity extends AppCompatActivity
{

    // 1. 初始化搜索框变量
    private SearchView searchView;
    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);

        // 2. 绑定视图
        setContentView(R.layout.activity_search);

        // 3. 绑定组件
        searchView = (SearchView) findViewById(R.id.search_view);

        // 4. 设置点击搜索按键后的操作（通过回调接口）
        // 参数 = 搜索框输入的内容
        searchView.setOnClickSearch(new ICallBack()
        {
            @Override
            public void SearchAciton(String string)
            {
                System.out.println("我收到了" + string);
            }
        });

        // 5. 设置点击返回按键后的操作（通过回调接口）
        searchView.setOnClickBack(new BCallBack()
        {
            @Override
            public void BackAciton() {
                finish();
            }
        });
    }

```
