# twikoo-import-function


```
function loadScript(src,cb){var HEAD=document.getElementsByTagName('head')[0]||document.documentElement;var script=document.createElement('script');script.setAttribute('type','text/javascript');if(cb)script.onload=cb;script.setAttribute('src',src);HEAD.appendChild(script)}

$.ajax({
	 type: "GET",
	 url: "https://cdn.jsdelivr.net/gh/MHuiG/twikoo-import-function@main/package.json",
	 dataType: "json",
	 success: function(data){
		console.log(data.devDependencies.twikoo)
    loadScript('https://cdn.jsdelivr.net/npm/twikoo@'+data.devDependencies.twikoo)
	}
});

```
