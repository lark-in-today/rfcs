# 002_开发者

## Lark-in 组件

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


## Lark-in API

Lark-in API 的 base url 为 `https://api.lark-in.xyz`。

### `/{ident}`

| Method | Desc          | Params |
|:-------|---------------|--------|
| GET    | 获取用户信息  | -      |
| PUT    | 更新用户信息  | -      |
| POST   | 发布/修改文章 | -      |
| PATCH  | -             | -      |
| OPTION | -             | -      |

### `/{ident}/{number}`

| Method | Desc     | Params |
|--------|----------|--------|
| GET    | 获取文章 |        |
| POST   | 修改文章 |        |
