# 基于Electron和element UI的代码查重软件

## 零、分支简介
本项目是基于 [Electron-SIMGUI](https://github.com/ZxfBugProgrammer/Electron-SIMGUI) 的一款支持 HrbustOJ 代码查重的软件，简单来说就是将 OJ 比赛导出的单个 csv 文件自动转换成多个代码。

使用方法，在“选择源文件”窗口下选择从 OJ 上下载的 csv 文件（export code），该操作会在 csv 文件目录下创建一个 `codes` 文件夹，第二步选择该文件夹，第三步选择语言以及阈值即可查重。

可运行在 Windows,MacOS,Linux 上。

## 一、项目简介

本项目是基于Electron和element UI开发的一款代码查重软件，其内核使用了开源软件[SIM](https://dickgrune.com/Programs/similarity_tester/)（SIM是大佬[Dick Grune](https://dickgrune.com/)开发的一款代码查重软件）

本项目为SIM添加了GUI界面，简化了操作，**练手之作，技术含量不高，如有错漏，请大佬们指出**。

## 二、代码使用方式

```shell
# nodeJS版本 v12.19.0
# electron版本 v10.1.4

# Clone this repository
git clone https://github.com/Bubbleioa/Electron-SIMGUI-ForHrbustOJ.git
# Go into the repository
cd Electron-SIMGUI
# Install dependencies
npm install
# Run the app
npm start
```

## 三、打包应用方式

修改js/index.js（js文件夹下的index.js文件）中的第342-345行，取消342行的注释，注释345行。修改后的部分代码如下：

```javascript
//开发调试时调用SIM的命令
//let commandStr = '"' + path.join(__dirname, '/src/SIM/sim_' + chooseCodeData.value + '.exe') + '" ' + simArgs
                
//打包应用时调用SIM的命令
let commandStr = '"' + path.join(__dirname, '../SIM/sim_' + chooseCodeData.value + '.exe') + '" ' + simArgs
```

使用如下命令打包应用(仅限打包win32平台应用)

```shell
# 全局安装electron-packager
npm install electron-packager -g
# 运行打包命令 应用生成在./out 中
npm run build-electron
```
