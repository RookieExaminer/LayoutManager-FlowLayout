
来源此项目 https://github.com/xiangcman/LayoutManager-FlowLayout

[![](https://jitpack.io/v/RookieExaminer/LayoutManager-FlowLayout.svg)](https://jitpack.io/#RookieExaminer/LayoutManager-FlowLayout)

1.将其添加到存储库末尾的root build.gradle中：

	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}

2. 添加依赖项

	dependencies {
	        implementation 'com.github.RookieExaminer:LayoutManager-FlowLayout:Tag'
	}


说真的自从对**RecyclerView**的**LayoutManager**有新的认识后，完全不用担心很多的复杂布局了。而且对**ViewGroup**测量过程也不用担心了，因为里面有**LayoutManager**帮我们实现了。下面就进入该篇文章的主题吧，废话不多说，直接上图更有说服力。

<div>
    <image src="https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/photos/RecyclerView-LayoutManager-Text.gif" width="250" title="同一高度"/>
    <image hspace="20" src="https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/photos/RecyclerView-LayoutManager-DiffHeightText.gif" width="250"/>
    <image src="https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/photos/RecyclerView-LayoutManager-Image.gif" width="250"/>
</div>

上面的示例图是我把**ItemView**分别用了**TextView**和**ImageView**。其实这些是没什么好说的，主要是如何定义这样的**LayoutManager**。相信大家都用过了**LinearLayoutManager**吧，系统提供的**LayoutManager**都是对齐的方式进行排版的，我们这里的**flow**的样式就是在排版**item**之前，判断了该行多余的空间还够不够显示，如果不够直接换行显示的思路。

### 使用:
**详见[TextFlowActivity](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/app/src/main/java/com/single/flowlayout/TextFlowActivity.java)、[DiffHeightTextFlowActivity](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/app/src/main/java/com/single/flowlayout/DiffHeightTextFlowActivity.java)、[PhotoFlowActivity](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/app/src/main/java/com/single/flowlayout/PhotoFlowActivity.java)**
```
RecyclerView recyclerView = (RecyclerView) findViewById(R.id.flow);
FlowLayoutManager flowLayoutManager = new FlowLayoutManager();
//设置每一个item间距
recyclerView.addItemDecoration(new SpaceItemDecoration(dp2px(10)));
recyclerView.setLayoutManager(flowLayoutManager);
recyclerView.setAdapter(new FlowAdapter());
```

**RV嵌套RV高度问题:**
```
NestedRecyclerView recyclerView = (NestedRecyclerView) findViewById(R.id.flow);
FlowLayoutManager flowLayoutManager = new FlowLayoutManager(context);
//设置每一个item间距
recyclerView.addItemDecoration(new SpaceItemDecoration(dp2px(10)));
recyclerView.setLayoutManager(flowLayoutManager);
recyclerView.setAdapter(new FlowAdapter());
```

**常见商品属性界面:**

![商品属性界面.gif](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/photos/商品属性界面.gif)

使用:见[ProductActivity](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/app/src/main/java/com/single/flowlayout/ProductActivity.java)

**常见悬浮商品属性界面:**

![商品属性界面.gif](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/photos/悬浮商品属性界面.gif)

使用:见[SuspensionProductActivity](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/app/src/main/java/com/single/flowlayout/SuspensionProductActivity.java)

**动画修复:**

![动画修复.gif](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/photos/动画演示.gif)

使用:见[TextFlowActivity](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/master/app/src/main/java/com/single/flowlayout/TextFlowActivity.java)

**viewpager中流式布局应用:**

![viewpager中流式布局.gif](http://upload-images.jianshu.io/upload_images/2528336-e617484b3d42dc85.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

使用:见[ViewPagerActivity](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/vp_flow/app/src/main/java/com/single/flowlayout/ViewPagerActivity.java)

**常见长点击删除流式布局界面:**

![长点击删除界面.gif](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/vp_flow/photos/长点击删除界面.gif)

- 长点击删除图片问题

![长点击显示删除图片界面.gif](https://github.com/xiangcman/LayoutManager-FlowLayout/blob/master/photos/长点击显示删除图片界面.gif)

使用:见[LongClickDeleteTextFlowActivity](https://github.com/1002326270xc/LayoutManager-FlowLayout/blob/vp_flow/app/src/main/java/com/single/flowlayout/LongClickDeleteTextFlowActivity.java)

