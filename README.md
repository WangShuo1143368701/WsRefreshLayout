# WsRefreshLayout
WsRefreshLayout完全基于谷歌原生SwipeRefreshLayout，强于SwipeRefreshLayout。使用方法相同，且提供了更多的接口方法

### 引入方法：
```java
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
  
  dependencies {
	        compile 'com.github.WangShuo1143368701:WsRefreshLayout:V1.0'
	}
```
```java
<com.ws.weather.refreshlayout.WsRefreshLayout
        android:id="@+id/swipe_refresh"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
        ...
         </com.ws.weather.refreshlayout.WsRefreshLayout>
         
         
      private WsRefreshLayout mSwipeRefreshLayout;
      ... 
      
           mSwipeRefreshLayout= (WsRefreshLayout) mRootView.findViewById(R.id.swipe_refresh);//初始化
            mSwipeRefreshLayout.setColorSchemeResources(R.color.colorPrimary);//设置主题颜色
            mSwipeRefreshLayout.setCircleBackground(Color.parseColor("#00000000"));//设置背景色
            //设置下拉出现的图片
            Bitmap bitmap= BitmapFactory.decodeResource(getResources(),R.drawable.w0);
            mSwipeRefreshLayout.setProgressView(new WeatherProgressDrawable(getActivity(),mSwipeRefreshLayout,bitmap));
           //监听
           mSwipeRefreshLayout.setOnRefreshListener(new WsRefreshLayout.OnRefreshListener() {
                @Override
                public void onRefresh() {
                    ...
                }
            });
            
            
            //停止刷新
            mSwipeRefreshLayout.setRefreshing(false);
            
        
        //这里可以自定义下拉时的动画  ---》WeatherProgressDrawable  
              @Override
    public void setProgressRotation(float rotation) {
     //下拉时逆时针转加载时顺时针转，旋转因子是为了调整转的速度。
        this.rotation = -rotation*ROTATION_FACTOR;
        invalidateSelf();
    }

    @Override
    public void draw(Canvas c) {
        Rect bound = getBounds();
        c.rotate(rotation,bound.exactCenterX(),bound.exactCenterY());
        Rect src = new Rect(0,0,mBitmap.getWidth(),mBitmap.getHeight());
        c.drawBitmap(mBitmap,src,bound,paint);
    }
            
            ```
 ### 各位客官如果觉得不错，就双击666点亮star吧
