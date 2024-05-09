<html><head>

<meta charset="utf-8">
<meta name="generator" content="pandoc">
<meta http-equiv="X-UA-Compatible" content="IE=EDGE">


<meta name="author" content="Zheng Li">

<meta name="date" content="2022-06-07">

<title>Introduction to BASS</title>

<script src="site_libs/header-attrs-2.12.1/header-attrs.js"></script>
<script src="site_libs/jquery-3.6.0/jquery-3.6.0.min.js"></script>
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="site_libs/bootstrap-3.3.5/css/cosmo.min.css" rel="stylesheet">
<script src="site_libs/bootstrap-3.3.5/js/bootstrap.min.js"></script>
<script src="site_libs/bootstrap-3.3.5/shim/html5shiv.min.js"></script>
<script src="site_libs/bootstrap-3.3.5/shim/respond.min.js"></script>
<style>h1 {font-size: 34px;}
       h1.title {font-size: 38px;}
       h2 {font-size: 30px;}
       h3 {font-size: 24px;}
       h4 {font-size: 18px;}
       h5 {font-size: 16px;}
       h6 {font-size: 12px;}
       code {color: inherit; background-color: rgba(0, 0, 0, 0.04);}
       pre:not([class]) { background-color: white }</style>
<script src="site_libs/jqueryui-1.11.4/jquery-ui.min.js"></script>
<link href="site_libs/tocify-1.9.1/jquery.tocify.css" rel="stylesheet">
<script src="site_libs/tocify-1.9.1/jquery.tocify.js"></script>
<script src="site_libs/navigation-1.1/tabsets.js"></script>
<link href="site_libs/highlightjs-9.12.0/textmate.css" rel="stylesheet">
<script src="site_libs/highlightjs-9.12.0/highlight.js"></script>
<link href="site_libs/font-awesome-5.1.0/css/all.css" rel="stylesheet">
<link href="site_libs/font-awesome-5.1.0/css/v4-shims.css" rel="stylesheet">

<link rel="icon" href="https://github.com/workflowr/workflowr-assets/raw/main/img/reproducible.png">
<!-- Add a small amount of space between sections. -->
<style type="text/css">
div.section {
  padding-top: 12px;
}
</style>



<style type="text/css">
  code{white-space: pre-wrap;}
  span.smallcaps{font-variant: small-caps;}
  span.underline{text-decoration: underline;}
  div.column{display: inline-block; vertical-align: top; width: 50%;}
  div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
  ul.task-list{list-style: none;}
    </style>

<style type="text/css">code{white-space: pre;}</style>
<script type="text/javascript">
if (window.hljs) {
  hljs.configure({languages: []});
  hljs.initHighlightingOnLoad();
  if (document.readyState && document.readyState === "complete") {
    window.setTimeout(function() { hljs.initHighlighting(); }, 0);
  }
}
</script>









<style type="text/css">
.main-container {
  max-width: 940px;
  margin-left: auto;
  margin-right: auto;
}
img {
  max-width:100%;
}
.tabbed-pane {
  padding-top: 12px;
}
.html-widget {
  margin-bottom: 20px;
}
button.code-folding-btn:focus {
  outline: none;
}
summary {
  display: list-item;
}
details > summary > p:only-child {
  display: inline;
}
pre code {
  padding: 0;
}
</style>


<style type="text/css">
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu>.dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
  border-radius: 0 6px 6px 6px;
}
.dropdown-submenu:hover>.dropdown-menu {
  display: block;
}
.dropdown-submenu>a:after {
  display: block;
  content: " ";
  float: right;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
  border-width: 5px 0 5px 5px;
  border-left-color: #cccccc;
  margin-top: 5px;
  margin-right: -10px;
}
.dropdown-submenu:hover>a:after {
  border-left-color: #adb5bd;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left>.dropdown-menu {
  left: -100%;
  margin-left: 10px;
  border-radius: 6px 0 6px 6px;
}
</style>

<script type="text/javascript">
// manage active state of menu based on current page
$(document).ready(function () {
  // active menu anchor
  href = window.location.pathname
  href = href.substr(href.lastIndexOf('/') + 1)
  if (href === "")
    href = "index.html";
  var menuAnchor = $('a[href="' + href + '"]');

  // mark it active
  menuAnchor.tab('show');

  // if it's got a parent navbar menu mark it active as well
  menuAnchor.closest('li.dropdown').addClass('active');

  // Navbar adjustments
  var navHeight = $(".navbar").first().height() + 15;
  var style = document.createElement('style');
  var pt = "padding-top: " + navHeight + "px; ";
  var mt = "margin-top: -" + navHeight + "px; ";
  var css = "";
  // offset scroll position for anchor links (for fixed navbar)
  for (var i = 1; i <= 6; i++) {
    css += ".section h" + i + "{ " + pt + mt + "}\n";
  }
  style.innerHTML = "body {" + pt + "padding-bottom: 40px; }\n" + css;
  document.head.appendChild(style);
});
</script>

<!-- tabsets -->

<style type="text/css">
.tabset-dropdown > .nav-tabs {
  display: inline-table;
  max-height: 500px;
  min-height: 44px;
  overflow-y: auto;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.tabset-dropdown > .nav-tabs > li.active:before {
  content: "";
  font-family: 'Glyphicons Halflings';
  display: inline-block;
  padding: 10px;
  border-right: 1px solid #ddd;
}

.tabset-dropdown > .nav-tabs.nav-tabs-open > li.active:before {
  content: "&#xe258;";
  border: none;
}

.tabset-dropdown > .nav-tabs.nav-tabs-open:before {
  content: "";
  font-family: 'Glyphicons Halflings';
  display: inline-block;
  padding: 10px;
  border-right: 1px solid #ddd;
}

.tabset-dropdown > .nav-tabs > li.active {
  display: block;
}

.tabset-dropdown > .nav-tabs > li > a,
.tabset-dropdown > .nav-tabs > li > a:focus,
.tabset-dropdown > .nav-tabs > li > a:hover {
  border: none;
  display: inline-block;
  border-radius: 4px;
  background-color: transparent;
}

.tabset-dropdown > .nav-tabs.nav-tabs-open > li {
  display: block;
  float: none;
}

.tabset-dropdown > .nav-tabs > li {
  display: none;
}
</style>

<!-- code folding -->



<style type="text/css">

#TOC {
  margin: 25px 0px 20px 0px;
}
@media (max-width: 768px) {
#TOC {
  position: relative;
  width: 100%;
}
}

@media print {
.toc-content {
  /* see https://github.com/w3c/csswg-drafts/issues/4434 */
  float: right;
}
}

.toc-content {
  padding-left: 30px;
  padding-right: 40px;
}

div.main-container {
  max-width: 1200px;
}

div.tocify {
  width: 20%;
  max-width: 260px;
  max-height: 85%;
}

@media (min-width: 768px) and (max-width: 991px) {
  div.tocify {
    width: 25%;
  }
}

@media (max-width: 767px) {
  div.tocify {
    width: 100%;
    max-width: none;
  }
}

.tocify ul, .tocify li {
  line-height: 20px;
}

.tocify-subheader .tocify-item {
  font-size: 0.90em;
}

.tocify .list-group-item {
  border-radius: 0px;
}


</style>



<script type="text/javascript" src="https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script><style>body {padding-top: 65px; padding-bottom: 40px; }
.section h1{ padding-top: 65px; margin-top: -65px; }
.section h2{ padding-top: 65px; margin-top: -65px; }
.section h3{ padding-top: 65px; margin-top: -65px; }
.section h4{ padding-top: 65px; margin-top: -65px; }
.section h5{ padding-top: 65px; margin-top: -65px; }
.section h6{ padding-top: 65px; margin-top: -65px; }
</style><style type="text/css">.MathJax_Hover_Frame {border-radius: .25em; -webkit-border-radius: .25em; -moz-border-radius: .25em; -khtml-border-radius: .25em; box-shadow: 0px 0px 15px #83A; -webkit-box-shadow: 0px 0px 15px #83A; -moz-box-shadow: 0px 0px 15px #83A; -khtml-box-shadow: 0px 0px 15px #83A; border: 1px solid #A6D ! important; display: inline-block; position: absolute}
.MathJax_Menu_Button .MathJax_Hover_Arrow {position: absolute; cursor: pointer; display: inline-block; border: 2px solid #AAA; border-radius: 4px; -webkit-border-radius: 4px; -moz-border-radius: 4px; -khtml-border-radius: 4px; font-family: 'Courier New',Courier; font-size: 9px; color: #F0F0F0}
.MathJax_Menu_Button .MathJax_Hover_Arrow span {display: block; background-color: #AAA; border: 1px solid; border-radius: 3px; line-height: 0; padding: 4px}
.MathJax_Hover_Arrow:hover {color: white!important; border: 2px solid #CCC!important}
.MathJax_Hover_Arrow:hover span {background-color: #CCC!important}
</style><style type="text/css">#MathJax_About {position: fixed; left: 50%; width: auto; text-align: center; border: 3px outset; padding: 1em 2em; background-color: #DDDDDD; color: black; cursor: default; font-family: message-box; font-size: 120%; font-style: normal; text-indent: 0; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; z-index: 201; border-radius: 15px; -webkit-border-radius: 15px; -moz-border-radius: 15px; -khtml-border-radius: 15px; box-shadow: 0px 10px 20px #808080; -webkit-box-shadow: 0px 10px 20px #808080; -moz-box-shadow: 0px 10px 20px #808080; -khtml-box-shadow: 0px 10px 20px #808080; filter: progid:DXImageTransform.Microsoft.dropshadow(OffX=2, OffY=2, Color='gray', Positive='true')}
#MathJax_About.MathJax_MousePost {outline: none}
.MathJax_Menu {position: absolute; background-color: white; color: black; width: auto; padding: 2px; border: 1px solid #CCCCCC; margin: 0; cursor: default; font: menu; text-align: left; text-indent: 0; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; z-index: 201; box-shadow: 0px 10px 20px #808080; -webkit-box-shadow: 0px 10px 20px #808080; -moz-box-shadow: 0px 10px 20px #808080; -khtml-box-shadow: 0px 10px 20px #808080; filter: progid:DXImageTransform.Microsoft.dropshadow(OffX=2, OffY=2, Color='gray', Positive='true')}
.MathJax_MenuItem {padding: 2px 2em; background: transparent}
.MathJax_MenuArrow {position: absolute; right: .5em; padding-top: .25em; color: #666666; font-size: .75em}
.MathJax_MenuActive .MathJax_MenuArrow {color: white}
.MathJax_MenuArrow.RTL {left: .5em; right: auto}
.MathJax_MenuCheck {position: absolute; left: .7em}
.MathJax_MenuCheck.RTL {right: .7em; left: auto}
.MathJax_MenuRadioCheck {position: absolute; left: 1em}
.MathJax_MenuRadioCheck.RTL {right: 1em; left: auto}
.MathJax_MenuLabel {padding: 2px 2em 4px 1.33em; font-style: italic}
.MathJax_MenuRule {border-top: 1px solid #CCCCCC; margin: 4px 1px 0px}
.MathJax_MenuDisabled {color: GrayText}
.MathJax_MenuActive {background-color: Highlight; color: HighlightText}
.MathJax_MenuDisabled:focus, .MathJax_MenuLabel:focus {background-color: #E8E8E8}
.MathJax_ContextMenu:focus {outline: none}
.MathJax_ContextMenu .MathJax_MenuItem:focus {outline: none}
#MathJax_AboutClose {top: .2em; right: .2em}
.MathJax_Menu .MathJax_MenuClose {top: -10px; left: -10px}
.MathJax_MenuClose {position: absolute; cursor: pointer; display: inline-block; border: 2px solid #AAA; border-radius: 18px; -webkit-border-radius: 18px; -moz-border-radius: 18px; -khtml-border-radius: 18px; font-family: 'Courier New',Courier; font-size: 24px; color: #F0F0F0}
.MathJax_MenuClose span {display: block; background-color: #AAA; border: 1.5px solid; border-radius: 18px; -webkit-border-radius: 18px; -moz-border-radius: 18px; -khtml-border-radius: 18px; line-height: 0; padding: 8px 0 6px}
.MathJax_MenuClose:hover {color: white!important; border: 2px solid #CCC!important}
.MathJax_MenuClose:hover span {background-color: #CCC!important}
.MathJax_MenuClose:hover:focus {outline: none}
</style><style type="text/css">.MathJax_Preview .MJXf-math {color: inherit!important}
</style><style type="text/css">.MJX_Assistive_MathML {position: absolute!important; top: 0; left: 0; clip: rect(1px, 1px, 1px, 1px); padding: 1px 0 0 0!important; border: 0!important; height: 1px!important; width: 1px!important; overflow: hidden!important; display: block!important; -webkit-touch-callout: none; -webkit-user-select: none; -khtml-user-select: none; -moz-user-select: none; -ms-user-select: none; user-select: none}
.MJX_Assistive_MathML.MJX_Assistive_MathML_Block {width: 100%!important}
</style><style type="text/css">#MathJax_Zoom {position: absolute; background-color: #F0F0F0; overflow: auto; display: block; z-index: 301; padding: .5em; border: 1px solid black; margin: 0; font-weight: normal; font-style: normal; text-align: left; text-indent: 0; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; -webkit-box-sizing: content-box; -moz-box-sizing: content-box; box-sizing: content-box; box-shadow: 5px 5px 15px #AAAAAA; -webkit-box-shadow: 5px 5px 15px #AAAAAA; -moz-box-shadow: 5px 5px 15px #AAAAAA; -khtml-box-shadow: 5px 5px 15px #AAAAAA; filter: progid:DXImageTransform.Microsoft.dropshadow(OffX=2, OffY=2, Color='gray', Positive='true')}
#MathJax_ZoomOverlay {position: absolute; left: 0; top: 0; z-index: 300; display: inline-block; width: 100%; height: 100%; border: 0; padding: 0; margin: 0; background-color: white; opacity: 0; filter: alpha(opacity=0)}
#MathJax_ZoomFrame {position: relative; display: inline-block; height: 0; width: 0}
#MathJax_ZoomEventTrap {position: absolute; left: 0; top: 0; z-index: 302; display: inline-block; border: 0; padding: 0; margin: 0; background-color: white; opacity: 0; filter: alpha(opacity=0)}
</style><style type="text/css">.MathJax_Preview {color: #888}
#MathJax_Message {position: fixed; left: 1em; bottom: 1.5em; background-color: #E6E6E6; border: 1px solid #959595; margin: 0px; padding: 2px 8px; z-index: 102; color: black; font-size: 80%; width: auto; white-space: nowrap}
#MathJax_MSIE_Frame {position: absolute; top: 0; left: 0; width: 0px; z-index: 101; border: 0px; margin: 0px; padding: 0px}
.MathJax_Error {color: #CC0000; font-style: italic}
</style><style type="text/css">.MJXp-script {font-size: .8em}
.MJXp-right {-webkit-transform-origin: right; -moz-transform-origin: right; -ms-transform-origin: right; -o-transform-origin: right; transform-origin: right}
.MJXp-bold {font-weight: bold}
.MJXp-italic {font-style: italic}
.MJXp-scr {font-family: MathJax_Script,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-frak {font-family: MathJax_Fraktur,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-sf {font-family: MathJax_SansSerif,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-cal {font-family: MathJax_Caligraphic,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-mono {font-family: MathJax_Typewriter,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-largeop {font-size: 150%}
.MJXp-largeop.MJXp-int {vertical-align: -.2em}
.MJXp-math {display: inline-block; line-height: 1.2; text-indent: 0; font-family: 'Times New Roman',Times,STIXGeneral,serif; white-space: nowrap; border-collapse: collapse}
.MJXp-display {display: block; text-align: center; margin: 1em 0}
.MJXp-math span {display: inline-block}
.MJXp-box {display: block!important; text-align: center}
.MJXp-box:after {content: " "}
.MJXp-rule {display: block!important; margin-top: .1em}
.MJXp-char {display: block!important}
.MJXp-mo {margin: 0 .15em}
.MJXp-mfrac {margin: 0 .125em; vertical-align: .25em}
.MJXp-denom {display: inline-table!important; width: 100%}
.MJXp-denom > * {display: table-row!important}
.MJXp-surd {vertical-align: top}
.MJXp-surd > * {display: block!important}
.MJXp-script-box > *  {display: table!important; height: 50%}
.MJXp-script-box > * > * {display: table-cell!important; vertical-align: top}
.MJXp-script-box > *:last-child > * {vertical-align: bottom}
.MJXp-script-box > * > * > * {display: block!important}
.MJXp-mphantom {visibility: hidden}
.MJXp-munderover {display: inline-table!important}
.MJXp-over {display: inline-block!important; text-align: center}
.MJXp-over > * {display: block!important}
.MJXp-munderover > * {display: table-row!important}
.MJXp-mtable {vertical-align: .25em; margin: 0 .125em}
.MJXp-mtable > * {display: inline-table!important; vertical-align: middle}
.MJXp-mtr {display: table-row!important}
.MJXp-mtd {display: table-cell!important; text-align: center; padding: .5em 0 0 .5em}
.MJXp-mtr > .MJXp-mtd:first-child {padding-left: 0}
.MJXp-mtr:first-child > .MJXp-mtd {padding-top: 0}
.MJXp-mlabeledtr {display: table-row!important}
.MJXp-mlabeledtr > .MJXp-mtd:first-child {padding-left: 0}
.MJXp-mlabeledtr:first-child > .MJXp-mtd {padding-top: 0}
.MJXp-merror {background-color: #FFFF88; color: #CC0000; border: 1px solid #CC0000; padding: 1px 3px; font-style: normal; font-size: 90%}
.MJXp-scale0 {-webkit-transform: scaleX(.0); -moz-transform: scaleX(.0); -ms-transform: scaleX(.0); -o-transform: scaleX(.0); transform: scaleX(.0)}
.MJXp-scale1 {-webkit-transform: scaleX(.1); -moz-transform: scaleX(.1); -ms-transform: scaleX(.1); -o-transform: scaleX(.1); transform: scaleX(.1)}
.MJXp-scale2 {-webkit-transform: scaleX(.2); -moz-transform: scaleX(.2); -ms-transform: scaleX(.2); -o-transform: scaleX(.2); transform: scaleX(.2)}
.MJXp-scale3 {-webkit-transform: scaleX(.3); -moz-transform: scaleX(.3); -ms-transform: scaleX(.3); -o-transform: scaleX(.3); transform: scaleX(.3)}
.MJXp-scale4 {-webkit-transform: scaleX(.4); -moz-transform: scaleX(.4); -ms-transform: scaleX(.4); -o-transform: scaleX(.4); transform: scaleX(.4)}
.MJXp-scale5 {-webkit-transform: scaleX(.5); -moz-transform: scaleX(.5); -ms-transform: scaleX(.5); -o-transform: scaleX(.5); transform: scaleX(.5)}
.MJXp-scale6 {-webkit-transform: scaleX(.6); -moz-transform: scaleX(.6); -ms-transform: scaleX(.6); -o-transform: scaleX(.6); transform: scaleX(.6)}
.MJXp-scale7 {-webkit-transform: scaleX(.7); -moz-transform: scaleX(.7); -ms-transform: scaleX(.7); -o-transform: scaleX(.7); transform: scaleX(.7)}
.MJXp-scale8 {-webkit-transform: scaleX(.8); -moz-transform: scaleX(.8); -ms-transform: scaleX(.8); -o-transform: scaleX(.8); transform: scaleX(.8)}
.MJXp-scale9 {-webkit-transform: scaleX(.9); -moz-transform: scaleX(.9); -ms-transform: scaleX(.9); -o-transform: scaleX(.9); transform: scaleX(.9)}
.MathJax_PHTML .noError {vertical-align: ; font-size: 90%; text-align: left; color: black; padding: 1px 3px; border: 1px solid}
</style><style type="text/css">.MathJax_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax .merror {background-color: #FFFF88; color: #CC0000; border: 1px solid #CC0000; padding: 1px 3px; font-style: normal; font-size: 90%}
.MathJax .MJX-monospace {font-family: monospace}
.MathJax .MJX-sans-serif {font-family: sans-serif}
#MathJax_Tooltip {background-color: InfoBackground; color: InfoText; border: 1px solid black; box-shadow: 2px 2px 5px #AAAAAA; -webkit-box-shadow: 2px 2px 5px #AAAAAA; -moz-box-shadow: 2px 2px 5px #AAAAAA; -khtml-box-shadow: 2px 2px 5px #AAAAAA; filter: progid:DXImageTransform.Microsoft.dropshadow(OffX=2, OffY=2, Color='gray', Positive='true'); padding: 3px 4px; z-index: 401; position: absolute; left: 0; top: 0; width: auto; height: auto; display: none}
.MathJax {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax:focus, body :focus .MathJax {display: inline-table}
.MathJax.MathJax_FullWidth {text-align: center; display: table-cell!important; width: 10000em!important}
.MathJax img, .MathJax nobr, .MathJax a {border: 0; padding: 0; margin: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; vertical-align: 0; line-height: normal; text-decoration: none}
img.MathJax_strut {border: 0!important; padding: 0!important; margin: 0!important; vertical-align: 0!important}
.MathJax span {display: inline; position: static; border: 0; padding: 0; margin: 0; vertical-align: 0; line-height: normal; text-decoration: none}
.MathJax nobr {white-space: nowrap!important}
.MathJax img {display: inline!important; float: none!important}
.MathJax * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.MathJax_Processing {visibility: hidden; position: fixed; width: 0; height: 0; overflow: hidden}
.MathJax_Processed {display: none!important}
.MathJax_ExBox {display: block!important; overflow: hidden; width: 1px; height: 60ex; min-height: 0; max-height: none}
.MathJax .MathJax_EmBox {display: block!important; overflow: hidden; width: 1px; height: 60em; min-height: 0; max-height: none}
.MathJax_LineBox {display: table!important}
.MathJax_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}
.MathJax .MathJax_HitBox {cursor: text; background: white; opacity: 0; filter: alpha(opacity=0)}
.MathJax .MathJax_HitBox * {filter: none; opacity: 1; background: transparent}
#MathJax_Tooltip * {filter: none; opacity: 1; background: transparent}
@font-face {font-family: MathJax_Main; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Main-Regular.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Main-Regular.otf?V=2.7.2') format('opentype')}
@font-face {font-family: MathJax_Main-bold; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Main-Bold.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Main-Bold.otf?V=2.7.2') format('opentype')}
@font-face {font-family: MathJax_Main-italic; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Main-Italic.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Main-Italic.otf?V=2.7.2') format('opentype')}
@font-face {font-family: MathJax_Math-italic; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Math-Italic.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Math-Italic.otf?V=2.7.2') format('opentype')}
@font-face {font-family: MathJax_Caligraphic; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Caligraphic-Regular.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Caligraphic-Regular.otf?V=2.7.2') format('opentype')}
@font-face {font-family: MathJax_Size1; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Size1-Regular.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Size1-Regular.otf?V=2.7.2') format('opentype')}
@font-face {font-family: MathJax_Size2; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Size2-Regular.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Size2-Regular.otf?V=2.7.2') format('opentype')}
@font-face {font-family: MathJax_Size3; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Size3-Regular.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Size3-Regular.otf?V=2.7.2') format('opentype')}
@font-face {font-family: MathJax_Size4; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Size4-Regular.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Size4-Regular.otf?V=2.7.2') format('opentype')}
.MathJax .noError {vertical-align: ; font-size: 90%; text-align: left; color: black; padding: 1px 3px; border: 1px solid}
</style><style type="text/css">@font-face {font-family: MathJax_Math-bold-italic; src: url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/woff/MathJax_Math-BoldItalic.woff?V=2.7.2') format('woff'), url('https://mathjax.rstudio.com/latest/fonts/HTML-CSS/TeX/otf/MathJax_Math-BoldItalic.otf?V=2.7.2') format('opentype')}
</style></head>

<body><div style="visibility: hidden; overflow: hidden; position: absolute; top: 0px; height: 1px; width: auto; padding: 0px; border: 0px; margin: 0px; text-align: left; text-indent: 0px; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal;"><div id="MathJax_Hidden"></div></div><div id="MathJax_Message" style="display: none;"></div>


<div class="container-fluid main-container">


<!-- setup 3col/9col grid for toc_float and main content  -->
<div class="row">
<div class="col-xs-12 col-sm-4 col-md-3">
<div id="TOC" class="tocify">
<ul id="tocify-header1" class="tocify-header list-group"><li class="tocify-item list-group-item active" data-unique="Welcome_to_the_BASS_website">Welcome to the BASS website!</li></ul><ul id="tocify-header2" class="tocify-header list-group"><li class="tocify-item list-group-item" data-unique="Introduction_to_BASS">Introduction to BASS</li><ul class="tocify-subheader list-group" data-tag="2"><li class="tocify-item list-group-item" data-unique="BASS_workflow">BASS workflow</li><li class="tocify-item list-group-item" data-unique="BASS_Model_overview">BASS Model overview</li></ul></ul></div>
</div>

<div class="toc-content col-xs-12 col-sm-8 col-md-9">




<div class="navbar navbar-default  navbar-fixed-top" role="navigation">
  <div class="container">
    <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-bs-toggle="collapse" data-target="#navbar" data-bs-target="#navbar">
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="index.html">BASS</a>
    </div>
    <div id="navbar" class="navbar-collapse collapse">
      <ul class="nav navbar-nav">
        <li class="active">
  <a href="index.html">Introduction</a>
</li>
<li>
  <a href="about.html">Software tutorial</a>
</li>
<li>
  <a href="simu.html">Simulation</a>
</li>
<li class="dropdown">
  <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
    Real data analyses
     
    <span class="caret"></span>
  </a>
  <ul class="dropdown-menu" role="menu">
    <li>
      <a href="STARmap.html">STARmap (Wang et al., 2018)</a>
    </li>
    <li>
      <a href="MERFISH.html">MERFISH (Moffitt et al., 2018)</a>
    </li>
    <li>
      <a href="DLPFC.html">DLPFC (Maynard et al., 2021)</a>
    </li>
  </ul>
</li>
<li>
  <a href="license.html">License</a>
</li>
      </ul>
      <ul class="nav navbar-nav navbar-right">
        <li>
  <a href="https://github.com/zhengli09//BASS-analysis">
    <span class="fab fa-github"></span>
     
    Source code
  </a>
</li>
      </ul>
    </div><!--/.nav-collapse -->
  </div><!--/.container -->
</div><!--/.navbar -->

<div id="header">



<h1 class="title toc-ignore">Introduction to BASS</h1>
<h4 class="author">Zheng Li</h4>
<h4 class="date">2022-06-07</h4>

</div>


<p>
<button type="button" class="btn btn-default btn-workflowr btn-workflowr-report" data-toggle="collapse" data-target="#workflowr-report">
<span class="glyphicon glyphicon-list" aria-hidden="true"></span>
workflowr <span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span>
</button>
</p>
<div id="workflowr-report" class="collapse">
<ul class="nav nav-tabs">
<li class="active">
<a data-toggle="tab" href="#summary">Summary</a>
</li>
<li>
<a data-toggle="tab" href="#checks"> Checks <span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span>
</a>
</li>
<li>
<a data-toggle="tab" href="#versions">Past versions</a>
</li>
</ul>
<div class="tab-content">
<div id="summary" class="tab-pane fade in active">
<p>
<strong>Last updated:</strong> 2022-06-07
</p>
<p>
<strong>Checks:</strong> <span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span> 7
<span class="glyphicon glyphicon-exclamation-sign text-danger" aria-hidden="true"></span> 0
</p>
<p>
<strong>Knit directory:</strong> <code>BASS-analysis/</code> <span class="glyphicon glyphicon-question-sign" aria-hidden="true" title="This is the local directory in which the code in this file was executed.">
</span>
</p>
<p>
This reproducible <a href="https://rmarkdown.rstudio.com">R Markdown</a>
analysis was created with <a href="https://github.com/workflowr/workflowr">workflowr</a> (version
1.7.0). The <em>Checks</em> tab describes the reproducibility checks
that were applied when the results were created. The <em>Past
versions</em> tab lists the development history.
</p>
<hr>
</div>
<div id="checks" class="tab-pane fade">
<div id="workflowr-checks" class="panel-group">
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongRMarkdownfilestronguptodate">
<span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span> <strong>R Markdown file:</strong> up-to-date
</a>
</p>
</div>
<div id="strongRMarkdownfilestronguptodate" class="panel-collapse collapse">
<div class="panel-body">
<p>Great! Since the R Markdown file has been committed to the Git
repository, you know the exact version of the code that produced these
results.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongEnvironmentstrongempty">
<span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span> <strong>Environment:</strong> empty </a>
</p>
</div>
<div id="strongEnvironmentstrongempty" class="panel-collapse collapse">
<div class="panel-body">
<p>Great job! The global environment was empty. Objects defined in the
global environment can affect the analysis in your R Markdown file in
unknown ways. For reproduciblity it’s best to always run the code in an
empty environment.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongSeedstrongcodesetseed0code">
<span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span> <strong>Seed:</strong>
<code>set.seed(0)</code> </a>
</p>
</div>
<div id="strongSeedstrongcodesetseed0code" class="panel-collapse collapse">
<div class="panel-body">
<p>The command <code>set.seed(0)</code> was run prior to running the
code in the R Markdown file. Setting a seed ensures that any results
that rely on randomness, e.g. subsampling or permutations, are
reproducible.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongSessioninformationstrongrecorded">
<span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span> <strong>Session information:</strong>
recorded </a>
</p>
</div>
<div id="strongSessioninformationstrongrecorded" class="panel-collapse collapse">
<div class="panel-body">
<p>Great job! Recording the operating system, R version, and package
versions is critical for reproducibility.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongCachestrongnone">
<span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span> <strong>Cache:</strong> none </a>
</p>
</div>
<div id="strongCachestrongnone" class="panel-collapse collapse">
<div class="panel-body">
<p>Nice! There were no cached chunks for this analysis, so you can be
confident that you successfully produced the results during this
run.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongFilepathsstrongrelative">
<span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span> <strong>File paths:</strong> relative </a>
</p>
</div>
<div id="strongFilepathsstrongrelative" class="panel-collapse collapse">
<div class="panel-body">
<p>Great job! Using relative paths to the files within your workflowr
project makes it easier to run your code on other machines.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongRepositoryversionstrongahrefhttpsgithubcomzhengli09BASSanalysistree6a631f82816b7be00b249f66a2288f7a3bd35adftargetblank6a631f8a">
<span class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span> <strong>Repository version:</strong>
</a><a href="https://github.com/zhengli09//BASS-analysis/tree/6a631f82816b7be00b249f66a2288f7a3bd35adf" target="_blank">6a631f8</a>

</p>
</div>
<div id="strongRepositoryversionstrongahrefhttpsgithubcomzhengli09BASSanalysistree6a631f82816b7be00b249f66a2288f7a3bd35adftargetblank6a631f8a" class="panel-collapse collapse">
<div class="panel-body">
<p>
Great! You are using Git for version control. Tracking code development
and connecting the code version to the results is critical for
reproducibility.
</p>
<p>
The results in this page were generated with repository version
<a href="https://github.com/zhengli09//BASS-analysis/tree/6a631f82816b7be00b249f66a2288f7a3bd35adf" target="_blank">6a631f8</a>.
See the <em>Past versions</em> tab to see a history of the changes made
to the R Markdown and HTML files.
</p>
<p>
Note that you need to be careful to ensure that all relevant files for
the analysis have been committed to Git prior to generating the results
(you can use <code>wflow_publish</code> or
<code>wflow_git_commit</code>). workflowr only checks the R Markdown
file, but you know if there are other scripts or data files that it
depends on. Below is the status of the Git repository when the results
were generated:
</p>
<pre><code class="hljs">
Untracked files:
    Untracked:  code/run_giniclust3.py

Unstaged changes:
    Modified:   code/simu_utils.R
    Modified:   code/viz.R
    Modified:   data/MERFISH_Animal1.RData
    Modified:   data/starmap_mpfc.RData

</code></pre>
<p>
Note that any generated files, e.g.&nbsp;HTML, png, CSS, etc., are not
included in this status report because it is ok for generated content to
have uncommitted changes.
</p>
</div>
</div>
</div>
</div>
<hr>
</div>
<div id="versions" class="tab-pane fade">

<p>
These are the previous versions of the repository in which changes were
made to the R Markdown (<code>analysis/index.Rmd</code>) and HTML
(<code>docs/index.html</code>) files. If you’ve configured a remote Git
repository (see <code>?wflow_git_remote</code>), click on the hyperlinks
in the table below to view the files as they were in that past version.
</p>
<div class="table-responsive">
<table class="table table-condensed table-hover">
<thead>
<tr>
<th>
File
</th>
<th>
Version
</th>
<th>
Author
</th>
<th>
Date
</th>
<th>
Message
</th>
</tr>
</thead>
<tbody>
<tr>
<td>
Rmd
</td>
<td>
<a href="https://github.com/zhengli09//BASS-analysis/blob/6a631f82816b7be00b249f66a2288f7a3bd35adf/analysis/index.Rmd" target="_blank">6a631f8</a>
</td>
<td>
zhengli09
</td>
<td>
2022-06-07
</td>
<td>
Update software introduction and tutorial
</td>
</tr>
<tr>
<td>
html
</td>
<td>
<a href="https://rawcdn.githack.com/zhengli09//BASS-analysis/345228b446ca2cd0eb8ece1f6a832e9cf41b3958/docs/index.html" target="_blank">345228b</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-27
</td>
<td>
Build site.
</td>
</tr>
<tr>
<td>
Rmd
</td>
<td>
<a href="https://github.com/zhengli09//BASS-analysis/blob/9713c56c5fa59ac9a05dec6997a2af3bbb1d0da8/analysis/index.Rmd" target="_blank">9713c56</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-27
</td>
<td>
Link workflow figure to introduction page
</td>
</tr>
<tr>
<td>
html
</td>
<td>
<a href="https://rawcdn.githack.com/zhengli09//BASS-analysis/9a685114f1f29bb007c27088adaf8ce2582c56a2/docs/index.html" target="_blank">9a68511</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-27
</td>
<td>
Build site.
</td>
</tr>
<tr>
<td>
Rmd
</td>
<td>
<a href="https://github.com/zhengli09//BASS-analysis/blob/4ec8df1262087c7c78f682e56014a7087a756d4f/analysis/index.Rmd" target="_blank">4ec8df1</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-27
</td>
<td>
Publish the introduction, simulation analysis and STARmap analysis
</td>
</tr>
<tr>
<td>
html
</td>
<td>
<a href="https://rawcdn.githack.com/zhengli09//BASS-analysis/b2c476b7c59342294dc8304cd5d2f19213f27d43/docs/index.html" target="_blank">b2c476b</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-06
</td>
<td>
Build site.
</td>
</tr>
<tr>
<td>
html
</td>
<td>
<a href="https://rawcdn.githack.com/zhengli09//BASS-analysis/a6097f45ea3c63efeecda29c8c9305498aed39ee/docs/index.html" target="_blank">a6097f4</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-06
</td>
<td>
Build site.
</td>
</tr>
<tr>
<td>
Rmd
</td>
<td>
<a href="https://github.com/zhengli09//BASS-analysis/blob/9f8756a61ff477ed278dcfb8b2682e6c07fac36b/analysis/index.Rmd" target="_blank">9f8756a</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-06
</td>
<td>
Start workflowr project.
</td>
</tr>
</tbody>
</table>
</div>
<hr>
</div>
</div>
</div>
<div id="welcome-to-the-bass-website" class="section level1">
<div name="Welcome_to_the_BASS_website" data-unique="Welcome_to_the_BASS_website"></div><h1>Welcome to the BASS website!</h1>
<p>This website maintains code for reproducing simulation and real data
application results described in the upcoming paper. For the software,
please refer to <a href="https://github.com/zhengli09/BASS">BASS</a>.</p>
</div>
<div id="introduction-to-bass" class="section level1">
<div name="Introduction_to_BASS" data-unique="Introduction_to_BASS"></div><h1>Introduction to BASS</h1>
<p>BASS is a method for multi-scale and multi-sample analysis in spatial
transcriptomics. BASS performs multi-scale transcriptomic analyses in
the form of joint cell type clustering and spatial domain detection,
with the two analytic tasks carried out simultaneously within a Bayesian
hierarchical modeling framework. For both analyses, BASS properly
accounts for the spatial correlation structure and seamlessly integrates
gene expression information with spatial localization information to
improve their performance. In addition, BASS is capable of multi-sample
analysis that jointly models multiple tissue sections/samples,
facilitating the integration of spatial transcriptomic data across
tissue samples.</p>
<div id="bass-workflow" class="section level2">
<div name="BASS_workflow" data-unique="BASS_workflow"></div><h2>BASS workflow</h2>
<p><img src="BASS_workflow.png"></p>
</div>
<div id="bass-model-overview" class="section level2">
<div name="BASS_Model_overview" data-unique="BASS_Model_overview"></div><h2>BASS Model overview</h2>
<p>BASS relies on a Bayesian hierarchical modeling framework that
describes the relationship among gene expression features, cell type
labels, spatial domain labels, cell type compositions in each spatial
domain, and neighborhood graphs in a hierarchical fashion: <span class="math display"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><div class="MathJax_Display" style="text-align: center;"><span class="MathJax" id="MathJax-Element-1-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot; display=&quot;block&quot;><msubsup><mi mathvariant=&quot;bold-italic&quot;>x</mi><mi>i</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msubsup><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>|</mo></mrow><msubsup><mi>c</mi><mi>i</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msubsup><mo>=</mo><mi>c</mi><mo>&amp;#x223C;</mo><mi>M</mi><mi>V</mi><mi>N</mi><mo stretchy=&quot;false&quot;>(</mo><msub><mi mathvariant=&quot;bold-italic&quot;>&amp;#x03BC;</mi><mi>c</mi></msub><mo>,</mo><mi mathvariant=&quot;bold&quot;>&amp;#x03A3;</mi><mo stretchy=&quot;false&quot;>)</mo></math>" role="presentation" style="text-align: center; position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-1" style="width: 13.396em; display: inline-block;"><span style="display: inline-block; position: relative; width: 12.075em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.024em, 1011.96em, 2.766em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-2"><span class="msubsup" id="MathJax-Span-3"><span style="display: inline-block; position: relative; width: 1.505em; height: 0px;"><span style="position: absolute; clip: rect(3.366em, 1000.6em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-4" style="font-family: MathJax_Math-bold-italic;">x</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.306em, 1000.84em, 4.387em, -999.997em); top: -4.562em; left: 0.664em;"><span class="texatom" id="MathJax-Span-5"><span class="mrow" id="MathJax-Span-6"><span class="mo" id="MathJax-Span-7" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-8" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-9" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.366em, 1000.3em, 4.207em, -999.997em); top: -3.721em; left: 0.664em;"><span class="mi" id="MathJax-Span-10" style="font-size: 70.7%; font-family: MathJax_Math-italic;">i</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span><span class="texatom" id="MathJax-Span-11"><span class="mrow" id="MathJax-Span-12"><span class="mo" id="MathJax-Span-13" style="font-family: MathJax_Main;">|</span></span></span><span class="msubsup" id="MathJax-Span-14"><span style="display: inline-block; position: relative; width: 1.264em; height: 0px;"><span style="position: absolute; clip: rect(3.426em, 1000.42em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-15" style="font-family: MathJax_Math-italic;">c</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.306em, 1000.84em, 4.387em, -999.997em); top: -4.562em; left: 0.423em;"><span class="texatom" id="MathJax-Span-16"><span class="mrow" id="MathJax-Span-17"><span class="mo" id="MathJax-Span-18" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-19" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-20" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.366em, 1000.3em, 4.207em, -999.997em); top: -3.721em; left: 0.423em;"><span class="mi" id="MathJax-Span-21" style="font-size: 70.7%; font-family: MathJax_Math-italic;">i</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span><span class="mo" id="MathJax-Span-22" style="font-family: MathJax_Main; padding-left: 0.303em;">=</span><span class="mi" id="MathJax-Span-23" style="font-family: MathJax_Math-italic; padding-left: 0.303em;">c</span><span class="mo" id="MathJax-Span-24" style="font-family: MathJax_Main; padding-left: 0.303em;">∼</span><span class="mi" id="MathJax-Span-25" style="font-family: MathJax_Math-italic; padding-left: 0.303em;">M<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.063em;"></span></span><span class="mi" id="MathJax-Span-26" style="font-family: MathJax_Math-italic;">V<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.183em;"></span></span><span class="mi" id="MathJax-Span-27" style="font-family: MathJax_Math-italic;">N<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.063em;"></span></span><span class="mo" id="MathJax-Span-28" style="font-family: MathJax_Main;">(</span><span class="msubsup" id="MathJax-Span-29"><span style="display: inline-block; position: relative; width: 1.084em; height: 0px;"><span style="position: absolute; clip: rect(3.366em, 1000.66em, 4.447em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-30" style="font-family: MathJax_Math-bold-italic;">μ</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; top: -3.901em; left: 0.724em;"><span class="mi" id="MathJax-Span-31" style="font-size: 70.7%; font-family: MathJax_Math-italic;">c</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span><span class="mo" id="MathJax-Span-32" style="font-family: MathJax_Main;">,</span><span class="mi" id="MathJax-Span-33" style="font-family: MathJax_Main-bold; padding-left: 0.183em;">Σ</span><span class="mo" id="MathJax-Span-34" style="font-family: MathJax_Main;">)</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.397em; border-left: 0px solid; width: 0px; height: 1.67em;"></span></span></nobr><span class="MJX_Assistive_MathML MJX_Assistive_MathML_Block" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><msubsup><mi mathvariant="bold-italic">x</mi><mi>i</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msubsup><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">|</mo></mrow><msubsup><mi>c</mi><mi>i</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msubsup><mo>=</mo><mi>c</mi><mo>∼</mo><mi>M</mi><mi>V</mi><mi>N</mi><mo stretchy="false">(</mo><msub><mi mathvariant="bold-italic">μ</mi><mi>c</mi></msub><mo>,</mo><mi mathvariant="bold">Σ</mi><mo stretchy="false">)</mo></math></span></span></div><script type="math/tex; mode=display" id="MathJax-Element-1">
  \boldsymbol{x}_i^{(l)} | c_i^{(l)} = c \sim MVN(\boldsymbol{\mu}_c,
\boldsymbol{\Sigma})
</script></span> <span class="math display"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><div class="MathJax_Display" style="text-align: center;"><span class="MathJax" id="MathJax-Element-2-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot; display=&quot;block&quot;><msubsup><mi>c</mi><mi>i</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msubsup><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>|</mo></mrow><msubsup><mi>z</mi><mi>i</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msubsup><mo>=</mo><mi>r</mi><mo>&amp;#x223C;</mo><mi>C</mi><mi>a</mi><mi>t</mi><mo stretchy=&quot;false&quot;>(</mo><msub><mi mathvariant=&quot;bold-italic&quot;>&amp;#x03C0;</mi><mi>r</mi></msub><mo stretchy=&quot;false&quot;>)</mo></math>" role="presentation" style="text-align: center; position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-35" style="width: 10.754em; display: inline-block;"><span style="display: inline-block; position: relative; width: 9.673em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.024em, 1009.55em, 2.766em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-36"><span class="msubsup" id="MathJax-Span-37"><span style="display: inline-block; position: relative; width: 1.264em; height: 0px;"><span style="position: absolute; clip: rect(3.426em, 1000.42em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-38" style="font-family: MathJax_Math-italic;">c</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.306em, 1000.84em, 4.387em, -999.997em); top: -4.562em; left: 0.423em;"><span class="texatom" id="MathJax-Span-39"><span class="mrow" id="MathJax-Span-40"><span class="mo" id="MathJax-Span-41" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-42" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-43" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.366em, 1000.3em, 4.207em, -999.997em); top: -3.721em; left: 0.423em;"><span class="mi" id="MathJax-Span-44" style="font-size: 70.7%; font-family: MathJax_Math-italic;">i</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span><span class="texatom" id="MathJax-Span-45"><span class="mrow" id="MathJax-Span-46"><span class="mo" id="MathJax-Span-47" style="font-family: MathJax_Main;">|</span></span></span><span class="msubsup" id="MathJax-Span-48"><span style="display: inline-block; position: relative; width: 1.384em; height: 0px;"><span style="position: absolute; clip: rect(3.426em, 1000.48em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-49" style="font-family: MathJax_Math-italic;">z<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.306em, 1000.84em, 4.387em, -999.997em); top: -4.562em; left: 0.544em;"><span class="texatom" id="MathJax-Span-50"><span class="mrow" id="MathJax-Span-51"><span class="mo" id="MathJax-Span-52" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-53" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-54" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.366em, 1000.3em, 4.207em, -999.997em); top: -3.721em; left: 0.483em;"><span class="mi" id="MathJax-Span-55" style="font-size: 70.7%; font-family: MathJax_Math-italic;">i</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span><span class="mo" id="MathJax-Span-56" style="font-family: MathJax_Main; padding-left: 0.303em;">=</span><span class="mi" id="MathJax-Span-57" style="font-family: MathJax_Math-italic; padding-left: 0.303em;">r</span><span class="mo" id="MathJax-Span-58" style="font-family: MathJax_Main; padding-left: 0.303em;">∼</span><span class="mi" id="MathJax-Span-59" style="font-family: MathJax_Math-italic; padding-left: 0.303em;">C<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.063em;"></span></span><span class="mi" id="MathJax-Span-60" style="font-family: MathJax_Math-italic;">a</span><span class="mi" id="MathJax-Span-61" style="font-family: MathJax_Math-italic;">t</span><span class="mo" id="MathJax-Span-62" style="font-family: MathJax_Main;">(</span><span class="msubsup" id="MathJax-Span-63"><span style="display: inline-block; position: relative; width: 1.084em; height: 0px;"><span style="position: absolute; clip: rect(3.426em, 1000.66em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-64" style="font-family: MathJax_Math-bold-italic;">π</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; top: -3.901em; left: 0.664em;"><span class="mi" id="MathJax-Span-65" style="font-size: 70.7%; font-family: MathJax_Math-italic;">r</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span><span class="mo" id="MathJax-Span-66" style="font-family: MathJax_Main;">)</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.397em; border-left: 0px solid; width: 0px; height: 1.67em;"></span></span></nobr><span class="MJX_Assistive_MathML MJX_Assistive_MathML_Block" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><msubsup><mi>c</mi><mi>i</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msubsup><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">|</mo></mrow><msubsup><mi>z</mi><mi>i</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msubsup><mo>=</mo><mi>r</mi><mo>∼</mo><mi>C</mi><mi>a</mi><mi>t</mi><mo stretchy="false">(</mo><msub><mi mathvariant="bold-italic">π</mi><mi>r</mi></msub><mo stretchy="false">)</mo></math></span></span></div><script type="math/tex; mode=display" id="MathJax-Element-2">
  c_i^{(l)} | z_i^{(l)} = r \sim Cat(\boldsymbol{\pi}_r)
</script></span> <span class="math display"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><div class="MathJax_Display" style="text-align: center;"><span class="MathJax" id="MathJax-Element-3-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot; display=&quot;block&quot;><msup><mi mathvariant=&quot;bold-italic&quot;>z</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msup><mo>&amp;#x223C;</mo><mi>P</mi><mi>o</mi><mi>t</mi><mi>t</mi><mi>s</mi><mo stretchy=&quot;false&quot;>(</mo><msup><mi>V</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msup><mo>,</mo><mi>&amp;#x03B2;</mi><mo stretchy=&quot;false&quot;>)</mo></math>" role="presentation" style="text-align: center; position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-67" style="width: 9.673em; display: inline-block;"><span style="display: inline-block; position: relative; width: 8.712em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.144em, 1008.59em, 2.706em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-68"><span class="msubsup" id="MathJax-Span-69"><span style="display: inline-block; position: relative; width: 1.384em; height: 0px;"><span style="position: absolute; clip: rect(3.366em, 1000.54em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-70" style="font-family: MathJax_Math-bold-italic;">z</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; top: -4.441em; left: 0.544em;"><span class="texatom" id="MathJax-Span-71"><span class="mrow" id="MathJax-Span-72"><span class="mo" id="MathJax-Span-73" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-74" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-75" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span><span class="mo" id="MathJax-Span-76" style="font-family: MathJax_Main; padding-left: 0.303em;">∼</span><span class="mi" id="MathJax-Span-77" style="font-family: MathJax_Math-italic; padding-left: 0.303em;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.123em;"></span></span><span class="mi" id="MathJax-Span-78" style="font-family: MathJax_Math-italic;">o</span><span class="mi" id="MathJax-Span-79" style="font-family: MathJax_Math-italic;">t</span><span class="mi" id="MathJax-Span-80" style="font-family: MathJax_Math-italic;">t</span><span class="mi" id="MathJax-Span-81" style="font-family: MathJax_Math-italic;">s</span><span class="mo" id="MathJax-Span-82" style="font-family: MathJax_Main;">(</span><span class="msubsup" id="MathJax-Span-83"><span style="display: inline-block; position: relative; width: 1.685em; height: 0px;"><span style="position: absolute; clip: rect(3.186em, 1000.78em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-84" style="font-family: MathJax_Math-italic;">V<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.183em;"></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; top: -4.441em; left: 0.904em;"><span class="texatom" id="MathJax-Span-85"><span class="mrow" id="MathJax-Span-86"><span class="mo" id="MathJax-Span-87" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-88" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-89" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span><span class="mo" id="MathJax-Span-90" style="font-family: MathJax_Main;">,</span><span class="mi" id="MathJax-Span-91" style="font-family: MathJax_Math-italic; padding-left: 0.183em;">β<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mo" id="MathJax-Span-92" style="font-family: MathJax_Main;">)</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.33em; border-left: 0px solid; width: 0px; height: 1.47em;"></span></span></nobr><span class="MJX_Assistive_MathML MJX_Assistive_MathML_Block" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><msup><mi mathvariant="bold-italic">z</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msup><mo>∼</mo><mi>P</mi><mi>o</mi><mi>t</mi><mi>t</mi><mi>s</mi><mo stretchy="false">(</mo><msup><mi>V</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msup><mo>,</mo><mi>β</mi><mo stretchy="false">)</mo></math></span></span></div><script type="math/tex; mode=display" id="MathJax-Element-3">
  \boldsymbol{z}^{(l)} \sim Potts(V^{(l)}, \beta)
</script></span> Above, the first equation models the expression feature of the
<span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-4-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><mi>i</mi></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-93" style="width: 0.423em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.363em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.444em, 1000.3em, 2.465em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-94"><span class="mi" id="MathJax-Span-95" style="font-family: MathJax_Math-italic;">i</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.063em; border-left: 0px solid; width: 0px; height: 0.87em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><mi>i</mi></math></span></span><script type="math/tex" id="MathJax-Element-4">i</script></span>th cell on section <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-5-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><mi>l</mi></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-96" style="width: 0.363em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.303em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.384em, 1000.24em, 2.465em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-97"><span class="mi" id="MathJax-Span-98" style="font-family: MathJax_Math-italic;">l</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.063em; border-left: 0px solid; width: 0px; height: 0.937em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><mi>l</mi></math></span></span><script type="math/tex" id="MathJax-Element-5">l</script></span>, <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-6-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi mathvariant=&quot;bold-italic&quot;>x</mi><mi>i</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msubsup></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-99" style="width: 1.685em; display: inline-block;"><span style="display: inline-block; position: relative; width: 1.505em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.024em, 1001.5em, 2.766em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-100"><span class="msubsup" id="MathJax-Span-101"><span style="display: inline-block; position: relative; width: 1.505em; height: 0px;"><span style="position: absolute; clip: rect(3.366em, 1000.6em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-102" style="font-family: MathJax_Math-bold-italic;">x</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.306em, 1000.84em, 4.387em, -999.997em); top: -4.562em; left: 0.664em;"><span class="texatom" id="MathJax-Span-103"><span class="mrow" id="MathJax-Span-104"><span class="mo" id="MathJax-Span-105" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-106" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-107" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.366em, 1000.3em, 4.207em, -999.997em); top: -3.721em; left: 0.664em;"><span class="mi" id="MathJax-Span-108" style="font-size: 70.7%; font-family: MathJax_Math-italic;">i</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.397em; border-left: 0px solid; width: 0px; height: 1.67em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><msubsup><mi mathvariant="bold-italic">x</mi><mi>i</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msubsup></math></span></span><script type="math/tex" id="MathJax-Element-6">\boldsymbol{x}_i^{(l)}</script></span>, as depending on
its cell type label <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-7-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>c</mi><mi>i</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msubsup></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-109" style="width: 1.444em; display: inline-block;"><span style="display: inline-block; position: relative; width: 1.264em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.024em, 1001.26em, 2.766em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-110"><span class="msubsup" id="MathJax-Span-111"><span style="display: inline-block; position: relative; width: 1.264em; height: 0px;"><span style="position: absolute; clip: rect(3.426em, 1000.42em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-112" style="font-family: MathJax_Math-italic;">c</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.306em, 1000.84em, 4.387em, -999.997em); top: -4.562em; left: 0.423em;"><span class="texatom" id="MathJax-Span-113"><span class="mrow" id="MathJax-Span-114"><span class="mo" id="MathJax-Span-115" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-116" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-117" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; clip: rect(3.366em, 1000.3em, 4.207em, -999.997em); top: -3.721em; left: 0.423em;"><span class="mi" id="MathJax-Span-118" style="font-size: 70.7%; font-family: MathJax_Math-italic;">i</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.397em; border-left: 0px solid; width: 0px; height: 1.67em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><msubsup><mi>c</mi><mi>i</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msubsup></math></span></span><script type="math/tex" id="MathJax-Element-7">c_i^{(l)}</script></span> with
a multivariate normal distribution parameterized by a cell type-specific
mean parameter <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-8-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msub><mi mathvariant=&quot;bold-italic&quot;>&amp;#x03BC;</mi><mi>c</mi></msub></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-119" style="width: 1.204em; display: inline-block;"><span style="display: inline-block; position: relative; width: 1.084em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.625em, 1001.08em, 2.706em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-120"><span class="msubsup" id="MathJax-Span-121"><span style="display: inline-block; position: relative; width: 1.084em; height: 0px;"><span style="position: absolute; clip: rect(3.366em, 1000.66em, 4.447em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-122" style="font-family: MathJax_Math-bold-italic;">μ</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; top: -3.901em; left: 0.724em;"><span class="mi" id="MathJax-Span-123" style="font-size: 70.7%; font-family: MathJax_Math-italic;">c</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.33em; border-left: 0px solid; width: 0px; height: 0.87em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><msub><mi mathvariant="bold-italic">μ</mi><mi>c</mi></msub></math></span></span><script type="math/tex" id="MathJax-Element-8">\boldsymbol{\mu}_c</script></span>
and a variance-covariance matrix <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-9-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><mi mathvariant=&quot;bold&quot;>&amp;#x03A3;</mi></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-124" style="width: 0.964em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.844em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.444em, 1000.78em, 2.465em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-125"><span class="mi" id="MathJax-Span-126" style="font-family: MathJax_Main-bold;">Σ</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.063em; border-left: 0px solid; width: 0px; height: 0.87em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><mi mathvariant="bold">Σ</mi></math></span></span><script type="math/tex" id="MathJax-Element-9">\boldsymbol{\Sigma}</script></span> that is shared across
cell types. The second equation models the probability of the <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-10-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><mi>i</mi></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-127" style="width: 0.423em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.363em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.444em, 1000.3em, 2.465em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-128"><span class="mi" id="MathJax-Span-129" style="font-family: MathJax_Math-italic;">i</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.063em; border-left: 0px solid; width: 0px; height: 0.87em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><mi>i</mi></math></span></span><script type="math/tex" id="MathJax-Element-10">i</script></span>th cell belonging to the cell type <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-11-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><mi>c</mi></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-130" style="width: 0.483em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.423em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.685em, 1000.42em, 2.465em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-131"><span class="mi" id="MathJax-Span-132" style="font-family: MathJax_Math-italic;">c</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.063em; border-left: 0px solid; width: 0px; height: 0.67em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><mi>c</mi></math></span></span><script type="math/tex" id="MathJax-Element-11">c</script></span> as depending on the underlying spatial
domain with a categorical distribution parameterized by the <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-12-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><mi>r</mi></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-133" style="width: 0.544em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.483em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.685em, 1000.48em, 2.465em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-134"><span class="mi" id="MathJax-Span-135" style="font-family: MathJax_Math-italic;">r</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.063em; border-left: 0px solid; width: 0px; height: 0.67em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><mi>r</mi></math></span></span><script type="math/tex" id="MathJax-Element-12">r</script></span> domain-specific cell type composition
vector <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-13-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msub><mi mathvariant=&quot;bold-italic&quot;>&amp;#x03C0;</mi><mi>r</mi></msub></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-136" style="width: 1.204em; display: inline-block;"><span style="display: inline-block; position: relative; width: 1.084em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.685em, 1001.08em, 2.646em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-137"><span class="msubsup" id="MathJax-Span-138"><span style="display: inline-block; position: relative; width: 1.084em; height: 0px;"><span style="position: absolute; clip: rect(3.426em, 1000.66em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-139" style="font-family: MathJax_Math-bold-italic;">π</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; top: -3.901em; left: 0.664em;"><span class="mi" id="MathJax-Span-140" style="font-size: 70.7%; font-family: MathJax_Math-italic;">r</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.263em; border-left: 0px solid; width: 0px; height: 0.803em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><msub><mi mathvariant="bold-italic">π</mi><mi>r</mi></msub></math></span></span><script type="math/tex" id="MathJax-Element-13">\boldsymbol{\pi}_r</script></span>. The
third equation models the spatial domain label of all cells on the
section <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-14-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><mi>l</mi></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-141" style="width: 0.363em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.303em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.384em, 1000.24em, 2.465em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-142"><span class="mi" id="MathJax-Span-143" style="font-family: MathJax_Math-italic;">l</span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.063em; border-left: 0px solid; width: 0px; height: 0.937em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><mi>l</mi></math></span></span><script type="math/tex" id="MathJax-Element-14">l</script></span>, <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-15-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msup><mi mathvariant=&quot;bold-italic&quot;>z</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msup></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-144" style="width: 1.565em; display: inline-block;"><span style="display: inline-block; position: relative; width: 1.384em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.204em, 1001.38em, 2.465em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-145"><span class="msubsup" id="MathJax-Span-146"><span style="display: inline-block; position: relative; width: 1.384em; height: 0px;"><span style="position: absolute; clip: rect(3.366em, 1000.54em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-147" style="font-family: MathJax_Math-bold-italic;">z</span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; top: -4.381em; left: 0.544em;"><span class="texatom" id="MathJax-Span-148"><span class="mrow" id="MathJax-Span-149"><span class="mo" id="MathJax-Span-150" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-151" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-152" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.063em; border-left: 0px solid; width: 0px; height: 1.137em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><msup><mi mathvariant="bold-italic">z</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msup></math></span></span><script type="math/tex" id="MathJax-Element-15">\boldsymbol{z}^{(l)}</script></span>, as a function of
the neighborhood graph <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-16-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msup><mi>V</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mo stretchy=&quot;false&quot;>(</mo><mi>l</mi><mo stretchy=&quot;false&quot;>)</mo></mrow></msup></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-153" style="width: 1.865em; display: inline-block;"><span style="display: inline-block; position: relative; width: 1.685em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.204em, 1001.68em, 2.465em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-154"><span class="msubsup" id="MathJax-Span-155"><span style="display: inline-block; position: relative; width: 1.685em; height: 0px;"><span style="position: absolute; clip: rect(3.186em, 1000.78em, 4.207em, -999.997em); top: -4.021em; left: 0em;"><span class="mi" id="MathJax-Span-156" style="font-family: MathJax_Math-italic;">V<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.183em;"></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span><span style="position: absolute; top: -4.381em; left: 0.904em;"><span class="texatom" id="MathJax-Span-157"><span class="mrow" id="MathJax-Span-158"><span class="mo" id="MathJax-Span-159" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-160" style="font-size: 70.7%; font-family: MathJax_Math-italic;">l</span><span class="mo" id="MathJax-Span-161" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span></span><span style="display: inline-block; width: 0px; height: 4.027em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.063em; border-left: 0px solid; width: 0px; height: 1.137em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><msup><mi>V</mi><mrow class="MJX-TeXAtom-ORD"><mo stretchy="false">(</mo><mi>l</mi><mo stretchy="false">)</mo></mrow></msup></math></span></span><script type="math/tex" id="MathJax-Element-16">V^{(l)}</script></span>
through a homogeneous Potts model characterized by an interaction
parameter <span class="math inline"><span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-17-Frame" tabindex="0" data-mathml="<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><mi>&amp;#x03B2;</mi></math>" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-162" style="width: 0.604em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.544em; height: 0px; font-size: 111%;"><span style="position: absolute; clip: rect(1.384em, 1000.54em, 2.646em, -999.997em); top: -2.279em; left: 0em;"><span class="mrow" id="MathJax-Span-163"><span class="mi" id="MathJax-Span-164" style="font-family: MathJax_Math-italic;">β<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span></span><span style="display: inline-block; width: 0px; height: 2.285em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.263em; border-left: 0px solid; width: 0px; height: 1.137em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><mi>β</mi></math></span></span><script type="math/tex" id="MathJax-Element-17">\beta</script></span>.</p>
<br>
<p>
<button type="button" class="btn btn-default btn-workflowr btn-workflowr-sessioninfo" data-toggle="collapse" data-target="#workflowr-sessioninfo" style="display: block;">
<span class="glyphicon glyphicon-wrench" aria-hidden="true"></span>
Session information
</button>
</p>
<div id="workflowr-sessioninfo" class="collapse">
<pre class="r"><code class="hljs">sessionInfo()</code></pre>
<pre><code class="hljs">R version 4.2.0 (2022-04-22)
Platform: x86_64-pc-linux-gnu (64-bit)
Running under: Ubuntu 18.04.5 LTS

Matrix products: default
BLAS:   /usr/lib/x86_64-linux-gnu/openblas/libblas.so.3
LAPACK: /usr/lib/x86_64-linux-gnu/libopenblasp-r0.2.20.so

locale:
 [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C              
 [3] LC_TIME=en_US.UTF-8        LC_COLLATE=en_US.UTF-8    
 [5] LC_MONETARY=en_US.UTF-8    LC_MESSAGES=en_US.UTF-8   
 [7] LC_PAPER=en_US.UTF-8       LC_NAME=C                 
 [9] LC_ADDRESS=C               LC_TELEPHONE=C            
[11] LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C       

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
[1] workflowr_1.7.0

loaded via a namespace (and not attached):
 [1] Rcpp_1.0.8.3     bslib_0.3.1      compiler_4.2.0   pillar_1.7.0    
 [5] later_1.1.0.1    git2r_0.28.0     jquerylib_0.1.4  tools_4.2.0     
 [9] getPass_0.2-2    digest_0.6.29    jsonlite_1.8.0   evaluate_0.15   
[13] tibble_3.1.6     lifecycle_1.0.1  pkgconfig_2.0.3  rlang_1.0.1     
[17] cli_3.2.0        rstudioapi_0.13  yaml_2.3.5       xfun_0.29       
[21] fastmap_1.1.0    httr_1.4.2       stringr_1.4.0    knitr_1.37      
[25] sass_0.4.1       fs_1.5.2         vctrs_0.3.8      rprojroot_2.0.2 
[29] glue_1.6.2       R6_2.5.1         processx_3.5.2   fansi_1.0.2     
[33] rmarkdown_2.12.1 callr_3.7.0      magrittr_2.0.2   whisker_0.4     
[37] ps_1.6.0         promises_1.1.1   htmltools_0.5.2  ellipsis_0.3.2  
[41] httpuv_1.5.4     utf8_1.2.2       stringi_1.7.6    crayon_1.5.0    </code></pre>
</div>
</div>
</div>


<!-- Adjust MathJax settings so that all math formulae are shown using
TeX fonts only; see
https://docs.mathjax.org/en/latest/web/configuration.html. This will make
the presentation more consistent at the cost of the webpage sometimes
taking slightly longer to load. Note that this only works because the
footer is added to webpages before the MathJax javascript. -->
<script type="text/x-mathjax-config;executed=true">
  MathJax.Hub.Config({
    "HTML-CSS": { availableFonts: ["TeX"] }
  });
</script>




</div>
</div>

</div>

<script>

// add bootstrap table styles to pandoc tables
function bootstrapStylePandocTables() {
  $('tr.odd').parent('tbody').parent('table').addClass('table table-condensed');
}
$(document).ready(function () {
  bootstrapStylePandocTables();
});


</script>

<!-- tabsets -->

<script>
$(document).ready(function () {
  window.buildTabsets("TOC");
});

$(document).ready(function () {
  $('.tabset-dropdown > .nav-tabs > li').click(function () {
    $(this).parent().toggleClass('nav-tabs-open');
  });
});
</script>

<!-- code folding -->

<script>
$(document).ready(function ()  {

    // temporarily add toc-ignore selector to headers for the consistency with Pandoc
    $('.unlisted.unnumbered').addClass('toc-ignore')

    // move toc-ignore selectors from section div to header
    $('div.section.toc-ignore')
        .removeClass('toc-ignore')
        .children('h1,h2,h3,h4,h5').addClass('toc-ignore');

    // establish options
    var options = {
      selectors: "h1,h2,h3",
      theme: "bootstrap3",
      context: '.toc-content',
      hashGenerator: function (text) {
        return text.replace(/[.\\/?&!#<>]/g, '').replace(/\s/g, '_');
      },
      ignoreSelector: ".toc-ignore",
      scrollTo: 0
    };
    options.showAndHide = true;
    options.smoothScroll = true;

    // tocify
    var toc = $("#TOC").tocify(options).data("toc-tocify");
});
</script>

<!-- dynamically load mathjax for compatibility with self-contained -->
<script>
  (function () {
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src  = "https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
    document.getElementsByTagName("head")[0].appendChild(script);
  })();
</script>



<div style="position: absolute; width: 0px; height: 0px; overflow: hidden; padding: 0px; border: 0px; margin: 0px;"><div id="MathJax_Font_Test" style="position: absolute; visibility: hidden; top: 0px; left: 0px; width: auto; padding: 0px; border: 0px; margin: 0px; white-space: nowrap; text-align: left; text-indent: 0px; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal; font-size: 40px; font-weight: normal; font-style: normal; font-family: MathJax_Main-bold, sans-serif;"></div></div></body></html>
