# 000_摘要

lark-in 是一个开放式的内容创作平台，意在帮助内容创作者们进行不受限制地记录与表达。

# 产品

### Lark-in 编辑器

用于编辑发布内容，[网页版]()，[移动版]()，[桌面版]()。

# 特色

## 博客系统

用户可以通过 [lark-in]() 编辑器进行内容编辑，lark-in 将会为创作者生成独立的[个人博客]()。

举例如用户 x，用户 x 使用 `lark-in` 创作了一篇内容，那么用户 x 的博客地址为: `x.lark-in.blog`。

## 版权系统

通过 `lark-in` 发布并传播的内容，将会绑定上用户的身份标识，当创作者遭遇侵权问题时，可通过对应内容的哈希签名进行[维权]()。

## 广告系统

用户可以选择为自己的内容插入适当的广告，广告的收益将按比例返还给 App 开发者与内容创作者, 具体的比例由内容创作者决定，详情请见[广告系统]()。

### Lark-in 组件

可以通过 `lark-in` 组件库将特定文章嵌入对应的 App 当中，以 `React` 为例：

```
yarn add lark-in
```

登录组件：

```jsx
import LarkIn from 'lark-in';

const Login = () => (
	<Login 
		name="x"
	/>
);
```

展示文章：

```jsx
import LarkIn from 'lark-in';

const article = () => (
	<LarkIn.Article
		no="0"
		author="x"
		developer="0x7424f0f51232e4c58c2ab1db849d128af303bda08fd4db8a084c884ad87a033d"
	/>
);
```

文章列表：
```jsx
import LarkIn from 'lark-in';

const articleList = () => (
	<LarkIn.ArticleList
		author="x"
		range={[0, 10]}
		developer="0x7424f0f51232e4c58c2ab1db849d128af303bda08fd4db8a084c884ad87a033d"
	/>
);
```

Lark-in 同时支持 React-Native, Flutter, Electron 等，[详细文档]()。


#### Lark-in API

> Lark-in API 的 base url 为 `https://api.lark-in.xyz`。

`/{ident}`:

| Method | Desc          | Params |
|:-------|---------------|--------|
| GET    | 获取用户信息  | -      |
| PUT    | 更新用户信息  | -      |
| POST   | 发布/修改文章 | -      |
| PATCH  | -             | -      |
| OPTION | -             | -      |

`/{ident}/{number}`:

| Method | Desc     | Params |
|--------|----------|--------|
| GET    | 获取文章 |        |
| POST   | 修改文章 |        |


# 路线图

Lark-in 所涵盖的全部功能有 3 个部分，身份验证、内容制作、以及数据存储。

#### Stage 1

在 __服务端__ 完成登录验证、内容发布存储数据 CURD、信息验证系统。在 __网页端__ 完成登录流程、内容(文章)编辑器、用户信息更新界面。

将产品推送给朋友请求意见，并进行相应优化，最后将网页版内容移植到移动版，进行测试上线，开始进入维护期。

#### Stage 2

优化/简化并稳定服务端结构，制作 Desktop 版简易界面。

用 RUST 重构服务端，将数据库从 `rethinkdb` 迁徙到 `sled`，制作分布式存储系统，包括 `StQL` 的制作，制定并实现出出稳定版，

#### Stage 3

将项目(身份验证、内容制作，数据存储)稳定化，对广告系统进行探索，脱离编辑器的限制，开始着手准备社交媒体。
