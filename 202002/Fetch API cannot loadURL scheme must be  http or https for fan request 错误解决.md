 # Fetch API cannot load，URL scheme must be "http" or "https" for fan request 错误解决  

 这种问题是跨域资源共享问题，一般放生在做单纯的前端界面的时候，尤其是使用了vue.js或者其他的前端框架的时候。这个问题是因为你的资源存放在本地也就是file://这样的系统下，而不是网络资源比如http://。所以造成了这些框架可能找不到对应的资源。所以解决方案也很简单，只需要把其部署成网站（web服务）即可。因为我经常使用python，所以只需要在当前目录下，使用`python -m http.server`，即可以当前目录为站点部署成一个web服务，这个时候就不会报上面的错了。或者用node.js开启一个服务也可以，原理都是一样的，就是把当前目录变为web服务，这样就能在访问资源的时候避免使用file://了。