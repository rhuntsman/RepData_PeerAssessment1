<!DOCTYPE html>
<!-- saved from url=(0014)about:internet -->
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<meta http-equiv="x-ua-compatible" content="IE=9" >

<title>Loading and preprocessing the data</title>

<style type="text/css">
body, td {
   font-family: sans-serif;
   background-color: white;
   font-size: 12px;
   margin: 8px;
}

tt, code, pre {
   font-family: 'DejaVu Sans Mono', 'Droid Sans Mono', 'Lucida Console', Consolas, Monaco, monospace;
}

h1 { 
   font-size:2.2em; 
}

h2 { 
   font-size:1.8em; 
}

h3 { 
   font-size:1.4em; 
}

h4 { 
   font-size:1.0em; 
}

h5 { 
   font-size:0.9em; 
}

h6 { 
   font-size:0.8em; 
}

a:visited {
   color: rgb(50%, 0%, 50%);
}

pre {	
   margin-top: 0;
   max-width: 95%;
   border: 1px solid #ccc;
   white-space: pre-wrap;
}

pre code {
   display: block; padding: 0.5em;
}

code.r, code.cpp {
   background-color: #F8F8F8;
}

table, td, th {
  border: none;
}

blockquote {
   color:#666666;
   margin:0;
   padding-left: 1em;
   border-left: 0.5em #EEE solid;
}

hr {
   height: 0px;
   border-bottom: none;
   border-top-width: thin;
   border-top-style: dotted;
   border-top-color: #999999;
}

@media print {
   * { 
      background: transparent !important; 
      color: black !important; 
      filter:none !important; 
      -ms-filter: none !important; 
   }

   body { 
      font-size:12pt; 
      max-width:100%; 
   }
       
   a, a:visited { 
      text-decoration: underline; 
   }

   hr { 
      visibility: hidden;
      page-break-before: always;
   }

   pre, blockquote { 
      padding-right: 1em; 
      page-break-inside: avoid; 
   }

   tr, img { 
      page-break-inside: avoid; 
   }

   img { 
      max-width: 100% !important; 
   }

   @page :left { 
      margin: 15mm 20mm 15mm 10mm; 
   }
     
   @page :right { 
      margin: 15mm 10mm 15mm 20mm; 
   }

   p, h2, h3 { 
      orphans: 3; widows: 3; 
   }

   h2, h3 { 
      page-break-after: avoid; 
   }
}

</style>

<!-- Styles for R syntax highlighter -->
<style type="text/css">
   pre .operator,
   pre .paren {
     color: rgb(104, 118, 135)
   }

   pre .literal {
     color: rgb(88, 72, 246)
   }

   pre .number {
     color: rgb(0, 0, 205);
   }

   pre .comment {
     color: rgb(76, 136, 107);
   }

   pre .keyword {
     color: rgb(0, 0, 255);
   }

   pre .identifier {
     color: rgb(0, 0, 0);
   }

   pre .string {
     color: rgb(3, 106, 7);
   }
</style>

<!-- R syntax highlighter -->
<script type="text/javascript">
var hljs=new function(){function m(p){return p.replace(/&/gm,"&amp;").replace(/</gm,"&lt;")}function f(r,q,p){return RegExp(q,"m"+(r.cI?"i":"")+(p?"g":""))}function b(r){for(var p=0;p<r.childNodes.length;p++){var q=r.childNodes[p];if(q.nodeName=="CODE"){return q}if(!(q.nodeType==3&&q.nodeValue.match(/\s+/))){break}}}function h(t,s){var p="";for(var r=0;r<t.childNodes.length;r++){if(t.childNodes[r].nodeType==3){var q=t.childNodes[r].nodeValue;if(s){q=q.replace(/\n/g,"")}p+=q}else{if(t.childNodes[r].nodeName=="BR"){p+="\n"}else{p+=h(t.childNodes[r])}}}if(/MSIE [678]/.test(navigator.userAgent)){p=p.replace(/\r/g,"\n")}return p}function a(s){var r=s.className.split(/\s+/);r=r.concat(s.parentNode.className.split(/\s+/));for(var q=0;q<r.length;q++){var p=r[q].replace(/^language-/,"");if(e[p]){return p}}}function c(q){var p=[];(function(s,t){for(var r=0;r<s.childNodes.length;r++){if(s.childNodes[r].nodeType==3){t+=s.childNodes[r].nodeValue.length}else{if(s.childNodes[r].nodeName=="BR"){t+=1}else{if(s.childNodes[r].nodeType==1){p.push({event:"start",offset:t,node:s.childNodes[r]});t=arguments.callee(s.childNodes[r],t);p.push({event:"stop",offset:t,node:s.childNodes[r]})}}}}return t})(q,0);return p}function k(y,w,x){var q=0;var z="";var s=[];function u(){if(y.length&&w.length){if(y[0].offset!=w[0].offset){return(y[0].offset<w[0].offset)?y:w}else{return w[0].event=="start"?y:w}}else{return y.length?y:w}}function t(D){var A="<"+D.nodeName.toLowerCase();for(var B=0;B<D.attributes.length;B++){var C=D.attributes[B];A+=" "+C.nodeName.toLowerCase();if(C.value!==undefined&&C.value!==false&&C.value!==null){A+='="'+m(C.value)+'"'}}return A+">"}while(y.length||w.length){var v=u().splice(0,1)[0];z+=m(x.substr(q,v.offset-q));q=v.offset;if(v.event=="start"){z+=t(v.node);s.push(v.node)}else{if(v.event=="stop"){var p,r=s.length;do{r--;p=s[r];z+=("</"+p.nodeName.toLowerCase()+">")}while(p!=v.node);s.splice(r,1);while(r<s.length){z+=t(s[r]);r++}}}}return z+m(x.substr(q))}function j(){function q(x,y,v){if(x.compiled){return}var u;var s=[];if(x.k){x.lR=f(y,x.l||hljs.IR,true);for(var w in x.k){if(!x.k.hasOwnProperty(w)){continue}if(x.k[w] instanceof Object){u=x.k[w]}else{u=x.k;w="keyword"}for(var r in u){if(!u.hasOwnProperty(r)){continue}x.k[r]=[w,u[r]];s.push(r)}}}if(!v){if(x.bWK){x.b="\\b("+s.join("|")+")\\s"}x.bR=f(y,x.b?x.b:"\\B|\\b");if(!x.e&&!x.eW){x.e="\\B|\\b"}if(x.e){x.eR=f(y,x.e)}}if(x.i){x.iR=f(y,x.i)}if(x.r===undefined){x.r=1}if(!x.c){x.c=[]}x.compiled=true;for(var t=0;t<x.c.length;t++){if(x.c[t]=="self"){x.c[t]=x}q(x.c[t],y,false)}if(x.starts){q(x.starts,y,false)}}for(var p in e){if(!e.hasOwnProperty(p)){continue}q(e[p].dM,e[p],true)}}function d(B,C){if(!j.called){j();j.called=true}function q(r,M){for(var L=0;L<M.c.length;L++){if((M.c[L].bR.exec(r)||[null])[0]==r){return M.c[L]}}}function v(L,r){if(D[L].e&&D[L].eR.test(r)){return 1}if(D[L].eW){var M=v(L-1,r);return M?M+1:0}return 0}function w(r,L){return L.i&&L.iR.test(r)}function K(N,O){var M=[];for(var L=0;L<N.c.length;L++){M.push(N.c[L].b)}var r=D.length-1;do{if(D[r].e){M.push(D[r].e)}r--}while(D[r+1].eW);if(N.i){M.push(N.i)}return f(O,M.join("|"),true)}function p(M,L){var N=D[D.length-1];if(!N.t){N.t=K(N,E)}N.t.lastIndex=L;var r=N.t.exec(M);return r?[M.substr(L,r.index-L),r[0],false]:[M.substr(L),"",true]}function z(N,r){var L=E.cI?r[0].toLowerCase():r[0];var M=N.k[L];if(M&&M instanceof Array){return M}return false}function F(L,P){L=m(L);if(!P.k){return L}var r="";var O=0;P.lR.lastIndex=0;var M=P.lR.exec(L);while(M){r+=L.substr(O,M.index-O);var N=z(P,M);if(N){x+=N[1];r+='<span class="'+N[0]+'">'+M[0]+"</span>"}else{r+=M[0]}O=P.lR.lastIndex;M=P.lR.exec(L)}return r+L.substr(O,L.length-O)}function J(L,M){if(M.sL&&e[M.sL]){var r=d(M.sL,L);x+=r.keyword_count;return r.value}else{return F(L,M)}}function I(M,r){var L=M.cN?'<span class="'+M.cN+'">':"";if(M.rB){y+=L;M.buffer=""}else{if(M.eB){y+=m(r)+L;M.buffer=""}else{y+=L;M.buffer=r}}D.push(M);A+=M.r}function G(N,M,Q){var R=D[D.length-1];if(Q){y+=J(R.buffer+N,R);return false}var P=q(M,R);if(P){y+=J(R.buffer+N,R);I(P,M);return P.rB}var L=v(D.length-1,M);if(L){var O=R.cN?"</span>":"";if(R.rE){y+=J(R.buffer+N,R)+O}else{if(R.eE){y+=J(R.buffer+N,R)+O+m(M)}else{y+=J(R.buffer+N+M,R)+O}}while(L>1){O=D[D.length-2].cN?"</span>":"";y+=O;L--;D.length--}var r=D[D.length-1];D.length--;D[D.length-1].buffer="";if(r.starts){I(r.starts,"")}return R.rE}if(w(M,R)){throw"Illegal"}}var E=e[B];var D=[E.dM];var A=0;var x=0;var y="";try{var s,u=0;E.dM.buffer="";do{s=p(C,u);var t=G(s[0],s[1],s[2]);u+=s[0].length;if(!t){u+=s[1].length}}while(!s[2]);if(D.length>1){throw"Illegal"}return{r:A,keyword_count:x,value:y}}catch(H){if(H=="Illegal"){return{r:0,keyword_count:0,value:m(C)}}else{throw H}}}function g(t){var p={keyword_count:0,r:0,value:m(t)};var r=p;for(var q in e){if(!e.hasOwnProperty(q)){continue}var s=d(q,t);s.language=q;if(s.keyword_count+s.r>r.keyword_count+r.r){r=s}if(s.keyword_count+s.r>p.keyword_count+p.r){r=p;p=s}}if(r.language){p.second_best=r}return p}function i(r,q,p){if(q){r=r.replace(/^((<[^>]+>|\t)+)/gm,function(t,w,v,u){return w.replace(/\t/g,q)})}if(p){r=r.replace(/\n/g,"<br>")}return r}function n(t,w,r){var x=h(t,r);var v=a(t);var y,s;if(v){y=d(v,x)}else{return}var q=c(t);if(q.length){s=document.createElement("pre");s.innerHTML=y.value;y.value=k(q,c(s),x)}y.value=i(y.value,w,r);var u=t.className;if(!u.match("(\\s|^)(language-)?"+v+"(\\s|$)")){u=u?(u+" "+v):v}if(/MSIE [678]/.test(navigator.userAgent)&&t.tagName=="CODE"&&t.parentNode.tagName=="PRE"){s=t.parentNode;var p=document.createElement("div");p.innerHTML="<pre><code>"+y.value+"</code></pre>";t=p.firstChild.firstChild;p.firstChild.cN=s.cN;s.parentNode.replaceChild(p.firstChild,s)}else{t.innerHTML=y.value}t.className=u;t.result={language:v,kw:y.keyword_count,re:y.r};if(y.second_best){t.second_best={language:y.second_best.language,kw:y.second_best.keyword_count,re:y.second_best.r}}}function o(){if(o.called){return}o.called=true;var r=document.getElementsByTagName("pre");for(var p=0;p<r.length;p++){var q=b(r[p]);if(q){n(q,hljs.tabReplace)}}}function l(){if(window.addEventListener){window.addEventListener("DOMContentLoaded",o,false);window.addEventListener("load",o,false)}else{if(window.attachEvent){window.attachEvent("onload",o)}else{window.onload=o}}}var e={};this.LANGUAGES=e;this.highlight=d;this.highlightAuto=g;this.fixMarkup=i;this.highlightBlock=n;this.initHighlighting=o;this.initHighlightingOnLoad=l;this.IR="[a-zA-Z][a-zA-Z0-9_]*";this.UIR="[a-zA-Z_][a-zA-Z0-9_]*";this.NR="\\b\\d+(\\.\\d+)?";this.CNR="\\b(0[xX][a-fA-F0-9]+|(\\d+(\\.\\d*)?|\\.\\d+)([eE][-+]?\\d+)?)";this.BNR="\\b(0b[01]+)";this.RSR="!|!=|!==|%|%=|&|&&|&=|\\*|\\*=|\\+|\\+=|,|\\.|-|-=|/|/=|:|;|<|<<|<<=|<=|=|==|===|>|>=|>>|>>=|>>>|>>>=|\\?|\\[|\\{|\\(|\\^|\\^=|\\||\\|=|\\|\\||~";this.ER="(?![\\s\\S])";this.BE={b:"\\\\.",r:0};this.ASM={cN:"string",b:"'",e:"'",i:"\\n",c:[this.BE],r:0};this.QSM={cN:"string",b:'"',e:'"',i:"\\n",c:[this.BE],r:0};this.CLCM={cN:"comment",b:"//",e:"$"};this.CBLCLM={cN:"comment",b:"/\\*",e:"\\*/"};this.HCM={cN:"comment",b:"#",e:"$"};this.NM={cN:"number",b:this.NR,r:0};this.CNM={cN:"number",b:this.CNR,r:0};this.BNM={cN:"number",b:this.BNR,r:0};this.inherit=function(r,s){var p={};for(var q in r){p[q]=r[q]}if(s){for(var q in s){p[q]=s[q]}}return p}}();hljs.LANGUAGES.cpp=function(){var a={keyword:{"false":1,"int":1,"float":1,"while":1,"private":1,"char":1,"catch":1,"export":1,virtual:1,operator:2,sizeof:2,dynamic_cast:2,typedef:2,const_cast:2,"const":1,struct:1,"for":1,static_cast:2,union:1,namespace:1,unsigned:1,"long":1,"throw":1,"volatile":2,"static":1,"protected":1,bool:1,template:1,mutable:1,"if":1,"public":1,friend:2,"do":1,"return":1,"goto":1,auto:1,"void":2,"enum":1,"else":1,"break":1,"new":1,extern:1,using:1,"true":1,"class":1,asm:1,"case":1,typeid:1,"short":1,reinterpret_cast:2,"default":1,"double":1,register:1,explicit:1,signed:1,typename:1,"try":1,"this":1,"switch":1,"continue":1,wchar_t:1,inline:1,"delete":1,alignof:1,char16_t:1,char32_t:1,constexpr:1,decltype:1,noexcept:1,nullptr:1,static_assert:1,thread_local:1,restrict:1,_Bool:1,complex:1},built_in:{std:1,string:1,cin:1,cout:1,cerr:1,clog:1,stringstream:1,istringstream:1,ostringstream:1,auto_ptr:1,deque:1,list:1,queue:1,stack:1,vector:1,map:1,set:1,bitset:1,multiset:1,multimap:1,unordered_set:1,unordered_map:1,unordered_multiset:1,unordered_multimap:1,array:1,shared_ptr:1}};return{dM:{k:a,i:"</",c:[hljs.CLCM,hljs.CBLCLM,hljs.QSM,{cN:"string",b:"'\\\\?.",e:"'",i:"."},{cN:"number",b:"\\b(\\d+(\\.\\d*)?|\\.\\d+)(u|U|l|L|ul|UL|f|F)"},hljs.CNM,{cN:"preprocessor",b:"#",e:"$"},{cN:"stl_container",b:"\\b(deque|list|queue|stack|vector|map|set|bitset|multiset|multimap|unordered_map|unordered_set|unordered_multiset|unordered_multimap|array)\\s*<",e:">",k:a,r:10,c:["self"]}]}}}();hljs.LANGUAGES.r={dM:{c:[hljs.HCM,{cN:"number",b:"\\b0[xX][0-9a-fA-F]+[Li]?\\b",e:hljs.IMMEDIATE_RE,r:0},{cN:"number",b:"\\b\\d+(?:[eE][+\\-]?\\d*)?L\\b",e:hljs.IMMEDIATE_RE,r:0},{cN:"number",b:"\\b\\d+\\.(?!\\d)(?:i\\b)?",e:hljs.IMMEDIATE_RE,r:1},{cN:"number",b:"\\b\\d+(?:\\.\\d*)?(?:[eE][+\\-]?\\d*)?i?\\b",e:hljs.IMMEDIATE_RE,r:0},{cN:"number",b:"\\.\\d+(?:[eE][+\\-]?\\d*)?i?\\b",e:hljs.IMMEDIATE_RE,r:1},{cN:"keyword",b:"(?:tryCatch|library|setGeneric|setGroupGeneric)\\b",e:hljs.IMMEDIATE_RE,r:10},{cN:"keyword",b:"\\.\\.\\.",e:hljs.IMMEDIATE_RE,r:10},{cN:"keyword",b:"\\.\\.\\d+(?![\\w.])",e:hljs.IMMEDIATE_RE,r:10},{cN:"keyword",b:"\\b(?:function)",e:hljs.IMMEDIATE_RE,r:2},{cN:"keyword",b:"(?:if|in|break|next|repeat|else|for|return|switch|while|try|stop|warning|require|attach|detach|source|setMethod|setClass)\\b",e:hljs.IMMEDIATE_RE,r:1},{cN:"literal",b:"(?:NA|NA_integer_|NA_real_|NA_character_|NA_complex_)\\b",e:hljs.IMMEDIATE_RE,r:10},{cN:"literal",b:"(?:NULL|TRUE|FALSE|T|F|Inf|NaN)\\b",e:hljs.IMMEDIATE_RE,r:1},{cN:"identifier",b:"[a-zA-Z.][a-zA-Z0-9._]*\\b",e:hljs.IMMEDIATE_RE,r:0},{cN:"operator",b:"<\\-(?!\\s*\\d)",e:hljs.IMMEDIATE_RE,r:2},{cN:"operator",b:"\\->|<\\-",e:hljs.IMMEDIATE_RE,r:1},{cN:"operator",b:"%%|~",e:hljs.IMMEDIATE_RE},{cN:"operator",b:">=|<=|==|!=|\\|\\||&&|=|\\+|\\-|\\*|/|\\^|>|<|!|&|\\||\\$|:",e:hljs.IMMEDIATE_RE,r:0},{cN:"operator",b:"%",e:"%",i:"\\n",r:1},{cN:"identifier",b:"`",e:"`",r:0},{cN:"string",b:'"',e:'"',c:[hljs.BE],r:0},{cN:"string",b:"'",e:"'",c:[hljs.BE],r:0},{cN:"paren",b:"[[({\\])}]",e:hljs.IMMEDIATE_RE,r:0}]}};
hljs.initHighlightingOnLoad();
</script>




</head>

<body>
<hr/>

<p>title: &ldquo;Peer Assessment 1&rdquo;
author: &ldquo;Robert Huntsman&rdquo;
date: &ldquo;Saturday, March 26, 2016&rdquo;
output: html_document
keep_md: true</p>

<hr/>

<!-- rmarkdown v1 -->

<h1>Loading and preprocessing the data</h1>

<pre><code class="r">setwd(&quot;C:/Users/rhuntsman/Desktop/Coursera/Reproducible Research/Project 1&quot;)
library(ggplot2)
</code></pre>

<pre><code>## Warning: package &#39;ggplot2&#39; was built under R version 3.1.3
</code></pre>

<pre><code class="r">library(plyr)
</code></pre>

<pre><code>## Warning: package &#39;plyr&#39; was built under R version 3.1.3
</code></pre>

<pre><code class="r">library(dplyr)
</code></pre>

<pre><code>## Warning: package &#39;dplyr&#39; was built under R version 3.1.3
</code></pre>

<pre><code>## 
## Attaching package: &#39;dplyr&#39;
</code></pre>

<pre><code>## The following objects are masked from &#39;package:plyr&#39;:
## 
##     arrange, count, desc, failwith, id, mutate, rename, summarise,
##     summarize
</code></pre>

<pre><code>## The following objects are masked from &#39;package:stats&#39;:
## 
##     filter, lag
</code></pre>

<pre><code>## The following objects are masked from &#39;package:base&#39;:
## 
##     intersect, setdiff, setequal, union
</code></pre>

<pre><code class="r">library(lattice)
</code></pre>

<pre><code>## Warning: package &#39;lattice&#39; was built under R version 3.1.3
</code></pre>

<pre><code class="r">library(data.table)
</code></pre>

<pre><code>## Warning: package &#39;data.table&#39; was built under R version 3.1.3
</code></pre>

<pre><code>## 
## Attaching package: &#39;data.table&#39;
</code></pre>

<pre><code>## The following objects are masked from &#39;package:dplyr&#39;:
## 
##     between, last
</code></pre>

<pre><code class="r">library(knitr)
library(lubridate)
</code></pre>

<pre><code>## Warning: package &#39;lubridate&#39; was built under R version 3.1.3
</code></pre>

<pre><code>## 
## Attaching package: &#39;lubridate&#39;
</code></pre>

<pre><code>## The following objects are masked from &#39;package:data.table&#39;:
## 
##     hour, mday, month, quarter, wday, week, yday, year
</code></pre>

<pre><code>## The following object is masked from &#39;package:plyr&#39;:
## 
##     here
</code></pre>

<pre><code class="r">library(psych)
</code></pre>

<pre><code>## Warning: package &#39;psych&#39; was built under R version 3.1.3
</code></pre>

<pre><code>## 
## Attaching package: &#39;psych&#39;
</code></pre>

<pre><code>## The following objects are masked from &#39;package:ggplot2&#39;:
## 
##     %+%, alpha
</code></pre>

<pre><code class="r">library(reshape)
</code></pre>

<pre><code>## Warning: package &#39;reshape&#39; was built under R version 3.1.3
</code></pre>

<pre><code>## 
## Attaching package: &#39;reshape&#39;
</code></pre>

<pre><code>## The following object is masked from &#39;package:lubridate&#39;:
## 
##     stamp
</code></pre>

<pre><code>## The following object is masked from &#39;package:data.table&#39;:
## 
##     melt
</code></pre>

<pre><code>## The following object is masked from &#39;package:dplyr&#39;:
## 
##     rename
</code></pre>

<pre><code>## The following objects are masked from &#39;package:plyr&#39;:
## 
##     rename, round_any
</code></pre>

<pre><code class="r">library(rmarkdown)
</code></pre>

<pre><code>## Warning: package &#39;rmarkdown&#39; was built under R version 3.1.3
</code></pre>

<pre><code class="r">activity &lt;- read.csv(&quot;activity.csv&quot;,stringsAsFactors=FALSE)
activity$date &lt;- as.Date(activity$date)
</code></pre>

<h1>What is mean number of steps taken per day?</h1>

<pre><code class="r">dailySteps &lt;- aggregate(steps ~ date, activity, sum)
names(dailySteps) &lt;- c(&quot;date&quot;,&quot;steps&quot;)
hist(dailySteps$steps,col=&quot;blue&quot;,xlab=&quot;# Steps&quot;,ylab=&quot;Frequency of Days with X Steps&quot;, main=&quot;Histogram of Total Steps by Day&quot;)
</code></pre>

<p><img src="data:image/png;base64,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" alt="plot of chunk unnamed-chunk-2"/></p>

<pre><code class="r">meanSteps&lt;- round(mean(dailySteps$steps),0)
medianSteps &lt;- round(median(dailySteps$steps),0)

sprintf(&quot;Mean Steps Per Day: %s&quot;, meanSteps)
</code></pre>

<pre><code>## [1] &quot;Mean Steps Per Day: 10766&quot;
</code></pre>

<pre><code class="r">sprintf(&quot;Median Steps Per Day: %s&quot;, medianSteps)
</code></pre>

<pre><code>## [1] &quot;Median Steps Per Day: 10765&quot;
</code></pre>

<h1>What is the average daily activity pattern?</h1>

<pre><code class="r">intMeanSteps &lt;- aggregate(steps ~ interval, activity, mean)
intMedianSteps &lt;- aggregate(steps ~ interval, activity, median)

xyplot(steps ~ interval,data=intMeanSteps,type=&quot;l&quot;,col=&quot;blue&quot;, lwd=2, main = &quot;Avgerage Steps Per Interval&quot;, xlab = &quot;Interval&quot;, ylab = &quot;Steps&quot;)
</code></pre>

<p><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAfgAAAH4CAMAAACR9g9NAAAAjVBMVEUAAAAAADoAAGYAAP8AOjoAOmYAOpAAZrY6AAA6ADo6AGY6OgA6OmY6OpA6kNtmAABmADpmAGZmOgBmOjpmZjpmZmZmtv+QOgCQOjqQOmaQZgCQkGaQkLaQtpCQ2/+2ZgC2tma225C2/7a2/9u2///bkDrbtmbb/7bb/9vb////tmb/25D//7b//9v///84PoMBAAAACXBIWXMAAAsSAAALEgHS3X78AAAQ3UlEQVR4nO3di3rayAGGYdlqbXfb4M1ui5N2a7YtNDWGuf/Lq87ofJxBh//7niwxiBkUvUgI4nU8Q5J5c68AzRPwogEvGvCiAS8a8KItGf765j3bmOfy6nlPH8EXh32PewbV3u3y+njMXe2cqzJiWS0Z/vPFs7HlYs3gKXSoF63c1Xt4r12WX5nuuYAf3cn7W7h5D9F+H14Gh4DHf7+GO+8p3i+vbw9/DZjOCVZledTny9NHYPCft5g/G/r4uxc9sYLnV/oEu0SDD96u/AgmZkwHXctzhXf6c7aeyfoAP65gK//rJdiW5/A4fXl9eI829x8CxmDrhu1MdMvTj2g/ffqoLo8KYPfRdBFWYWg46pKMDu96gy8+wodJ4aObn+vmevpvup7pjMCP6/Ml2MDBpgv2p/dI//MluHaKvgg2cbjsdhYQbuTq8mhRxBJ+HR6e80N34aF9H91i0lmSQ33DI0SDoidiea5nc1vP9N7Aj+sUbNvwv+BiF23oc7h5w53y7CU+0bY2Mdjjsbo8mekQy8dzZENDlWDqCDs71CfjKo+QwkdH8AS+fKd0PdP1AX5U6WE1svwRbsMm+PBFuhU+OdzXw8fD0ydQsvc3wgeDGuHT9UzXB/hRxZsvPkY//CN8wS4eysPiLR7rlQ/1Waf0jD47PMdDk0N9dC05Sc/gS48QLyvDV+6UrGe6PsCP6hSdnEUiwXMgOWkvnLyFp3Ph7efkGVJdHk2U7oDhrc+5ockX2WKTgy89QrysCF+YK75Tsp7p+gA/pgAm3AlP2XskE710Jm/XDrFrssWDa7vwbKCyPC6kTV4SkidFfFL2e3yfdLHJw5cewZThS3Mld0rWM1kf4G129vKH8eHL07KTftHWBJ+82dqNXV4I+BV1Tk7zxy7PBzxJBrxowIsGvGjAiwa8aMCLBrxowIsGvGjAiwa8aMCLBrxowIsGvGjAiwa8aMCLBrxoDuDtTslsbiYDfpuzAS86G/CiswEvOhvworM5hPdo4bmCHz2S7hLwogEvGvCiAS8a8KIBLxrwogEvGvCiAS8a8KIBLxrwogEvGvCiAS8a8KIBLxrwogEvGvCiAS+aHrzvz70Gi0gRHnkDvGzAiwa8aMCLBrxowIsGvGjj4cN/Yj36t7LDfyT7kP5T2/3mnTPgo8bDn58D7/356SP71X/eOQM+atqh/rQ/7czl6zG+TMb0+EkbcwZ8VDtTB1+w05/25vr9GF8OGDljwEdN2eMPwcG+usf3GTlnwEdNObnbB5e8xq+08fCH8CVix1n9SuN9vGjAiwa8aJLwyAMvG/CiAS8a8KIBLxrwogEvGvCiAS8a8KIBLxrwogEvGvCiAS8a8KIBLxrwogEvGvCiacIjD7xqwIsGvGjAiwa8aMCLpgjPTy43wMsGvGhy8CE68MDLBrxowIsGvGjAiwa8aMCLBrxowIsGvGhq8D7wccCLBrxowIsGvGjAiwa8aMCLJgmPPPCyAS8a8KIBL5omPPLAqwa8aMCLBrxowIsmCo888KIBLxrwoonB+8AnAS+aKry8PPCiAS+aHHz1K82AF00WXl0eeNGAFw140abAX74ejTl43sN7cBlc9B85W8CnTYA/e49Hc/0Wgp+fPoJf/eedLeDTxsNff7t+P5rLry/esznt4t0/GhNnbxVtltfWlm9naucL4c/BXn/an/bRld4jZwv4tCmv8an1eZff4/uMnC3g06bCn3cm2OPX+BoP/Oil0R4fnNXvzBrP6oEfvdTNSKcBnyYMry0PvGjAiwa8aMCLBrxoyvDS8sCLBrxowIsGvGjAiwa8aMCLBrxowIsGvGjAiwa8aMCLBrxowIsGvGjAiwa8aMCLBrxowIsGvGjAi6YFX5IGftxSNyNdBnwW8KIBLxrwogEvGvCiAS8a8KIBL5o0vLI88KIBLxrwogEvGvCiAS8a8KIBLxrwogEvGvCiAS8a8KIBLxrwogEvGvCiAS8a8KIBL1pf+NPTx8nz9pbmnSvgs3rCX35+D359/nS0M+9cAZ/VF/7rMdjngd9OvQ/13sP7mUP9dlI/uZOV14YX3uX7wl/fPM97tjXvXAGf1RP++rYLLk/95YFfeP3P6rNLC/POFfBZvc/qnw17/Jbqu8e/enGPPfd54BceZ/WiAS/agLdzTz9+frc071wBn9X/7dznl4/z04edeeeq6iwr3//tXAC/vbdzwHcsjff4E3u8hYdcRoM+si25RweAg/fwnl72nneuZoFfpvyEs/pz+KY+eNnPfvWfd66Azxr/ke31t+v3ozntom/S2N2WJZ/0uFjZyQGf1c6U3J59blfcqyP4ffhbfFkzcmEtHv5+z5JBe3yp+j2+z7xztQL4e8lP+eQuhOc1vvMh1wx/eX02ny/lv6GJju6c1Xc95JrhD7vg/dx+g38tC3zr0vD1O/zWaj65G/OQK4cPP7Xb3PfVA9+x9LCPvunusL1DvXP5dcMHb+SfPsIzPEvzztVE+DEq64a3Pe9cAZ8FPPCDl7oZ6TLgs4AHfvBSNyNdNhl+OAvwSwj4LOCBH7zUzUiXAZ8FPPCDl7oZ6TLgs4AHfvBSNyNdBnwW8P23tA/81HnnCvgs4JcGfyd54BcHnzT4kYYF/GLgwzsG/wHvoIXD+7m1cS0PPPCDl7oZ6bJ54HsOAt5d94cvYHZOD7yjgM8CHvjBS92MdBnwWcA7h+/7EMC7C/gs4IEfvNTNSJctDL64AHh3LQ7eL10D3k3zwDc+RgXeB95NK4J3LQ888IOXuhnpMuCzgJ8X3i9eA95Ns8JXB5fO5oB31kzwKX95dA38qBUbkxR8Hdyy4Met2JiAnw++/MYdeFcBfwt44AcvdTPSYbPBJx/ZAz9PtXDAD1/qZqS7gM+lAJ9uQuBzacCnWx/4LCF4v/YbXoEfvtTNSPvd4GsXDplnLHz8rOuEH7liYwJ+OPwQEuBnzD78kDHZ78DfOz/54Kxh4ZB5gJ82731rhR+wgUfAZ/cEfoaWAF85aTfAOw/4mrYGX7e5LMFnnwMA72TktOo/nPNbtmPfDXybZcD7eeDvlTP43GEDeCcjp+UKPv9ZwEj4yiMBbzF38LffRsFXHyl+hwe8nZrgmzdjrw2c+xymQtT2NAD+XrmB9zvg+00OvMOcwN8mTc/w8oMGwJdlgbeWC/iCjqmB73kCUTlSFO4A/KQa4Pu+DHfdoxG+z6dDXfBD12tSwNuAb5TvD1+ZAPhBzQTfNAvw9+q+8Dm7+mmAv1dN8G0juucsfun7N+3il12Tl94M5G8CflrV7d/1OZsl+Pp5gL9X88HXTgT8vWr/kKR+RPecxemBdzJyUtVPQdrP7Mx0eB94OyMnBXzfgK+8JW+7x+3Ynly4g3csv0H48lvnjg1Yg9F8D+CzDp738B5cBhcDR7qoDH1P+Dqp7cJfv4Xg56eP4NewkU6aDt++21qFL9y0NvjLry/eszntzOXrMRkTZ2PlhmcBvlVvQ/CtTN1858ejOe1Pe3P9fhw20kk18F0bsAPer/urOLMB+AlL0867/B4/ZKTt/OTzmsIJ11R4vxY++UoW/rwzwR6/lNf4HPxtswJfl42z+p1Zyln93PDlR6p53Sh/vVp46yOndIMv6HSNyX09Bj5315a5q49VuAn4KRXg01OwZcKXwYGfUoqdoliCL927N3zdEyEdDLzN8vDGMXx6WBkG7yfPx8oZYQO8M/0Nw992/e4x2dc94HNU4+ALU3bCO5LfCHz+TKl8PO3adAWFOvjSnTvhczdUHqrsDvy0/Nvrbk6v31azDO/7nfB1jw78qOrh+47NTzME3m+AL79+N85mgJ/YIuAN8HPAZy/n4+GrB+Ju+MqJGvD3zCV8+WobvO8X71Gzng2PDvyo5oI3FXgf+Hvm596yj4avOefugDfW4GvWGPgezQNvSjDZBI2aDfC1a5weUQb8UQa0Dfh0Y98VPh1TuDIKvn6FK6cQVtsOfM5kIfBNh+/SLU24wHc3Eb74ol0zdeHqFPjaR2+4H/DdVeCHDc6eLn3gizfUw5vbRd9Hr10CfEfpHjZqKxXha3bx0p1tw7esF/AdLRG+59oAP6XFwfd/a9FyL+A7G3VSdxtsD97k4Xs+etuKAd/eVPj8ueEE+Nxy4O+STXhTlq27c/567XIbYsB3dnsnPmpwC3z13V0/+JFPwspct2ksPwOAXzx8/uMlewG/Knh7+MDnPrHLvRPLvSGv3LvlqslDjViXylwVeFvy24IfOXjR8IUzV+CL2Ya/zQq81XltB/zggDe3rVuCv53vFe/dctXK+/f8XKXnI/DFgB8c8K3w1Q0N/JR5bWcV3gAP/CLg05XzbX7TLfC37VuZrU6xCl2ZbMK61K9YBm9xduAHwlcHt16fEvCduYMf+sjW4bNHAb4mu/D5JSMmm7AqTXMB39DEzQH8sKVuRo5pOvyg20dMNaZW+KmPA7xZAXz8GSLwlYAfHPAG+KFL3Ywc02R4a9M6gs/YgS9kcWtPzC58YV6/8PYD+LBtwpfmTc/s0xumTQi83RzCm/SlPrlh2oTA280tfO6rqQ+0CfjluDuDrzwE8EYN3s63ZABvt7usio1P7YFfY8BHybknp/eT/uDArzXgZeEnHe2BX2vAAz8m4Nca8MCPCfjVBjzwIwJ+tQEP/IiAX21l+GGbAfjVVoUfsh2AX23Fv6Ib+u4O+NXmF35OAvBa5b8VD3ih8t9nrwav7A68asCLlv8fa4AXqgRfeofXMnCF8OU/D/DJb7n/l9rPLatvlfAT3r5urQp87oOdTcFnz+rsujq8n728587vSv9PdU1zwE85Vtf8fABpeJPbHvlt4Xf9G6f3hi/9X97JbZUVLNyU+9ovwWujJ+Ve1Asvga1bxxL8wXt47zfSbypbbrJzlNyIupEG+GJV+ObtYwf+/PQR/Oo1shG+X+kfrvx8IVOGb3+VtwN/2pnL12MyJq5jDctX6vb/wp6d/hnyxwbcG+vcMu1MveH35vr9OGYkzZT9PX7YSJqpu7/G0zK6+1k9LaO1fXJHlgJeNOBFA1404EUDXjTgRQNeNOBFA1404EUDXjTgRQNeNOBFA1404EUDXjTgRXMGTwvPEfydpmQ2N5MBv83ZgBedDXjR2YAXnQ140dnmgKc1BLxowIsGvGjAiwa8aMCLZh2+8pMzRs8TThTPNnXO6Kf35KeaNGEym5XVu7553tOHvXXrn2346s/KGdf123s229Q5z97jsTDVpAmj2Wyt3vk5kN5bW7cB2Yav/nSscV1+ffGek9kmznn9LfxBbfmppkwYz2Zx9cxpb2vdhmQdvvLz8MZ1DnarYItEs02eM4LPTTVtwnCoxdULdnp769a/pe7xYeedpZ3A5h5vMhc7q3d4NhbXrX9LfY0/78Kjh6WXvWgftfY6Gs1mafWub3tjLK5b/5Z8Vr+zdaIb7aPWzpyT2ays3iH83rjdFs7qaSUBLxrwogEvGvCiAS8a8KIBLxrwogEvGvCiAS+aKPznT8fKV8332WLAA69UgPr55e+et7+8eo/H6MJ8/uWX8Bsfr9/eP1+CJcBvsRD+ZRd+B0TIe9iZ07P5fNmH30P5+eXHz+/RHYDfXolr/NslgL58jW447cJfxqTXtxvwP4VH+vC75KMbvvzvW/RdMMGxH/gNVoSPv7kxvOH67Z9fPi6vew71G60AH77GJ6/25uTtomfA55/egd9gN/jrW3RW//Aen8UH4KG+98df9sDTBgNeNOBFA1404EUDXjTgRQNeNOBFA1404EUDXrT/A4/ARS3BAv3aAAAAAElFTkSuQmCC" alt="plot of chunk unnamed-chunk-3"/></p>

<pre><code class="r">maxInterval &lt;- intMeanSteps[which(intMeanSteps$steps==max(intMeanSteps$steps)),]
sprintf(&quot;Max Step Interval: %s&quot;, maxInterval$interval)
</code></pre>

<pre><code>## [1] &quot;Max Step Interval: 835&quot;
</code></pre>

<pre><code class="r">sprintf(&quot;Max Steps: %s&quot;, maxInterval$steps)
</code></pre>

<pre><code>## [1] &quot;Max Steps: 206.169811320755&quot;
</code></pre>

<h1>Imputing missing values</h1>

<pre><code class="r">missing &lt;- nrow(activity[is.na(activity$steps) == TRUE,])
sprintf(&quot;Numberof NA&#39;s in original data set is %s&quot;, missing)
</code></pre>

<pre><code>## [1] &quot;Numberof NA&#39;s in original data set is 2304&quot;
</code></pre>

<pre><code class="r">activity$steps2 &lt;- ifelse(is.na(activity$steps), intMeanSteps[intMeanSteps$interval == activity$interval, 2], activity$steps)

dailySteps2 &lt;- aggregate(steps2 ~ date, activity, sum)
names(dailySteps2) &lt;- c(&quot;date&quot;,&quot;steps&quot;)

hist(dailySteps2$steps, col=&quot;blue&quot;, main = &quot;Total Daily Steps (NA&#39;s Replaced)&quot;, xlab=&quot;Daily Steps&quot;, ylab=&quot;# Days&quot;)
</code></pre>

<p><img src="data:image/png;base64,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" alt="plot of chunk unnamed-chunk-4"/></p>

<pre><code class="r">meanDailySteps2 &lt;- mean(dailySteps2$steps)
medianDailySteps2 &lt;- median(dailySteps2$steps)

sprintf(&quot;Original Mean Steps Per Day: %s&quot;, meanSteps)
</code></pre>

<pre><code>## [1] &quot;Original Mean Steps Per Day: 10766&quot;
</code></pre>

<pre><code class="r">sprintf(&quot;Original Median Steps Per Day: %s&quot;, medianSteps)
</code></pre>

<pre><code>## [1] &quot;Original Median Steps Per Day: 10765&quot;
</code></pre>

<pre><code class="r">sprintf(&quot;New Mean Steps Per Day, NA replaced: %s&quot;, round(meanDailySteps2,0))
</code></pre>

<pre><code>## [1] &quot;New Mean Steps Per Day, NA replaced: 10766&quot;
</code></pre>

<pre><code class="r">sprintf(&quot;New Median Steps Per Day, NA replaced: %s&quot;, round(medianDailySteps2,0))
</code></pre>

<pre><code>## [1] &quot;New Median Steps Per Day, NA replaced: 10766&quot;
</code></pre>

<h2>The mean and median number of steps between the original and new (NA&#39;s replaced) data sets are approximately equal.</h2>

<h3>The impact of imputing values for NA&#39;s is minimal.  However, the new mean and median are identical, a result</h3>

<h3>of replacing NA&#39;s with mean values.</h3>

<h1>Are there differences in activity patterns between weekdays and weekends?</h1>

<pre><code class="r">activity$weekdayGroup &lt;- as.factor(ifelse(weekdays(activity$date) %in% c(&quot;Saturday&quot;,&quot;Sunday&quot;),&quot;Weekend&quot;,&quot;Weekday&quot;))
weekdayIntervalSteps &lt;- aggregate(steps2 ~ interval + weekdayGroup, activity, mean)

xyplot(steps2 ~ interval | weekdayGroup,
       data = weekdayIntervalSteps,
       type = &quot;l&quot;,
       layout=c(1,2),
       lty = c(1, 2, 2, 1),
       lwd = c(2,2),
       col = c(&quot;blue&quot;),
       main = &quot;Average Steps Per Interval: Weekdays vs. Weekends&quot;,
       xlab = &quot;Interval&quot;,
       ylab = &quot;Average Steps Per Interval&quot;)
</code></pre>

<p><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAfgAAAH4CAMAAACR9g9NAAABFFBMVEUAAAAAAC4AADoAAFIAAGYAAP8AM1IAM3MAOjoAOmYAOpAAXJEAZrY6AAA6AC46ADo6AFI6AGY6MwA6M1I6M3M6OgA6Ojo6OmY6OpA6XJE6gHM6gK86kJA6kNtmAABmAC5mADpmAFJmAGZmMwBmMy5mM3NmOgBmOjpmXFJmZjpmZmZmkJBmo8xmtrZmtv+QMwCQMy6QM1KQOgCQOjqQOmaQXACQZgCQkGaQkLaQo3OQtpCQxZGQxcyQ27aQ29uQ2/+2XAC2XC62ZgC2tma225C25cy2/7a2/9u2///bgC7bkDrbtmbb25Db5a/b5czb/7bb/9vb////o1L/tmb/xXP/25D/5ZH/5a//5cz//7b//9v///8r+X0ZAAAACXBIWXMAAAsSAAALEgHS3X78AAAa4ElEQVR4nO2dC5vbuHWGuY4Zt7OaZpNsWm9cTZxNNpumruwd97JJpx2vEqdjtfHG1lzF//8/CpAgCZAgBeJCgjzf98xIBHVwAOIlbhQJJRlEUsnUGYCmEcATFcATFcATFcATFcATlRfwh/Nk5RD94SxJTj6wje3GwJJJa/Zw9vhKCh71pcQ4nD+6ZHF4Nh7O8rz0ONdaHNegNHS5tUq1S17A35wmvXnuV0FzxcvEEDwvQM1nch6O+1JjcHvmnXne605iH+AHpaH7OD7wu+R3vJy3+eHkr7uiXrKT/J/Yge4FLNYyPP5znv+dVG9vTk8+sIP+n/MCfxX18R+T/Hxip1V5XhUHv03WzRSyotzKSIemL270syp7Ij88Rlnae+bz5vSfTzcszlrKn9gonLMt7vlfeC4KHyzBKxG3ymRdDNLOIWm0i6BKteHRQT7Aswz+6XTFDyxvxViRbvOKuc4znJx8n9fTkw956G8Y5urzXOxgNllxcKywlKg81oOIzU1r8GoKH7Kq3PLWQ+fr5H/L7JUeZfD87Ns/+q8z5lnKf7XBzXaCu5IrvnNbu+Su9s10ynIyTKNZBCt9WTjKB/ib01V+5uedGD9sfoT8dLiqO39+VDenzGgnf55/lB8W3+ZNoRyVl0WyyfdkpRfR1HekkEfKC77pa5XV2Sut5baVm21P/nqeH0kVsdpgpn86XfNDFYdQH1Mdo3IlF4Mk4zTkIigcyQXnRz7A89N0VzRR67zE94ngU4xnCmCPr/KejVfa6nPhYFuQb0TlVJjHHHbV1It4rRRK8HkLLsA3jcrslflROtXto/8+X2U71hWt6ojVBqvAP+Mxq0MofRzOWYO2yuRMVukoO4ekIWe7KC+RasujvTyAr1oknrfvz/JOTylx3jH1ghfNvR58Eb08gcQZ3wmeReoEX2avzI8Cfpfwznf/6A+nay2UosSrQyh9ZLs8hpzJKh1l55A05CJQwLc82ssD+KIMisb60X8kZWPFVZR4Qa/Z1FfalSP6qnkuooqmPg+JQXoFvpFC8VkTfMtIZK/MjwL+5vTv8/r1O/ZaRaw2iv53XTf1VYAdfZmDaiYh0lF3DkijyrY4GqWDMZqwHJcH8PkQtchOWQpbMRgpSnwvTozm4K468qRs6qsBmRgJJolUtzJ5SqOmUHymgld8FUYie2V+lH6enWP5MEWMNkT+yo3StMpV6YPHKGti1QiLdFoti1kaUrbF0WjLwlHu4IsZSFFvxVSmOKp8iFKeB+td0emJ6dw2kQan/HBEQYlyKEY3fyxsyo8zZS6rppA1wTd8CSORPZEfdYC3lQ+gyp/YeDgT0zbO4B/FmbXe1ZNYKZO1F7FzaBpSEYijqVJVk3HR6Jds9zXwXlWD/ti189Lyjq4xwYvJ2Pq4ZTYf8HPJZ1Oj1vi8YzS8qj+TAt11fHMQvfDtHFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFEBPFH5B+/Roz9XyFTAxP17XEgZh/cE8OE9LSVTAD+dK4AP7wqZCpi4f48LKePwnkYFn0BRaTzw91BEAniiAniiAni93ry4v/+Y8JdP1Q/uXl1oI9y9fDFCtvwJ4PV694z9//ZZsSEL4JcN/vrz93evfs9fLu5vz5IfvL0Xb2zH3csn74vA9ef/lvBmgYV++CuAXwL421++vf3qL9+8Ze/3b57dv2MNfvHGwLMNEbg+fXb/8cl7Hsr7hRkJ4PVifK+/YD09e7n9xUV+HhRvd69+wriLwPVnrNZ/lp8daOqXAf7+3Yt3L+4/PmNd/C1fg+mTC/F29/LnX70v9wnw/C0fDs5IAN+hj59+d3F//cV3ec3mO8Qbawr4yVAEUOOXB/7215+/Z5R/+jbvz8uO/Akf7fEBXxEQ4NHHLwj83Us+gX/DX1i7/slF+cap80qeB0rwdy8xql8K+KVrRPBQVBoPvHVMKIAAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqgAnqhkHIfzJDn5kG2TR5eZeO21t08Jmlwyjv2K8d7sTz5Uf/32xmlYrb0BBVUTym6zW2cPX14Vrxp7+5SsY0IB1MDBKv1ukx3+9ap4PWpvnxI0rVQcW9bYo8aTkDq427BX/328a0wogGQcW97brzGqJyHM44kK4IkK4IkK4IkK4IkK4IkK4IkK4IkK4IkK4IkK4IkK4IkK4IXSdOocjCuAF0qJkQd4IYD3a+8j5igCeL/2PmKOIoD3a+8j5igCeL/2PmKOIoD3a+8j5igCeL/2PmKOIoD3a+8j5igCeL/2PmIGVE0b4P3a+4gZUDVugPdr7yNmQE0BPo4zDOBbW+OlOaUAvrU1XppTCuBbW+GTjA98/mT0NuHPS9J4aBLgc+2Tx1fZ4TUHTmQpFMLgJSiHb/kiGA9fnyarjMjCCJbgXdDFAl4JcfB7Vut3GyJLoViDt2cXLXiu/Ro13iyaVZJxgt+v+dpXRJZCAfhCeY3f8vVQMKo3i2aVZHzg/dv7iBlQAB/K3kfMgAL4UPY+YgaUT/CGDgA+BvkFb+QB4GMQwIey9xEzoOzA69kBvO+YAVVTAHi/9j5iBtT44JkRwE8vz+ANXAB8FBoRfJUOwE+uNB0NvJQOwE+uccGnYgPgJ9cE4PkrwE+tnEZVEwODLxIC+BiUShhcwFeVudsHwMekCkXmCl446gWv/EsZmEYAPy34ycgDfNlOhwdfWgD81PIKvr/3BviY5B18N3k5FYCfWvXUehrw8nWEsQXwY4LPdOCnIQ/wY4CXL9hKVgA/kezBq4TNwcvpVuAnIQ/wI4Fvp1uDn4I8wNfgjcu/G3wHeT343A3AT6AmeFMA7uDraT3ATyBpxOUCPrUBnwL8dFLA9113a8dbGHixBg5/TpbC07K94HtwVJdea80bfL4GTvFkPIk1cI6A77vw3gVeT14LXnLhfCTD1V4Dp1gLg8SKGM7gS0MX8EqU8c6B9sIIxeo3JNbA8Qm+nptrI8wBPGq82BsdeJ+nhWYNHO99vGvMYJJgxQH+SHfvczSgXQOH2KjeB/h0MPg0La0V8H1ow4H3b+8jZjCFAK8l3/SljuUBfmxZgm+MCVrg2/EAPi4BfDh7HzGDaTLwKmKAH1t24KsBWT0btALfykaZj578ArwXybCGg1fQjQXeG3q64OVSHgK+2N0NXscO4CPSeOB1vAB+MlmClzt22XYweM12E3wzFsD7UKNf1oHXFbIWvGo8lFcPeM0ssMfREAF8uW0GvjERkK1bNrqU9Dmp3wE+uEKCb3uyAN+OFgP4hzNxC8djzXe3XlIKrUa/XE7Olc81keqNXvBNT4PBp2mc4MOnFFqxgi9nDe02COC9yAa8MnQPCL7G351lRzmA39Fr6kcCX9m3wPfP84fIHvzD88v9KtutQqUUWv3gBYBmFHmzH3xjrmcAXmQhVa4vNA1jAP/lVfEXKKXQOgpeNy+TN6mCP7y+ZH83P14I+Pq13uENfD+vIeC9kXfo4xnzff4TdWFSCi1NNYwEfBo5+NFihlHfZE0GL4GYGLy2+7EVwOt3yRR0g+zj4BV6BuDL1+jBP5zp7rv3l1JoGYPP1DpZfd4HvtlOLAk86+RPk8R4NjdT8MoHhuBFOAB4fbat5NrU72d8Aadvl2fwBjmZEfhZ13hdAcrTuwZ4zXTvOPjW6dKXldmAn3kfPxR8o9Apgze+ZmeXUmCNBv44KXX82AavnEHtqw92UnBsE/6kZMfjkk37w+tuq6MpTa9j4ItXJ/CmVVQx04NX24RjDk0k4yhQdj0g3bQXt2IYDO6iXAolXvDZOOAlKA9fn7LBWteSCMLePiXrmEHUC75ud8twDbKyOAbeuFNuzs9l8KmUVrAaz6dmu03XIihte/uUIpAF+HQa8MV/GhA8135tXOMP58nJ98+NO/oZgZd4Vxs24LMG0c6sNLy1wWeSSYAav85YjTft4w/n65unfaY9KUWgyMA3nMleqg4+GHg+ql93LoLStGfNAgM/1xsxtKXXLFkJxzTgZQfm1wWM5HAjRl7jdzOt8T3gm2OrcrMBXvWgB986PzryMivwvI9PEvOrdzMCX4dV0pOCb727iej38frCa47CncBrzTqzYwC+P+9D5XrJdqZ9vA/wjaiO4LvzGRf46hGqWfbxHWXXLGZ38Iaz7hmBn/eXNIbgs7HA92Y0NvChUwqonvrVV6pdjYEufGy/oaIEv5/tI1Td4I05mYJ3xBQj+IezTdCUAqoPvLELfdNunJZ5Ok0H7cuINqLYx/dAGgDet2FX9G7wTp4dmvqt8UM0VimFkw/w7omZRg/Ulrg09bPs4/vghgDvqAjBh04pgNK0f/wG8P7sfcT0o5J6T3kB/HH72S1+ZDIiAnh/9j5i+pDRUDg+7n143Qb2iwavfsF6fAoUI/huuU3pyIA3KSiA92fvI6a1qmIR37ceBx8+T/40FfgZXLlTvyLzcJ0zKrldvnNa/ChoSh5U3w0h3giANz3ERV+5K75mTaWKvzjwmu/u1JFNl5bex8tFsyjsfeBNDnj54M3KYYbqAm92prvdXh3pI1TSYF4FP14WRlAneKP7vlwfqJj8ESrNsamdulmXN0ulmht0xBWL+vMOOU3nYniEqj1iq2kvazDXId2tQPXxd0aL4hGqQXjU6py1K3VarftNALsefH3lojNa46HJnsclW/a+HqFKvSvLGufDkqU7eoMvpZTHpHsfkG7bm6p/KRQHvMVb/UV768gtMjs7ablL7WFHNBlK/5IIwt46g1PfiAEpknH0L4LSsOerGw66vxrgo5ICfkCNP5xvMvMfKWimBE0u2z6enyHDvqYB+KhkO6rPwZ8PaesBPipZ32wJ8PMWmbtsIVWL/nYO6hbAExXAExXAE9WI4KGoZA9+d/JhN+CybXIPRSSHGzGeX7K/Ab8tO/WhQrKc7sBhdR7gZyqXpj55dLlfbFP/5sX9/ceEv3yqfnD36qLcevli9Gx504iDu6kPdZjePWP/v31WbMgC+GWDv/78/d2r3/OXi/vbs+QHb+/FG9tx9/LJexb44a9e3F+fJqxZYM0Ds586y4Pkdl/9oF+anPpQh+n2l29vv/rLN2/Z+/2bZ/fvWINfvDHwbIMHWE9w+4uL++vP3n5kgWfHfcYkp7ts2evOmPzMwDO+11+wqsxeOF1+HhRvd69+8iw/L8qmPj9F3n93ccxjXHJ9THrAffVTH+pAvXvx7gWrx6yLv+XfRH5yId7uXv78q/e8mhcDwDcJa//vXv3nV/Nq6Z1G9atswTWejeZZJb7+4ru8mvMd4o01BfxkKGr87dmL/BzIh4GzkvNj0sbfyM8N/O2v2XDt7tVP3xb9+ZP34o0P7tiAr+jjOfTrv7vI/+cljOq7dPeST+Df8BfWyH9yUb5x6oz33ct8VP8uyd/uvnk7dX4HCuC9iA0BZ6YRH5OGopI1+Egek4bsNPvHpCE7RfGYNDS+XC/ZzvWXJskL99wR1YiXbAemBAWV85M06OPnqUWvZQt1C308UVmDfzhb8VUxjJ+ZBPi4ZA1+u84fkx7wtezAlKCgcnk+nt9aPetRPY1lsfRyAc+v2g24r35gSiOIyIJoWtk39Zv8prvtnJt6gLewZxP5kw98hBcqpREE8OHsfcQMJoAPZ+8jZjABfDh7HzGDCeDD2fuIGUwAH87eR8xgAngr+3h/k8ZUVFY214n0zZYAb2O/gJstAd7GfgE3WwK8lf38b7YE+HD2PmIGE8CHs/cRM5gA3sa+vN3S9B4cgI9KDjV+WyyFYjqhA/io5H5f/Z8NJ3QAH5WcFz86+b+nqPEzlMvgbst6+NXDmeHalgAflQiP6nt/enXx8gmeX9FhI73iR8xaP2UG8FHJaRHjxmxuv+L3YBY/W9j+8UKAj0oOo/rnl4x084GK3ab4oVL550rtFl0JLuLgB0JRpnPFn/wxPxXynyZu/0AxwEclh+nc60v2pz5Qwe+yb9d4u5SCC+At7RnzfZKs6x3FT46ij5+FfI7q+byenQgY1c9BhBdGSEmTd+rjg6YUXABvZy++lp3vr0kDfEh7HzEDCeBD2vuIGUgcOsBb2M/8gYoCOcAPtp/7AxUAb2k/9wcqAN7Sfu4PVAC8rf3MH6gA+KD2PmKGUQmeKHnq4Mned+dy5c68mbdJKbRK3kTJu9T4m9NBPyo8MKXQqnGTRO/a1O9ne61egk2RPGp8O0BC6ON1IQIiP6rXhgjIEfxuvt/HA7y1/T5p3lfnM6XQAng7ezaye3S5NXxg0ial0AJ4K/viWzmAn62sazy/5W4D8LOV0+Cude+8z5RCC+Bd7A/nGNXPU5jH60IEBPC6EAEBvC5EQH7B55O8bX5dJ/qHJgHen/2eX8AtnqmL/zFpgPdmf/iWL4Lx8PVpssriXwqFOnjrpVB04uD5rRm7TfxLoVAH79W+ZL1fx78UCsB7tM9r/JqvfYU+PnIFqPHbfGEcjOrjFubxuhABAbwuREAArwsREMDrQgQE8LoQAQG8LkRAAK8LERDA60IEBPC6EAEBvC5EQACvCxEQwOtCBATwuhABAbw+uHgBvD64eAG8Prh4Abw+uHgBvD64eAG8PjilRskKwOuDU2qUVfcAXh+cUgAfVAAf1N5HzDAC+KD2PmKGEcAHtfcRM4wAPqi9j5hhBPBB7X3EDCOAD2rvI2YYAbxHe7EUyix+P74FPhry8wOfL4VSPCA9t8ekY/qVitmBL5ZCKZZEmNtSKPTAe18KpVgEZW5LodAD79VeX+PtUgotgPdony+Fgj7+aGLHjGcJfr6j+qDgBzifIfgwMcMI4IPa+4gZRmODN/aepmOMNwC+CoYs7WHgx2AP8FUwIvAjVHuAr4JRgc9Cd/UAXwVjAx/2iyNq4DtLNe9ZAyYL8NOqBKAjMRX4zi+IAd6fvIAfDuQIeBm1ZAjw/iQKWdujDwA/lIg5+BTg3aUpOIAXogm+uEZiYN7lF+DHiGmtuYMPSZ4k+OIf4EPa+4hprXmCt8nRcC0ZvK6w03LCpP3M3PFAIj0xlEoO8D7ULOyyoncVJ8B7tPcR01Yd4HsQmDsG+BFi2qoJOS3VaT/A8dCs9LQzAO9XLcq91DOA92rvI6alIgPf5R7gfau4SiNfBzsCbBD4YUgAfkSV4Muy9Ax+EJMB4K1yNFzLBq9cnJ0afIf/Bni7HA0XDfBpGQb4UksEL4GupnBZrODVISjAu6gFXr5C3xvPxPWxqwE9rnVxAN6fpBpeNqR+wNfMxcuALHUloHoCeBdpwPddQZHiGRso0wWjLJWvzThqJ6D9NIgCgN8m/EHZ6Z6WVWp3Df54GQYHn2kiLQf84TUHPuHz8VrwJpT6LVoXgwBe1cPXp8kqm3ANHKVpHzIMswBv6Lq0iwm81zVwuPaP+To4E66B0+jTB1fLzk/dwWvOw+XUeK79esI1cKqmfWihyRHakScCHwq9f/D7dcZq/MR9vAfwzdiNPUWToklDl7ApeF2igciHGdWvp1wDp2rifYNvBrXdifbiTmM6oCRzHHwQ9Aucxw/u2xsRxfYw8EqVBng/MQfKupzUa6dG4Ot+RXKR1h9oogJ8KE0LPqvAy7W8yw/Ae5QH8P3NdRlUwFcAa/D6k0gPvvSjyxLAm2kq8OXFmRq8drQxCLx+rOhDAC9HHA4+q8ClNT1xRoiTwRB82vyszgnAG8m+nGR0reI2AS95ae/X+amBt0aEtQHAm8kb+G5emR687KXzFGqCl/cDvIucwZdD8yPgpR68Bb5u31vclHlAY9IH8C4aB3zWCb74qHNiqIz8VPAaxD3g3c4HgFdilu1t2qp+A8F3V1PFXtfht7LUCd6FPMC34g4EXzcQw8BrOvVO8FpfAN+QI/hytNaogEPA6yuvFE/qUo7kvA2+sw8ZpuWBdyqOJnhlvNY0lT8cBF6a9x3LrNZ1Y8NKAN+IXA+6U1Ua0zpOu1oagO+zUqwVO4DvkDfwWaaw70mnpznoSMQ4r6JfAPjjcgWvvNe7+7xagzfPkzpXtHHTEMA3Io8AfnCeMrWVAHitXAd3OieTgm94rPodfQ9kKoA389nrdAzwmQI+rTZs0wF4M5/Tg8+qXqi6AATwsiYBPzCCZSbqN8G8NYk09wbwZj6HOg2XC3n42ZzgD0gV4KfyOVxpY2IH8LLiYBREevDSBH/IwQP8fKQbzcnXfwcd/LLADzv2uUk/jKcLXrmoFWI4HYv0R1dP6+WBX7Grx1kw8KYPTZaZThu7Gkbyx4qlBHvh3LtUfouU1nP8VNrXoVDgzR+TTj1q4MEsRtXB1+VwrExCgTdfCsUHburgK6Vyt9f7HYP/pVAKTbgUCmSiMWq8XUpQUE3fx0OTaPJRPTSNFjCPh2wE8EQF8EQF8EQF8EQF8EQ1IngoKo0GfgSP/lwhUwET9+9xIWUc3hPAh/e0lEwB/HSuAD68K2QqYOL+PS6kjMN7igI8NAsBPFEBPFEBPFEBPFEBPFEBPFH5Bt+6J9POSf371S4O8xvCZTf2zoQr53wdzpPk5IOnTLnIM/j2XdgWkn+/2sXhPnl8pbixd5a78pGv/YqR3vjJlJM8g28/d2Eh+ferHRwevuXP/shurJ0Vrjzli/9Es49Muck3+NaTVhaSf7/ayWEOXnLj4IzH85QvVuk9ZcpFMdZ4rvL3q50ceqvxWcXGPV/bVeYrUy6KsY+Xf7/ayWFeTf10p7krD/k6nG+yzFemXBTrqH7tY8ybV1M/A2jhyjlfW3573Hp5o3poLgJ4ogJ4ogJ4ogJ4ogJ4ogJ4ogJ4ogJ4ogJ4ogJ4ogJ4oqIF/ubHV62tbptFC+C7bRYtcuBvnv57kmwezpLHV/lLdvMPv+G3Px5eX96csk8Afoni4E/X/D4Ijne7znar7OZ0w++ivHn6/fPL3ADglyfBtXh7YKAfvsx37Nb8L8vKMAFRBn+W8Pvk8x1P//o6vxeGtf0Av0Cp4ItbHPmOw+s/PP3wcLZBU79QKeB5Hy96+2yXrPMz4OZHlwC/QNXgD+f5qP7RZTGKZ8A5/eRvf7MBeGjJAniiAniiAniiAniiAniiAniiAniiAniiAniiAniiAnii+n/u7l7XGIIG8wAAAABJRU5ErkJggg==" alt="plot of chunk unnamed-chunk-5"/></p>

<p><img src="data:image/png;base64,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" alt="plot of chunk unnamed-chunk-6"/></p>

<pre><code>## png 
##   3
</code></pre>

<pre><code>## png 
##   2
</code></pre>

<p><img src="data:image/png;base64,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" alt="plot of chunk unnamed-chunk-6"/></p>

<pre><code>## png 
##   3
</code></pre>

<pre><code>## png 
##   2
</code></pre>

<p><img src="data:image/png;base64,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" alt="plot of chunk unnamed-chunk-6"/></p>

<pre><code>## png 
##   3
</code></pre>

<pre><code>## png 
##   2
</code></pre>

<p><img src="data:image/png;base64,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" alt="plot of chunk unnamed-chunk-6"/></p>

<pre><code>## png 
##   3
</code></pre>

<pre><code>## png 
##   2
</code></pre>

</body>

</html>

