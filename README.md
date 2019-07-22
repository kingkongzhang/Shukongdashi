# Shukongdashi
使用知识图谱，自然语言处理，卷积神经网络等技术，基于python语言，设计了一个数控领域故障诊断专家系统

## 项目介绍
本项目是第八届中国软件杯大赛，基于移动端在线设备故障诊断平台的参赛作品。\
数控机床故障诊断和维修是企业设备管理的难点和重点，设备在运行中会产生各种“疑难杂症”，不及时排出就会影响生产生活，甚至酿成事故。数控机床出了故障，一旦查清了故障点和故障原因，维修起来其实是一件比较容易的事。通过自适应设备故障诊断APP，根据故障信息，自动抓取互联网中适应的故障产生原因和优秀解决方法，形成知识库，将辅助设备维修人员快速诊断排出故障，保障生产。
>### 石家庄铁道大学软件工程系
>团队名称：集结号\
>指导教师：王建民\
>团队成员：王金萱、马佳慧
## 目录结构
  |--Shukongdashi\
    --demo\
      --checkpoints\
      --data  //目录\
    --Model\
    --test_my\
    --toolkit\
    --settings.py\
    --urls.py\
    --view.py\
    --wsgi.py\
## 项目配置

## 系统功能

## 设计思路

通过学习大量数控机床的历史维修案例，基于知识图谱、自然语言处理技术，融合规则推理，我们设计了一个越用越聪明的诊断数控机床故障专家系统。\
首先，我们爬取了大量数控机床维修案例，使用NLP自然语言处理技术对文本做了噪声移除和句法分析，然后使用CNN卷积神经网络识别出了故障描述中用户所做的操作和出现的故障现象，结合词性标注，正则表达式处理等技术，最终提取出了故障描述中，对机床执行的操作，故障的现象，故障的部位，存在的报警信号。\
基于Neo4j图数据库能够清晰的表示数据模型的优点，我们经过上面对故障描述的拆分和标注，表示出了做了什么操作会引起了什么故障现象，故障现象之间的并发或间接导致的关联关系，一个故障原因会间接或直接导致哪些故障现象的发生，机床的某个部位会出现的故障现象，报警代码和故障现象之间的关联，构成了知识图谱，使用基于规则的推理模型实现了我们的推理算法。\
当一个新的故障发生时，通过分析，如果现有的知识不能解决新的故障，这时通过在线分析，爬取解决方案，通过用户人为反馈和语料库对比分析程序，确认结果可靠之后，分析当前的故障描述，原理同上述构建知识库的过程，拆分之后，对新的知识进行补充，对已经存在的知识，进一步完善和优化，最终实现知识库的自学习功能。\
在故障诊断的过程中，类似上述的处理方法，分析故障描述，通过分析故障部位，出现的现象，所做的操作，结合知识图谱，分析出导致这些现象出现的最可能的故障原因，设置权值，然后通过CNN卷积神经网络对故障现象进行预测，对诊断出的故障结果的权值进行微调，排序之后展示给用户。
