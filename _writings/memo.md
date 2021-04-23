---
layout: post
title: memo
img: "assets/img/title.png"
---

## Colab 연결끊김 방지 스크립트

{% highlight js %}
function ClickConnect() { 
    var buttons = document.querySelectorAll("colab-dialog.yes-no-dialog paper-button#cancel"); 
    buttons.forEach(function(btn) { btn.click(); }); 
    console.log("1분마다 자동 재연결"); 
    document.querySelector("#top-toolbar > colab-connect-button").click(); 
    } 
setInterval(ClickConnect,1000*60);

clearInterval(/*code generated by setInterval */);
{% endhighlight %}