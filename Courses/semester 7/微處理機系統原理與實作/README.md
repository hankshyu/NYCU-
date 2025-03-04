# 微處理機系統原理與實作
## 概述
- 課程名稱：微處理機系統原理與實作
- 選修年度：111上
- 授課教師：蔡淳仁老師
- 開課單位：資工系 
- 永久課號：CSCS20019
- 學分數：3.00
- 必/選修：選修

這一堂課是交大資工系軟硬體整合主題學程的課程之一，內容涵蓋微處理器系統的設計實作細節。整堂課圍繞著[老師實驗室所開發的開源 RISC-V 處理器](https://github.com/eisl-nctu/aquila)設計了五個作業，分別涵蓋不同微處理機的重要模組。這堂課很考驗修課同學的硬體設計（Verilog HDL）以及處理複雜軟體的耐心，最好也看過一些組合語言，做起來會更上手。整堂課以微處理機為中心圍繞著複雜軟硬體系統，算是軟硬體整合領域非常核心的課程。作業中電路設計的部分需要在開發版上實測，也因為我們是第二屆，老師替換掉上一屆不敷使用的設備引進更加先進的 Xilinx Artix-7 XC7A100T FPGA，讓同學可以盡情地使用板子上的硬體資源來合成電路。在課堂的一開始老師還讓兩個人共用一塊板子，不過在期中退選和放棄的人走得差不多後，剛好每個人都可以獨享一片，還蠻幸福的。老師在課堂之中也有說到，這堂課的名稱應該改成應用處理器比較合適，因為現在處理器設計趨勢已經不再強調鑽研日趨飽和的微架構設計，而是設計並整合處理器微架構，錯綜復雜的記憶體模組以及各式各樣的應用加速電路形成系統單晶片（SoC）。像是蘋果成功的M系列晶片，高通驍龍系列及聯發科的天機系列都是很好的例子。

## 上課模式

老師將整堂課切分成6個單元如下：

#### 單元列表

編號 | 單元名稱
--------|:-----
0 |[Intorduction][h0]
1 |[RISC-V Instruction Set Architecture][h1]
2 |[Overview of Microprocessor Designs][h2]
3 |[Application Processors and Aquila SoC][h3]
4 |[Memory Subsystem of Microprocessors][h4]
5 |[Microprocessor Support for Operating Systems][h5]
6 |[Microprocessor I/O Subsystems][h6]

[h0]:handouts/0.%20Introduction.pdf
[h1]:handouts/1.%20RISCV%20ISA.pdf
[h2]:handouts/2.%20Overview%20Of%20Microprocessor%20Designs.pdf
[h3]:handouts/3.%20%20Application%20Processors%20and%20Aquila%20SoC.pdf
[h4]:handouts/4.%20Memory%20Subsystem.pdf
[h5]:handouts/5.%20Operating%20System%20Support.pdf
[h6]:handouts/6.%20I-O%20Subsystems.pdf

每個單元都對應一份作業，老師會先利用投影片的方式講解該單元的課程內容，接下來再說明對應該單元的作業。作業內容通常是要同學分析並改進一個微處理機系統的糢組，例如Branch Predictor或Cache System。老師會提供一個BenchMark Program來衡量系統的運作效能，所以效能如果有所提升都會很直觀地反映在測試程式上面。各單元對應的作業如下：

#### 作業內容

| 作業 | 單元名稱 | 作業報告 | 程式碼 |
|:-------: | :----- |:---:| :---:|
| HW0 | [Simulation of a HW-SW Platform][hw0]           |   ✏️          | 🔨        |
| HW1 | [Real-time Analysis of a HW-SW Platform][hw1]   |   [✏️][R1]    | [🔨][s1]  |
| HW2 | [Branch Predictor Design][hw2]                  |   [✏️][R2]    | [🔨][s2]  |
| HW3 | [Cache Optimization][hw3]                       |   [✏️][R3]    | [🔨][s3]  |
| HW4 | [Real-time operating system(RTOS) Analysis][hw4]|   [✏️][R4]    | [🔨][s4]  |
| HW5 | [Domain-Specific Accelerator][hw5]              |   [✏️][R5]    | [🔨][s5]  |

[hw0]:homeworks/HW0%20Simulation%20of%20a%20HW-SW%20Platform.pdf
[hw1]:homeworks/HW1/HW1%20Real-time%20Analysis%20of%20a%20HW-SW%20Platform.pdf
[hw2]:homeworks/HW2/HW2%20Branch%20Predictor.pdf
[hw3]:homeworks/HW3/HW3%20Cache%20Optimization.pdf
[hw4]:homeworks/HW4/HW4%20RTOS%20Analysis.pdf
[hw5]:homeworks/HW5/HW5%20Domain-specific%20Accelerator.pdf

[R1]:homeworks/HW1/0813358_徐子瀚_HW1-Report.pdf
[R2]:homeworks/HW2/mpd_hw2_2.pdf
[R3]:homeworks/HW3/0813358_hw3_Report.pdf
[R4]:homeworks/HW4/mpd_hw4.pdf
[R5]:homeworks/HW5/mpd_hw5.pdf

[s1]:src/HW1
[s2]:src/HW2
[s3]:src/HW3
[s4]:src/HW4
[s5]:src/HW5

老師有特別說明他強調的是對於系統的分析而不是改進。老師希望我們分析不同模組設計如何影響整體微處理機的效能，因此如何收集硬體系統的運作的數據並提出解釋就成了這一堂課的核心技能。每一份作業都需要撰寫寫成一份報告，報告的格式是使用IEEE論文的格式，中英文皆可。我是建議同學可以順便練習英文論文寫作，老師會親自批改。每份作業也都要向助教Demo，確保自己設計的模組在開發版上實際運沒有問題並回答一些助教的提問。雖然有要Demo的環節，不過報告的撰寫才是重點，如何將自己的實驗結果加以整合，放進一篇報告裡面也是這堂課會磨練到的技能。期中考和期末考都是考作業的內容，利用寫作業會用到的觀念加以延伸，來完成一些指定的任務。整體而言難度不算很高，只要有認真寫作業的同學都拿到很高的分數。


## 評分方式
在學期初老師公布的配分比例如下：

- 作業1~5(70%)
- 期中考(5%)
- 期末考(25%)

因為這一堂課的重點就是那五份作業，所以所佔的比例也非常的高。至於期中考及期末考懸殊的比例老師解釋除了難度的差異之外，還有期中考希望同學們先熟悉上機考的環境，所以不希望把比例調太高。最後的學期成績計算方式為按照上面的的配分比算出原始成績，再把及格同學的分數用線性調分調到介於 75 ~ 99 之間。最後同學們的成績分布如下：

#### 成績分布
   區間 | 人數
--------|:-----
90 ~ 100 分| 6 人
80 ~ 90 分| 1 人
75 ~ 80 分| 2 人
0分| 5 人
退選| 7 人
修課總人數| 21 人

可以看到，這堂課有一半的同學都放棄或是退選。很大的原因是因為這堂課需要花很多時間分析軟硬體系統的運作，許多的同學在還來不及研究透徹整個系統之前就選擇放棄了。但是有認真修完這堂課的同學都拿到很不錯的分數。總體而言，我認為這堂課的給分還蠻甜的吧！如果你有乖乖寫作業話。

## 結語
老師人非常的好也很樂於幫助同學，除了週末休息時間之外老師回信非常積極，我認為這堂課遇到問題最好的方式就是直接寫信和老師互動！這一堂課我非常推薦給想要走硬體領域的資工系同學修習，算是集合了數位電路設計、計算機組織與系統軟體於一身的好課。課堂上的訓練非常扎實，還能磨練其他課練習不到的論文寫作能力，可謂一舉數得！記得老師在大一基礎程式設計的課程時，就提到寫程式不要使用try and error 的方法，因為這會養成壞習慣不去深度思考程式是如何運作的。這一堂課我就深有感觸。到作業後半段的時候有進行電路合成都要耗費許多時間，每一次合成之前都要再三確認自己的程式碼是否正確。說了那麼多好話，這一堂課或許也不適合每一個人，過多的先備知識對於不是鑽研硬體領域的資工系同學很難上手。作業平均而言也需要花費許多的時間。或許天底下就沒有白吃的午餐吧！想要獲得豐盛的回報就要付出相應的努力。推薦給喜歡軟硬體整合且喜歡認真學習的你。
