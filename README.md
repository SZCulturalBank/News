# szcb

[源页面](https://a.xiumi.us/board/v5/2QREi/99016015?from=singlemessage&isappinstalled=0)

db.json的内容修改完去http://www.bejson.com/看下格式是否正确，不正确会错误。


## 页面地址
https://szculturalbank.github.io/News/

## 图片存放路径
https://github.com/SZCulturalBank/News/tree/master/docs/static/img

点击右上角有upload files上传图片，注意图片后缀

## 内容编辑
修改这个链接的内容：
https://github.com/SZCulturalBank/News/blob/master/docs/static/db.json

### db.json内容解释
- `date`不填则默认为当天时间
- `"picture": "xxx"`对应的文件为SZCB/static/img/下的图片，支持`.png/.jpg/.jpeg/.gif`之类的图片

##

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
