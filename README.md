# -Xocde-SVN-
新手常常用不好svn，老是冲突或是删不掉多余文件一更新在文件夹里又会有，对项目里面的错乱文件也不敢轻易更改目录。

下面我就一步步分享一下自己是怎么随意使用svn的，最后分享一个绝招。

##第一篇：svn提交

Tools文件夹下文件非常乱，项目结构与文件结构如下图。<br>
![screen1.jpeg](http://upload-images.jianshu.io/upload_images/301102-312d361666f0733f.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)               ![screen2.jpeg](http://upload-images.jianshu.io/upload_images/301102-63e72b54ac848356.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>
下面的演示是将Tools文件夹下的LXHelpClass.h与LXHelpClass.m文件移动到class/Tool/Help下，我将步骤分为两大步骤：svn提交前准备与svn提交。
<br>


###第一步： svn提交前准备

1.在项目上双击LXHelpClass.h，在弹出菜单中选中Show in Finder，会来到具体的文件目录下.
<br>
![screen3.jpeg](http://upload-images.jianshu.io/upload_images/301102-d04de5f75c72eeec.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

2.将LXHelpClass.h与LXHelpClass.m文件托送到class/Tool/Help下的过程（必须在文件里操作不能在项目里拖动，不然将会出现两份一样的文件）。
<br>
![screen4.jpeg](http://upload-images.jianshu.io/upload_images/301102-e16e3afb2837c830.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)           ![screen5.jpeg](http://upload-images.jianshu.io/upload_images/301102-37a1dee71a4c23d7.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

3.现在看项目的结构如图。
<br>
![screen6.jpeg](http://upload-images.jianshu.io/upload_images/301102-1613206df2258c72.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

4.将class/Tool/Help文件夹下的LXHelpClass.h与LXHelpClass.m文件add到项目结构class/Tool/Help中。（仅这一步在文件夹里拖文件到项目中也是可以的）
<br>

![screen7.jpeg](http://upload-images.jianshu.io/upload_images/301102-af3262d1662ea3f1.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)        ![screen8.jpeg](http://upload-images.jianshu.io/upload_images/301102-113f8ca73fb75e5c.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

5.在项目中选中Tools下报红的LXHelpClass.h与LXHelpClass.m文件，然后按键盘上的delete键可直接删除。注意看LXHelpClass.h与LXHelpClass.m后面有一个问号。
<br>
![screen9.jpeg](http://upload-images.jianshu.io/upload_images/301102-f96833e4ccbe9428.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

####目前svn操作前的处理已经完成，然后就是提交了。

我这里直接使用的Xcode集成好的svn，Xcode版本是7.3.1

###第二步：svn提交

1.commit提交，看图。
<br>
![screen10.jpeg](http://upload-images.jianshu.io/upload_images/301102-a6cc744d7e3de5cd.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

2.待提交文件界面，默认没有选择提交LXHelpClass.h文件，须双击提交目录，然后弹出菜单选择Check All. (注意：1.在提交目录中有两组LXHelpClass.h与LXHelpClass.m，在其后分别有“？与！”标记。 2.下图弹出的提交界面左上角tab有三个选项，选择的是中间的tab)
<br>
![screen11.jpeg](http://upload-images.jianshu.io/upload_images/301102-72ec2df57fcf19a2.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

3.在下方输入提交备注信息，然后点击右下角 Commit 23 Files 按钮。然后提示"*** is not under version control (1)"，这就对了，别怕。（提交文件后面跟随有“？或！”的时候是会提交失败的）
<br>
![screen12.jpeg](http://upload-images.jianshu.io/upload_images/301102-84a0e037de2190bd.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

4.点击右下方的cancle取消按钮，然后再跟随第一步的commit提交，接着提交界面就改变成下面这样了，发现啥改变了吗？之前的LXHelpClass.h后面的“？与！”相应改变成了“A与D”。
<br>
![screen13.jpeg](http://upload-images.jianshu.io/upload_images/301102-66748dc20ff3c48c.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

5.点击右下角 Commit 6 Files 按钮，哇哇哇，Successful!!!然后看一下项目结构中LXHelpClass.h与LXHelpClass.m后面的“？”也消失了，这就对了。
<br>

6.最后验证是否删掉了旧目录，生成了新目录。再show in finder进入文件夹检查一下Tools文件夹里是不是没有LXHelpClass.h与LXHelpClass.m，class/Tool/Help文件夹里是有LXHelpClass.h与LXHelpClass.m的。然后再点击工具栏里的下拉菜单update按钮，查看是否还正确。最后一步验证特别重要，重新checkout一个路径下载项目，查看文件夹结构是否对应正确。若按照上面的步骤完成的提交，那么一定是正确的。

* 现在已经顺利完成了挪动项目里的文件结构，有了清晰的文件结构便于查找，整理，维护。
* 接下来是不是该大胆的更改你现有项目中错乱的文件位置，第一大步骤svn提交前准备，可先整理完所有的需挪动的文件夹与文件，然后再一并commit。（挪动文件夹与文件是一样的步骤与效果）。

##第二篇：svn撤销

对了，刚开始说的需要分享一下绝招。那就是在开发时巧妙使用 Discard All Changes 与 DisCard Changes这两个功能。有了这个绝活你现在可以任意删除或修改代码与文件（在试验这个步骤前请提交完有用的修改的代码），在项目结构中可以看到在修改的文件后面又一个“M”标记，然后点击Discard All Changes选项，将会撤销所有的修改（包括增删改文件与代码），与上次svn操作（包括commit与update）后的代码一样。

不知道Discard All Changes 与 DisCard Changes 功能的位置在哪的看图。
<br>
![screen14.jpeg](http://upload-images.jianshu.io/upload_images/301102-a9ec4c5e3c69a89e.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
          ![screen15.jpeg](http://upload-images.jianshu.io/upload_images/301102-ba7d04d36fe37b8f.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>

当然需要有改动的文件双击后才会有DisCard Changes功能，否则它是灰色按钮，它的功能是撤销当前文件的修改，保持与最后一次svn操作后的代码一致。同时，也可以使用DisCard Changes上面的Commit与Update功能，也是针对当前文件的svn操作。

有了Discard All Changes这个功能还怕项目跑不起来？还怕改错文件？还怕引入新文件或第三方库导致项目报错吗？哈哈，错了就直接Discard All Changes。一定要保证每次提交到svn时的项目能够正常运行。
