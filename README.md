### rn 练习

npm install

react-native run-android  /  react-native run-ios

**快速实现圆角+阴影效果**

```css
shadowColor: '#ccc',
shadowOffset: {width: 2, height: 2,},
shadowOpacity: 0.5,
shadowRadius: 10,
backgroundColor: Color.white,
borderWidth: 0,
borderRadius: 5,
borderColor: 'rgba(0,0,0,0.1)',
padding: Size.public_margin,
elevation: 3,
overflow: 'hidden',
```



### 调试

模拟器 `cmd + M`  & 真机摇晃手机调起调试菜单。常用功能：

**Reload** 重新加载

**Debug JS Remotely**

调试应用，会打开本地 `http://localhost:8081/debugger-ui` 调试界面，最好使用 `Chrome`

**Enable Live Reload** 实时预览，`cmd + s` 有文件变化便重新编译。

### Android 打包

首先在项目根目录使用终端执行 `react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/` 命令，会生成 `index.android.bundle`（这个文件很重要）和相关的资源文件到 `android/app` 的相关目录下。

其次就是正常的 `Android` 打包流程了。这里贴出教程链接： [Android 打包](https://www.jianshu.com/p/1380d4c8b596)

## 总结

### 学习来源

### 数据来源

[聚合数据](https://www.juhe.cn/) 每天每个接口有 500 次的请求限制。

### 采坑心得

1.  `unable to connect with remote debugger Timeout while connecting to remote debugger`

- 检查是否连接设备 & 有且仅有一台设备
- 手机调试模式是否打开
- 调试服务是否打开
- 将存在的 `apk` 卸载重新运行
- 检查端口是否被占用

2. 使用 `createStackNavigator` 创建 `bottomBar` `titleBar` 白色

   在 `createStackNavigator`配置出添加 `headerMode: 'none',` 隐藏 `titleBar`，然后使用 `native-base` 中的 `Head` 创建 `TitleBar`。

3. `FlatList` 列表使用 `navigation` 进行跳转，`navigation not defined`

   `FlatList`属于自定义组件，如果需要使用 `navigation` 跳转，需要将 `navigation` 对象传到每个 `item`。
