# twikoo-update

# 这里是twikoo自动更新工具

# 实现流程

- twikoo 发布更新触发 [renovate[bot]](https://github.com/MHuiG/twikoo-update/blob/main/renovate.json) 提交[PR](https://github.com/MHuiG/twikoo-update/pull/1).

- [mergify[bot]](https://github.com/MHuiG/twikoo-update/blob/main/.mergify.yml) 合并 PR.

- 合并 PR Push 触发本仓库 [Github Actions](https://github.com/MHuiG/twikoo-update/blob/main/.github/workflows/main.yml).

- Github Actions 自动部署云函数.

# 前端导入twikoo

前端从jsdelivr读取[package.json](https://github.com/MHuiG/twikoo-update/blob/main/package.json)的twikoo版本号，加载twikoo，保证版本一致.

```
function loadScript(src,cb){var HEAD=document.getElementsByTagName('head')[0]||document.documentElement;var script=document.createElement('script');script.setAttribute('type','text/javascript');if(cb)script.onload=cb;script.setAttribute('src',src);HEAD.appendChild(script)}

$.ajax({
	 type: "GET",
	 url: "https://cdn.jsdelivr.net/gh/MHuiG/twikoo-update@main/package.json?v="+new Date().getTime(),  // this repo
	 dataType: "json",
	 success: function(data){
		console.log(data.devDependencies.twikoo)
		loadScript('https://cdn.jsdelivr.net/npm/twikoo@'+data.devDependencies.twikoo)
	}
});

```

# bot

- [Renovate[bot]](https://github.com/marketplace/renovate)

- [Mergify[bot]](https://github.com/marketplace/mergify)



