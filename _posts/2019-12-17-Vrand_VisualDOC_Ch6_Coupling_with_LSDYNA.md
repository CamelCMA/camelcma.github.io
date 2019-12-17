---
layout: post
title: Vrand_VisualDOC_Ch6_Coupling_with_LSDYNA
categories:
  - Vrand
tags:
  - Cae
  - Vrand
  - VisualDOC
  - Optimization
  - LSDYNA
  - LSOPT
excerpt_separator: <!--more-->
---

<body>
    <div id="doc" class="markdown-body container-fluid comment-enabled" data-hard-breaks="true" style="position: relative;"><h2 id="-0-目錄"><a class="anchor hidden-xs" href="#-0-目錄" title="-0-目錄"><span class="octicon octicon-link"></span></a><img alt=":bulb:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/bulb.png" title=":bulb:"> 0. 目錄</h2><p><span class="toc"><ul>
<li><a href="#Vrand_VisualDOC_Ch6_Coupling_with_LSDYNA" title="Vrand_VisualDOC_Ch6_Coupling_with_LSDYNA">Vrand_VisualDOC_Ch6_Coupling_with_LSDYNA</a><ul>
<li><a href="#-0-目錄" title=" 0. 目錄"> 0. 目錄</a></li>
<li><a href="#-1-老駱提醒" title=" 1. 老駱提醒"> 1. 老駱提醒</a></li>
<li><a href="#-2-問題描述" title=" 2. 問題描述"> 2. 問題描述</a></li>
<li><a href="#-3-前置作業" title=" 3. 前置作業"> 3. 前置作業</a><ul>
<li><a href="#31-LS-DYNA-K檔修改" title="3.1 LS-DYNA K檔修改">3.1 LS-DYNA K檔修改</a></li>
</ul>
</li>
<li><a href="#-4-LS-OPT" title=" 4. LS-OPT"> 4. LS-OPT</a></li>
<li><a href="#-5-VisualDOC操作細節" title=" 5. VisualDOC操作細節"> 5. VisualDOC操作細節</a><ul>
<li><a href="#51-Optimization" title="5.1 Optimization">5.1 Optimization</a></li>
<li><a href="#52-DOE" title="5.2 DOE">5.2 DOE</a></li>
<li><a href="#53-Optimization-Using-DOE" title="5.3 Optimization Using DOE">5.3 Optimization Using DOE</a></li>
<li><a href="#54-RSA-Using-DOE" title="5.4 RSA Using DOE">5.4 RSA Using DOE</a></li>
</ul>
</li>
<li><a href="#-6-結語" title=" 6. 結語"> 6. 結語</a></li>
<li><a href="#-7-聯絡老駱" title="  7. 聯絡老駱">  7. 聯絡老駱</a></li>
</ul>
</li>
</ul>
</span></p>

<!--more-->

<h2 id="-1-老駱提醒"><a class="anchor hidden-xs" href="#-1-老駱提醒" title="-1-老駱提醒"><span class="octicon octicon-link"></span></a><img alt=":mega:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/mega.png" title=":mega:"> 1. 老駱提醒</h2><div class="alert alert-info">
<ul>
<li>請先確認，您已經閱讀 <ins><a href="{% post_url 2019-12-17-Vrand_VisualDOC_Ch0_Introduction %}" target="_blank" rel="noopener">Vrand_VisualDOC_Ch0_Introduction</a></ins> 中的聲明。</li>
<li>本文例題修改自 <ins><a href="https://www.lsoptsupport.com" target="_blank" rel="noopener">LS-OPT Support</a></ins> ，版權屬於該網站。</li>
<li>本文篇幅較長，但如果能融會貫通，相信您已經可以依樣畫葫蘆，連接你想要的程式至<code>VisualDOC</code>。</li>
<li>如果對不熟或沒接觸過<code>LS-DYNA</code>的朋友，閱讀本文可能會有些吃力。</li>
<li>如果對接觸過<code>LS-DYNA</code>但對<code>LS-OPT</code>不熟悉的朋友，可以跳過相關內容。利用<code>LS-OPT</code>求解的用意是，在於提供一個可與<code>VisualDOC</code>比較的參考答案，並不在具體上比較兩者優劣。目前老駱暫時沒有寫<code>LS-OPT</code>介紹的計畫，但如果您有興趣想了解，可以透過 <img alt=":camel:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/camel.png" title=":camel:"> <ins><a href="mailto:camel@caeml.ai" target="_blank" rel="noopener">camel@caeml.ai</a></ins> 聯絡老駱。如果有一定人數來信的話，老駱可以規劃一個<code>LS-OPT</code>的系列教學文。老駱認為<code>LS-OPT</code>的原理相當類似於<code>VisualDOC</code>裡<code>RSA</code> + <code>DOE</code>的概念。</li>
<li>在<code>Windows</code>環境下，使用<code>LS-OPT version 6.0.0</code>時，如果在<code>Setup</code>內，新增一變數，並手動輸入變數名超過兩個字元，程式會當掉。老駱已經有回報原廠，相信未來版次會修復。</li>
</ul>
</div><h2 id="-2-問題描述"><a class="anchor hidden-xs" href="#-2-問題描述" title="-2-問題描述"><span class="octicon octicon-link"></span></a><img alt=":question:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/question.png" title=":question:"> 2. 問題描述</h2><p>本文例題修改自 <ins><a href="https://www.lsoptsupport.com/examples/optimization/co/lsopt2010/examples/optimization/co/linear-ten-iteration" target="_blank" rel="noopener">Linear response surface with strategy Sequential with Domain Reduction (SRSM)</a></ins> ，是 <ins><a href="https://www.lsoptsupport.com/examples/optimization/co" target="_blank" rel="noopener">Crashworthiness Optimization</a></ins> 內的一個子題。進入<code>Download</code>，可以下載<code>crash_srsm.zip</code>檔案。</p><p>因為原來的題目內牽涉到<code>HIC</code>的計算，雖然在<code>VisualDOC</code>裡面也可以實現，但本文旨在分享如何結合<code>VisualDOC</code>和<code>LS-DYNA</code>進行計算，所以老駱稍微將題目修改如下:</p><p><code>Minimize Objective Function</code>:<br>
<span class="mathjax"><span class="MathJax_Preview" style="color: inherit;"></span><div class="MathJax_Display" style="text-align: center;"><span class="MathJax" id="MathJax-Element-1-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot; display=&quot;block&quot;><mi>M</mi><mi>a</mi><mi>s</mi><mi>s</mi></math>" role="presentation" style="text-align: center; position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-1" style="width: 2.966em; display: inline-block;"><span style="display: inline-block; position: relative; width: 2.535em; height: 0px; font-size: 116%;"><span style="position: absolute; clip: rect(1.511em, 1002.48em, 2.535em, -999.997em); top: -2.368em; left: 0em;"><span class="mrow" id="MathJax-Span-2"><span class="mi" id="MathJax-Span-3" style="font-family: MathJax_Math-italic;">M<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.11em;"></span></span><span class="mi" id="MathJax-Span-4" style="font-family: MathJax_Math-italic;">a</span><span class="mi" id="MathJax-Span-5" style="font-family: MathJax_Math-italic;">s</span><span class="mi" id="MathJax-Span-6" style="font-family: MathJax_Math-italic;">s</span></span><span style="display: inline-block; width: 0px; height: 2.373em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.059em; border-left: 0px solid; width: 0px; height: 0.941em;"></span></span></nobr><span class="MJX_Assistive_MathML MJX_Assistive_MathML_Block" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><mi>M</mi><mi>a</mi><mi>s</mi><mi>s</mi></math></span></span></div><script type="math/tex; mode=display" id="MathJax-Element-1">
Mass
</script></span></p><p><code>Subject to the Constraint</code>:<br>
<span class="mathjax"><span class="MathJax_Preview" style="color: inherit;"></span><div class="MathJax_Display" style="text-align: center;"><span class="MathJax" id="MathJax-Element-2-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot; display=&quot;block&quot;><mi>I</mi><mi>n</mi><mi>t</mi><mi>r</mi><mi>u</mi><mi>s</mi><mi>i</mi><mi>o</mi><mi>n</mi><mo>&amp;lt;</mo><mn>485</mn><mi>m</mi><mi>m</mi></math>" role="presentation" style="text-align: center; position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-7" style="width: 10.401em; display: inline-block;"><span style="display: inline-block; position: relative; width: 8.947em; height: 0px; font-size: 116%;"><span style="position: absolute; clip: rect(1.511em, 1008.95em, 2.589em, -999.997em); top: -2.368em; left: 0em;"><span class="mrow" id="MathJax-Span-8"><span class="mi" id="MathJax-Span-9" style="font-family: MathJax_Math-italic;">I<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.057em;"></span></span><span class="mi" id="MathJax-Span-10" style="font-family: MathJax_Math-italic;">n</span><span class="mi" id="MathJax-Span-11" style="font-family: MathJax_Math-italic;">t</span><span class="mi" id="MathJax-Span-12" style="font-family: MathJax_Math-italic;">r</span><span class="mi" id="MathJax-Span-13" style="font-family: MathJax_Math-italic;">u</span><span class="mi" id="MathJax-Span-14" style="font-family: MathJax_Math-italic;">s</span><span class="mi" id="MathJax-Span-15" style="font-family: MathJax_Math-italic;">i</span><span class="mi" id="MathJax-Span-16" style="font-family: MathJax_Math-italic;">o</span><span class="mi" id="MathJax-Span-17" style="font-family: MathJax_Math-italic;">n</span><span class="mo" id="MathJax-Span-18" style="font-family: MathJax_Main; padding-left: 0.272em;">&lt;</span><span class="mn" id="MathJax-Span-19" style="font-family: MathJax_Main; padding-left: 0.272em;">485</span><span class="mi" id="MathJax-Span-20" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-21" style="font-family: MathJax_Math-italic;">m</span></span><span style="display: inline-block; width: 0px; height: 2.373em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.122em; border-left: 0px solid; width: 0px; height: 0.941em;"></span></span></nobr><span class="MJX_Assistive_MathML MJX_Assistive_MathML_Block" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><mi>I</mi><mi>n</mi><mi>t</mi><mi>r</mi><mi>u</mi><mi>s</mi><mi>i</mi><mi>o</mi><mi>n</mi><mo>&lt;</mo><mn>485</mn><mi>m</mi><mi>m</mi></math></span></span></div><script type="math/tex; mode=display" id="MathJax-Element-2">
Intrusion < 485mm
</script></span></p><p><code>Design Variables (Side Constraints)</code>:<br>
<span class="mathjax"><span class="MathJax_Preview" style="color: inherit;"></span><div class="MathJax_Display"><span class="MathJax MathJax_FullWidth" id="MathJax-Element-3-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot; display=&quot;block&quot;><mn>1.0</mn><mi>m</mi><mi>m</mi><mo>&amp;lt;</mo><mi>t</mi><mi>b</mi><mi>u</mi><mi>m</mi><mi>p</mi><mi>e</mi><mi>r</mi><mo>&amp;lt;</mo><mn>5.0</mn><mi>m</mi><mi>m</mi><mspace linebreak=&quot;newline&quot; /><mn>1.0</mn><mi>m</mi><mi>m</mi><mo>&amp;lt;</mo><mi>t</mi><mi>h</mi><mi>o</mi><mi>o</mi><mi>d</mi><mo>&amp;lt;</mo><mn>5.0</mn><mi>m</mi><mi>m</mi><mspace linebreak=&quot;newline&quot; /><mn>1.0</mn><mi>m</mi><mi>m</mi><mo>&amp;lt;</mo><mi>t</mi><mi>f</mi><mi>r</mi><mi>o</mi><mi>n</mi><mi>t</mi><mo>&amp;lt;</mo><mn>5.0</mn><mi>m</mi><mi>m</mi><mspace linebreak=&quot;newline&quot; /><mn>1.0</mn><mi>m</mi><mi>m</mi><mo>&amp;lt;</mo><mi>t</mi><mi>u</mi><mi>n</mi><mi>d</mi><mi>e</mi><mi>r</mi><mo>&amp;lt;</mo><mn>5.0</mn><mi>m</mi><mi>m</mi></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-22" style="width: 100%; display: inline-block; min-width: 14.388em;"><span style="display: inline-block; position: relative; width: 100%; height: 0px; font-size: 116%;"><span style="position: absolute; clip: rect(4.744em, 1012.34em, 9.647em, -999.997em); top: -5.601em; left: 0em; width: 100%;"><span class="mrow" id="MathJax-Span-23"><span style="display: inline-block; position: relative; width: 100%; height: 0px;"><span style="position: absolute; clip: rect(3.128em, 1012.34em, 4.367em, -999.997em); top: -3.984em; left: 50%; margin-left: -6.193em;"><span class="mn" id="MathJax-Span-24" style="font-family: MathJax_Main;">1.0</span><span class="mi" id="MathJax-Span-25" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-26" style="font-family: MathJax_Math-italic;">m</span><span class="mo" id="MathJax-Span-27" style="font-family: MathJax_Main; padding-left: 0.272em;">&lt;</span><span class="mi" id="MathJax-Span-28" style="font-family: MathJax_Math-italic; padding-left: 0.272em;">t</span><span class="mi" id="MathJax-Span-29" style="font-family: MathJax_Math-italic;">b</span><span class="mi" id="MathJax-Span-30" style="font-family: MathJax_Math-italic;">u</span><span class="mi" id="MathJax-Span-31" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-32" style="font-family: MathJax_Math-italic;">p</span><span class="mi" id="MathJax-Span-33" style="font-family: MathJax_Math-italic;">e</span><span class="mi" id="MathJax-Span-34" style="font-family: MathJax_Math-italic;">r</span><span class="mo" id="MathJax-Span-35" style="font-family: MathJax_Main; padding-left: 0.272em;">&lt;</span><span class="mn" id="MathJax-Span-36" style="font-family: MathJax_Main; padding-left: 0.272em;">5.0</span><span class="mi" id="MathJax-Span-37" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-38" style="font-family: MathJax_Math-italic;">m</span><span style="display: inline-block; width: 0px; height: 3.99em;"></span></span><span style="position: absolute; clip: rect(3.128em, 1011.1em, 4.205em, -999.997em); top: -2.691em; left: 50%; margin-left: -5.547em;"><span class="mspace" id="MathJax-Span-39" style="height: 0em; vertical-align: 0em; width: 0em; display: inline-block; overflow: hidden;"></span><span class="mn" id="MathJax-Span-40" style="font-family: MathJax_Main;">1.0</span><span class="mi" id="MathJax-Span-41" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-42" style="font-family: MathJax_Math-italic;">m</span><span class="mo" id="MathJax-Span-43" style="font-family: MathJax_Main; padding-left: 0.272em;">&lt;</span><span class="mi" id="MathJax-Span-44" style="font-family: MathJax_Math-italic; padding-left: 0.272em;">t</span><span class="mi" id="MathJax-Span-45" style="font-family: MathJax_Math-italic;">h</span><span class="mi" id="MathJax-Span-46" style="font-family: MathJax_Math-italic;">o</span><span class="mi" id="MathJax-Span-47" style="font-family: MathJax_Math-italic;">o</span><span class="mi" id="MathJax-Span-48" style="font-family: MathJax_Math-italic;">d<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mo" id="MathJax-Span-49" style="font-family: MathJax_Main; padding-left: 0.272em;">&lt;</span><span class="mn" id="MathJax-Span-50" style="font-family: MathJax_Main; padding-left: 0.272em;">5.0</span><span class="mi" id="MathJax-Span-51" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-52" style="font-family: MathJax_Math-italic;">m</span><span style="display: inline-block; width: 0px; height: 3.99em;"></span></span><span style="position: absolute; clip: rect(3.128em, 1011.48em, 4.367em, -999.997em); top: -1.452em; left: 50%; margin-left: -5.762em;"><span class="mspace" id="MathJax-Span-53" style="height: 0em; vertical-align: 0em; width: 0em; display: inline-block; overflow: hidden;"></span><span class="mn" id="MathJax-Span-54" style="font-family: MathJax_Main;">1.0</span><span class="mi" id="MathJax-Span-55" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-56" style="font-family: MathJax_Math-italic;">m</span><span class="mo" id="MathJax-Span-57" style="font-family: MathJax_Main; padding-left: 0.272em;">&lt;</span><span class="mi" id="MathJax-Span-58" style="font-family: MathJax_Math-italic; padding-left: 0.272em;">t</span><span class="mi" id="MathJax-Span-59" style="font-family: MathJax_Math-italic;">f<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.057em;"></span></span><span class="mi" id="MathJax-Span-60" style="font-family: MathJax_Math-italic;">r</span><span class="mi" id="MathJax-Span-61" style="font-family: MathJax_Math-italic;">o</span><span class="mi" id="MathJax-Span-62" style="font-family: MathJax_Math-italic;">n</span><span class="mi" id="MathJax-Span-63" style="font-family: MathJax_Math-italic;">t</span><span class="mo" id="MathJax-Span-64" style="font-family: MathJax_Main; padding-left: 0.272em;">&lt;</span><span class="mn" id="MathJax-Span-65" style="font-family: MathJax_Main; padding-left: 0.272em;">5.0</span><span class="mi" id="MathJax-Span-66" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-67" style="font-family: MathJax_Math-italic;">m</span><span style="display: inline-block; width: 0px; height: 3.99em;"></span></span><span style="position: absolute; clip: rect(3.128em, 1011.64em, 4.205em, -999.997em); top: -0.159em; left: 50%; margin-left: -5.816em;"><span class="mspace" id="MathJax-Span-68" style="height: 0em; vertical-align: 0em; width: 0em; display: inline-block; overflow: hidden;"></span><span class="mn" id="MathJax-Span-69" style="font-family: MathJax_Main;">1.0</span><span class="mi" id="MathJax-Span-70" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-71" style="font-family: MathJax_Math-italic;">m</span><span class="mo" id="MathJax-Span-72" style="font-family: MathJax_Main; padding-left: 0.272em;">&lt;</span><span class="mi" id="MathJax-Span-73" style="font-family: MathJax_Math-italic; padding-left: 0.272em;">t</span><span class="mi" id="MathJax-Span-74" style="font-family: MathJax_Math-italic;">u</span><span class="mi" id="MathJax-Span-75" style="font-family: MathJax_Math-italic;">n</span><span class="mi" id="MathJax-Span-76" style="font-family: MathJax_Math-italic;">d<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mi" id="MathJax-Span-77" style="font-family: MathJax_Math-italic;">e</span><span class="mi" id="MathJax-Span-78" style="font-family: MathJax_Math-italic;">r</span><span class="mo" id="MathJax-Span-79" style="font-family: MathJax_Main; padding-left: 0.272em;">&lt;</span><span class="mn" id="MathJax-Span-80" style="font-family: MathJax_Main; padding-left: 0.272em;">5.0</span><span class="mi" id="MathJax-Span-81" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-82" style="font-family: MathJax_Math-italic;">m</span><span style="display: inline-block; width: 0px; height: 3.99em;"></span></span></span></span><span style="display: inline-block; width: 0px; height: 5.606em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -4.559em; border-left: 0px solid; width: 0px; height: 5.441em;"></span></span></nobr><span class="MJX_Assistive_MathML MJX_Assistive_MathML_Block" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><mn>1.0</mn><mi>m</mi><mi>m</mi><mo>&lt;</mo><mi>t</mi><mi>b</mi><mi>u</mi><mi>m</mi><mi>p</mi><mi>e</mi><mi>r</mi><mo>&lt;</mo><mn>5.0</mn><mi>m</mi><mi>m</mi><mspace linebreak="newline"></mspace><mn>1.0</mn><mi>m</mi><mi>m</mi><mo>&lt;</mo><mi>t</mi><mi>h</mi><mi>o</mi><mi>o</mi><mi>d</mi><mo>&lt;</mo><mn>5.0</mn><mi>m</mi><mi>m</mi><mspace linebreak="newline"></mspace><mn>1.0</mn><mi>m</mi><mi>m</mi><mo>&lt;</mo><mi>t</mi><mi>f</mi><mi>r</mi><mi>o</mi><mi>n</mi><mi>t</mi><mo>&lt;</mo><mn>5.0</mn><mi>m</mi><mi>m</mi><mspace linebreak="newline"></mspace><mn>1.0</mn><mi>m</mi><mi>m</mi><mo>&lt;</mo><mi>t</mi><mi>u</mi><mi>n</mi><mi>d</mi><mi>e</mi><mi>r</mi><mo>&lt;</mo><mn>5.0</mn><mi>m</mi><mi>m</mi></math></span></span></div><script type="math/tex; mode=display" id="MathJax-Element-3">
1.0mm < tbumper < 5.0mm\\
1.0mm < thood < 5.0mm\\
1.0mm < tfront < 5.0mm\\
1.0mm < tunder < 5.0mm
</script></span></p><p><code>Initial Conditions</code>:<br>
<span class="mathjax"><span class="MathJax_Preview" style="color: inherit;"></span><div class="MathJax_Display"><span class="MathJax MathJax_FullWidth" id="MathJax-Element-4-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot; display=&quot;block&quot;><mi>t</mi><mi>b</mi><mi>u</mi><mi>m</mi><mi>p</mi><mi>e</mi><mi>r</mi><mo>=</mo><mi>t</mi><mi>u</mi><mi>p</mi><mi>p</mi><mi>e</mi><mi>r</mi><mo>=</mo><mi>t</mi><mi>f</mi><mi>r</mi><mi>o</mi><mi>n</mi><mi>t</mi><mo>=</mo><mi>t</mi><mi>u</mi><mi>n</mi><mi>d</mi><mi>e</mi><mi>r</mi><mo>=</mo><mn>3</mn><mi>m</mi><mi>m</mi><mspace linebreak=&quot;newline&quot; /></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-83" style="width: 100%; display: inline-block; min-width: 23.009em;"><span style="display: inline-block; position: relative; width: 100%; height: 0px; font-size: 116%;"><span style="position: absolute; clip: rect(3.128em, 1019.83em, 5.337em, -999.997em); top: -3.984em; left: 0em; width: 100%;"><span class="mrow" id="MathJax-Span-84"><span style="display: inline-block; position: relative; width: 100%; height: 0px;"><span style="position: absolute; clip: rect(3.128em, 1019.83em, 4.367em, -999.997em); top: -3.984em; left: 50%; margin-left: -9.911em;"><span class="mi" id="MathJax-Span-85" style="font-family: MathJax_Math-italic;">t</span><span class="mi" id="MathJax-Span-86" style="font-family: MathJax_Math-italic;">b</span><span class="mi" id="MathJax-Span-87" style="font-family: MathJax_Math-italic;">u</span><span class="mi" id="MathJax-Span-88" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-89" style="font-family: MathJax_Math-italic;">p</span><span class="mi" id="MathJax-Span-90" style="font-family: MathJax_Math-italic;">e</span><span class="mi" id="MathJax-Span-91" style="font-family: MathJax_Math-italic;">r</span><span class="mo" id="MathJax-Span-92" style="font-family: MathJax_Main; padding-left: 0.272em;">=</span><span class="mi" id="MathJax-Span-93" style="font-family: MathJax_Math-italic; padding-left: 0.272em;">t</span><span class="mi" id="MathJax-Span-94" style="font-family: MathJax_Math-italic;">u</span><span class="mi" id="MathJax-Span-95" style="font-family: MathJax_Math-italic;">p</span><span class="mi" id="MathJax-Span-96" style="font-family: MathJax_Math-italic;">p</span><span class="mi" id="MathJax-Span-97" style="font-family: MathJax_Math-italic;">e</span><span class="mi" id="MathJax-Span-98" style="font-family: MathJax_Math-italic;">r</span><span class="mo" id="MathJax-Span-99" style="font-family: MathJax_Main; padding-left: 0.272em;">=</span><span class="mi" id="MathJax-Span-100" style="font-family: MathJax_Math-italic; padding-left: 0.272em;">t</span><span class="mi" id="MathJax-Span-101" style="font-family: MathJax_Math-italic;">f<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.057em;"></span></span><span class="mi" id="MathJax-Span-102" style="font-family: MathJax_Math-italic;">r</span><span class="mi" id="MathJax-Span-103" style="font-family: MathJax_Math-italic;">o</span><span class="mi" id="MathJax-Span-104" style="font-family: MathJax_Math-italic;">n</span><span class="mi" id="MathJax-Span-105" style="font-family: MathJax_Math-italic;">t</span><span class="mo" id="MathJax-Span-106" style="font-family: MathJax_Main; padding-left: 0.272em;">=</span><span class="mi" id="MathJax-Span-107" style="font-family: MathJax_Math-italic; padding-left: 0.272em;">t</span><span class="mi" id="MathJax-Span-108" style="font-family: MathJax_Math-italic;">u</span><span class="mi" id="MathJax-Span-109" style="font-family: MathJax_Math-italic;">n</span><span class="mi" id="MathJax-Span-110" style="font-family: MathJax_Math-italic;">d<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mi" id="MathJax-Span-111" style="font-family: MathJax_Math-italic;">e</span><span class="mi" id="MathJax-Span-112" style="font-family: MathJax_Math-italic;">r</span><span class="mo" id="MathJax-Span-113" style="font-family: MathJax_Main; padding-left: 0.272em;">=</span><span class="mn" id="MathJax-Span-114" style="font-family: MathJax_Main; padding-left: 0.272em;">3</span><span class="mi" id="MathJax-Span-115" style="font-family: MathJax_Math-italic;">m</span><span class="mi" id="MathJax-Span-116" style="font-family: MathJax_Math-italic;">m</span><span style="display: inline-block; width: 0px; height: 3.99em;"></span></span><span style="position: absolute; clip: rect(3.828em, 1000em, 4.151em, -999.997em); top: -2.799em; left: 50%; margin-left: 0em;"><span class="mspace" id="MathJax-Span-117" style="height: 0em; vertical-align: 0em; width: 0em; display: inline-block; overflow: hidden;"></span><span style="display: inline-block; width: 0px; height: 3.99em;"></span></span></span></span><span style="display: inline-block; width: 0px; height: 3.99em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -1.434em; border-left: 0px solid; width: 0px; height: 2.316em;"></span></span></nobr><span class="MJX_Assistive_MathML MJX_Assistive_MathML_Block" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><mi>t</mi><mi>b</mi><mi>u</mi><mi>m</mi><mi>p</mi><mi>e</mi><mi>r</mi><mo>=</mo><mi>t</mi><mi>u</mi><mi>p</mi><mi>p</mi><mi>e</mi><mi>r</mi><mo>=</mo><mi>t</mi><mi>f</mi><mi>r</mi><mi>o</mi><mi>n</mi><mi>t</mi><mo>=</mo><mi>t</mi><mi>u</mi><mi>n</mi><mi>d</mi><mi>e</mi><mi>r</mi><mo>=</mo><mn>3</mn><mi>m</mi><mi>m</mi><mspace linebreak="newline"></mspace></math></span></span></div><script type="math/tex; mode=display" id="MathJax-Element-4">
tbumper=tupper=tfront=tunder=3mm\\
</script></span></p><ul>
<li>
<p><code>Mass</code>計算方式為<code>Part 2</code> + <code>Part 3</code> + <code>Part 4</code> +<code>Part 5</code></p>
</li>
<li>
<p><code>Intrusion</code>計算方式為<code>nodes 167</code> 的<code>x</code>位移剪去<code>node</code> <code>432</code> 的<code>x</code>位移。在這裡，<code>node</code> <code>432</code>僅是作為一參考點，因為該點是模型內較無變形的地方。</p>
</li>
<li>
<p><code>tbumper</code>: <code>Part 2</code>的厚度</p>
</li>
<li>
<p><code>tupper</code>: <code>Part 3</code>的厚度</p>
</li>
<li>
<p><code>tfront</code>: <code>Part 4</code>的厚度</p>
</li>
<li>
<p><code>tunder</code>: <code>Part 5</code>的厚度</p>
</li>
</ul><h2 id="-3-前置作業"><a class="anchor hidden-xs" href="#-3-前置作業" title="-3-前置作業"><span class="octicon octicon-link"></span></a><img alt=":wrench:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/wrench.png" title=":wrench:"> 3. 前置作業</h2><h3 id="31-LS-DYNA-K檔修改"><a class="anchor hidden-xs" href="#31-LS-DYNA-K檔修改" title="31-LS-DYNA-K檔修改"><span class="octicon octicon-link"></span></a>3.1 LS-DYNA K檔修改</h3><ol>
<li>打開<code>main.k</code>，修改<code>*PARAMETER</code>。定義<code>Part2</code>~<code>Part5</code>的厚度變數及一個設定<code>dt</code>的時間變數。</li>
</ol><div class="alert alert-warning">
<p><img alt=":flashlight:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/flashlight.png" title=":flashlight:"> <code>*PARAMETER</code> 可以設定的變數，總共有<code>R(實數)</code>、<code>I(整數)</code>、  <code>C(字串)</code> <code>3</code>種。</p>
</div><ol start="2">
<li>剪下<code>car5.k</code>內的<code>*include ../../rigid2</code>，貼到<code>main.k</code>內。這個修改只是<code>老駱</code>個人的習慣，將<code>barrier</code>與<code>car</code>兩者分離開來。最後<code>main.k</code>檔應該看起來像:</li>
</ol><pre><code class="python hljs"><div class="wrapper"><div class="gutter linenumber"><span data-linenumber="1"></span>
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
<span data-linenumber="12"></span></div><div class="code">*KEYWORD
*PARAMETER
rtbumper,<span class="hljs-number">3.0</span>
rthood,<span class="hljs-number">3.0</span>
rtfront,<span class="hljs-number">3.0</span>
rtunder,<span class="hljs-number">3.0</span>
rdt,<span class="hljs-number">5e-2</span>
*INCLUDE
../../car5.k
*INCLUDE
../../rigid2
*END
</div></div></code></pre><ol start="2">
<li>打開<code>car5.k</code>，刪除<code>*DATABASE_RWFORC</code>及<code>*DATABASE_BINARY_RUNRSF</code>這兩項不需要的輸出。</li>
<li>對於這個問題僅需要<code>t = 5e-2</code>秒時的資訊，所以可以修改<code>car5.k</code>最上方幾行。</li>
</ol><pre><code class="python hljs"><div class="wrapper"><div class="gutter linenumber"><span data-linenumber="1"></span>
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
<span data-linenumber="18"></span></div><div class="code">*CONTROL_TERMINATION
&amp;dt
*DATABASE_NODOUT
&amp;dt
*DATABASE_BINARY_D3PLOT
&amp;dt
*DATABASE_GLSTAT_MASS_PROPERTIES
&amp;dt
*DATABASE_SSSTAT_MASS_PROPERTIES
&amp;dt
*DATABASE_EXTENT_SSSTAT
      <span class="hljs-number">9999</span>
*SET_PART_LIST
      <span class="hljs-number">9999</span>
<span class="hljs-number">2</span>,<span class="hljs-number">3</span>,<span class="hljs-number">4</span>,<span class="hljs-number">5</span>
$
$ DEFINITION OF MATERIAL     <span class="hljs-number">1</span>
$
</div></div></code></pre><ol start="4">
<li>指定適當的厚度變數至各<code>*SECTION_SHELL</code>。</li>
</ol><pre><code class="python hljs"><div class="wrapper"><div class="gutter linenumber"><span data-linenumber="1"></span>
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
<span data-linenumber="15"></span></div><div class="code">*SECTION_SHELL
<span class="hljs-number">2</span>,<span class="hljs-number">2</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0</span>
&amp;tbumper,&amp;tbumper,&amp;tbumper,&amp;tbumper,<span class="hljs-number">0.</span>

*SECTION_SHELL
<span class="hljs-number">3</span>,<span class="hljs-number">2</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0</span>
&amp;thood,&amp;thood,&amp;thood,&amp;thood,<span class="hljs-number">0.</span>

*SECTION_SHELL
<span class="hljs-number">4</span>,<span class="hljs-number">2</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0</span>
&amp;tfront,&amp;tfront,&amp;tfront,&amp;tfront,<span class="hljs-number">0.</span>

*SECTION_SHELL
<span class="hljs-number">5</span>,<span class="hljs-number">2</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0.</span>,<span class="hljs-number">0</span>
&amp;tunder,&amp;tunder,&amp;tunder,&amp;tunder,<span class="hljs-number">0.</span>
</div></div></code></pre><div class="alert alert-warning">
<p><img alt=":flashlight:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/flashlight.png" title=":flashlight:"> 至此，上述修改已經可以用於<code>LS-OPT</code>分析。但<code>main.k</code>內<code>car5.k</code>及<code>rigid2</code>被<code>INCLUDE</code>的路徑是<code>../../car5.k</code>及<code>../../rigid2</code>。這樣的設定方便<code>LS-OPT</code>分析，但不太利於使用<code>VisualDOC</code>，所以我們可以複製一份<code>main.k</code>、<code>car5.k</code>及<code>rigid2</code>至一新資料夾，然候將<code>main.k</code>中<code>car5.k</code>的<code>INCLUDE</code>路徑改為<code>car5.k</code>及將<code>rigid2</code>的<code>INCLUDE</code>路徑改為<code>rigid2</code>，作為後續<code>VisualDOC</code>分析使用。</p>
</div><p>用於<code>VisualDOC</code>分析的<code>main.k</code>檔應該會像:</p><pre><code class="python hljs"><div class="wrapper"><div class="gutter linenumber"><span data-linenumber="1"></span>
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
<span data-linenumber="12"></span></div><div class="code">*KEYWORD
*PARAMETER
rtbumper,<span class="hljs-number">3.0</span>
rthood,<span class="hljs-number">3.0</span>
rtfront,<span class="hljs-number">3.0</span>
rtunder,<span class="hljs-number">3.0</span>
rdt,<span class="hljs-number">5e-2</span>
*INCLUDE
car5.k
*INCLUDE
rigid2
*END
</div></div></code></pre><h2 id="-4-LS-OPT"><a class="anchor hidden-xs" href="#-4-LS-OPT" title="-4-LS-OPT"><span class="octicon octicon-link"></span></a><img alt=":mag_right:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/mag_right.png" title=":mag_right:"> 4. LS-OPT</h2><ol>
<li>打開<code>srsm.lsopt</code>，<code>Metamodel-based</code>維持<code>Optimization</code>，<code>Strategy for Metamodel-based Optimization</code> 維持<code>Sequential woth Domain Reduction(SRSM)</code>。</li>
<li>點選<code>Setup</code> <code>block</code>將<code>tbumper</code>、<code>thood</code>、<code>tfront</code>、<code>tunder</code>的<code>Type</code>設為<code>Continous</code>、<code>Starting</code>設為<code>3</code>、<code>Minumum</code>設為<code>1</code>、<code>Maximum</code>設為<code>5</code>。</li>
<li>將<code>dt</code>的<code>Type</code>設為<code>Constant</code>，維持<code>Starting</code>為<code>0.05</code>。</li>
<li>點選<code>Sampling crash</code> <code>block</code>。<code>Metamodel</code>選用<code>Radial Basis Function Network</code>，<code>Pointselection</code>選用<code>Space Filling</code>，<code>Number of Simulation Points</code>維持<code>8</code>。</li>
<li>點選<code>Crash</code> <code>block</code>下的<code>Setup</code>，在<code>Command</code>中輸入呼叫<code>LS-DYNA</code>的指令。此外，可以考慮輸入<code>d=nodump</code>減少輸出。</li>
<li>點選<code>Crash</code> <code>block</code>下<code>reponses</code>下刪除<code>MaxAccel</code>、<code>HIC</code> 兩項。</li>
<li>點選<code>Optimization</code> <code>block</code>，將<code>Objectives</code>改為<code>Mass</code>。點選<code>Constraint</code>，選擇<code>Intrusions</code>，設定<code>Upper Bound</code>為<code>485</code>。</li>
</ol><table>
<thead>
<tr>
<th style="text-align:center">()內為<code>LS-DYNA</code>運行次數 <code>Unit: ton &amp; mm</code></th>
<th style="text-align:center"><code>tbumper</code></th>
<th style="text-align:center"><code>thood</code></th>
<th style="text-align:center"><code>tfront</code></th>
<th style="text-align:center"><code>tunder</code></th>
<th style="text-align:center"><code>mass</code></th>
<th style="text-align:center"><code>disp</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center"><code>LS-OPT(49)</code></td>
<td style="text-align:center">4.83</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">4.53</td>
<td style="text-align:center">0.871</td>
<td style="text-align:center">483.216</td>
</tr>
</tbody>
</table><h2 id="-5-VisualDOC操作細節"><a class="anchor hidden-xs" href="#-5-VisualDOC操作細節" title="-5-VisualDOC操作細節"><span class="octicon octicon-link"></span></a><img alt=":mag_right:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/mag_right.png" title=":mag_right:"> 5. VisualDOC操作細節</h2><p>先進行<code>1</code>次<code>Baserun</code>，看看<code>LS-DYNA</code>是否能夠成功求解。求解成功後的<code>ssstat</code>及<code>nodout</code>檔，將用來進行後續<code>VisualDOC</code>的設定。</p><table>
<thead>
<tr>
<th style="text-align:center">()內為<code>LS-DYNA</code>運行次數 <code>Unit: ton &amp; mm</code></th>
<th style="text-align:center"><code>tbumper</code></th>
<th style="text-align:center"><code>thood</code></th>
<th style="text-align:center"><code>tfront</code></th>
<th style="text-align:center"><code>tunder</code></th>
<th style="text-align:center"><code>mass</code></th>
<th style="text-align:center"><code>disp</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center"><code>LS-OPT(49)</code></td>
<td style="text-align:center">4.83</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">4.53</td>
<td style="text-align:center">0.871</td>
<td style="text-align:center">483.216</td>
</tr>
<tr>
<td style="text-align:center"><code>Baserun(1)</code></td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">0.865</td>
<td style="text-align:center">504.997</td>
</tr>
</tbody>
</table><h3 id="51-Optimization"><a class="anchor hidden-xs" href="#51-Optimization" title="51-Optimization"><span class="octicon octicon-link"></span></a>5.1 Optimization</h3><h4 id="511-Work-Flow"><a class="anchor hidden-xs" href="#511-Work-Flow" title="511-Work-Flow"><span class="octicon octicon-link"></span></a>5.1.1 Work Flow</h4><p>使用<code>Quick Start</code>-&gt;<code>Direct Optimization</code>-&gt;<code>User Defined Program</code>，快速搭建此問題的<code>Work Flow</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/101_work_flow.jpg" alt="101_work_flow"></p><p><img src="/assets/img/vrand_vdoc/ch6/102_work_flow.jpg" alt="102_work_flow"></p><p><img src="/assets/img/vrand_vdoc/ch6/103_work_flow.jpg" alt="103_work_flow"></p><h4 id="512-Component-Editor內層"><a class="anchor hidden-xs" href="#512-Component-Editor內層" title="512-Component-Editor內層"><span class="octicon octicon-link"></span></a>5.1.2 Component Editor內層</h4><p>點選<code>C欄</code> <code>Component Editor</code> <code>Optimization</code>下的第一個<code>File I/O</code> <code>component</code>。</p><p>按下下方<code>Add an input file</code>，於<code>File Path</code>中選擇<code>Main.k</code>，<code>VisualDOC</code>會自動生成<code>main.k.tmpl</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/201_component_editor.jpg" alt="201_component_editor"></p><div class="alert alert-warning">
<p><img alt=":flashlight:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/flashlight.png" title=":flashlight:"> <code>*.tmpl</code>檔可以視為一種範本，<code>VisualDOC</code>將會記住這個檔案的<code>pattern</code>，在之後與<code>LS-DYNA</code>進行<code>coupling</code>時，可以自動替換正確的變數值給<code>LS-DYNA</code>求解(每次求解可以視為建立<code>1</code>個<code>DOE</code>點位)，也可以讀入<code>LS-DYNA</code>的結果進入<code>VisualDOC</code>進行後續<code>Optimization</code>或<code>RSA</code>等計算。進行<code>*.tmpl</code>檔設定的時候，特別要注意的是選用<code>Format Specification</code>時要使用<code>Free Format</code>或是<code>Fixed Format</code>。老駱一般喜歡用<code>Fixed Format</code>，但要特別注意數格子的時候，記得考慮變數本身的正負號也會佔一格。有時候，也會意外多含入跟隨其後數字的正負號。所以設定完之後，要記得在求解過程中觀察各個變數有沒有出現不合理的變化，通常問題都出現在最佳化求解的時候，讀入或寫出的變數有問題。</p>
</div><p>於右方<code>Template File</code>中點選<code>*PARAMETER</code>(第<code>2</code>行)，按下下方<code>Add new search action</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/202_component_editor.jpg" alt="202_component_editor"></p><p>點選<code>rtbumper</code>(第<code>3</code>行)，按下下方<code>Add new search action</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/203_component_editor.jpg" alt="203_component_editor"></p><p>點選<code>rtbumper</code>逗號後的<code>3.0</code>，按下下方<code>Add new modify action</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/204_component_editor.jpg" alt="204_component_editor"></p><p>查閱 <ins><a href="https://www.dynasupport.com/manuals/ls-dyna-manuals" target="_blank" rel="noopener">LS-DYNAKEYWORD USER’S MANUAL VOLUME I</a></ins> 可以知道<code>*PARAMETER</code>這張卡每行有<code>8</code>個欄位，每個欄位可佔<code>10</code>格。所以可以將<code>Format Specification</code>設為<code>Fixed Format</code>，並將<code>Fixed Length</code>設為<code>10</code>，確保變數的每一個位數都能被<code>VisualDOC</code>找到。</p><p><img src="/assets/img/vrand_vdoc/ch6/205_component_editor.jpg" alt="205_component_editor"></p><p>依照上述邏輯，依序對<code>rtbumper</code>、<code>rthood</code>、<code>rtfront</code>及<code>rtunder</code>完成類似的設定。</p><p><img src="/assets/img/vrand_vdoc/ch6/206_component_editor.jpg" alt="206_component_editor"></p><p>此外，也可以選擇<code>raw array</code>的方法，一次選取多個值，完成設定。事實上這也是<code>Advanced Examples Manual 5.2 Coupling VisualDOC with LS-DYNA</code>中建議的操作方式。但這麼一來，在左方的欄位將難以區分各變數，各變數名將變成<code>t[0]</code>、<code>t[1]</code>。當然，也可以在<code>component editor外層</code>中重新對各變數命名。一般來說，這種設定方法適用於變數很多的情況。對於變數較少的問題，老駱習慣在這邊一個一個設定，這樣一來在<code>component editor外層</code>也能夠不重新命名，就能從變數名識別各變數。</p><p>第一個<code>File I/O</code>設定完後，應該會像:</p><p><img src="/assets/img/vrand_vdoc/ch6/207_component_editor.jpg" alt="207_component_editor"></p><p>點選<code>C欄</code> <code>Component Editor</code> <code>Optimization</code>下的第二個<code>File I/O</code> <code>component</code>。</p><p>按下下方<code>Add an outout file</code>，於<code>File Path</code>中選擇<code>ssstat</code>，<code>VisualDOC</code>會自動生成<code>ssstat.tmpl</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/208_component_editor.jpg" alt="208_component_editor"></p><p>於右方<code>Template File</code>中點選<code>total mass of subsystem</code>(第<code>28</code>行)，按下下方<code>Add new search action</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/209_component_editor.jpg" alt="209_component_editor"></p><p>於右方<code>Template File</code>中點選<code>total mass of subsystem =</code>後的<code>8.65123510E-01</code>，按下下方<code>Add new extract action</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/210_component_editor.jpg" alt="210_component_editor"></p><p>將<code>Format Specification</code>設為<code>Fixed Format</code>，將<code>Strarting Column</code>設為<code>35</code>，<code>Fixed Length</code>設為<code>16</code>，重新命名變數名為<code>mass</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/211_component_editor.jpg" alt="211_component_editor"></p><p>按下下方<code>Add an outout file</code>，於<code>File Path</code>中選擇<code>nodout</code>，<code>VisualDOC</code>會自動生成<code>nodout.tmpl</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/212_component_editor.jpg" alt="212_component_editor"></p><p>於右方<code>Template File</code>中點選<code>n o d a l__p r i n t__o u t</code>，並按下<code>2</code>次<code>Find Next</code>，此時應該能找到位於第<code>29</code>列的正確資訊。(注意<code>__</code>是代表<code>2</code>個空格，這是<code>LS-DYNA</code> <code>nodout</code>輸出的格式)。按下下方<code>Add new search action</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/213_component_editor.jpg" alt="213_component_editor"></p><p>於右方<code>Template File</code>中點選<code>x-disp</code>(第<code>32</code>行)，按下下方<code>Add new extract action</code>。重新命名變數名為<code>disp_167_x</code>。</p><div class="alert alert-warning">
<p><img alt=":flashlight:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/flashlight.png" title=":flashlight:"> 有時候，<code>*.tmpl</code>內可能有多列都符合搜尋結果，此時就要靠<code>Find Prev</code>和<code>Find Next</code>來正確指定變數的位置。</p>
</div><p><img src="/assets/img/vrand_vdoc/ch6/214_component_editor.jpg" alt="214_component_editor"></p><p>點選<code>Format Specification</code>為<code>Fixed Format</code>，並將<code>Start Column</code>設為<code>11</code>及<code>Fixed Length</code>設為<code>12</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/215_component_editor.jpg" alt="215_component_editor"></p><p>對<code>node 432</code>進行類似的操作，並重新命名變數名為<code>disp_432_x</code></p><p><img src="/assets/img/vrand_vdoc/ch6/216_component_editor.jpg" alt="216_component_editor"></p><p>新增一個變數，命名為<code>disp</code>，將其<code>Input/Output</code>設定為<code>Output</code>，並將其<code>Adv, Attribute</code>設為<code>Synthetic</code>(<code>Synthetic</code>可以想成這個變數須要經由其它變數的運算後才能產生)。對<code>disp_x</code>欄按右鍵，選擇<code>Edit dependence equation</code>後，於上方<code>Input</code>輸入<code>disp_167_x,disp_432_x</code>，並於下方編輯區輸入<code>disp_x = disp_167_x - disp_432_x</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/217_component_editor.jpg" alt="217_component_editor"></p><p>第二個<code>File I/O</code>設定完後，應該會像:</p><p><img src="/assets/img/vrand_vdoc/ch6/218_component_editor.jpg" alt="218_component_editor"></p><p>點選<code>Executable</code> <code>component</code>，於<code>Local Analysis Program Definition</code>中的<code>File Path</code>選擇求解器的位置，老駱自己是習慣使用環境變數，您也可以直接用路徑來選擇求解器。另外可以在<code>Program Arguments</code>裡輸入求解的選項，老駱這邊設定想求解的檔案名為<code>main.k</code>，用<code>4</code>個<code>cpu</code>求解，並且不須要產生<code>dump</code> <code>file</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/219_component_editor.jpg" alt="219_component_editor"></p><h4 id="513-Data-Linker"><a class="anchor hidden-xs" href="#513-Data-Linker" title="513-Data-Linker"><span class="octicon octicon-link"></span></a>5.1.3 Data Linker</h4><p>點選<code>C欄</code>中的<code>Data Linker</code>，使用<code>Automatically add data to the selected model</code>來自動連接。</p><p><img src="/assets/img/vrand_vdoc/ch6/301_data_linker.jpg" alt="301_data_linker"></p><p>接下來點選<code>C欄</code>中的<code>component editor外層</code>的<code>Optimization</code> <code>component</code>，變數已經新增好了。</p><h4 id="514-Component-Editor外層"><a class="anchor hidden-xs" href="#514-Component-Editor外層" title="514-Component-Editor外層"><span class="octicon octicon-link"></span></a>5.1.4 Component Editor外層</h4><p><img src="/assets/img/vrand_vdoc/ch6/220_component_editor.jpg" alt="220_component_editor"></p><p>進行下列設定:</p><ul>
<li>設定<code>rtbumper</code>、<code>rthood</code>、<code>rtfront</code>及<code>rtunder</code>的<code>Lower Bound</code>為<code>1</code>及<code>Upper Bound</code>為<code>5</code></li>
<li>勾選<code>f</code>為<code>Objective</code>、不勾選其為<code>Constraint</code>，並確定其<code>Goal</code>維持預設的<code>Minimize</code></li>
<li>刪除<code>disp_167_x</code>及<code>disp_432_x</code></li>
<li>勾選<code>disp_x</code>為<code>Constraint</code>，並設定其<code>Upper Bound</code>為<code>485</code></li>
</ul><p><img src="/assets/img/vrand_vdoc/ch6/221_component_editor.jpg" alt="221_component_editor"></p><h4 id="515-Simulation-Monitors"><a class="anchor hidden-xs" href="#515-Simulation-Monitors" title="515-Simulation-Monitors"><span class="octicon octicon-link"></span></a>5.1.5 Simulation Monitors</h4><p>點選<code>C欄</code> <code>Simulation Monitors</code>，按下右方<code>Add a generic monitor</code>，輸入<code>6</code>，來創造一個觀看<code>6</code>個變數的表格，分別觀察<code>rtbumper</code>、<code>rthood</code>、<code>rtfront</code>、<code>rtunder</code>、<code>mass</code>及<code>disp_x</code>。</p><p>接著新增<code>BestObjetive</code>及<code>WrostConstraint</code>這兩個<code>monitor</code>。</p><p>手動完成連接後，應該會像:</p><p><img src="/assets/img/vrand_vdoc/ch6/401_simulation_monitors.jpg" alt="401_simulation_monitors"></p><h4 id="516-Post-Processing"><a class="anchor hidden-xs" href="#516-Post-Processing" title="516-Post-Processing"><span class="octicon octicon-link"></span></a>5.1.6 Post Processing</h4><p>這是老駱試了幾次之後，比較好的答案，另存一<code>task</code>，命名為<code>Opt good</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/501_post_processing.jpg" alt="501_post_processing"></p><p>這是老駱試了幾次之後，比較差的答案，另存一<code>task</code>，命名為<code>Opt bad</code>。</p><p><img src="/assets/img/vrand_vdoc/ch6/502_post_processing.jpg" alt="502_post_processing"></p><table>
<thead>
<tr>
<th style="text-align:center">()內為<code>LS-DYNA</code>運行次數 <code>Unit: ton &amp; mm</code></th>
<th style="text-align:center"><code>tbumper</code></th>
<th style="text-align:center"><code>thood</code></th>
<th style="text-align:center"><code>tfront</code></th>
<th style="text-align:center"><code>tunder</code></th>
<th style="text-align:center"><code>mass</code></th>
<th style="text-align:center"><code>disp</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center"><code>LS-OPT(49)</code></td>
<td style="text-align:center">4.83</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">4.53</td>
<td style="text-align:center">0.871</td>
<td style="text-align:center">483.216</td>
</tr>
<tr>
<td style="text-align:center"><code>Baserun(1)</code></td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">0.865</td>
<td style="text-align:center">504.997</td>
</tr>
<tr>
<td style="text-align:center"><code>Opt good(207)</code></td>
<td style="text-align:center">4.56</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.30</td>
<td style="text-align:center">4.17</td>
<td style="text-align:center">0.833</td>
<td style="text-align:center">486.276</td>
</tr>
<tr>
<td style="text-align:center"><code>Opt bad(93)</code></td>
<td style="text-align:center">4.18</td>
<td style="text-align:center">3.27</td>
<td style="text-align:center">3.70</td>
<td style="text-align:center">4.01</td>
<td style="text-align:center">1.091</td>
<td style="text-align:center">486.144</td>
</tr>
</tbody>
</table><div class="alert alert-danger">
<p><img alt=":bangbang:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/bangbang.png" title=":bangbang:"> <code>LS-DYNA</code>由於考慮其計算效率，所以每次計算的結果，即使是用同一台電腦及同樣的<code>CPU</code>數，跑同樣的問題，也會有微小的差異。在一般的顯性問題中，這樣的誤差是可以接受的。但在跑最佳化問題時，會容易在最佳解附近振盪，花費許多計算資源在等結果收斂，甚至有時候收斂的答案離最佳解還有一段不小的距離。簡單講，直接與<code>LS-DYNA</code>進行<code>Optimization</code>的話，每次跑可能都不同的答案，有時答案很好，有時卻會很差(例如<code>Opt good</code>與<code>Opt bad</code>)。所以老駱一般不建議直接進行<code>Optimization</code>，而是用<code>DOE</code>搭配<code>Optimization</code>或<code>RSA</code>來求解，才是比較實務的作法。</p>
</div><h3 id="52-DOE"><a class="anchor hidden-xs" href="#52-DOE" title="52-DOE"><span class="octicon octicon-link"></span></a>5.2 DOE</h3><p>開啟<code>Opt good</code> <code>task</code>，另存一<code>task</code>，命名為<code>DOE with responses Composite</code>。將<code>2</code>個<code>File I/O</code>及<code>1</code>個<code>Executable</code> <code>component</code>置入<code>DOE</code> <code>component</code>中，並刪除<code>Optimization</code> <code>component</code>，最後完成<code>work flow</code>連接。步驟與 <ins><a href="{% post_url 2019-12-17-Vrand_VisualDOC_Ch2_DOE %}" target="_blank" rel="noopener">Vrand_VisualDOC_Ch2_DOE</a></ins> 類似。</p><p>點選<code>DOE</code> <code>component</code>進行下列設定:</p><ul>
<li>設定<code>rtbumper</code>、<code>rthood</code>、<code>rtfront</code>及<code>rtunder</code>的<code>Lower Bound</code>為<code>1</code>及<code>Upper Bound</code>為<code>5</code>，並設定為<code>Variable</code></li>
<li>勾選<code>mass</code>及<code>disp_x</code>為<code>Response</code></li>
<li>刪除<code>disp_167_x</code>及<code>disp_432_x</code></li>
<li><code>DOE Action</code>選擇<code>Create DOE points with responses</code></li>
<li><code>Designs</code>選擇<code>Composites</code>，共產生<code>25</code>個點位</li>
<li>勾選<code>Reuse approximation from first invocation when run as subflow</code></li>
</ul><p><img src="/assets/img/vrand_vdoc/ch6/222_component_editor.jpg" alt="222_component_editor"></p><h3 id="53-Optimization-Using-DOE"><a class="anchor hidden-xs" href="#53-Optimization-Using-DOE" title="53-Optimization-Using-DOE"><span class="octicon octicon-link"></span></a>5.3 Optimization Using DOE</h3><p>開啟<code>DOE with responses Composite</code> <code>task</code>，另存一<code>task</code>，命名為<code>Opt Using DOE</code>。 將<code>DOE</code> <code>component</code>置入<code>Optimization</code> <code>component</code>中並完成<code>work flow</code>連接。</p><p>點選<code>DOE</code> <code>component</code>後可以使用<code>User Defined</code>的功能，讀入<code>DOE with responses Composite</code> <code>task</code>產生的<code>25</code>個點位，並將<code>DOE Action</code>改為<code>Create DOE with approximations</code>。</p><p>其餘<code>Data Linker</code>、<code>Optimization</code> <code>component</code> 及<code>Simulation Monitors</code>設定與 <ins><a href="#51-Optimization">5.1 Optimization</a></ins> 類似。</p><p><img src="/assets/img/vrand_vdoc/ch6/503_post_processing.jpg" alt="503_post_processing"></p><table>
<thead>
<tr>
<th style="text-align:center">()內為<code>LS-DYNA</code>運行次數 <code>Unit: ton &amp; mm</code></th>
<th style="text-align:center"><code>tbumper</code></th>
<th style="text-align:center"><code>thood</code></th>
<th style="text-align:center"><code>tfront</code></th>
<th style="text-align:center"><code>tunder</code></th>
<th style="text-align:center"><code>mass</code></th>
<th style="text-align:center"><code>disp</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center"><code>LS-OPT(49)</code></td>
<td style="text-align:center">4.83</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">4.53</td>
<td style="text-align:center">0.871</td>
<td style="text-align:center">483.216</td>
</tr>
<tr>
<td style="text-align:center"><code>Baserun(1)</code></td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">0.865</td>
<td style="text-align:center">504.997</td>
</tr>
<tr>
<td style="text-align:center"><code>Opt good(207)</code></td>
<td style="text-align:center">4.56</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.30</td>
<td style="text-align:center">4.17</td>
<td style="text-align:center">0.833</td>
<td style="text-align:center">486.276</td>
</tr>
<tr>
<td style="text-align:center"><code>Opt bad(93)</code></td>
<td style="text-align:center">4.18</td>
<td style="text-align:center">3.27</td>
<td style="text-align:center">3.70</td>
<td style="text-align:center">4.01</td>
<td style="text-align:center">1.091</td>
<td style="text-align:center">486.144</td>
</tr>
<tr>
<td style="text-align:center"><code>Opt Using DOE(25)</code></td>
<td style="text-align:center">4.07</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.64</td>
<td style="text-align:center">5.00</td>
<td style="text-align:center">0.899</td>
<td style="text-align:center">486.404</td>
</tr>
</tbody>
</table><h3 id="54-RSA-Using-DOE"><a class="anchor hidden-xs" href="#54-RSA-Using-DOE" title="54-RSA-Using-DOE"><span class="octicon octicon-link"></span></a>5.4 RSA Using DOE</h3><p>開啟<code>Opt good</code> <code>task</code>，另存一<code>task</code>，命名為<code>RSA Using DOE</code>。將<code>2</code>個<code>File I/O</code>及<code>1</code>個<code>Executable</code> <code>component</code>置入<code>RSA</code> <code>component</code>中，並刪除<code>Optimization</code> <code>component</code>，最後完成<code>work flow</code>連接。</p><p>點選<code>RSA</code> <code>component</code>後可以使用<code>User Defined</code>的功能，讀入<code>DOE with responses Composite</code> <code>task</code>作為<code>Starting Strategy</code>。</p><p>其餘<code>Data Linker</code>、<code>RSA</code> <code>component</code> 及<code>Simulation Monitors</code>設定與 <ins><a href="#51-Optimization">5.1 Optimization</a></ins> 類似。</p><p><img src="/assets/img/vrand_vdoc/ch6/504_post_processing.jpg" alt="504_post_processing"></p><table>
<thead>
<tr>
<th style="text-align:center">()內為<code>LS-DYNA</code>運行次數 <code>Unit: ton &amp; mm</code></th>
<th style="text-align:center"><code>tbumper</code></th>
<th style="text-align:center"><code>thood</code></th>
<th style="text-align:center"><code>tfront</code></th>
<th style="text-align:center"><code>tunder</code></th>
<th style="text-align:center"><code>mass</code></th>
<th style="text-align:center"><code>disp</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center"><code>LS-OPT(49)</code></td>
<td style="text-align:center">4.83</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">4.53</td>
<td style="text-align:center">0.871</td>
<td style="text-align:center">483.216</td>
</tr>
<tr>
<td style="text-align:center"><code>Baserun(1)</code></td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">3.00</td>
<td style="text-align:center">0.865</td>
<td style="text-align:center">504.997</td>
</tr>
<tr>
<td style="text-align:center"><code>Opt good(207)</code></td>
<td style="text-align:center">4.56</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.30</td>
<td style="text-align:center">4.17</td>
<td style="text-align:center">0.833</td>
<td style="text-align:center">486.276</td>
</tr>
<tr>
<td style="text-align:center"><code>Opt bad(93)</code></td>
<td style="text-align:center">4.18</td>
<td style="text-align:center">3.27</td>
<td style="text-align:center">3.70</td>
<td style="text-align:center">4.01</td>
<td style="text-align:center">1.091</td>
<td style="text-align:center">486.144</td>
</tr>
<tr>
<td style="text-align:center"><code>Opt Using DOE(25)</code></td>
<td style="text-align:center">4.07</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.64</td>
<td style="text-align:center">5.00</td>
<td style="text-align:center">0.899</td>
<td style="text-align:center">486.404</td>
</tr>
<tr>
<td style="text-align:center"><code>RSA Using DOE(52)</code></td>
<td style="text-align:center">4.39</td>
<td style="text-align:center">1.00</td>
<td style="text-align:center">1.30</td>
<td style="text-align:center">4.53</td>
<td style="text-align:center">0.858</td>
<td style="text-align:center">484.591</td>
</tr>
</tbody>
</table><h2 id="-6-結語"><a class="anchor hidden-xs" href="#-6-結語" title="-6-結語"><span class="octicon octicon-link"></span></a><img alt=":smiley_cat:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/smiley_cat.png" title=":smiley_cat:"> 6. 結語</h2><ul>
<li>直接使用<code>Optimization</code>來couple<code>LS-DYNA</code>，須要耗費較多的計算資源，且不保證每次都能得到滿意的答案。</li>
<li>使用<code>Optimization</code>+<code>DOE</code>來couple<code>LS-DYNA</code>，僅須要在<code>DOE</code>時呼叫<code>LS-DYNA</code>。一旦得到了問題的近似函數，後續的<code>Optimization</code>計算速度非常快，且求得的近似解也有一定的品質，是一個經濟實惠的選擇。</li>
<li>使用<code>RSA</code>+<code>DOE</code>來couple<code>LS-DYNA</code>，除了<code>DOE</code>時，做<code>RSA</code>也要呼叫<code>LS-DYNA</code>，但總呼叫次數<code>52</code>次也差不多等於<code>LS-OPT</code>的<code>49</code>次。比較<code>LS-OPT</code>與<code>RSA Using DOE</code>後，可以發現兩者的答案也相去不遠。</li>
<li>使用<code>RSA</code>+<code>DOE</code>來couple<code>LS-DYNA</code>，應該是一可得最佳解的穩定策略。但此策略的後期，因為須確保收斂，可能會多次呼叫<code>LS-DYNA</code>。也就是說，可能會增加很多求解時間，卻無法帶來相對應的最佳解提升。</li>
<li><strong>老駱認為，在適當挑選<code>DOE</code>點位的前提下，使用<code>Optimization</code>+<code>DOE</code>來couple<code>LS-DYNA</code>，應該是一個不錯的策略。如果覺得所求的近似解不是很滿意，可逐步加入<code>DOE</code>點位，來提升準確度。這樣的操作方式應該會比使用<code>RSA</code>+<code>DOE</code>來得更有效益一些。當然如果使用<code>Optimization</code>+<code>DOE</code>來couple<code>LS-DYNA</code>求解，過程中可能須要反覆調試，略嫌有些麻煩。至於最終採用什麼策略來解題，得取決於問題的難度、求解所需的精度與使用者所擁有的計算資源及時間來綜合考量。</strong></li>
</ul><h2 id="-7-聯絡老駱"><a class="anchor hidden-xs" href="#-7-聯絡老駱" title="-7-聯絡老駱"><span class="octicon octicon-link"></span></a><img alt=":mailbox:" class="emoji" src="https://cdnjs.cloudflare.com/ajax/libs/emojify.js/1.1.0/images/basic/mailbox.png" title=":mailbox:">  7. 聯絡老駱</h2><div class="alert alert-info">
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

