---
---


<div id="streak"></div>


<script>
var firstmonday = Date.parse("2022-01-03");

var today = new Date();

function getWeekNum(date){
  var days_mon = Math.floor((Date.parse(date) - firstmonday) / 8.64e7);
  var week_num = Math.floor(days_mon / 7) + 1;
  return week_num;
}

var posts = [];

{% for post in site.posts %}
var object = {};
posts.push({"title":"{{post.title | escape}}","date":"{{post.date | date: "%Y-%m-%d"}}","week":"{{post.date | date: '%W'}}","year":"{{post.date | date: '%Y'}}"});
{% endfor %}

var today_week_num = getWeekNum(today);
var latest_week_num = getWeekNum(posts[0].date);


if (today_week_num - latest_week_num < 2){
  var streak = 1;
  for (var i = 0; i < posts.length ; i++){
    if(getWeekNum(posts[i].date) - getWeekNum(posts[i+1].date) == 0){

    }else if(getWeekNum(posts[i].date) - getWeekNum(posts[i+1].date) == 1){
      streak++;
    }else{
      break
    }
  };

}

console.log("Streak "+streak)

if(streak > 0){
  document.getElementById("streak").innerHTML = streak;
};



</script>





