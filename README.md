# builder-test
两大前端构建工具的斗争

## 1. Vite

###  1. Vite介绍

Vite 是一种新型的前端构建工具，它利用了现代浏览器的原生 ES 模块支持和模块热替换（HMR）功能，从而实现了快速的开发体验。Vite 的核心思想是利用浏览器对 ES 模块的支持，直接从源代码中构建应用，而不是像传统的构建工具那样先进行打包。这使得 Vite 在开发过程中能够实现极快的冷启动和热更新，从而大大提高了开发效率。

### 2. Vite 的优势

Vite 的优势在于其快速的开发体验和高效的构建性能。它利用了现代浏览器的原生 ES 模块支持和模块热替换（HMR）功能，从而实现了极快的冷启动和热更新，大大提高了开发效率。同时，Vite 还支持 TypeScript、CSS 预处理器、代码分割等功能，使得开发过程更加便捷。

### 3. Vite的使用

#### 1. create-vite
```bash
npm init vite@latest --template vue-ts

```

#### 2. 安装依赖
```bash
npm install
```

#### 3. 启动项目
```bash
npm run dev
```
可以看到, 启动速度非常快, 只用了几百毫秒。

##### 测试热更新
修改src/App.vue文件，可以看到，热更新速度也非常快，只需要几十毫秒。

#### 4. 测试构建
```bash
npm run build
```
构建速度也很快，只用了一秒。

##### 测试打包体积
现在，在src/components目录下新建十个Vue组件，但不要在App.vue中引入它们。然后，再次运行npm run build命令
```bash
npm run build
```
可以看到，打包体积并没有增加，这是因为Vite使用了Tree Shaking技术，只有被引入的组件才会被打包。

### 4. 生态
Vite 的生态也非常丰富，支持各种插件和扩展，可以满足各种开发需求。还衍生了许多框架，例如：

- VitePress：基于 Vite 的静态网站生成器，用于构建文档网站。
- Remix：基于 Vite 的 生产级React SSR框架，用于构建高性能的 React 应用。
- Vitest: 基于 Vite 的测试框架，用于编写和运行测试用例。
- Nuxt:  基于 Vite 的 生产级Vue 框架，用于构建高性能的 Vue 应用。
- Sveltekit：Kit基于 Vite 的 生产级Svelte 框架，用于构建高性能的 Svelte 应用。

### 5. 总结
Vite 是一种新型的前端构建工具，它利用了现代浏览器的原生 ES 模块支持和模块热替换（HMR）功能，从而实现了快速的开发体验。Vite 的优势在于其快速的开发体验和高效的构建性能，它支持 TypeScript、CSS 预处理器、代码分割等功能，使得开发过程更加便捷。Vite 的使用也非常简单，只需要几步就可以完成项目的创建、依赖安装和启动。


## 2. Rspack

### 1.  Rspack介绍

Rspack 是一个基于 Rust 编写的高性能 JavaScript 打包工具， 它提供对 webpack 生态良好的兼容性，能够无缝替换 webpack， 并提供闪电般的构建速度。

### 2. Rspack 的优势

Rspack 的优势在于其高性能和易用性。它利用 Rust 编写，能够提供比 JavaScript 编写的构建工具更快的构建速度。同时，Rspack 也提供了对 webpack 生态的良好兼容性，能够无缝替换 webpack，并提供了丰富的插件和扩展功能，使得开发过程更加便捷。

### 3. Rspack 的使用

#### 1. 使用Rsbuild创建项目
```bash
npm create rsbuild@latest
```

#### 2. 启动项目
```bash
npm i
npm run dev
```
可以看到，虽然Rspack不像Vite那样使用原生ESM，先构建再启动开发服务器，但得益于其使用Rust，开发服务器的启动速度依然很快，同样只需要几百毫秒。

##### 测试热更新
修改src/App.vue文件，可以看到，热更新速度也非常快，只需要几十毫秒。

#### 3. 测试构建
```bash
npm run build
```
刚刚说过，Rspack使用Rust，构建速度肯定是比Vite快的, 只用了不到0.5秒。

#####  测试打包体积
在src/components目录下新建十个Vue组件，但不要在App.vue中引入它们。然后，再次运行npm run build命令

```bash

npm run build
```
打包体积同样没有增加，Rspack也使用了Tree Shaking技术

### 4. 生态
Rspack 继承了Webpack的生态，支持各种插件和扩展，可以满足各种开发需求，还衍生了许多框架，例如：

- Rspress: Rspress 是一个基于 Rsbuild、React 和 MDX 的静态站点生成器，内置了一套默认的文档主题，你可以通过 Rspress 来快速搭建一个文档站点，同时也可以自定义主题，来满足个性化静态站需求，比如博客站、产品主页等。

- Rslib：Rslib 是一个基于 Rsbuild 的 npm 库开发工具，它复用了 Rsbuild 精心设计的构建配置和插件系统，使开发者能够以简单直观的方式创建 JavaScript 库。

- Modern.js：Modern.js 是一个基于 Rspack 实现的渐进式 React 框架，支持嵌套路由、服务器端渲染（SSR）和模块联邦，并提供开箱即用的 CSS 解决方案

### 5. 总结
Rspack 是一个基于 Rust 编写的高性能 JavaScript 打包工具，它提供对 webpack 生态良好的兼容性，能够无缝替换 webpack，并提供了丰富的插件和扩展功能，使得开发过程更加便捷。Rspack 的使用也非常简单，只需要几步就可以完成项目的创建、依赖安装和启动。