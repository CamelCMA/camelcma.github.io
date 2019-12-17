---
layout: post
title: Vrand_VisualDOC_Ch0_Introduction
categories:
  - Vrand
tags:
  - Cae
  - Vrand
  - VisualDOC
  - Optimization
excerpt_separator: <!--more-->
---

<body>
    <div id="doc" class="markdown-body container-fluid comment-enabled" data-hard-breaks="true" style="position: relative;"><h2 id="-0-目錄"><a class="anchor hidden-xs" href="#-0-目錄" title="-0-目錄"><span class="octicon octicon-link"></span></a><img alt=":bulb:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/bulb.png" title=":bulb:"> 0. 目錄</h2><p><span class="toc"><ul>
<li><a href="#Vrand_VisualDOC_Ch0_Introduction" title="Vrand_VisualDOC_Ch0_Introduction">Vrand_VisualDOC_Ch0_Introduction</a><ul>
<li><a href="#-0-目錄" title=" 0. 目錄"> 0. 目錄</a></li>
<li><a href="#-1-聲明" title=" 1. 聲明"> 1. 聲明</a></li>
<li><a href="#-2-VRampD介紹" title=" 2. VR&amp;D介紹"> 2. VR&amp;D介紹</a></li>
<li><a href="#-3-VRampD產品" title=" 3. VR&amp;D產品"> 3. VR&amp;D產品</a></li>
<li><a href="#-4-VisualDOC介面" title=" 4. VisualDOC介面"> 4. VisualDOC介面</a></li>
<li><a href="#-5-VisualDOC設定流程" title=" 5. VisualDOC設定流程"> 5. VisualDOC設定流程</a><ul>
<li><a href="#51-Work-Flow" title="5.1 Work Flow">5.1 Work Flow</a></li>
<li><a href="#52-Component-Editor" title="5.2 Component Editor">5.2 Component Editor</a></li>
<li><a href="#53-Data-Linker" title="5.3. Data Linker">5.3. Data Linker</a></li>
<li><a href="#54-Simulation-Monitors" title="5.4 Simulation Monitors">5.4 Simulation Monitors</a></li>
<li><a href="#55-Post-Processing" title="5.5 Post Processing">5.5 Post Processing</a></li>
</ul>
</li>
<li><a href="#-6-觀念解說" title=" 6. 觀念解說"> 6. 觀念解說</a><ul>
<li><a href="#61-Project-and-Task" title="6.1 Project and Task">6.1 Project and Task</a></li>
<li><a href="#62-模組化設定" title="6.2 模組化設定">6.2 模組化設定</a></li>
</ul>
</li>
<li><a href="#-7-VisualDOC手冊" title=" 7. VisualDOC手冊"> 7. VisualDOC手冊</a></li>
<li><a href="#-8-合作夥伴推薦" title=" 8. 合作夥伴推薦"> 8. 合作夥伴推薦</a></li>
<li><a href="#-9-本系列文使用之軟硬體" title="  9. 本系列文使用之軟硬體">  9. 本系列文使用之軟硬體</a></li>
<li><a href="#-10-聯絡老駱" title="  10. 聯絡老駱">  10. 聯絡老駱</a></li>
</ul>
</li>
</ul>
</span></p>

<!--more-->

<h2 id="-1-聲明"><a class="anchor hidden-xs" href="#-1-聲明" title="-1-聲明"><span class="octicon octicon-link"></span></a><img alt=":mega:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/mega.png" title=":mega:"> 1. 聲明</h2><div class="alert alert-info">
<ul>
<li><code>VisualDOC</code>及其編寫之<a href="#-7-VisualDOC%E6%89%8B%E5%86%8A">手冊</a>皆屬<code>VR&amp;D</code>財產。</li>
<li>本系列文共計<code>7</code>篇，目的為讓初學者能快速認識<code>VisualDOC</code>。系列文中所有引用及軟體截圖，業已經過<code>VR&amp;D</code>授權使用。
<ul>
<li><ins><a href="" target="_blank" rel="noopener">Vrand_VisualDOC_Ch0_Introduction</a></ins></li>
<li><ins><a href="{% post_url 2019-12-17-Vrand_VisualDOC_Ch1_PythonEquation %}" target="_blank" rel="noopener">Vrand_VisualDOC_Ch1_PythonEquation</a></ins></li>
<li><ins><a href="{% post_url 2019-12-17-Vrand_VisualDOC_Ch2_DOE %}" target="_blank" rel="noopener">Vrand_VisualDOC_Ch2_DOE</a></ins></li>
<li><ins><a href="{% post_url 2019-12-17-Vrand_VisualDOC_Ch3_Opt_RSA_Using_DOE %}" target="_blank" rel="noopener">Vrand_VisualDOC_Ch3_Opt_RSA_Using_DOE</a></ins></li>
<li><ins><a href="{% post_url 2019-12-17-Vrand_VisualDOC_Ch4_Executable_Wrapper %}" target="_blank" rel="noopener">Vrand_VisualDOC_Ch4_Executable_Wrapper</a></ins></li>
<li><ins><a href="{% post_url 2019-12-17-Vrand_VisualDOC_Ch5_Python_Scipy %}" target="_blank" rel="noopener">Vrand_VisualDOC_Ch5_Python_Scipy</a></ins></li>
<li><ins><a href="{% post_url 2019-12-17-Vrand_VisualDOC_Ch6_Coupling_with_LSDYNA %}" target="_blank" rel="noopener">Vrand_VisualDOC_Ch6_Coupling_with_LSDYNA_Opt</a></ins></li>
</ul>
</li>
<li>您可以在 <ins><a href="http://www.vrand.com/" target="_blank" rel="noopener">VR&amp;D官網</a></ins> 找到其相關產品及聯絡方式。</li>
<li>您可以在 <ins><a href="https://www.youtube.com/channel/UCwypCCBH4XiInvSqxHkGvrA/videos" target="_blank" rel="noopener">VisualDOC的YouTube Channel</a></ins> 找到一些教學影片。</li>
<li><img alt=":tada:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/tada.png" title=":tada:"> 特別感謝<code>VR&amp;D</code> <code>President/COO Mr. Juan Pablo Leiva</code>免費提供老駱<code>VisualDOC</code> trial license作學習之用，並於過程中持續提供技術支援。</li>
</ul>
</div><h2 id="-2-VRampD介紹"><a class="anchor hidden-xs" href="#-2-VRampD介紹" title="-2-VRampD介紹"><span class="octicon octicon-link"></span></a><img alt=":earth_americas:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/earth_americas.png" title=":earth_americas:"> 2. VR&amp;D介紹</h2><iframe width="662" height="371" src="https://www.youtube.com/embed/DpYWaOAB1FE" allowfullscreen=""></iframe><p><code>VR&amp;D</code>全名為<code>Vanderplaats Research &amp; Development</code>，是由<code>Dr. Garret N. Vanderplaats</code>於<code>1984</code>年在美國創立，詳細介紹可以參考 <ins><a href="http://www.vrand.com/about-us/" target="_blank" rel="noopener">VR&amp;D官網About Us</a></ins>。</p><p>關於<code>Dr. Garret N. Vanderplaats</code>的生平，<code>VR&amp;D</code>官網提供了 <ins><a href="http://www.vrand.com/sites/default/files/pub/VR&amp;D_GV_Interview.pdf" target="_blank" rel="noopener">Interview with Dr. Garret (Gary) N. Vanderplaats</a></ins> 及 <ins><a href="http://www.vrand.com/sites/default/files/pub/GradientOpt.pdf" target="_blank" rel="noopener">Technical Story of Dr. Garret (Gary) N. Vanderplaats</a></ins> 兩篇文章，老駱覺得都相當值得一看。其中也提到了許多有關最佳化演算法及程式的歷史故事，例如:<code>GENESIS</code>和<code>MSC Nastran SOL200</code>的淵源、現在市售的某些結構最佳化軟體，是源自當初他所開發的<code>CONMIN(1972)</code>和<code>ADS(1984)</code>程式等等。對最佳化理論及應用有興趣的朋友，可以繼續觀看下面這個由<code>Dr. Garret (Gary) N. Vanderplaats</code>所主講的影片。</p><iframe width="662" height="371" src="https://www.youtube.com/embed/1XdXHrf3nFE" allowfullscreen=""></iframe><p>此外，官網也提供了許多論文，<ins><a href="http://www.vrand.com/resources/publications/archive/" target="_blank" rel="noopener">可以下載</a></ins> 。</p><p>這邊老駱引用一段<code>Interview with Dr. Garret (Gary) N. Vanderplaats</code>內的話，裡面提到了成立<code>VR&amp;D</code>的兩大初衷是:</p><ul>
<li>提供世界上最好的最佳化軟體</li>
<li>打造最頂尖的專家團隊</li>
</ul><p>而他確信他已經完成了目標，所以可以將管理公司的任務交棒給非常優秀的繼任者，<code>Mr. Juan Pablo Leiva</code>。自己則能夠多點空閒時間，來做點其它想做的事。</p><blockquote style="border-left-color: rgb(144, 123, 247);">
<p>To back up, creating the company, I had two goals: one is to have the best software in the optimization world, and the other is to have the best staff of experts. I’m very confident that I’ve achieved those goals.That’s why about five years ago or six years ago, I forget when, I was able to turn the management of the company over to Juan Pablo Leiva who is a superstar in his own right. Now I can spend time doing a little bit of research, a little bit of relaxing, and letting other people do the day-to-day operations.<small><i class="fa fa-user"></i> Dr. Garret N. Vanderplaats</small><span class="color" data-color="#907bf7"></span></p>
</blockquote><h2 id="-3-VRampD產品"><a class="anchor hidden-xs" href="#-3-VRampD產品" title="-3-VRampD產品"><span class="octicon octicon-link"></span></a><img alt=":thumbsup:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/thumbsup.png" title=":thumbsup:"> 3. VR&amp;D產品</h2><p><code>VR&amp;D</code>旗下有兩條主要產品線，<ins><a href="http://www.vrand.com/products/genesis/" target="_blank" rel="noopener">GENESIS</a></ins> 及 <ins><a href="http://www.vrand.com/products/visualdoc/" target="_blank" rel="noopener">VisualDOC</a></ins>。</p><p><code>GENESIS</code>是一款偏向結構分析及結構最佳化的產品，可以進行下列分析:</p><ul>
<li><code>Topology</code></li>
<li><code>Sizing</code></li>
<li><code>Shape</code></li>
<li><code>Topometry</code></li>
<li><code>Topography</code></li>
<li><code>Freeform</code></li>
</ul><p><img src="/assets/img/vrand_vdoc/ch0/51_genesis.jpg" alt="51_genesis"></p><p><code>Design Studio</code>是專為<code>GENESIS</code>量身打造的前後處理環境，提供許多方便的介面來設定問題。但美中不足的是，目前並沒有產生網格的功能。</p><p><img src="/assets/img/vrand_vdoc/ch0/52_design_studio.jpg" alt="52_design_studio"></p><p><code>VisualDOC</code>則是一款通用型的最佳化軟體，並可以和幾乎所有<code>Script</code>或第三方分析軟體進行耦合分析，例如:<code>Excel</code>、<code>Python</code>、<code>Excel</code>、<code>MATLAB</code>、<code>ANSYS</code>、<code>LS-DYNA</code>、<code>TAITherm</code>及<code>Modelx3D</code>等。</p><p><img src="/assets/img/vrand_vdoc/ch0/53_capability_chart.png" alt="53_capability_chart"></p><p><img alt=":orange_book:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/orange_book.png" title=":orange_book:"> <ins><a href="http://www.vrand.com/products/multidiscipline-design-optimization/" target="_blank" rel="noopener">Multidiscipline Design Optimization</a></ins> 是由<code>Dr. Garret N. Vanderplaats</code>編寫的最佳化書籍，內容深入淺出，老駱閱讀之後，著實獲益良多。有興趣的朋友於官網訂購後，可直接寄送至台灣。</p><p><img src="/assets/img/vrand_vdoc/ch0/54_textbook_cover.png" alt="54_textbook_cover" width="400" height="600"></p><p>目錄:</p><ul>
<li>Chapter 1:	Basic Concepts</li>
<li>Chapter 2:	Functions of One Variable</li>
<li>Chapter 3:	Unconstrained Functions of N Variables</li>
<li>Chapter 4:	Constrained Functions of N Variables: Linear Programming</li>
<li>Chapter 5:	Constrained Functions of N Variables: Sequential Unconstrained Minimization Techniques</li>
<li>Chapter 6:	Constrained Functions of N Variables: Direct Methods</li>
<li>Chapter 7:	Approximation Techniques</li>
<li>Chapter 8:	Discrete Variable Optimization and Multi-Objective Optimization</li>
<li>Chapter 9:	Structural Optimization</li>
<li>Chapter 10:	General Design Applications</li>
<li>Chapter 11:	Multidiscipline Design Optimization</li>
<li>Appendix A:	Basic Matrix Theory</li>
<li>Appendix B:	Optimization Software</li>
</ul><h2 id="-4-VisualDOC介面"><a class="anchor hidden-xs" href="#-4-VisualDOC介面" title="-4-VisualDOC介面"><span class="octicon octicon-link"></span></a><img alt=":mag_right:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/mag_right.png" title=":mag_right:"> 4. VisualDOC介面</h2><p>下面是<code>VisualDOC</code>剛打開的全景圖。<br>
<img src="/assets/img/vrand_vdoc/ch0/61_overview.jpg" alt="61_overview"></p><table>
<thead>
<tr>
<th style="text-align:center">欄位</th>
<th style="text-align:left">功能</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center">A</td>
<td style="text-align:left">操作欄</td>
</tr>
<tr>
<td style="text-align:center">B</td>
<td style="text-align:left">將<code>A欄</code>內一些常用的功能以<code>icon</code>顯示</td>
</tr>
<tr>
<td style="text-align:center">C</td>
<td style="text-align:left">主要工作區，方便設定問題時，可以切換不同的<code>panel</code></td>
</tr>
<tr>
<td style="text-align:center">D</td>
<td style="text-align:left">流程樹，可以確認各<code>component</code> 在<code>Work Flow</code>內的順序</td>
</tr>
<tr>
<td style="text-align:center">E</td>
<td style="text-align:left">每種<code>icon</code>代表一種<code>component</code></td>
</tr>
<tr>
<td style="text-align:center">F</td>
<td style="text-align:left"><code>Work Flow</code>，圖像化設定流程</td>
</tr>
<tr>
<td style="text-align:center">G</td>
<td style="text-align:left"><code>Work Flow</code>連接工具</td>
</tr>
<tr>
<td style="text-align:center">H</td>
<td style="text-align:left">一些視覺輔助工具</td>
</tr>
<tr>
<td style="text-align:center">I</td>
<td style="text-align:left">顯示<code>VisualDOC</code>執行情況</td>
</tr>
</tbody>
</table><h2 id="-5-VisualDOC設定流程"><a class="anchor hidden-xs" href="#-5-VisualDOC設定流程" title="-5-VisualDOC設定流程"><span class="octicon octicon-link"></span></a><img alt=":mag_right:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/mag_right.png" title=":mag_right:"> 5. VisualDOC設定流程</h2><p><code>C欄</code>內有<code>5</code>個<code>panel</code>，依序由左至右即是設定問題的流程。</p><table>
<thead>
<tr>
<th style="text-align:left">Panel</th>
<th style="text-align:left">說明</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left"><a href="#51-Work-Flow">5.1 Work Flow</a></td>
<td style="text-align:left">選出求解問題所須具備的<code>component</code>並正確連接</td>
</tr>
<tr>
<td style="text-align:left"><a href="#52-Component-Editor">5.2 Component Editor</a></td>
<td style="text-align:left">針對個別<code>component</code>做細部設定</td>
</tr>
<tr>
<td style="text-align:left"><a href="#53-Data-Linker">5.3 Data Linker</a></td>
<td style="text-align:left">連接<code>Component Editor</code>中各層關係</td>
</tr>
<tr>
<td style="text-align:left"><a href="#54-Simulation-Monitors">5.4 Simulation Monitors</a></td>
<td style="text-align:left">進階視覺化輔助工具(雖非必要設定，但很有用!)</td>
</tr>
<tr>
<td style="text-align:left"><a href="#55-Post-Processing">5.5 Post Processing</a></td>
<td style="text-align:left">提供預先設定好的後處理工具</td>
</tr>
</tbody>
</table><h3 id="51-Work-Flow"><a class="anchor hidden-xs" href="#51-Work-Flow" title="51-Work-Flow"><span class="octicon octicon-link"></span></a>5.1 Work Flow</h3><p>設定<code>Work Flow</code>有兩個方法。</p><h4 id="511-拖曳法"><a class="anchor hidden-xs" href="#511-拖曳法" title="511-拖曳法"><span class="octicon octicon-link"></span></a>5.1.1 拖曳法</h4><p>拖曳法是利用拖拉的方式從<code>E欄</code>中選取所需要的<code>icon</code>，並拖曳至<code>F欄</code>，進行適當的組合後，再利用<code>G欄</code>的按鍵，完成<code>Work Flow</code>的連接。</p><p>拖曳法的特點為:</p><ul>
<li>操作上比較直觀</li>
<li>須要手動進行拖曳並連接</li>
<li>擁有比較高的建模彈性</li>
<li>適用於有多步流程的大模型或客製化的修改</li>
</ul><p>拖曳法須要用到<code>G欄</code>內的四個按鈕:</p><ul>
<li><code>Switch to connection mode</code>: 可以進入<code>connetion mode</code>，手動連接各個<code>component</code>。連接完成後，可按鍵盤<code>ESC</code>鍵跳離<code>connection mode</code>。</li>
<li><code>Auto connect all models</code> : 連接的邏輯是根據<code>D欄</code>內的順序，可以利用<code>D欄</code>下方的上下鍵調整各<code>component</code>的位置。如果使用者的滑鼠是點在<code>D欄</code>裡的<code>Flowchart Components</code>的話，會對整個<code>Work Flow</code>進行自動連接。但如果使用者只想自動連接特定<code>Component Editor外/中層</code>內<code>component</code>的話，須要在<code>D欄</code>先將滑鼠點在那個<code>Component Editor外/中層</code>上。</li>
<li><code>Remove all connectors</code> : 除去所有連接。</li>
<li><code>Automatically rearrange all models</code> : 重新排版連接後的版面。</li>
</ul><div class="alert alert-warning">
<p><img alt=":flashlight:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/flashlight.png" title=":flashlight:"> 連接時，請使用以<code>component4個端點</code>連到<code>component4個端點</code>的方式操作(避免<code>component</code>直接連到<code>component</code>)，比較容易成功。</p>
</div><p>舉例來說，假如想要最小化一個函數，如何利用拖曳法完成呢?<br>
一個可能的參考作法是:</p><p>從<code>E欄</code>中選擇<code>Add optimization component</code>拖曳至<code>F欄</code>。</p><p><img src="/assets/img/vrand_vdoc/ch0/101_work_flow.jpg" alt="101_work_flow"></p><p>從<code>E欄</code>中選擇<code>Add PythonEquation component</code>拖曳進<code>F欄</code>。接著對<code>Add PythonEquation component</code>按右鍵<code>cut</code>，然候對<code>optimization component</code>按右鍵<code>Paste</code>。如此就可以利用<code>PythonEquation component</code>來進行<code>optimization</code>。</p><p><img src="/assets/img/vrand_vdoc/ch0/102_work_flow.jpg" alt="102_work_flow"></p><p>從<code>E欄中</code>選擇<code>stop</code>拖曳至<code>F欄</code>(很容易忘記…)。</p><p><img src="/assets/img/vrand_vdoc/ch0/103_work_flow.jpg" alt="103_work_flow"></p><p>利用<code>G欄</code>內的第一個按鍵<code>Switch to connection mode</code>，手動連接各個<code>component</code>。或是將各<code>component</code>於<code>D欄</code>中的位置調整好後，再使用<code>Auto connect all models</code>連接。</p><p><img src="/assets/img/vrand_vdoc/ch0/104_work_flow.jpg" alt="104_work_flow"></p><p>利用<code>G欄</code>內的最後一個按鍵<code>Automatically rearrange all models</code>，重新排版。</p><p><img src="/assets/img/vrand_vdoc/ch0/105_work_flow.jpg" alt="105_work_flow"></p><h4 id="512-Quick-Start"><a class="anchor hidden-xs" href="#512-Quick-Start" title="512-Quick-Start"><span class="octicon octicon-link"></span></a>5.1.2 Quick Start</h4><p><code>Quick start</code>是<code>VisualDOC</code>內建的流程精靈。<br>
<code>Quick start</code>的特點為:</p><ul>
<li>必須事先明確想做的分析類型</li>
<li>幾個鍵即能快速搭建並自動連接想要的應用</li>
<li>建模彈性比較小</li>
<li>適用流程單純的小模型及常規分析</li>
<li><a href="#61-Project-and-Task">僅適用於每個<code>project</code>的第<code>1</code>個<code>task</code></a></li>
</ul><p>同樣地，假如想要最小化一個函數，如何利用<code>Quick start</code>完成呢?<br>
一個可能的參考作法是:</p><p>從<code>A欄</code>中點選<code>File</code>後，再點選<code>Quick Start</code>(另一個方法是點選<code>B欄</code>中的<code>Quick Start icon</code>)。</p><p><img src="/assets/img/vrand_vdoc/ch0/106_work_flow.jpg" alt="106_work_flow"></p><p>選擇<code>Direct Optimization</code>。</p><p><img src="/assets/img/vrand_vdoc/ch0/107_work_flow.jpg" alt="107_work_flow"></p><p>選擇<code>PythonEquation</code>。</p><p><img src="/assets/img/vrand_vdoc/ch0/108_work_flow.jpg" alt="108_work_flow"></p><p>填入想要的檔案名並存檔後，<code>Work Flow</code>就完成了。</p><p><img src="/assets/img/vrand_vdoc/ch0/109_work_flow.jpg" alt="109_work_flow"></p><h3 id="52-Component-Editor"><a class="anchor hidden-xs" href="#52-Component-Editor" title="52-Component-Editor"><span class="octicon octicon-link"></span></a>5.2 Component Editor</h3><p><code>Component Editor</code>的功能是設定<code>Work Flow</code>中選取<code>component</code>的細部設定。</p><h4 id="521-5種component類型"><a class="anchor hidden-xs" href="#521-5種component類型" title="521-5種component類型"><span class="octicon octicon-link"></span></a>5.2.1 5種component類型</h4><p>老駱自己將<code>component</code>分為<code>5</code>種類型。</p><h5 id="5211-Component-Editor內層直接支援的第三方軟體"><a class="anchor hidden-xs" href="#5211-Component-Editor內層直接支援的第三方軟體" title="5211-Component-Editor內層直接支援的第三方軟體"><span class="octicon octicon-link"></span></a>5.2.1.1 Component Editor內層(直接支援的第三方軟體)</h5><p><code>VisualDOC</code>針對以下軟體的使用特性，幫使用者處理好<code>I/O</code>介面，方便使用。</p><ul>
<li><code>MATLAB</code></li>
<li><code>Excel</code></li>
<li><code>GENESIS</code></li>
<li><code>ANSYS</code></li>
<li><code>Moldex3D</code></li>
<li><code>TAITherm</code></li>
<li><code>Lua Equation</code></li>
<li><code>PythonEquation</code></li>
</ul><h4 id="5212-Component-Editor內層客製化串接其它軟體"><a class="anchor hidden-xs" href="#5212-Component-Editor內層客製化串接其它軟體" title="5212-Component-Editor內層客製化串接其它軟體"><span class="octicon octicon-link"></span></a>5.2.1.2 Component Editor內層(客製化串接其它軟體)</h4><p><code>VisualDOC</code>是一個通用型的最佳化軟體，所以也提供了使用者串接<code>Script</code>及軟體的接口。你也可以使用<code>*.exe</code>、本機<code>Python</code>環境，或是第三方軟體來作為媒介。當串接的是第三方軟體時，通常須要同時利用<code>File I/O</code>加上<code>Executable</code>這兩個<code>component</code>才能完成設定。</p><ul>
<li><code>File I/O</code></li>
<li><code>Executable</code></li>
<li><code>Executable Wrapper</code></li>
<li><code>Shared Library</code></li>
</ul><h4 id="5213-Component-Editor外中層"><a class="anchor hidden-xs" href="#5213-Component-Editor外中層" title="5213-Component-Editor外中層"><span class="octicon octicon-link"></span></a>5.2.1.3 Component Editor外/中層</h4><p><code>Component Editor外層/中層</code>是<code>VisualDOC</code>的核心，能不能得到滿意的答案，取決於是否於此，正確定義問題及挑選適宜的演算法及其參數。</p><p>至於為什麼有個<code>中層</code>呢，是因為有時候可以將一層套進另一層裡，老駱習慣稱這個情形為<code>層中有層</code>。一個常見的應用是，將<code>Design of Experiments</code>當作<code>中層</code>，而<code>Optimization</code>當作<code>外層</code>，如此一來就可以利用<code>VisualDOC</code>針對客製好的<code>DOE</code>來做最佳化。</p><ul>
<li><code>Optimization</code></li>
<li><code>Design of Experiments</code> (<code>DOE</code>)</li>
<li><code>Response Surface Approximated Optimization</code> (<code>RSA</code>)</li>
<li><code>Probabilistic</code></li>
</ul><h4 id="5214-流程控制工具"><a class="anchor hidden-xs" href="#5214-流程控制工具" title="5214-流程控制工具"><span class="octicon octicon-link"></span></a>5.2.1.4 流程控制工具</h4><p><code>流程控制工具</code>屬於比較進階的功能，老駱以後有機會再介紹。</p><ul>
<li><code>If</code></li>
<li><code>While loop</code></li>
<li><code>For loop</code></li>
</ul><h4 id="5215-輔助工具"><a class="anchor hidden-xs" href="#5215-輔助工具" title="5215-輔助工具"><span class="octicon octicon-link"></span></a>5.2.1.5 輔助工具</h4><p>利用拖曳法建模，一定要記得<code>stop</code>，再次提醒…。</p><ul>
<li><code>Message</code></li>
<li><code>File Backup</code></li>
<li><code>Container</code></li>
<li><code>Stop</code></li>
</ul><h4 id="522-快速輸入變數"><a class="anchor hidden-xs" href="#522-快速輸入變數" title="522-快速輸入變數"><span class="octicon octicon-link"></span></a>5.2.2 快速輸入變數</h4><p><code>Component Editor外/中/內三層</code>輸入變數的方式及相關設定很直觀。</p><p>老駱這邊提供兩個快速設定變數的方法。</p><h4 id="5221-Add-new-data"><a class="anchor hidden-xs" href="#5221-Add-new-data" title="5221-Add-new-data"><span class="octicon octicon-link"></span></a>5.2.2.1 Add new data</h4><p><code>Add new data</code> 方便新增單一變數。</p><p>例如要新增一個<code>test_input</code>的<code>scalar</code> <code>input</code>變數。<br>
可以，先按下<code>Add new data</code>，輸入變數名<code>test_input</code>，按下<code>Next</code>。</p><p><img src="/assets/img/vrand_vdoc/ch0/201_component_editor.jpg" alt="201_component_editor"></p><p>再按下<code>Finish</code>。</p><p><img src="/assets/img/vrand_vdoc/ch0/202_component_editor.jpg" alt="202_component_editor"></p><p>這樣就創建完成。</p><p><img src="/assets/img/vrand_vdoc/ch0/203_component_editor.jpg" alt="203_component_editor"></p><h4 id="5222-Component-Data-Generator"><a class="anchor hidden-xs" href="#5222-Component-Data-Generator" title="5222-Component-Data-Generator"><span class="octicon octicon-link"></span></a>5.2.2.2 Component Data Generator</h4><p><code>Component Data Generator</code>適用於:</p><ul>
<li>大規模的建立變數及賦值</li>
<li>大規模的修改變數及其值</li>
</ul><p>舉例來說，如果要建造<code>w1~w5</code> <code>5</code>個<code>input</code>變數，並將各變數的<code>Lower Bound</code>設為<code>2</code>，<code>Upper Bound</code>設為<code>4</code>及<code>Initial Value</code>設為<code>2</code>，可以在<code>create panel</code>下這樣設定。</p><p><img src="/assets/img/vrand_vdoc/ch0/204_component_editor.jpg" alt="204_component_editor"></p><p>按下<code>Create Variables</code>即創建完成。</p><p><img src="/assets/img/vrand_vdoc/ch0/205_component_editor.jpg" alt="205_component_editor"></p><p>假如要將變數名改為<code>a101~a105</code>，並將各變數的<code>Lower Bound</code>設為<code>20</code>，<code>Upper Bound</code>設為<code>40</code>及<code>Initial Value</code>設為<code>30</code>，可以在<code>Modify panel</code>下這樣設定(輸入好數字後，請記得按下旁邊的<code>set</code>或<code>Rename</code>按鍵，<code>VisualDOC</code>才會更新變數)。</p><p><img src="/assets/img/vrand_vdoc/ch0/206_component_editor.jpg" alt="206_component_editor"></p><p>變數即修改完成。</p><p><img src="/assets/img/vrand_vdoc/ch0/207_component_editor.jpg" alt="207_component_editor"></p><h3 id="53-Data-Linker"><a class="anchor hidden-xs" href="#53-Data-Linker" title="53-Data-Linker"><span class="octicon octicon-link"></span></a>5.3. Data Linker</h3><p><code>Data Linker</code>是一個建立<code>Component Editor外/中層</code>及<code>Component Editor內層</code>溝通的橋粱。一般來說<code>外/中/內三層</code>的變數名最好設為一樣，但有時候因為建模的方便性或是想讓最後輸出的變數名有較好的辨識度時，各層變數名可能會不一致。此時，須要利用<code>Data Linker</code>連接各層變數。</p><p>如果<code>外/中/內三層</code>的各個變數皆相同，則可以利用左側的<code>Automatically add data to the selected model</code>來自動連接。</p><div class="alert alert-warning">
<p><img alt=":flashlight:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/flashlight.png" title=":flashlight:"> 請記得要先按旁邊綠色橢圓圈起來的<code>Component Editor外/中層</code>，<code>Automatically add data to the selected model</code>這個按鈕才會有作用。</p>
</div><p><img src="/assets/img/vrand_vdoc/ch0/301_data_linker.jpg" alt="301_data_linker"></p><p>設定完成後，可以藉由旁邊的表格來觀察<code>Data Linker</code>的連接狀態。</p><p><img src="/assets/img/vrand_vdoc/ch0/302_data_linker.jpg" alt="302_data_linker"></p><p>一般來說，設定問題時，會先依照<a href="#52-Component-Editor">5.2 Component Editor</a>所述，設定好<code>Component Editor</code>，再來設定<code>Data Linker</code>。但如果如果遇到變數名一樣的問題時，可以考慮先設定<code>Component Editor內層</code>，接著就設定<code>Data Linker</code>。因為如果先進行<code>Data Linker</code>中的<code>Automatically add data to the selected model</code>，<code>VisualDOC</code>將會自動將<code>Component Editor內層</code>設立的變數傳送到<code>Component Editor外/中層</code>，可以省去建立參數的功夫，專注於其它的設定。</p><p>另外要注意的是，如果選擇先手動建立<code>Component Editor外/中層</code>，那麼就無法使用<code>Data Linker</code>中的<code>Automatically add data to the selected model</code>的功能，須要手動連接各個變數之間的關係。</p><p>最後，如果模型只有<code>外/內兩層</code>，<code>Data Linker</code>僅須設定一次；但若模型<br>
是有<code>外/中/內三層</code>，那麼<code>Data Linker</code>須要設定兩次，一次是<code>外層</code>與<code>中層</code>的連接，一次是<code>中層</code>與<code>內層</code>的連接。</p><div class="alert alert-warning">
<p><img alt=":flashlight:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/flashlight.png" title=":flashlight:"> 連接時，請使用以<code>箭頭</code>連到<code>箭頭</code>的方式操作(避免<code>變數</code>直接連到<code>變數</code>)，比較容易成功。</p>
</div><h3 id="54-Simulation-Monitors"><a class="anchor hidden-xs" href="#54-Simulation-Monitors" title="54-Simulation-Monitors"><span class="octicon octicon-link"></span></a>5.4 Simulation Monitors</h3><p><code>Simulation Monitors</code>是很好的視覺化輔助工具，但不是必要的設置。如果使用者覺得<a href="#55-Post-Processing">5.5 Post Processing</a>預先建立好的模板結果已經能提供足夠的資訊，那麼即使沒有設置<code>Simulation Monitors</code>，<code>VisualDOC</code>還是能正確執行。</p><p><code>BestObjetive</code>及<code>WrostConstraint</code>是在做<code>optimization</code>時，最常觀察的圖表。</p><p>按兩下<code>Add optimization history monitor</code>，來新增兩個<code>monitor</code>。<br>
連接<code>BestObjetive</code>到<code>Optimization History Monitor 1</code>及<code>WrostConstraint</code>到<code>Optimization History Monitor 2</code>。</p><p><img src="/assets/img/vrand_vdoc/ch0/401_simulation_monitors.jpg" alt="401_simulation_monitors"></p><p>設定完成後，可以藉由旁邊的表格來觀察<code>Simulation Monitors</code>的連接狀態。</p><p><img src="/assets/img/vrand_vdoc/ch0/402_simulation_monitors.jpg" alt="402_simulation_monitors"></p><div class="alert alert-warning">
<p><img alt=":flashlight:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/flashlight.png" title=":flashlight:"> 連接時，請使用以<code>箭頭</code>連到<code>箭頭</code>的方式操作(避免<code>變數</code>直接連到<code>變數</code>)，比較容易成功。</p>
</div><h3 id="55-Post-Processing"><a class="anchor hidden-xs" href="#55-Post-Processing" title="55-Post-Processing"><span class="octicon octicon-link"></span></a>5.5 Post Processing</h3><p><code>Post Processing</code>有<code>6</code>個按鍵。</p><ul>
<li><code>Generate Summary Report</code><br>
提供求解的摘要報告。</li>
</ul><p><img src="/assets/img/vrand_vdoc/ch0/501_post_processing.jpg" alt="501_post_processing"></p><ul>
<li><code>Show Design Points Table</code><br>
顯示出所使用的<code>Deign Points</code>。</li>
</ul><p><img src="/assets/img/vrand_vdoc/ch0/502_post_processing.jpg" alt="502_post_processing"></p><ul>
<li><code>Launch 2D Approximation Viewer</code><br>
做<code>RSA</code>分析時，才能使用此功能，觀察<code>2</code>個變數間的關係。</li>
</ul><p><img src="/assets/img/vrand_vdoc/ch0/503_post_processing.jpg" alt="503_post_processing"></p><ul>
<li><code>Launch 3D Approximation Viewer</code><br>
做<code>RSA</code>分析時，才能使用此功能，觀察<code>3</code>個變數間的關係。</li>
</ul><p><img src="/assets/img/vrand_vdoc/ch0/504_post_processing.jpg" alt="504_post_processing"></p><ul>
<li><code>Launch What-If Post-Processing Tool</code><br>
可以快速概略評估對變數做微小改動時的近似解。</li>
</ul><p><img src="/assets/img/vrand_vdoc/ch0/505_post_processing.jpg" alt="505_post_processing"></p><ul>
<li><code>Passed/Failed Designed Points Pie Chart</code><br>
可以觀察有多少<code>Deign Points</code>是<code>Failed</code>，代表其傳回值可能是<code>NaN</code>、<code>inf</code>或<code>無效回傳值</code>等。</li>
</ul><p><img src="/assets/img/vrand_vdoc/ch0/506_post_processing.jpg" alt="506_post_processing"></p><h2 id="-6-觀念解說"><a class="anchor hidden-xs" href="#-6-觀念解說" title="-6-觀念解說"><span class="octicon octicon-link"></span></a><img alt=":closed_lock_with_key:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/closed_lock_with_key.png" title=":closed_lock_with_key:"> 6. 觀念解說</h2><h3 id="61-Project-and-Task"><a class="anchor hidden-xs" href="#61-Project-and-Task" title="61-Project-and-Task"><span class="octicon octicon-link"></span></a>6.1 Project and Task</h3><p>每一個檔案(<code>*.vdbx</code>)就是一個<code>project</code>，但一個<code>project</code>裡可以有多個<code>task</code>。每一個<code>task</code>都可以當作是一種分析，所以可以將同一個題目的各種研究主題都放在一個<code>project</code>裡，方便保存。同時，<code>VisualDOC</code>允許使用者從另一個<code>project</code>或同一個<code>project</code>裡的另一個<code>task</code>裡，讀入所需要的資料。</p><p>例如下面這個例子是<code>Advanced Examples Manual</code>第一章的例子。其中<code>task0</code>先做了一個<code>Create DOE points with responses</code>，後面的<code>task3</code>就可以基於此基礎下，繼續做<code>RSA</code>。又例如，<code>task1</code>先做了一個<code>Create DOE with approximations</code>，後面的<code>task2</code>就可以基於此基礎下，繼續做<code>Optimization</code>。</p><p><img src="/assets/img/vrand_vdoc/ch0/901_camel.jpg" alt="901_camel.JPG"></p><h3 id="62-模組化設定"><a class="anchor hidden-xs" href="#62-模組化設定" title="62-模組化設定"><span class="octicon octicon-link"></span></a>6.2 模組化設定</h3><p><code>VisualDOC</code>的每一個<code>component</code>都是模組化的設計，方便使用者可以獨立的讀入或保存。對於一些常用的<code>component</code>，甚至可以先進行客製化的設定後保存起來，於之後的分析重新利用。</p><div class="alert alert-warning">
<p><img alt=":flashlight:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/flashlight.png" title=":flashlight:"> 有時候<code>Component Editor內層</code>及<code>Component Editor外層</code>會長得很像，有些人會覺得重做了一次相同的工作。但其實這樣設計的原意就是模組化，可以將各個<code>component</code>都獨立設定或保存，而不影響其它<code>component</code>。</p>
</div><p>於<code>Work Flow</code>中選取<code>component</code>按右鍵後，選擇<code>save this compoent</code>，可以將其存為一個<code>*.vdoc</code>檔。</p><p><img src="/assets/img/vrand_vdoc/ch0/902_camel.jpg" alt="902_camel.JPG"></p><p>若要讀入這個檔的話，可以從<code>A欄</code>中點選<code>File</code>後，再點選<code>Import Component</code>(另一個方法是點選<code>B欄</code>中的<code>Import Component icon</code>)。</p><p><img src="/assets/img/vrand_vdoc/ch0/903_camel.jpg" alt="903_camel.JPG"></p><h2 id="-7-VisualDOC手冊"><a class="anchor hidden-xs" href="#-7-VisualDOC手冊" title="-7-VisualDOC手冊"><span class="octicon octicon-link"></span></a><img alt=":books:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/books.png" title=":books:"> 7. VisualDOC手冊</h2><p><code>VisualDOC</code>安裝後，有幾本內建的手冊可以供使用者參考。</p><ul>
<li>
<p><code>Getting Started Examples Manual</code><br>
提供一些基礎的操作及例題說明，適合剛開始接觸<code>VisualDOC</code>的使用者閱讀。</p>
</li>
<li>
<p><code>User's Manual</code><br>
詳細說明<code>VisualDOC</code>各個按鍵如何使用，可以在操作遇到疑問或不確定時查找。</p>
</li>
<li>
<p><code>Advanced Examples Manual</code><br>
說明如何利用<code>VisualDOC</code>進行進階的分析，適合當作字典來查找所需要的分析類型。</p>
</li>
<li>
<p><code>Theory Manual</code><br>
提供簡短的理論說明。如果沒心力閱讀整本 <ins><a href="http://www.vrand.com/products/multidiscipline-design-optimization/" target="_blank" rel="noopener">Multidiscipline Design Optimization</a></ins> 的話，這本手冊是一個很好的導論(僅86頁)。</p>
</li>
</ul><h2 id="-8-合作夥伴推薦"><a class="anchor hidden-xs" href="#-8-合作夥伴推薦" title="-8-合作夥伴推薦"><span class="octicon octicon-link"></span></a><img alt=":electric_plug:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/electric_plug.png" title=":electric_plug:"> 8. 合作夥伴推薦</h2><p>總部位於英國的 <ins><a href="http://www.grm-consulting.co.uk" target="_blank" rel="noopener">GRM Consulting</a></ins> ，除了是一家專業的<code>CAE</code>顧問公司外，也是<code>VR&amp;D</code>長期的合作夥伴，創辦人為<code>Mr. Martin Gambling</code>。<code>GRM Consulting</code>為<code>Design Studio</code>開發了不少<code>Plug-in</code>，特別是在複材設定方面，可以大幅減少設定的時間。此外，其獨家開發的 <ins><a href="http://www.grm-consulting.co.uk/presentation-grm-ot-rdm" target="_blank" rel="noopener">Reinforcement Derivation Method(RDM)</a></ins> 技術利用<code>GENESIS</code>找出在給定想增加的質量下，如何最有效率的分配這些質量於模型中進行頻率、強度或碰撞性能等補強，且操作起來相當簡單，老駱個人給予這方法很高的評價。</p><iframe width="662" height="371" src="https://www.youtube.com/embed/68DHHAVDaHk" allowfullscreen=""></iframe><h2 id="-9-本系列文使用之軟硬體"><a class="anchor hidden-xs" href="#-9-本系列文使用之軟硬體" title="-9-本系列文使用之軟硬體"><span class="octicon octicon-link"></span></a><img alt=":computer:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/computer.png" title=":computer:">  9. 本系列文使用之軟硬體</h2><p>老駱使用<code>GIGABYTE</code>的<code>P15</code>筆電作為本系列文的測試環境。</p><ul>
<li><code>CPU</code> : i7-6700HQ</li>
<li><code>Memory</code> : DD3L 8G</li>
<li><code>OS</code> : Windpws 10 Home</li>
<li><code>Python(Anoconda3)</code> : version 3.7.3</li>
<li><code>NumPy</code> : version 1.16.4</li>
<li><code>SciPy</code> : version 1.2.1</li>
<li><code>VisualDOC</code> : version 10.0</li>
<li><code>LS-DYNA</code> : smp single precison version 10.1</li>
<li><code>LS-OPT</code> : version 6.0.0</li>
</ul><h2 id="-10-聯絡老駱"><a class="anchor hidden-xs" href="#-10-聯絡老駱" title="-10-聯絡老駱"><span class="octicon octicon-link"></span></a><img alt=":mailbox:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/mailbox.png" title=":mailbox:">  10. 聯絡老駱</h2><div class="alert alert-info">
<p>如果您或貴單位:</p>
<ul>
<li>有導入<code>VR&amp;D</code>產品的意願，但是有報價、採購及發票等問題</li>
<li>有教育訓練或顧問需求</li>
<li>有些建言指教</li>
<li>想交個朋友<br>
歡迎透過 <img alt=":camel:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/camel.png" title=":camel:"> <ins><a href="mailto:camel@caeml.ai" target="_blank" rel="noopener">camel@caeml.ai</a></ins> 聯絡老駱。</li>
</ul>
</div>
</div>
</body>


