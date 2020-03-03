---
layout: post
title: DOT_00_Introduction
categories:
  - Cae
tags:
  - Cae
  - Vrand
  - DOT
  - Optimization
excerpt: "DOT最佳化運算子介紹。<br/>"
---

<body>
    <div id="doc" class="markdown-body container-fluid comment-enabled" data-hard-breaks="true" style="position: relative;"><h2 id="-0-目錄"><a class="anchor hidden-xs" href="#-0-目錄" title="-0-目錄"><span class="octicon octicon-link"></span></a><img class="emoji" alt=":bulb:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/bulb.png"> 0. 目錄</h2><p><span class="toc"><ul>
<li><a href="#DOT_00_Introduction" title="DOT_00_Introduction">DOT_00_Introduction</a><ul>
<li><a href="#-0-目錄" title=" 0. 目錄"> 0. 目錄</a></li>
<li><a href="#-1-聲明" title=" 1. 聲明"> 1. 聲明</a></li>
<li><a href="#-2-DOT介紹" title=" 2. DOT介紹"> 2. DOT介紹</a></li>
<li><a href="#-3-利用Python呼叫DOT" title=" 3. 利用Python呼叫DOT"> 3. 利用Python呼叫DOT</a></li>
<li><a href="#-4-DOT範例" title=" 4. DOT範例"> 4. DOT範例</a></li>
<li><a href="#-5本文使用之軟硬體" title="  5.本文使用之軟硬體">  5.本文使用之軟硬體</a></li>
<li><a href="#-6-聯絡老駱" title="  6. 聯絡老駱">  6. 聯絡老駱</a></li>
</ul>
</li>
</ul>
</span></p>

<h2 id="-1-聲明"><a class="anchor hidden-xs" href="#-1-聲明" title="-1-聲明"><span class="octicon octicon-link"></span></a><img class="emoji" alt=":mega:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/mega.png"> 1. 聲明</h2><div class="alert alert-info">
<ul>
<li><code>DOT</code>及其編寫之<a href="#-7-VisualDOC%E6%89%8B%E5%86%8A">手冊</a>皆屬<code>VR&amp;D</code>財產。</li>
<li>本文目的為讓初學者能快速認識<code>DOT</code>。文中所有引用及軟體截圖，業已經過<code>VR&amp;D</code>授權使用。</li>
<li>您可以在 <ins><a href="https://www.vrand.com/" target="_blank" rel="noopener">VR&amp;D官網</a></ins> 找到其相關產品及聯絡方式。。</li>
<li><img class="emoji" alt=":tada:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/tada.png"> 特別感謝<code>VR&amp;D</code> <code>President/COO Mr. Juan Pablo Leiva</code>免費提供老駱<code>DOT</code> trial license作學習之用，並於過程中持續提供技術支援。</li>
</ul>
</div><h2 id="-2-DOT介紹"><a class="anchor hidden-xs" href="#-2-DOT介紹" title="-2-DOT介紹"><span class="octicon octicon-link"></span></a><img class="emoji" alt=":earth_americas:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/earth_americas.png"> 2. DOT介紹</h2><p>於 <ins><a href="{% post_url 2019-12-17-VDOC_01_PythonEquation %}" target="_blank" rel="noopener">Vrand_VisualDOC_Ch0_Introduction</a></ins> 中老駱提到<code>VR&amp;D</code>旗下有兩條主要產品線，<ins><a href="https://www.vrand.com/products/genesis/" target="_blank" rel="noopener">GENESIS</a></ins> 及 <ins><a href="https://www.vrand.com/products/visualdoc/" target="_blank" rel="noopener">VisualDOC</a></ins>。</p><p>其實兩個產品背後所呼叫的程式為以<code>Fortran 77</code>的最佳化運算子<code>DOT</code>及<code>BIGDOT</code>。如果<code>Design Variable</code>數量在一兩千以下，可以呼叫<code>DOT</code>來計算，如果<code>Design Variable</code>數量在百萬級別以上，則比較適合呼叫<code>BIGDOT</code>，特別是<code>Topology</code>時。</p><p>以下是老駱與<code>Mr. Juan Pablo Leiva</code>討論時的部份內容。</p><blockquote style="border-left-color: rgb(144, 123, 247);">
<p>DOT works well for problems with 100s variables, for 1000s still work but start to consume computer resources. BIGDOT was developed for problems like Topology were you need millions of design variablies.<small><i class="fa fa-user"></i><br/>Mr. Juan Pablo Leiva</small><span class="color" data-color="#907bf7"></span></p>
</blockquote><h2 id="-3-利用Python呼叫DOT"><a class="anchor hidden-xs" href="#-3-利用Python呼叫DOT" title="-3-利用Python呼叫DOT"><span class="octicon octicon-link"></span></a><img class="emoji" alt=":battery:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/battery.png"> 3. 利用Python呼叫DOT</h2><p>基本上，<code>DOT</code>應該可以與各種程式語言串接。<code>Prof Gerhard Venter</code>於<a href="https://github.com/MODRG/DOTWrapper" target="_blank" rel="noopener">Github中開發了DOTWrapper</a>，讓我們可以方便使用<code>Python</code>來呼叫<code>DOT</code>。此外，老駱將其略為修改為<a href="https://github.com/CamelCMA/DOTWrapper/" target="_blank" rel="noopener">個人比較容易操作的格式</a>，但參數定義皆相同。這邊須要注意的是，<code>DOT</code>其實有內建的<code>JWRITE</code>參數，可以將求解過程輸出至檔案中，但老駱覺得這樣設定比較麻煩。所以選擇於每次求解時直接儲存資訊。</p><p>以下說明利用<code>Python</code>呼叫<code>DOT</code>求解最佳化問題的<code>4</code>個步驟:</p><ol>
<li>將想求解問題的<code>Objective function</code>及<code>Constraint(s)</code>定義於<code>myEvaluate</code>的函數中。</li>
<li>設定<code>nDvar</code>為待求解<code>Design variable(s)</code>數量，而<code>nCons</code>為<code>Constraint(s)</code>數量。<code>nDvar</code>及<code>nCons</code>須設為整數。</li>
<li>設定<code>x</code>為<code>Design variable(s)</code>的初始值，而<code>xl</code>及<code>xu</code>為其上下限。<code>x</code>、<code>xl</code>及<code>xu</code>須設為<code>Numpy array</code>。</li>
<li>定義<code>DOT</code>求解參數，並呼叫<code>DOT</code>進行求解。</li>
</ol><p><code>DOT</code>雖然有很多參數，但是一般使用下，使用者幾乎不須要調整這些參數，即可以得到不錯的結果。</p><p>通常使用者僅須調整<code>MINMAX</code>、<code>METHOD</code>及<code>IPRINT</code>這<code>3</code>個參數，對應我們的<code>Wrapper</code>,即為<code>nMinMax</code>、<code>nMethod</code>及<code>nPrint</code>。</p><ul>
<li><code>nMinMax</code>為控制求解問題是<code>最小化</code>或是<code>最大化</code>的參數。
<ul>
<li><code>nMinMax</code>為<code>-1</code>或<code>0</code>，則設定此問題為最小化問題。</li>
<li><code>nMinMax</code>為<code>1</code>，則設定此問題為最大化問題。</li>
</ul>
</li>
<li><code>nMethod</code>則是控制求解問題演算法的參數。
<ul>
<li>如果是有給定<code>Constraint(s)</code>的最佳化問題:
<ul>
<li>當<code>METHOD</code>為<code>1</code>，則呼叫<code>the Modified Method of Feasible Directions(MMFD)</code>。</li>
<li>當<code>METHOD</code>為<code>2</code>，則呼叫<code>Sequential Linear Programming method(SLP)</code>。</li>
<li>當<code>METHOD</code>為<code>3</code>，則呼叫<code>Sequential Quadratic Programming method(SQP)</code>。</li>
</ul>
</li>
<li>如果是沒有給定<code>Constraint(s)</code>的最佳化問題:
<ul>
<li>當<code>METHOD</code>為<code>0</code>或<code>1</code>時，則呼叫<code>BFGS algorithm</code>。</li>
<li>當<code>METHOD</code>為<code>2</code>時，則呼叫<code>FletcherReeves algorithm</code>。</li>
</ul>
</li>
</ul>
</li>
<li><code>nPrint</code>是控制求解過程輸出的參數。
<ul>
<li>可以設定為<code>0</code>~<code>7</code>。數字越高代表越詳細的輸出，一般推薦將<code>nPrint</code>設為<code>3</code>。</li>
</ul>
</li>
</ul><h2 id="-4-DOT範例"><a class="anchor hidden-xs" href="#-4-DOT範例" title="-4-DOT範例"><span class="octicon octicon-link"></span></a><img class="emoji" alt=":mag_right:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/mag_right.png"> 4. DOT範例</h2><p>這邊老駱使用<a href="https://github.com/CamelCMA/DOTWrapper/" target="_blank" rel="noopener">自己修改的Wrapper</a>說明<code>DOT 5.X Manual</code>裡<code>Sec4.2</code>的<code>Box Design</code>問題。</p><pre><code class="python hljs"><div class="wrapper"><div class="gutter linenumber"><span data-linenumber="1"></span>
<span data-linenumber="2"></span>
<span data-linenumber="3"></span>
<span data-linenumber="4"></span>
<span data-linenumber="5"></span>
<span data-linenumber="6"></span>
<span data-linenumber="7"></span>
<span data-linenumber="8"></span>
<span data-linenumber="9"></span>
<span data-linenumber="10"></span>
<span data-linenumber="11"></span>
<span data-linenumber="12"></span>
<span data-linenumber="13"></span>
<span data-linenumber="14"></span>
<span data-linenumber="15"></span>
<span data-linenumber="16"></span>
<span data-linenumber="17"></span>
<span data-linenumber="18"></span>
<span data-linenumber="19"></span>
<span data-linenumber="20"></span>
<span data-linenumber="21"></span>
<span data-linenumber="22"></span>
<span data-linenumber="23"></span>
<span data-linenumber="24"></span>
<span data-linenumber="25"></span>
<span data-linenumber="26"></span>
<span data-linenumber="27"></span>
<span data-linenumber="28"></span>
<span data-linenumber="29"></span>
<span data-linenumber="30"></span>
<span data-linenumber="31"></span>
<span data-linenumber="32"></span></div><div class="code"><span class="hljs-keyword">from</span> dot <span class="hljs-keyword">import</span> Dot
<span class="hljs-keyword">import</span> numpy <span class="hljs-keyword">as</span> np
<span class="hljs-keyword">import</span> math

<span class="hljs-function"><span class="hljs-keyword">def</span> <span class="hljs-title">myEvaluate</span><span class="hljs-params">(x, obj, g, param)</span>:</span>
    h, w, d = x[<span class="hljs-number">0</span>], x[<span class="hljs-number">1</span>], x[<span class="hljs-number">2</span>]

    obj.value = <span class="hljs-number">2.0</span> * (h * w + h * d + <span class="hljs-number">2.0</span> * w * d) + <span class="hljs-number">1.25</span> * h / <span class="hljs-number">12.0</span>

    g[<span class="hljs-number">0</span>] = <span class="hljs-number">1.0</span> - h * w * d / <span class="hljs-number">2.</span>

nDvar = <span class="hljs-number">3</span>  <span class="hljs-comment"># Number of design variables</span>
nCons = <span class="hljs-number">1</span>  <span class="hljs-comment"># Number of constraints</span>

<span class="hljs-comment"># Set the initial values and upper and lower bounds for the design variables</span>
x = np.ones(nDvar, float) * <span class="hljs-number">1.0</span>
xl = np.ones(nDvar, float) * <span class="hljs-number">0.001</span>
xu = np.ones(nDvar, float) * <span class="hljs-number">100.00</span>

<span class="hljs-comment"># Append different DOT instances into a list</span>
models = []
models.append(Dot(nMethod=<span class="hljs-number">1</span>, nPrint=<span class="hljs-number">0</span>))
models.append(Dot(nMethod=<span class="hljs-number">2</span>, nPrint=<span class="hljs-number">0</span>))
models.append(Dot(nMethod=<span class="hljs-number">3</span>, nPrint=<span class="hljs-number">0</span>))

<span class="hljs-keyword">for</span> model <span class="hljs-keyword">in</span> models:
    <span class="hljs-comment"># model.print_init()</span>
    model.fit(x=x, xl=xl, xu=xu, nCons=nCons, evalfunc=myEvaluate)
    model.print_info()

<span class="hljs-keyword">for</span> model <span class="hljs-keyword">in</span> models:
    model.plot_fig(is_savefig=<span class="hljs-keyword">True</span>)
</div></div></code></pre><p>依照先前提到的<code>4</code>個步驟定義問題:</p><ol>
<li><code>Line5~10</code> : 於<code>myEvaluate</code>中，將<code>3</code>個<code>Design Variables</code> <code>h</code>,<code>w</code>及<code>d</code>分別指定為<code>x[0]</code>, <code>x[1]</code>及<code>x[2]</code>。接著利用這些<code>Design Variables</code>來建構<code>Onjective function</code>及<code>Constraint</code>。</li>
<li><code>Line12~13</code> : 指定<code>nDvar = 3</code>(因為有<code>3</code>個<code>Design Variables</code>)，並指定<code>nCons = 1</code>(因為有<code>1</code>個<code>Constraint</code>)。</li>
<li><code>Line16~18</code> : 指定<code>3</code>個<code>Design Variables</code>的初始值為<code>1.0</code>，下限為<code>0.001</code>，上限為<code>100.00</code>。</li>
<li><code>Line21~32</code> : 定義<code>3</code>個使用不同<code>nMthod</code>的模型。另外，<code>nMinMax</code>其<code>default</code>為<code>0</code>，即最小化問題，不須設置。<code>nPrint</code>則設為常用的<code>3</code>。接著:
<ul>
<li>呼叫<code>fit</code>方法串接<code>DOT</code>進行運算。</li>
<li>呼叫<code>print_info</code>方法，將初始及最佳結果輸出於營幕上。此時，若搭配將<code>nPrint</code>設為<code>0</code>，則營幕上僅會輸出初始及最佳結果，適合<code>Debug</code>時使用。</li>
<li>呼叫<code>plot_fig</code>方法，利用<code>matplotlib</code>繪製求解過程，並使用<code>is_savefig=True</code>將所匯圖檔存為<code>*.png</code>檔。</li>
</ul>
</li>
</ol><p><img src="/assets/img/vrand_dot/ch0/51_nMinMax_0_nMethod_1.png" alt="51_nMinMax_0_nMethod_1"></p><p><img src="/assets/img/vrand_dot/ch0/61_nMinMax_0_nMethod_2.png" alt="61_nMinMax_0_nMethod_2"></p><p><img src="/assets/img/vrand_dot/ch0/71_nMinMax_0_nMethod_3.png" alt="71_nMinMax_0_nMethod_3"></p><p>將求解結果表列如下:</p><table>
<thead>
<tr>
<th style="text-align:center">Parameter</th>
<th style="text-align:center">Initial value</th>
<th style="text-align:center">nMethod=1</th>
<th style="text-align:center">nMethod=2</th>
<th style="text-align:center">nMethod=3</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center"><code>H</code></td>
<td style="text-align:center">1.00000E+00</td>
<td style="text-align:center">1.93192E+00</td>
<td style="text-align:center">1.94269E+00</td>
<td style="text-align:center">2.13252E+00</td>
</tr>
<tr>
<td style="text-align:center"><code>W</code></td>
<td style="text-align:center">1.00000E+00</td>
<td style="text-align:center">1.01727E+00</td>
<td style="text-align:center">1.00799E+00</td>
<td style="text-align:center">9.68432E-01</td>
</tr>
<tr>
<td style="text-align:center"><code>D</code></td>
<td style="text-align:center">1.00000E+00</td>
<td style="text-align:center">1.01727E+00</td>
<td style="text-align:center">1.02126E+00</td>
<td style="text-align:center">9.68432E-01</td>
</tr>
<tr>
<td style="text-align:center"><code>Obj</code></td>
<td style="text-align:center">8.10417E+00</td>
<td style="text-align:center">1.22018E+01</td>
<td style="text-align:center">1.22045E+01</td>
<td style="text-align:center">1.22344E+01</td>
</tr>
<tr>
<td style="text-align:center"><code>Max G</code></td>
<td style="text-align:center">5.00000E-01</td>
<td style="text-align:center">3.81227E-04</td>
<td style="text-align:center">7.35958E-01</td>
<td style="text-align:center">-1.55971E-06</td>
</tr>
<tr>
<td style="text-align:center"><code>Function calls</code></td>
<td style="text-align:center">N/A</td>
<td style="text-align:center">55</td>
<td style="text-align:center">65</td>
<td style="text-align:center">68</td>
</tr>
</tbody>
</table><div class="alert alert-warning">
<p><img class="emoji" alt=":flashlight:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/flashlight.png"> 其實此例題也可以利用<code>VisualDOC</code>進行求解，畢竟<code>VisualDOC</code>也是依靠<code>DOT</code>或<code>BIGDOT</code>做為最佳化運算子。詳細設定請參考<a href="https://caeml.ai/tags.html#visualdoc" target="_blank" rel="noopener">VisualDOC系列文</a>。</p>
</div><h2 id="-5本文使用之軟硬體"><a class="anchor hidden-xs" href="#-5本文使用之軟硬體" title="-5本文使用之軟硬體"><span class="octicon octicon-link"></span></a><img class="emoji" alt=":computer:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/computer.png">  5.本文使用之軟硬體</h2><p>老駱使用<code>GIGABYTE</code>的<code>P15</code>筆電作為本文的測試環境。</p><ul>
<li><code>CPU</code> : i7-6700HQ</li>
<li><code>Memory</code> : DD3L 8G</li>
<li><code>OS</code> : Windpws 10 Home</li>
<li><code>Python(Anoconda3)</code> : version 3.7.3</li>
<li><code>NumPy</code> : version 1.16.4</li>
<li><code>Matplotlib</code> : version 3.1.0</li>
<li><code>VisualDOC</code> : version 10.0</li>
<li><code>DOT</code> : version 7.2</li>
</ul><h2 id="-6-聯絡老駱"><a class="anchor hidden-xs" href="#-6-聯絡老駱" title="-6-聯絡老駱"><span class="octicon octicon-link"></span></a><img class="emoji" alt=":mailbox:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/mailbox.png">  6. 聯絡老駱</h2><div class="alert alert-info">
<p>如果您或貴單位:</p>
<ul>
<li>有導入<code>VR&amp;D</code>產品的意願，但是有報價、採購及發票等問題</li>
<li>有教育訓練或顧問需求</li>
<li>有些建言指教</li>
<li>想交個朋友<br>
歡迎透過 <img class="emoji" alt=":camel:" src="https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/camel.png"> <ins><a href="mailto:camel@caeml.ai" target="_blank" rel="noopener">camel@caeml.ai</a></ins> 聯絡老駱。</li>
</ul>
</div>
</div>
</body>
