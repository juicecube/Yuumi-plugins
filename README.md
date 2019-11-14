# Yuumi
yuumi(内部项目)的cli工具扩展

# yuumi插件列表
- @yuumi/cli-plugin-unit-jest

# 使用插件
yummi add [plugin-name]


# 如何开发插件
#### 插件文件结构
├── generator //该插件需要插入到项目中的文件或者文件夹
│   ├── index.js 
│   └── template
│       ├── __test__
│       └── jest.config.js
├── index.js
├── jest-preset.js
├── package-lock.json
├── package.json
└── readme.md

#### 插件核心文件
- index.js
需导出扩展脚手架program命令的函数

- generator/index.js
需导出一个函数，函数传入generatorApi，generatorApi提供了一些常用方法给插件使用。
```js
//extendPackage 该函数会合并传入的对象到项目中的package.json文件，
generatorApi.extendPackage({
  scripts: {
    "test:unit": "yummi test:unit"
  }
})

//addFolderOrFile 该函数会将template目录下的所有文件插入到项目中
generatorApi.addFolderOrFile('./template') 
```


