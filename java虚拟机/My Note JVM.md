# 097的JVM笔记

<div class="mxgraph" style="max-width:100%;border:1px solid transparent;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;resize&quot;:true,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;Electron\&quot; modified=\&quot;2021-09-20T05:42:42.509Z\&quot; agent=\&quot;5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/13.5.7 Chrome/83.0.4103.122 Electron/9.1.2 Safari/537.36\&quot; etag=\&quot;ssOFkQXi_RMm05LbtCeh\&quot; version=\&quot;13.5.7\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;4BP3AKqU9UJVQk_IDlQQ\&quot; name=\&quot;Page-1\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;,&quot;toolbar&quot;:&quot;pages zoom layers lightbox&quot;,&quot;page&quot;:0}"></div>
<script type="text/javascript" src="https://app.diagrams.net/js/viewer-static.min.js"></script>

![img](https://gitee.com/gu097/note/raw/master/img/Untitled%20Diagram.png)

# 内存调优方法

**一、导致Full GC一般由于以下几种情况**：

1、旧生代空间不足
   调优时尽量让对象在新生代GC时被回收、让对象在新生代多存活一段时间和不要创建过大的对象及数组避免直接在旧生代创建对象
 2、Pemanet Generation空间不足
   增大Perm Gen空间，避免太多静态对象
   统计得到的GC后晋升到旧生代的平均大小大于旧生代剩余空间
   控制好新生代和旧生代的比例
 3、System.gc()被显示调用
   垃圾回收不要手动触发，尽量依靠JVM自身的机制

**二、主要的调优手段**

调优手段主要是通过控制堆内存的各个部分的比例和GC策略来实现，内存比例不良设置会导致一下不良后果：
 1). 新生代设置过小
   一是新生代GC次数非常频繁，增大系统消耗；二是导致大对象直接进入旧生代，占据了旧生代剩余空间，诱发Full GC
 2). 新生代设置过大
   一是新生代设置过大会导致旧生代过小（堆总量一定），从而诱发Full GC；二是新生代GC耗时大幅度增加
   一般说来新生代占整个堆1/3比较合适
 3). Survivor设置过小
   导致对象从eden直接到达旧生代，降低了在新生代的存活时间
 4). Survivor设置过大
   导致eden过小，增加了GC频率。
   另外，通过-XX:MaxTenuringThreshold=n来控制新生代存活时间，尽量让对象在新生代被回收

**三、新生代和旧生代GC策略和组合搭配**
 由内存管理和垃圾回收可知新生代和旧生代都有多种GC策略和组合搭配，选择这些策略对于我们这些开发人员是个难题，JVM提供两种较为简单的GC策略的设置方式。
 1). 吞吐量优先
   JVM以吞吐量为指标，自行选择相应的GC策略及控制新生代与旧生代的大小比例，来达到吞吐量指标。这个值可由-XX:GCTimeRatio=n来设置
 2). 暂停时间优先
   JVM以暂停时间为指标，自行选择相应的GC策略及控制新生代与旧生代的大小比例，尽量保证每次GC造成的应用停止时间都在指定的数值范围内完成。这个值可由-XX:MaxGCPauseRatio=n来设置

**四、几种常见的JVM配置原则**

-Xms:初始堆大小

-Xmx:最大堆大小

-XX:NewSize=n:设置年轻代大小

-XX:NewRatio=n:设置年轻代和年老代的比值。如:为3，表示年轻代与年老代比值为1：3，年轻代占整个年轻代年老代和的1/4

-XX:SurvivorRatio=n:年轻代中Eden区与两个Survivor区的比值。注意Survivor区有两个。如：3，表示Eden：Survivor=3：2一个Survivor区占整个年轻代的1/5

-XX:MaxPermSize=n:设置持久代大小

2、收集器设置

-XX:+UseSerialGC:设置串行收集器

-XX:+UseParallelGC:设置并行收集器

-XX:+UseParalledlOldGC:设置并行年老代收集器

-XX:+UseConcMarkSweepGC:设置并发收集器

3、垃圾回收统计信息

-XX:+PrintGC

-XX:+PrintGCDetails

-XX:+PrintGCTimeStamps

-Xloggc:filename

4、并行收集器设置

-XX:ParallelGCThreads=n:设置并行收集器收集时使用的CPU数。并行收集线程数。

-XX:MaxGCPauseMillis=n:设置并行收集最大暂停时间

-XX:GCTimeRatio=n:设置垃圾回收时间占程序运行时间的百分比。公式为1/(1+n)

5、并发收集器设置

-XX:+CMSIncrementalMode:设置为增量模式。适用于单CPU情况。

-XX:ParallelGCThreads=n:设置并发收集器年轻代收集方式为并行收集时，使用的CPU数。并行收集线程数。
https://blog.csdn.net/LeegooWang/article/details/88696195