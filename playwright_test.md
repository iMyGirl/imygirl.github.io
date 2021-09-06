[TOC]  

#  playwright_test 

## 1 写在前面
针对 Node.js 版本的 playwright 进行API梳理与测试应用  
参考[官方网站](https://playwright.dev/)  
[源码](https://github.com/microsoft/playwright)  
（先安装好Node.js v12.10.0，**macOS**: Requires 10.14 or above.）  

项目相关[Playwright走查工具](https://joyspace.jd.com/page/g5hD5XgCXbneuNEI69U8)  
走查网站[分期商城](https://mxxq.jd.com/mx/home?from=818xyyicon&pageId=2894&jrcontainer=h5&jrlogin=true&utm_term=copyurl)  
## 2 安装与运行
[官网参照](https://playwright.dev/docs/1.10.0/intro)
需要先安装好Node.js，然后照如下安装：  
version: 1.12.0及其以前的，仅可安装 playwright 操作

```shell
# 用 node xxx.js 运行，安装 playwright
$ npm i -D playwright
# Playwright Test 默认情况下不捆绑浏览器，所以您需要显式安装它们
$ npx playwright install 
```
安装完成后，针对脚本 xxx.js ，利用 <kbd>require</kbd> 引入playwright，可选择三种浏览器（Chrome / firefox / webkit）方式载入。使用 <kbd>the async/await pattern</kbd>执行代码（Playwright API是异步的，返回Promise对象）。

```javascript
/*  xxx.js   */
// 引入 playwright
const { chromium } = require('playwright');
// 代码包装在一个正在调用自身的未命名异步箭头函数中
(async () => {  
	const browser = await chromium.launch();  
// ...
	await browser.close();
})();
```
编辑好脚本 xxx.js 后，可利用当作js脚本运行
```shell
# 用 node xxx.js 运行
$ node xxx.js
```
* * *
version: 1.13.0及以后可安装 [playwright/test](https://playwright.dev/docs/api/class-test) 操作

>playwright/test提供了一个test()函数来声明测试，以及expect()函数来编写断言
```shell
# 用 test 运行，安装 Playwright Test
$ npm i -D @playwright/test
# Playwright Test 默认情况下不捆绑浏览器，所以您需要显式安装它们
$ npx playwright install 
# 用 test 运行
$ npx playwright test
```

>案例一  —— 转到 www.baidu.com ，然后截屏
```javascript
/* xxx.js */

const { webkit } = require('playwright');         // 引入Playwright

(async () => {
  const browser = await webkit.launch({           // 启动浏览器 
    headless: false
  });
  const page = await browser.newPage();         // 打开新的标签页
  await page.goto('http://baidu.com')           // 转到指定网站
  await page.screenshot({ path: 'example.png' });     // 截屏
  await browser.close();							// 关闭浏览器
})();
```
P.S.  await webkit.launch({  headless: false  });  ，将 headless设为 false 即可视化运行，默认后台运行。

## 3 录制脚本

### codegen方式
[codegen[options][url]](https://playwright.dev/docs/cli/#generate-code)（打开浏览器，录制并生成脚本）  

>options含义：  

 -o：将录制的脚本保存到一个文件  
 --target：规定生成脚本的语言，有JS和Python两种，默认为Python  
 -b：指定浏览器驱动  
 --save-storage=[cookie.json]  
 --load-storage=[cookie.json]  

```shell
$ npx playwright codegen wikipedia.org

# 自动存储cookies
$ npx playwright codegen --save-storage=auth.json
# 载入cookies
$ npx playwright codegen --load-storage=auth.json my.web.app

# 自动存储脚本（-o），指定浏览器（-b）
npx playwright codegen -o 'my1.py' -b chromium https://u.jd.com/MyHO6C
```

### open方式
[open [options] [url]](https://playwright.dev/docs/cli/#open-pages)（打开浏览器，可选择录制）
>options含义：  

--device： 指定模拟设备  
[设备支持列表](https://github.com.cnpmjs.org/microsoft/playwright/blob/master/src/server/deviceDescriptorsSource.json)  

```
# 在WebKit中打开
$ npx playwright wk example.com

# 模拟 iPhone 11.
npx playwright open --device="iPhone 11" wikipedia.org
```

>help信息：
```
# --help
$ npx playwright -h

// Usage: npx playwright [options] [command]

// Options:
//   -V, --version                          output the version number
//   -h, --help                             display help for command

// Commands:
//   open [options] [url]                   open page in browser specified via -b, --browser
//   codegen [options] [url]                open page and generate code for user actions
//   debug <app> [args...]                  run command in debug mode: disable timeout, open inspector
//   install [browserType...]               ensure browsers necessary for this version of Playwright are installed
//   install-deps [browserType...]          install dependencies necessary to run browsers (will ask for sudo permissions)
//   cr [options] [url]                     open page in Chromium
//   ff [options] [url]                     open page in Firefox
//   wk [options] [url]                     open page in WebKit
//   screenshot [options] <url> <filename>  capture a page screenshot
//   pdf [options] <url> <filename>         save page as pdf
//   help [command]                         display help for command

```

>例句
```shell
$ npx playwright codegen --load-storage=session.json --device="Pixel 2" -o 'shop9.js' --target 'javascript' https://mxxq.jd.com/mx/home\?from\=818xyyicon\&pageId\=2894\&jrcontainer\=h5\&jrlogin\=true\&utm_term\=copyurl


$ npx playwright open --load-storage=session.json --device="iPhone 6" -b webkit https://mxxq.jd.com/mx/home\?from\=818xyyicon\&pageId\=2894\&jrcontainer\=h5\&jrlogin\=true\&utm_term\=copyurl

$ npx playwright open --load-storage=session.json --device="iPad (gen 6) landscape" https://q.jd.com/m/xj/index.html?skuId=100004770247&groupId=5285&xxfSceneId=A334969906062647296

$ npx playwright open --load-storage=session.json --device="iPad Mini" -b webkit https://mxxq.jd.com/mx/home\?from\=818xyyicon\&pageId\=2894\&jrcontainer\=h5\&jrlogin\=true\&utm_term\=copyurl

$ npx playwright open --device="iPad Mini" -b webkit https://mxxq.jd.com/mx/home\?from\=818xyyicon\&pageId\=2894\&jrcontainer\=h5\&jrlogin\=true\&utm_term\=copyurl

$ npx playwright codegen --load-storage=session.json --device="iPhone 11 Pro" -o 'shop11.js' -b webkit --target 'javascript' https://mxxq.jd.com/mx/home\?from\=818xyyicon\&pageId\=2894\&jrcontainer\=h5\&jrlogin\=true\&utm_term\=copyurl

$ npx playwright codegen --load-storage=session.json -o "shop11.js" --target "javascript"  
```



## 5 核心概念
[官网参照](https://playwright.dev/docs/1.10.0/core-concepts)  

Playwright框架提供一套API以实现Web自动化，以下为部分常用API：



### Brower(浏览器)

Brower一般可选三种（Chrome / firefox / webkit），Playwright脚本一般以启动浏览器开始，以关闭浏览器结束，而浏览器可以无头模式（即没用用户交互界面）运行。启动浏览器比较耗费资源，所以Playwright最大限度利用地利用一个实例在多个浏览器的Context（对应汉语意为上下文，Playwright的API中的一个类，可包含多个页面，多个Context可以由一个实例启动）中实现。

```javascript
const { chromium } = require('playwright');  // Or 'firefox' or 'webkit'.

const browser = await chromium.launch({ headless: false });
await browser.close();
```

API 链接[Browser](https://playwright.dev/docs/1.10.0/api/class-browser)

### Browser contexts

Browser contexts 是Playwright启动浏览器后可创建的一种会话。
创建 Browser contexts 占用资源比较少，推荐新建 Browser contexts 来运行每个测试场景，此时不同 Browser contexts 中的测试场景是相互独立的。

```javascript
const browser = await chromium.launch();
const context = await browser.newContext();
```
Browser contexts 可以用来模拟不同的移动设备及其权限、位置信息、颜色主题等多页场景。
```javascript
const { devices } = require('playwright');
const iPhone = devices['iPhone 11 Pro'];

const context = await browser.newContext({
  ...iPhone,
  permissions: ['geolocation'],
  geolocation: { latitude: 52.52, longitude: 13.39},
  colorScheme: 'dark',
  locale: 'de-DE'
});
```
API 链接[BrowserContext](https://playwright.dev/docs/1.10.0/api/class-browsercontext)   [browser.newContext](https://playwright.dev/docs/1.10.0/api/class-browser#browsernewcontextoptions)

### Pages and frames（页面和框架）

一个 Browser contexts 可以有多个页面（Pages）。一个 Page 就是单个标签页，它可以导航到 URL，并进行交互。

```javascript
const {chromium} = require('playwright');

(async() => {
  const browser = await chromium.launch({
    headless: false
  })

  const context = await browser.newContext();
  // Create a page.
  const page = await context.newPage();
  
  // Navigate explicitly, similar to entering a URL in the browser.
  await page.goto('https://baidu.com');
  // Click input[name="wd"]
  await page.click('input[name="wd"]');
  // Click input[name="wd"]
  await page.click('input[name="wd"]');
  // Fill input[name="wd"]
  await page.fill('input[name="wd"]', '京东');
  // Press ArrowDown
  await page.press('input[name="wd"]', 'ArrowDown');
  // Press Enter
  await page.press('input[name="wd"]', 'Enter');
  // assert.equal(page.url(), 'https://www.baidu.com/s?ie=utf-8&f=8&rsv_bp=1&rsv_idx=1&tn=baidu&wd=%E4%BA%AC%E4%B8%9C%E5%95%86%E5%9F%8E&fenlei=256&rsv_pq=dbd3f14500083f54&rsv_t=588cSM8AbykRJYkT0k1hOyMJfbdfzK7P3vc5Z2y3ZWCUlBEhbOKsG56Jvvw&rqlang=cn&rsv_enter=1&rsv_dl=ib&rsv_sug3=12&rsv_sug1=9&rsv_sug7=100&sug=%25E4%25BA%25AC%25E4%25B8%259C%25E5%2595%2586%25E5%259F%258E&rsv_n=1');
  // Click text=京东JD.COM官网 多快好省 只为品质生活

  console.log(page.url());

  const [page1] = await Promise.all([
    page.waitForEvent('popup'),
    page.waitForNavigation(/*{ url: 'https://www.jd.com/?cu=true&utm_source=baidu-pinzhuan&utm_medium=cpc&utm_campaign=t_288551095_baidupinzhuan&utm_term=0f3d30c8dba7459bb52f2eb5eba8ac7d_0_423f2e181dfa4369bdc66c7dc2ef5fab' }*/),
    page.click('text=京东JD.COM官网 多快好省 只为品质生活')
  ]);
  // Page can navigate from the script - this will be picked up by Playwright.
  window.location.href = 'https://baidu.com';  // 报错 UnhandledPromiseRejectionWarning: ReferenceError: window is not defined
})()
```

一个 Page 可以有一个或多个 frame（框架）。每个页面都有一个主框架，假设页面级交互（如点击）在主框架中运行。

一个页面可以附加附加有 iframe HTML 标签的框架。 可以访问这些框架以进行框架内的交互。


```javascript
// Get frame using the frame's name attribute
const frame = page.frame('frame-login');

// Get frame using frame's URL
const frame = page.frame({ url: /.*domain.*/ });

// Get frame using any other selector
const frameElementHandle = await page.$('.frame-class');
const frame = await frameElementHandle.contentFrame();

// Interact with the frame
await frame.fill('#username-input', 'John');
```








API 链接[Page](https://playwright.dev/docs/1.10.0/api/class-page/) /  [Frame](https://playwright.dev/docs/1.10.0/api/class-frame) /  [page.frame(frameSelector)](https://playwright.dev/docs/1.10.0/api/class-page/#pageframeframeselector)


### Selectors (选择器)









#### 鼠标点击

[page.click(selector[, options])](https://playwright.dev/docs/api/class-page#page-click)  

page.click('[JSpath]') —— [JSpath]可被保证点击，而[字段方式]（text=[字段内容]）不一定。

```javascript
// [字段方式]
await page.click('text=Apple iPhone 11 (A2223) 64GB 白色 移动联通电信4G手机 双卡双待 ¥195.92 x24期 >> img');
 
// [JSpath]
await page.click('#app > div > div > div.cls-brand-page-head > div.home-store-container > div > div.tran > div > div:nth-child(1) > div.item-img > img');
```

#### 截屏
[page.screenshot({ path: 'screenshot.png' })](https://playwright.dev/docs/screenshots#full-page-screenshots)
截全屏如下：

```javascript
await page.screenshot({ path: 'screenshot.png', fullPage: true });
```

## 6 API梳理

### playwright
#### playwright.chromium



### Page



页面提供了与 [Browser](https://playwright.dev/docs/api/class-browser)中的单个选项卡或Chromium中的[extension background page](https://developer.chrome.com/extensions/background_pages)交互的方法。一个 [Browser](https://playwright.dev/docs/api/class-browser)实例可能有多个[Page](https://playwright.dev/docs/api/class-page) 实例。

本例创建 一个Page，将其导航到URL，然后保存屏幕截图：

```javascript
const { webkit } = require('playwright');  // Or 'chromium' or 'firefox'.

(async () => {
  const browser = await webkit.launch();
  const context = await browser.newContext();
  const page = await context.newPage();
  await page.goto('https://example.com');
  await page.screenshot({path: 'screenshot.png'});
  await browser.close();
})();
```

Page类发出各种事件（如下所述），可以使用 Node 的任何本机 EventEmitter 方法（如<kbd>on</kbd>、<kbd>once</kbd>或<kbd>removeListener</kbd>）处理这些事件。

此示例记录单个页面 <kbd>load</kbd> 事件的消息：

```javascript
page.once('load', () => console.log('Page loaded!'));
```

要取消订阅事件，请使用<kbd>removeListener</kbd>方法：

```javascript
function logRequest(interceptedRequest) {
  console.log('A request was made:', interceptedRequest.url());
}
page.on('request', logRequest);
// Sometime later...
page.removeListener('request', logRequest);
```

 [page.on](https://playwright.dev/docs/api/class-page#page-event-close)

...

Page即页面操作，可通过[browserContext.newPage()](https://playwright.dev/docs/api/class-browsercontext/#browser-context-new-page)创建

+ returns: <[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) < [Page](https://playwright.dev/docs/api/class-page) >>

主要完成页面点击等操作。



> selector 即选择器，选择文字/图片/区域块等，例如“text=16:00”

| 动作 | 函数 | 元素/options |  |
|  :----| :----|  :----| :----|
| 单击 | [page.click(selector[, options])](https://playwright.dev/docs/api/class-page#page-click) | 【选择器[，选项]】 | /---------------例句---------------/ |
|  | / | 不加options | page.click('text=16:00')  //左击'text=16:00'元素 |
|  | / | /-----加入options如下-----/ | / |
|  | /点击次数 | clickCount: <num> | page.click('text=16:00', {clickCount: 11})  //左击'text=16:00'元素，且点击了11次； |
|  | /鼠标键位（左击/滑轮点击/右击） | button: <"left"/"right"/"middle"> | page.click('text=16:00', {button: "right"}) //右击'text=16:00'元素 |
|  | /延时（鼠标从下落到上升的时间） | delay:<num> | page.click('text=16:00', {delay: 1000})  //左击'text=16:00'元素且按下持续一秒 |
|  | /按下修饰键（如"Ctl"+单击） | modifiers:<Array<"Alt"/"Control"/"Meta"/"Shift">> | page.click('text=16:00', {modifiers: ["Control"]}) //按下"Control"+左击'text=16:00'元素 |
|  | /定位（相对于元素填充框的左上角使用的点，若未指定则使用元素某个可见点） | position < Object> x:<num>,y:<num> | page.click('text=16:00',{position:{x:0,y:33}}) |
| 双击 | [page.dblclick(selector[, options])](https://playwright.dev/docs/api/class-page#page-dblclick) | 【选择器[，选项]】/------options如下------/ | /---------------例句---------------/ |
|  | / | 不加options | page.click('text=16:00')  //左击'text=16:00'元素 |
|  | / | /-----加入options如下-----/ | / |
|  | /鼠标键位（左击/滑轮点击/右击） | button: <"left"/"right"/"middle"> | page.click('text=16:00', {button: "right"}) //右击'text=16:00'元素 |
|  | /延时（鼠标从下落到上升的时间） | delay:<num> | page.click('text=16:00', {delay: 1000})  //左击'text=16:00'元素且按下持续一秒 |
|  | /按下修饰键（如"Ctl"+单击） | modifiers:<Array<"Alt"/"Control"/"Meta"/"Shift">> | page.click('text=16:00', {modifiers: ["Control"]}) //按下"Control"+左击'text=16:00'元素 |
|  | /定位（相对于元素填充框的左上角使用的点，若未指定则使用元素某个可见点） | position < Object > x:<num>,y:<num> | page.click('text=16:00',{position:{x:0,y:33}}) |
| 填写 | [page.fill(selector, value[, options])](https://playwright.dev/docs/api/class-page#page-fill) | 【选择器，值[选项]】 | /------------例句--------------/ |
|  | / | `value`填在`<input>`, `<textarea>` , `[contenteditable]` 元素中 | page.fill('[placeholder="Search"]', 'page');  //在'[placeholder="Search"元素中填入'page' |
| 聚焦 | [page.focus(selector[, options])](https://playwright.dev/docs/api/class-page#page-focus) | 【选择器[，选项]】 | /------------例句--------------/ |
|  | / | / | page.focus('text=16:00'); //聚焦元素'text=16:00' |
| 转到 | [page.goto(url[, options])](https://playwright.dev/docs/api/class-page#page-goto) | 【链接[，选项]】 | /------------例句--------------/ |
|  | / | `url` :填入地址栏<str>要转到的链接 | page.goto('https://m.jd.com/') //通过地址栏转到'https://m.jd.com/' |
|  | / | /-----加入options如下-----/ | / |
|  | /引用标题值 | referer: < [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#String_type) > | page.goto('https://m.jd.com/',{referer:'多快好省，购物上京东！'})//引用标题'多快好省，购物上京东！' |
| 按键 | [page.press(selector, key[, options])](https://playwright.dev/docs/api/class-page#page-press) | 【选择器，键[，选项]】 | /------------例句--------------/ |
|  | / | `key` :填入键<string>的名字【+ 单个字符键区分大小写，如'a'和'A'不同】 | page.press('[placeholder="oppo手机"]', 'Enter')//在搜索栏处，按下"Enter"键 |
|  | /支持快捷键组合 |支持快捷键组合，如"Control+Shift+T"  | page.press('body','Control+A')//在'body'页面，按下'Control+A' |
|  | / | /-----加入options如下-----/ | / |
|  | /延时（键盘按下到抬起的时间） | delay :<number> | page.press('[placeholder="oppo手机"]', 'Enter',{delay:3000})//在搜索栏处，按下"Enter"键不动，3秒后抬起 |
| 截屏 | [page.screenshot([options])](https://playwright.dev/docs/api/class-page#page-screenshot) | 【[选项]】 | /------------例句--------------/ |
|  | / | /-----加入options如下-----/ | / |
|  | /路径 | path:<string>【得指明类型'xxx.png'，否则抛出异常。若未提供路径，则不会保存到磁盘】 | page.screenshot({path:'Test_test/screenshot_1.png'}) //存储到'Test_test'，命名为'screenshot_1.png' |
|  | /裁剪 | clip <Object>x:<num>,y:<num>,【左上角位置】width:<num>,height:<num>【裁剪大小】 | page.screenshot({path:'Test_test/screenshot_clip.png',clip:{x:100,y:100,width:300,height:300}})  //存储到'Test_test'，命名为'screenshot_clip.png'，300*300大小，位置左上角（100，100） |
|  | /滚动截屏 | fullPage :<boolean>【默认为false，选择true即滚动截屏】 | page.screenshot({path:'Test_test/screenshot_full.png',fullPage:true})//存储到'Test_test'，命名为'screenshot_full.png'，滚动截屏 |
|  | /隐藏背景 | omitBackground: <boolean> 【隐藏默认白色背景，并允许捕获具有透明度的屏幕截图。不适用于jpeg图像。默认为false】 | page.screenshot({path:'Test_test/screenshot_omitBackground.png',omitBackground:true})//存储到'Test_test'，命名为'screenshot_omitBackground.png'，隐藏默认白色背景 |
|  | /类型 | type: <"png"/"jpeg">【选截屏图片的类型，默认为"png"】 | page.screenshot({path:'Test_test/screenshot_quality-jpep-2.jpeg',type:"jpeg"})//存储到'Test_test'，命名为'screenshot_quality-jpep-2.jpeg'，类型为"jpeg" |
|  | /图像质量 | quality:<num>【介于0-100之间。不适用于png图像】 |page.screenshot({path:'Test_test/screenshot_quality.jpeg',quality:50})//存储到'Test_test'，命名为'screenshot_quality.png'，质量设置为50|
| 关闭网页 | [page.close([options])](https://playwright.dev/docs/api/class-page#page-close) | 【[选项]】 | /------------例句--------------/ |
|  | / | / | page.close()//关闭页面 |
|  | / | /-----加入options如下-----/ | / |
|  | /运行BeforeUnload | runBeforeUnload: <boolean> 【默认为false，如果runBeforeUnload作为true传递，则可能会调用beforeunload对话框，并应通过page.on（'dialog'）事件手动处理该对话框。】 | page.close({runBeforeUnload:true})//关闭页面，运行BeforeUnload |






### Frame

Frame 对象的生命周期由三个事件控制，在页面对象上调度。

page.on('frameattached') - 当框架附加到页面时触发。 一个框架只能附加到页面一次。  
page.on('framenavigated') - 当框架提交导航到不同的 URL 时触发。   
page.on('framedetached') - 当框架与页面分离时触发。 一个框架只能从页面上分离一次。  

```javascript
const { firefox } = require('playwright');  // Or 'chromium' or 'webkit'.

(async () => {
  const browser = await firefox.launch();
  const page = await browser.newPage();
  await page.goto('https://webkit.org/blog/11958/release-notes-for-safari-technology-preview-130/');
  dumpFrameTree(page.mainFrame(), '');
  await browser.close();

  function dumpFrameTree(frame, indent) {
    console.log(indent + frame.url());
    for (const child of frame.childFrames()) {
      dumpFrameTree(child, indent + '  ');
    }
  }
})();
```



