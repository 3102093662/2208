## git

git clone 地址 克隆远程仓库

git add . 将代码放到暂存区

git status 对比代码

git commit -m '' 备注

git push origin 分支名称  提交到远程仓库  (orign 名称可以省略)

git push -f  origin 分支名 强制提交

### 解决冲突  合并分支

git merge **分支名**     意思:将**这个分支**合并到当前分支  

场景：当两个人同时修改一个分支里同一块 代码 会冲突，提交的时候会提示合并

第一个保留当前的，第二个保留另一个人的，第三个两个都保留，第四进行对比

解决完冲突会再走一遍git add .   ……

### 创建分支    

git branch 分支名  创建分支     不加分支名是查找所有分支  绿色的为当前分支

git checkout 分支  切换到分支

git checkout -b 分支    创建并切换分支  

添加分支后提交：git push -u origin 分支名 

### 回退前进版本

查看版本id ：git  log  、git reflog    前进不能用log   reflog比较好用id短  

查到后使用git reset --hard 版本id

因为回退或者前进是本地进行的远程仓库并没有同步 所有，前进或者后退 后更改代码(可以省略) 然后提交

git add .=> git commit -m '' =>git push （如果提示要进行git pull 的话，就看情况使用  git push -f  origin 分支  强制退回

因为git pull 是获取最新的远程库版本 ，而我们是要提交回退的版本 这是有违初衷的  。没有的话可省略）

其他指令
git reset --hard HEAD  回到最新的版本

git reset --har HEAD-1  回到相比于最新的其次1的版本

git push -f origin kuige1 强制删除远程分支(删除24小时内的)

## es6

### let const 新增的声明变量和常量 

相同 ： 都存在块级作用域 ，不能重复声明，不改变作用域，不存在变量提升

| 不同  | 必须设置初始值 | 值能否改变                                      |      |
| ----- | -------------- | ----------------------------------------------- | ---- |
| let   | 否             | 能                                              |      |
| const | 是             | 不能(基本类型不能,引用类型只要地址不改变就可以) |      |
|       |                |                                                 |      |

### 解构赋值

对象和数组两种格式   左边有变量名右边没有值 :undefined

数组:通过索引匹配        对象:对过属性名匹配

### 模板字符串

``里面可以放变量 必须要放在${}里

### 箭头函数

本身没有this,this为父的this,不能用作构造函数因为this问题，没有argument 