# VSCode-Setup

Help >> Toggle Developer Tools >> Sources >> Scripts

### For loading local fonts, create new script file and fill this:
```javascript
var styleNode = document.createElement('style'); 
styleNode.type = "text/css"; 
var styleText = document.createTextNode(`
    @font-face{
        font-family: 'Fira Code';
        src: url('file:///C:/Users/tanuj.sharma/Downloads/FiraCode-Retina.ttf') format('truetype');
        font-weight: normal;
    }
    @font-face{
        font-family: 'Operator';
        src: url('file:///C:/Users/tanuj.sharma/Downloads/OperatorMono-Book.otf') format('opentype');
        font-weight: normal;
    }
    @font-face{
        font-family: 'OperatorI';
        src: url('file:///C:/Users/tanuj.sharma/Downloads/OperatorMono-BookItalic.otf') format('opentype');
        font-weight: normal;
    }
    @font-face{
        font-family: 'ScriptBT';
        src: url('file:///C:/Users/tanuj.sharma/Downloads/SCRPT12N.ttf') format('truetype');
        font-weight: normal;
    }
    @font-face{
        font-family: 'Dank';
        src: url('file:///C:/Users/tanuj.sharma/Downloads/DankMono-Regular.otf') format('opentype');
        font-weight: normal;
    }
    @font-face{
        font-family: 'DankI';
        src: url('file:///C:/Users/tanuj.sharma/Downloads/DankMono-Italic.otf') format('opentype');
        font-weight: normal;
    }`); 
styleNode.appendChild(styleText); 
document.getElementsByTagName('head')[0].appendChild(styleNode);
```

### For setting fonts, create script files for each italic font; in that fill:
```javascript
function tabClick(){
	var els = document.querySelectorAll('.mtki');
    for(var index = 0; index<els.length; index++){
        els[index].style.fontFamily = 'OperatorI';
    }
}
function closeClick(){
	var crosses = document.querySelectorAll('a.close-editor-action');
	for(var j in crosses){
		crosses[j].onclick = function(){setTimeout(tabClick,100)};
	}
}
// Tab Switching
document.querySelector(".tabs-container").onclick = tabClick;

// Tab Opening
var monacoRows = document.querySelectorAll(".monaco-tree-row:not(.has-children)");
for(var i in monacoRows){
	monacoRows[i].onclick = function(){
		setTimeout(tabClick,100);
		
		// Hooking new set of Tabs 
		setTimeout(closeClick,100);
	};
}

// Hooking up already opened Tabs
closeClick()
```
