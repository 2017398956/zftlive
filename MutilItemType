# 一、Adapter的写法
1、继承自MultiTypeAdapter

2、添加一个带Activity入参的构造方法，必须含有该签名的构造方法，否则后续编译不过

3、实现registeViewTemplet和adjustItemViewType方法

``` java

/**
 * 头条多类型类别适配器
 *
 * @author 曾繁添
 * @version 1.0
 *
 */
public class NewsMutilTypeAdapter extends MultiTypeAdapter{

    public NewsMutilTypeAdapter(Activity mContext) {
        super(mContext);
    }

    @Override
    public void registeViewTemplet(Map<Integer, Class<? extends AbsViewTemplet>> mViewTemplet) {
        //注册一共含有的itemType以及对应的视图模板类
        mViewTemplet.put(0,ProductViewTemplet.class);
        mViewTemplet.put(1,TopicViewTemplet.class);
        mViewTemplet.put(2,ArticleViewTemplet.class);
        mViewTemplet.put(3,ArticleViewTemplet.class);
        mViewTemplet.put(4,ArticleSplitViewTemplet.class);
    }

    @Override
    public int adjustItemViewType(Object model, int position) {
        //拿到数据模型判断当前行对应的itemType
        return ((NewsListRowBean)model).itemType;
    }
}
```

# 二、一种itemType对应的视图模板写法

1、继承AbsViewTemplet 

2、添加一个含有Context形参签名的构造方法，并调用super对应的构造方法

3、依次实现bindLayout、initView、fillData方法，在对应的函数实现对应的代码即可

``` java
/**
 * 推荐文章与历史文章分隔线模板
 *
 * @author 曾繁添
 * @version 1.0
 *
 */
public class ArticleSplitViewTemplet extends AbsViewTemplet {

    private TextView tv_tips_text;

    public ArticleSplitViewTemplet(Context mContext) {
        super(mContext);
    }

    @Override
    public int bindLayout() {
        return R.layout.zc_news_recommend_history_split;
    }

    @Override
    public void initView() {
        tv_tips_text = (TextView) findViewById(R.id.tv_tips_text);
    }

    @Override
    public void fillData(Object model, int postion) {
        NewsListRowBean rowData = (NewsListRowBean)model;
        tv_tips_text.setText(rowData.recommendSplitText);
    }
}

```

# 三、待续
后续会在AbsViewTemplet中加入消费item的点击事件、长按事件以及跳转启动Activity/Fragment等共通处理能力



