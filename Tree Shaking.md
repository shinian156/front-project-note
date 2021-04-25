### Tree Shaking

    用于移除项目中未引用的代码。


``` js
// webpack.config.js

// 在开发环境中添加

optimization: {
    usedExports: true
}

```


    将文件标记为无副作用(side-effect-free)
    在一个纯粹的 ESM 模块世界中，识别出哪些文件有副作用很简单。然而，我们的项目无法达到这种纯度，所以，此时有必要向 webpack 的 compiler 提供提示哪些代码是“纯粹部分”。

    这种方式是通过 package.json 的 "sideEffects" 属性来实现的。
``` json
    {
      "name": "your-project",
      "sideEffects": false
    }
```

    如同上面提到的，如果所有代码都不包含副作用，我们就可以简单地将该属性标记为 false，来告知 webpack，它可以安全地删除未用到的 export 导出。