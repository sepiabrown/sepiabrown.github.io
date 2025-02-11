---
layout: blog-sidebar-nav
title: Notes
---

*My notes are hosted on Microblog. I'm [@sepiabrown](https://micro.blog/sepiabrown). See the [archive here](https://notes.sepiabrown.github.io/archive/). Quotes are styled using [Quotebacks](https://quotebacks.net/).*

<div id="microblog"></div>

<script note="" src="https://cdn.jsdelivr.net/gh/Blogger-Peer-Review/quotebacks@1/quoteback.js"></script>

<script>

fetch("https://notes.sepiabrown.github.io/feed.json")
    .then((response) => {return response.json()})
    .then((data) => {
        for(var i = 0; i <data.items.length; i++){
            var timestamp = data.items[i].date_published;
            var date = new Date(timestamp);
            var div = document.createElement("div");
            div.innerHTML = `<div class="bt bb b--black-20 pv4"><div class="f6 black-40"><a href="${data.items[i].url}">${date.getDate() + "/" + (date.getMonth()+1) + "/"+date.getFullYear() }</a></div><div>${data.items[i].content_html}</div></div>`;
            document.getElementById("microblog").appendChild(div);
            //trigger a domcontentloaded to force Quotebacks JS to work
        window.document.dispatchEvent(new Event("DOMContentLoaded", {
            bubbles: true,
            cancelable: true
        }));
        }
                
        console.log(data);
        

    });



</script>