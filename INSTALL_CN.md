## 说明
由于[原始工程](https://github.com/venmo/synx)许久没有更新，也不接受PR，安装后发现功能似乎正常，但IB与代码的Assistant(即各种绑定失效)。 
利用[查看活跃fork工具](https://github.com/techgaun/active-forks)、近期issue以及PR找到了[目前fork的库](https://github.com/dnedrow/synx)。
本fork仅为记录过程。

## 使用
不太熟悉ruby生态，没找到gem install指定远程git的方式。不过找到了本地编译的方法：

1. `git clone git@github.com:dnedrow/synx.git`
2. `gem build synx.gemspec`
生成`synx-1.0.0.gem`
3. `gem install --local synx-1.0.0.gem`
4. 安装成功后按照原库的说明整理项目: `synx path/to/my/project.xcodeproj`
5. `pod install`，可能非必要

## 补充
1. 安装过程可能会报找不到依赖，如: 
```
➜  synx git:(master) gem install --local synx-1.0.0.gem
ERROR:  Could not find a valid gem 'clamp' (~> 1.3) (required by 'synx-1.0.0.gem' (>= 0)) in any repository
```
根据提示安装所需依赖：`gem install clamp`

2. 如果项目中的OC桥接文件也被移动，整理完成后会发现报错找不到，这是原项目的遗留问题，在`target - Build Settings - Objective-C Bridging Header`里手动修改移动后的位置即可。
