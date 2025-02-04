
## 1. 介绍

cnchar-voice, cnchar-draw, cnchar-explain 由于使用了大量的在线词典和资源

所以没有跟随npm包一起下载到本地，而是使用cdn方式动态加载

cnchar 在 3.1.0 版本新增了 [cnchar-data](https://github.com/cn-char/cnchar-data) 用于帮助用于单独下载数据仓库，以支持离线使用和自定义部署。 

具体使用请参考 [cnchar-data](https://github.com/cn-char/cnchar-data/blob/master/README.md)

另外 voice, draw, explain 三个仓库也支持独立 setResourceBase

具体请参考 [cnchar-types](https://github.com/theajack/cnchar/tree/master/src/cnchar-types)

## 2. cnchar-data

该库为[cnchar](https://www.github.com/theajack/cnchar)的资源cdn库

也可以用于支持离线化使用cnchar部分在线资源，及生产环境部署到自己的服务器中

### 1. 安装

```
npm i cnchar-data -D
```

### 2. 运行

运行一个本地的服务，端口可以自定义

```
cnchar-serve [port]
```

### 3. 开发环境使用

```js
import cnchar from 'cnchar';
cnchar.setResourceBase('http://localhost:{port}/')
```

### 4. 生产环境使用

如需将资源部署到您的生产环境服务器

请执行

```js
cnchar-serve-prod
```

会在项目根目录生成cnchar-data目录, 将改文件夹放置在您的http服务器中

假设可访问路径为 `https://www.xxx.com/cnchar-data/`

则对cnchar设置如下

```js
import cnchar from 'cnchar';
cnchar.setResourceBase('https://www.xxx.com/cnchar-data/')
```

### 5. api

```ts
export const name: 'cnchar-data';

export const words: {
    dict: string;
}

export function serve(): void;

export function build(): void;

export default {
    name,
    words,
    serve,
    build,
}
```

```js
import {serve} from 'cnchar-data';
serve();
```