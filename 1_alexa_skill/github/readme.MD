# How to develop a Alexa Skill and earn free $100 AWS credits

# 如何开发Alexa Skill并赚100美金AWS使用劵

1. 点击[这里](https://developer.amazon.com/en-US/alexa/alexa-skills-kit)打开Alexa Skill开发页面。

2. 点击Console， 登录Alexa Skill开发环境，注意这里使用的是你的美国亚马逊账号（花钱剁手买东西的那个），并不是AWS账号，当然你也需要一个AWS账号，因为Alexa Skill的后端需要AWS Lambda Service的支持，而且最后你赚到的100美金也会存在这个AWS账号里，关于如何注册AWS账号请点[这里](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/)

3. 进入Alexa Skill开发者页面后，点击“Create Skill".

4. 在"skill name"下填入你想给你的alexa skill起的名字

5. 选择你默认的语言,Alexa Skill目前还不支持中文. 

6. 在"choose model"环节选择"Custom". "Custom"可以让你建一个很简单的skill同时还拥有很高的自由度.当然你也可以用其他Amazon提供的模板,具体每个模板有哪些功能和如何应用请点[这里](https://developer.amazon.com/en-US/docs/alexa/ask-overviews/build-skills-with-the-alexa-skills-kit.html)

7. 在"choose a method"环节选择"Provision your own"

8. 点击"create skill"正式进入skill设计环节

9. 在"choose a template"页面选择"Start from scratch",如果你选择其他built-in模板会有不同的功能.

10. 在左侧工具栏点击"Invocation", Invocation 是Alexa的唤醒词,比如你想创立了一个叫做"NBA news"的skill,当你想打开这个skill时你要说"Alexa, open NBA news这时你的Alexa就会去调用这个功能了.所以这个Invocation最好设成一个简单易懂同时又代表了你的Skill功能的词.

11. 设置intents,首先了解几个概念

- intents 意愿,表示通过这个Skill想实现什么功能,Amazon会有一些built-in intents,比如Stop, Help等等.比如通过StopIntent你可以停止Alexa现在在做的动作. 我们要开发的就是加入自己的intents,比如在我的演示中我加入了WhatZodiac 这个intent就是要通过询问Alexa来获得特定的年份的属相.
- Utterance 表达, 这个是在intents范畴下的一个概念,表示你想通过哪些句子来向Alexa提问.比如我想问姚明有多高,那Utterance可以是"What is the height of <Yaoming>". 在你的Alexa Skill下通过这个句式就可以触发后端程序来访问姚明的身高.注意这个Utterance中Yaoming的部分是可以被替换的,这个叫做slots,我们下面会讲到

- Slots 空位, Slots就像是我们在写代码时的变量,我们可以赋予这个变量不同的值.比如你要建一个介绍NBA巨星的Skill,那Slots就是这些巨星的名字的一个变量,或者你想建一个询问某年属相的Skill,那这个Slots就是哪一年这个变量.Amazon有一些自带的变量类型比如日期,数字,如果你的变量是新的一组数值或者文字,你就需要新建一个Slot Type来记录这些变量.

具体关于Intents, Utterance和Slots的官方解释请看[这里](https://developer.amazon.com/en-US/docs/alexa/custom-skills/create-intents-utterances-and-slots.html)


12. 保存和建立模型.还是在intents这个环节,如果你建立了相应的Intents, Utterance和Slots那接下来就可以点页面上方的"Save Model"和"Build Model"来建立模型了,如果在intents环节有问题系统会有提示哪里出现了问题.

13. 编写后端Lambda方程. 这时需要你打开AWS账户,找到Lambda Service,然后创立一个新的Python方程, 选用Alexa Skill作为trigger,然后去Alexa Skill界面的Endpoint部分找到Alexa Skill,复制粘贴在trigger部分, 然后编辑相应的部分,代码部分可以在这个repo的Lambda文件夹下找到.

14. 链接Alexa Skill和AWS Lambda Function. 首先复制你的Lambda Function的ARN, AWS中的ARN是 Amazon Resource Name 的缩写,是一个回溯查找AWS资源和功能的路径,只要有这个路径,我们的Alexa Skill就可以找到相对应的Lambda Function. 复制成功后,回到Alexa Skill Develop界面,点击左边工具栏的Endpoint, 粘贴之前的ARN到"Default Region"区域.然后在上方选择保存Endpoint

15. 点击页面最上边的"Test"部分,进入测试环节,这时你会被问道要不要打开麦克风来测试,如果选择不开可以通过键入测试内容来进行测试,和用语音测试时一样的效果. 在测试时首先要打开你的Alexa Skill,你可以通过"open <your Skill's Invocation>" 来触发你的Alexa Skill,然后你就能听到你在Lambda function里写入的介绍你的skill的话,这时你就可以通过你设定的intents来询问Alexa了,比如你的intents是"Tell me about what zodiac is 1988", 你就可以听到Alexa的相应的回答了.如果这时出现了bug那么你可以看Alexa返回的内容来debug或者去AWS Lambda function下的log里来寻找问题.具体如何debug请看[这里](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-test-and-debug.html)

16. 最后,点击Alexa Skill Develop页面最上方的"Distribution", 完成你的Skill的介绍和属性相关的问题,然后你就可以提交了.在经过一天的审理后你的Alexa Skill就可以上线了,上线后不要忘记去这个[网页](https://developer.amazon.com/en-US/alexa/alexa-skills-kit/new/aws-promotional-credits#application)申请你的100美元的AWS Credits哦.通常在下个月的12-15号左右打入你相应的AWS账户.你需要提供你的[AWS账户](https://enterprise.arcgis.com/en/server/10.3/cloud/amazon/find-your-amazon-account-number.htm)和vendorID,
