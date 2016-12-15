# js&ajax

Простой вывод новостей из группы ВК

<div class="test-w">
	<div class="social-block">
		<h2>Новости группы Вконтакте</h2>
		<div class="demo-container"><ul></ul></div>
	</div>
</div>
<script type="text/javascript">
(function() {
 var flickerAPI = "https://api.vk.com/method/wall.get?owner_id=-"+your_id+"&filter=owner&v=5.60&callback=?";
 $.getJSON( flickerAPI, {
   tags: "mount rainier",
   tagmode: "any",
   format: "json"
 })
 .done(function( result ) {
 	for(var i=0;i<result.response.items.length;i++){        
		if (result.response.items[i].attachments) {
			var text = result.response.items[i].text;
			var data = new Date(result.response.items[i].date);
			var img;
				if (result.response.items[i].attachments[0].photo) {
					img = result.response.items[i].attachments[0].photo.photo_604;
					img = '<img src="'+img+'">';
				};
				if (result.response.items[i].attachments[0].video) {
					// вывод видео
				};
				var newsVK = '<li class="wr wr-1"><div class="comment-head"><div class="comment-avatar" style="background-image: url("")></div><strong><span class="name">Title</span></strong><span class="gray">'+data+'</span></div><div class="num-block"><p>'+ text +'</p>'+img+'</div></li>';
			$('.demo-container ul').append(newsVK);	
		}else{
			console.log('пусто');
		}
		// return newsVK;   	
	}
 });
})();
</script>
