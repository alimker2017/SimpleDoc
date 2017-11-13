# HTML
## <!DOCTYPE HTML>
> 表示使用HTML5

## head
- meta标签
``` http
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta charset="utf-8" />
```
> 用于定义网页元数据，可以影响网页的加载，编码方式，刷新，搜索引擎关键字抓取，手机，平板等浏览器显示效果等
- style标签
``` http
<style type="text/css">
	h1{
		font-size:12px;
		color:#930;
		text-align:center;
	}
</style>
```
> 用于编写或者引入CSS代码
- script标签
``` http

```
> 用于编写JS代码
- link标签
``` http

```
> 用于引入其他文件(JS，CSS)

### 其他标签示例
``` http
<h1>这个是标题</h1>
<p>这个是段落</p>
<img src="http://img.mukewang.com/52b4113500018cf102000200.jpg" />
<div>块标签，用于布局</div>
<em>斜体</em>
<strong>粗体</strong>
<q>会在文本中开始结束文字追加双引号</q>
<blockquote>对长文本进行引用，但是不加双引号，并且会换行，缩进</blockquote>
```
``` http
<span>给内容添加标签，默认没有任何显示上的效果，一般使用CSS给span添加效果</span>
<p class="tip"><span>提示：</span>... ... ...</p>
p.tip span {
	font-weight:bold;
	color:#ff9955;
}
<!-- 这个是注释标签，要有结束 -->
```