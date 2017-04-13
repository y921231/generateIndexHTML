## 编译
go build -ldflags "-w -s"
然后通过upx壳压缩体积缩小到了原来的1/4

虽说我的网盘（exm，也许页面确实丑了点，不过页面生成的样式你自己可以改）美工已经被乱刀砍死，但是还是有小伙伴问我是怎么搭建的

## 关于搭建
这个真没什么好说的，vps我只安装了nginx，然后配置域名指向到我的同步目录，然后用其他工具同步上去就行了（关于问自己手动同步麻烦的，其实并不麻烦，有很多好用的软件，本人用的Resilio Sync）

## 关于页面的生成
### 第一阶段
那时候只有两三个文件，html页面是我手写的手动增加的

### 第二阶段
此时已经有了一个子目录，文件开始增多，我开始考虑写个简单的先用着，Python的写了，不过速度感觉有点不如意（原谅我的吹毛求疵）,并且有个麻烦事是每次重装系统后需要安装Python，然后我选用了Golang，时间仓促写了一个单页面生成，不进行目录深度遍历的，也就是说我每次新开一个目录需要把这个程序拷贝到当目录下双击生成html

### 第三阶段
文件夹和文件日益增多，上面的方式我已经感觉到特别繁琐了，需要找个机会把代码重构一下，使他更加优化
然后我开始着手写第二版，这个版本我没保留，具体功能就是对上一个版本做了一点改进，使它支持了深度遍历
但是自从**T00ls灵车漂移事件以来，官方管理员给*GetWriter*老哥（如果谁认识希望告知，希望能致个歉）的一纸封书将此事推上风口浪尖，作为始作俑者，我网站首当其冲，遭受了大量老哥多来自夜间的洗礼（说实话，希望高抬贵手，流量快没了）**，这件事情持续发酵了两三天，我一直在思考，如何为老哥们带来更良好的观感体验，于是我觉得应该要让这个页面生成器对前端展示的修改更加方便，无须从代码入手，开始了第三版的编写

#### 暂时实现的功能
- 支持模板
- 加入了配置文件（其实也是模板）
- 加入了noView.txt规则（具体表现为这个txt中的文件名将不参与生成html页面）
- 程序计时

## 更新记录
- 对一部分冗余的进行了优化，提升了一丁点效率
- 可以放到环境变量path了，不需要放到本目录里了，只需要在本目录调用就可以（当然），按照之前的方法也是可以的

可能以后会抽时间再进行优化，这个时间不定，看哪天自己的需求更高了

## 至于前端
你们别想了，前端之魂在我体内没存在过，哪天兴致来了可能会看看相关知识，这个丑页面就丑着凑合看吧，如果有能力可以进行二次修改