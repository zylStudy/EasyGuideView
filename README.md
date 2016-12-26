# EasyGuideView
Android app新手引导提示，简单易用

## 效果

<img src="https://github.com/smuyyh/EasyGuideView/blob/master/screenshot/1.png?raw=true" width=270/>
<img src="https://github.com/smuyyh/EasyGuideView/blob/master/screenshot/2.png?raw=true" width=270/>

## 添加依赖

```
compile 'com.yuyh.easyguideview:library:1.1.0'
```

## 基本使用

```
public void show(){
    EasyGuide easyGuide = new EasyGuide.Builder(MainActivity.this)
            // 增加View高亮区域，可同时显示多个
            .addHightArea(view, HShape.CIRCLE)
            // 添加箭头指示
            .addIndicator(R.drawable.right_top, loc[0], loc[1] + view.getHeight())
            // 复杂的提示布局，建议通过此方法，较容易控制
            .addView(createTipsView(), 0, loc[1] + view.getHeight(),
                            new RelativeLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,
                            ViewGroup.LayoutParams.WRAP_CONTENT))
            // 设置提示信息，默认居中。若需调整，可采用addView形式
            .addMessage("点击菜单显示", 14)
            // 设置确定按钮，默认居中显示在Message下面
            .setPositiveButton("朕知道了~", 15)
            // 是否点击任意区域消失，默认true
            .dismissAnyWhere(true)
            .build();

    easyGuide.show();
}

private View createTipsView() {

    View view = LayoutInflater.from(this).inflate(R.layout.tips_view, null);

    ImageView ivIsee = (ImageView) view.findViewById(R.id.ivIsee);
    ivIsee.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            if (easyGuide != null) {
                easyGuide.dismiss();
            }
        }
    });

    return view;
}

```

## LICENSES

```
Copyright (C) 2016 smuyyh

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
