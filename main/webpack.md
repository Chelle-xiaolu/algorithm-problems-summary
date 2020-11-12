webpack
1. entry 构建依赖图的起点 每个HTML文档只使用一个入口起点
entry: './src/index' entry: {entryChunkName: string}
如果想将项目的第三方库文件分离，使用optimization.splitChunks将wendors和app(应用文件分离)
2. output 在哪里输出bundle 并且如何命名这些文件
output:{
  path: path.resolve(__dirname, 'dist'),
  filename: [name].js
}
资源可以使用CDN和hash
output: {
  path: 'home/proj/cdn/assets/[fullhash]',
  publicPath: 'https://cdn.example.com/aeests/[fullhash]'
}
如果在编译时不知道输出的publicPath，可以在运行时通过入口起点文件进行设置__webpack_public_path=myPublicPath
3. loader webpack只能识别javascript和JSON文件，loader可以让webpack去处理其他类型的文件
module:{
  rules:[{test:/\.txt$/, use:'raw-loader'}]
}
4. plugin