# downcheck
place file for my agent download test

放置文件用于我的代理下载测试

参考以下
https://blog.csdn.net/AshleyXM/article/details/104766893
因为项目需要往github上上传一个大文件，发现无论是通过网站直接拖拽文件夹，还是通过Git Bash都无法上传，搜索了相关问题发现github只能上传25MB以下的文件，如果要上传大文件需要用到Git LFS（第一次接触这个，是用来上传大文件的一个工具），但是通过我自己的经验，发现即便是使用Git LFS也只能上传100MB以下的文件：文件达到50MB会警告，达到100MB报错无法上传成功！（不知道怎么上传100MB以上的文件，翻了各种资料也不知道咋解决，最后我只能把自己的文件压缩了。。。）

如何通过Git LFS上传“大”文件：
这里是Git LFS的官网：Git LFS官网
以下我来解读一下（不能确保一定正确，但我使用起来没问题）：

git lfs install （安装git lfs，一个账号只用安装一次）
git lfs track “*.gif” （eg:追踪记录.gif类型的文件；根据自己需要想要上传什么类型的文件，就追踪什么类型的文件）
git lfs track “demo/*.mp4”（可以添加多个追踪配置，冒号里表示demo文件夹下的mp4文件）
git add .gitattributes（运行完后当前文件夹下会生成一个.gitattributes文件，存储第二步的相关配置）
git add file_name1.gif
git add file_name2.mp4
git commit -m “Add design file”
git push origin master（这一步可能会报错：error: failed to push some refs to，报错解决方案详见下方）
第7步报错解决方案：
参考网址：https://blog.csdn.net/u013120247/article/details/53263169
总结方法就是在第七步报错后，输入：git pull --rebase origin master （原理我也不是太懂，反正可以解决问题）
之后再次输入： git push origin master
运行完成之后可以发现Github仓库上传成功！
