---
title: Setup
---

## Running on Sagehen (recommended at Pomona)

If you have a Pomona College HPC account, you can complete this workshop entirely in the browser via the Sagehen OnDemand portal — no local installation required:

1. Sign in at [https://ondemand.hpc.pomona.edu](https://ondemand.hpc.pomona.edu) with your Pomona credentials and DUO MFA at [https://duo.pomona.edu](https://duo.pomona.edu).
2. Open the **Interactive Apps > RStudio Server** app and request a small session on the **amd** partition (e.g., 4 cores, 16 GB RAM, 4 hours).
3. Save your project to `/bigdata/lab/<labname>/your-username/` so it persists between sessions and is backed up alongside your data.

If you do not yet have an HPC account, contact `its-hpc@pomona.edu` to request one.

This lesson assumes you have current versions of the following installed on your computer (or available in your OnDemand RStudio session on Sagehen):

1. the [R software](https://cran.r-project.org/mirrors.html) itself, and
2. [RStudio Desktop](https://www.rstudio.com/products/rstudio/download/#download).

You also need to download some files to follow this lesson:

1. Make a new folder in your Desktop called `r-novice-inflammation`.
2. Download [r-novice-inflammation-data.zip](data/r-novice-inflammation-data.zip)
  and move the file to this folder.
3. If it's not unzipped yet, double-click on it to unzip it. You should end up
  with a new folder called `data`.
4. You can access this folder from the Unix shell with:

```bash
$ cd
$ cd Desktop/r-novice-inflammation/data
```

<!-- highlight <labname>/<myusername> placeholders in code blocks; remove if the varnish theme handles this natively -->
<script>(function(){var CSS='.sh-placeholder{color:#c2410c;font-weight:700}[data-bs-theme="dark"] .sh-placeholder,html.dark .sh-placeholder{color:#fdba74}@media (prefers-color-scheme: dark){[data-bs-theme="auto"] .sh-placeholder{color:#fdba74}}';var RX=/<labname>|<myusername>/g;function firstMatch(el){var w=document.createTreeWalker(el,NodeFilter.SHOW_TEXT,null),nodes=[],full='';while(w.nextNode()){nodes.push({n:w.currentNode,s:full.length});full+=w.currentNode.nodeValue;}RX.lastIndex=0;var m;while((m=RX.exec(full))){var s=m.index,e=s+m[0].length,inSpan=false,parts=[];for(var j=0;j<nodes.length;j++){var ns=nodes[j].s,ne=ns+nodes[j].n.nodeValue.length;if(ne<=s||ns>=e)continue;parts.push({node:nodes[j].n,a:Math.max(s-ns,0),b:Math.min(e-ns,nodes[j].n.nodeValue.length)});var p=nodes[j].n.parentNode;while(p&&p!==el){if(p.classList&&p.classList.contains('sh-placeholder')){inSpan=true;break;}p=p.parentNode;}}if(!inSpan&&parts.length)return parts;}return null;}function wrapParts(parts){for(var i=parts.length-1;i>=0;i--){var t=parts[i].node,txt=t.nodeValue,a=parts[i].a,b=parts[i].b;var span=document.createElement('span');span.className='sh-placeholder';span.textContent=txt.slice(a,b);var f=document.createDocumentFragment();if(a>0)f.appendChild(document.createTextNode(txt.slice(0,a)));f.appendChild(span);if(b<txt.length)f.appendChild(document.createTextNode(txt.slice(b)));t.parentNode.replaceChild(f,t);}}function run(){var st=document.createElement('style');st.textContent=CSS;document.head.appendChild(st);document.querySelectorAll('pre,code').forEach(function(el){var guard=0,parts;while((parts=firstMatch(el))&&guard++<500){wrapParts(parts);}});}if(document.readyState==='loading'){document.addEventListener('DOMContentLoaded',run);}else{run();}})();</script>
