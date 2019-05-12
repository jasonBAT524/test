# 一级标题
-   -   - 
## 二级标题
3. **第一行代码**
2. 第二行代码
4. 第三行代码
> 毛爷爷说的都对
> [这是个链接](www.baidu.com)
```
public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_download);

        final ProgressBar progressBar = (ProgressBar)findViewById(R.id.progressBar);

        /**
         * 主线程 -->start
         * 点击按钮 |
         * 发起下载 |
         * 开启子线程做下载 |
         * 下载完成后通知主线程 | -->主线程更新进度条
         */

        findViewById(R.id.button2).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                new Thread(new Runnable() {
                    @Override
                    public void run() {
                        /**
                         * Looper.prepare();
                         * Handler handler = new Handler();
                         * Looper.loop();
                         * 在子线程里要自己去搞  主线程UI中都默认有了MQ和Looper
                         */
                        download("http://download.sj.qq.com/upload/connAssitantDownload/upload/MobileAssistant_1.apk");
                    }
                }).start();

            }
        });
        ```
