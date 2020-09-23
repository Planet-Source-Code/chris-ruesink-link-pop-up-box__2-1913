<div align="center">

## Link Pop Up Box


</div>

### Description

When Moving the mouse over a link, it brings up a box with description of the link in it.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Chris Ruesink](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/chris-ruesink.md)
**Level**          |Intermediate
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |
**Category**       |[Links](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/links__2-79.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/chris-ruesink-link-pop-up-box__2-1913/archive/master.zip)





### Source Code

```
<style type="text/css">
#divDescription{position:absolute; width:200; visibility:hidden; z-index:200}
.clDescription{width:150; font-family:verdana,arial,helvetica; font-size:11px; background-color:#cccccc; padding:3px; border: 1px solid #999999}
#divlinks{position:absolute; left:100; top:200; z-index:1}
</style>
<script type="text/javascript" language="JavaScript">
//Default browsercheck, added to all scripts!
function checkBrowser(){
	this.ver=navigator.appVersion
	this.dom=document.getElementById?1:0
	this.ie5=(this.ver.indexOf("MSIE 5")>-1 && this.dom)?1:0;
	this.ie4=(document.all && !this.dom)?1:0;
	this.ns5=(this.dom && parseInt(this.ver) >= 5) ?1:0;
	this.ns4=(document.layers && !this.dom)?1:0;
	this.bw=(this.ie5 || this.ie4 || this.ns4 || this.ns5)
	return this
}
bw=new checkBrowser()
/***************************************************************************************
Variables to set:
***************************************************************************************/
messages=new Array()
//Write your descriptions in here.
messages[0]="Description of test link 0"
messages[1]="Description of test link 1"
messages[2]="Description of test link 2"
messages[3]="Description of test link 3"
messages[4]="Description of test link 4"
//To have more descriptions just add to the array.
fromX=50 //How much from the actual mouse X should the description box appear?
fromY=-20////How much from the actual mouse Y should the description box appear?
//To set the font size, font type, border color or remove the border or whatever,
//change the clDescription class in the stylesheet.
//Makes crossbrowser object.
function makeObj(obj){
  	this.css=bw.dom? document.getElementById(obj).style:bw.ie4?document.all[obj].style:bw.ns4?document.layers[obj]:0;
  	this.wref=bw.dom? document.getElementById(obj):bw.ie4?document.all[obj]:bw.ns4?document.layers[obj].document:0;
	this.writeIt=b_writeIt;
	return this
}
function b_writeIt(text){if(bw.ns4){this.wref.write(text);this.wref.close()}
else this.wref.innerHTML=text}
//Capturing mousemove
var descx,descy;
function popmousemove(e){descx=bw.ns4?e.pageX:event.x; descy=bw.ns4?e.pageY:event.y}
//Initiates page
var isLoaded;
function popupInit(){
  oDesc=new makeObj('divDescription')
  if(bw.ns4)document.captureEvents(Event.MOUSEMOVE)
  document.onmousemove=popmousemove;
  isLoaded=true;
}
//Shows the messages
function popup(num){
  if(isLoaded){
	oDesc.writeIt('<span class="clDescription">'+messages[num]+'</span>')
	if(bw.ie5) descy=descy+document.body.scrollTop
	oDesc.css.left=descx+fromX; oDesc.css.top=descy+fromY
	oDesc.css.visibility='visible'
  }
}
//Hides it
function popout(num){
	if(isLoaded) oDesc.css.visibility='hidden'
}
//initiates page on pageload.
onload=popupInit;
</script>
</HEAD>
<BODY bgcolor="White">
<div id="divDescription">
<!--Empty div-->
</div>
<div id="divLinks">
	<!-- Just delete this layer, it's just here for the example links -->
	<a href="#" onmouseover="popup(0)" onmouseout="popout(0)">test link 0</a> -
	<a href="#" onmouseover="popup(1)" onmouseout="popout(1)">test link 1</a> -
	<a href="#" onmouseover="popup(2)" onmouseout="popout(2)">test link 2</a> -
	<a href="#" onmouseover="popup(3)" onmouseout="popout(3)">test link 3</a> -
	<a href="#" onmouseover="popup(4)" onmouseout="popout(4)">test link 4</a>
</div>
```

