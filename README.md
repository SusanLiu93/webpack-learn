# webpack-dev-server启动报错Error: Cannot find module ‘webpack-cli/bin/config-yargs‘
- 原因
  - 由于webpack-cli版本4，删除了webpack-cli/bin/config-yargs文件，看图bin目录下没有config-yargs.js
- 解决办法
  - npm uninstall webpack-cli
  - npm i webpack-cli webpack-cli@3.3 -S
- 文件指纹
  - js :chunkhash (入口文件)
  - css添加文件指纹(contenthash)：因为默认情况下打包好的css是通过style-loader添加到head中，想要给css添加文件指纹，先通过mini-css-extract-plugin 将css提取出单独的文件
- 文件压缩
   - js  内置ugliftjs-webpack-plugin
   - css optimize-css-assets-webpack-plugin + csscano
   - html html-webpack-plugin
- css 增强
   - 删除 打包文件
   - 添加前缀 postcss-loader autoprefixer
- devtool
   - eval :打包后的代码包裹在eval 中，并且用sourceURL 连接到源码文件中 不好debugger
   - cheap-source-map : 源代码 没有包裹在eval中，可以调试
- import 懒加载 文件，用到的时候才去加载（babel转换）
   - npm install @babel/plugin-syntax-dynamic-import --save-dev
   - babelrc 文件 配置 plugins:["@babel/plugin-syntax-dynamic-import"]
- 打包ssr 
   - vue + webpack + ssr
   - vue-server-renderer  方法 createRenderer() 加载模板
  
