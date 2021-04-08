要下载的包 webpack webpack-cli css-loader style-loader html-webpack-plugin

index.js : webpack入口起点文件

运行指令：

开发环境：webpack  ./src/index.js -o ./build/built.js --mode =development

​          webpack 会以 ./src/index.js 为入口文件开始打包，打包后输出到 ./build/built.js

​          整体打包环境是开发环境

生产环境：webpack  ./src/index.js -o ./build/built.js --mode =production

​          webpack 会以 ./src/index.js 为入口文件开始打包，打包后输出到 ./build/built.js

​          整体打包环境是生产环境

结论

- webpack能处理js/json资源，不能处理css/img等其它资源
- 生产环境和开发环境将es6模块化编译成浏览器能识别的模块化
- 生产环境比开发环境多一个压缩js代码

webpack.config.js用的是commnJS模块化规范

由5大配置  entry  output  loader（代码写的是module）  plugins  mode

不同的文件配置不同的loader例如css文件和less文件就要配置不同的loader

loader : 1.下载 2.使用

plugins ：1.下载 2.引用 3.使用

```
const { resolve } = require("path");
const HtmlWebpackPlugin = require('html-webpack-plugin');
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const OptimizeCssAssetsWebpackPlugin =require('optimize-css-assets-webpack-plugin')
module.exports={
    entry:'./src/index.js',
    output:{
        filename:'js/built.js',
        path:resolve(__dirname,'build'),
    },
    module:{
        rules:[
            //处理css资源
            {
               test:/.\css$/,
               use: [                 
                   //'style-loader',   //创建style标签，将样式放入
                   //这个loader取代style-loader，作用：提取js中的css成单独文件
                   MiniCssExtractPlugin.loader,
                   'css-loader',//将css文件整合到js文件中
                   //css兼容性处理:postcss -->postcss-loader postcss-preset-env
                   //帮postcss找到package.json中browserslist里面的配置，通过配置加载指定的css兼容性样式
                   /*
                    "browserslist":{
                        "development":[
                        "last 1 chrome version",
                        "last 1 firefox version",
                        "last 1 safari version"   
                        ],
                        "production":[
                        ">0.2%",
                        "not dead",
                        "not op_mini all"
                      ] }
                   */
                  //使用loader的默认配置
                  //'postcss-loader'
                  //修改loader的配置
                  {
                      loader:'postcss-loader',
                      options:{
                          ident:'postcss',
                          plugins:()=>[
                              //postcss的插件
                              require('postcss-preset-env')()
                          ]
                      }
                  }
               ]
            },
            //处理图片资源
            {
                test:/\.(jpg|png|gif)$/,
                //使用一个loader就直接写，不用写use
                //下载 url-loader file-loader
                loader:'url-loader',
                options:{
                    //图片大小小于8kb，就会被base64处理
                    //优点：减少请求数量，减轻服务器压力
                    //缺点:图片体积会更大，文件请求速度更慢
                    limit:8*1024,
                    //问题：因为url-loader默认使用es6模块化解析，而html-loader引入图片是commonjs规范，所以解析会出现问题
                    //解决：关闭url-loader的es6模块化，使用commonjs解析
                    esModule:false,
                    outputPath:'imgs'
                }
            },
            //处理html中img资源
            {
                test:/\.html$/,
                //处理html文件的img图片，从而能被url-loader进行处理
                loader:'html-loader'

            },
            //打包其它资源
            {
                exclude:/\.(css|js|html|less)$/,
                loader:'file-loader',
                options:{
                    name:'[hash:10].[ext]',
                    outputPath:'media'
                }

            }
        ]

        
    },
    plugins:[
        //功能:默认会创建一个空的html，自动引入打包输出的所有资源(css/js)
        //需求:需要有结构的html文件
        new HtmlWebpackPlugin({
            //赋值 './src/index.html'文件，并自动引入打包输出的所有资源(css/js)
            template:'./src/index.html'
        }),
        new MiniCssExtractPlugin({
            filename:'css/built.css'
        }),
        //压缩css
        new OptimizeCssAssetsWebpackPlugin
    ],
    mode:'development',
    //开发服务器devserver：用来自动化（自动编译，自动打开浏览器，自动刷新浏览器————）
    //特点：只会在内存中编译打包，不会有任何输出
    //启动devServer指令：npx webpack-dev-server
    devServer:{
        //项目构建后的路径
        contentBase:resolve(__dirname,'build'),
        //启动gzip压缩
        compress:true,
        //端口号
        port:3000,
        //自动打开浏览器
        open:true
    }
}
//webpack5.x : npx webpack serve
```

