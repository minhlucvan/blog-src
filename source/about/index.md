---
layout: page
title: Giới Thiệu
---
{% raw %}
<style>
	.row{
		width: 100%;
		margin-bottom: 10px;
	}
	.row.pull-right{
		text-align: right;
	}

	.pull-right{
		margin-right: 0;
	}

	.flag{
		display: inline-block;
		width: 45px;
		height: 30px;
		background-color: grey; 
		cursor: pointer;
		background-position: -3px -12px;
		background-size: 48px 51px;
	}

	.flag.vi{
		background-image: url('images/flag-vn.png'); 
	}

	.flag.en{
		background-image: url('images/flag-uk.png'); 
	}
.intro{
	margin-top: 22px !important;
}
.card-title{
	padding: 10px;
	position: absolute;
	top: 0;
	left: 0;
	transition: all 2s;
}
.card .ripper{
	background-color: #263740;
}
.card.dream .card-icon{
	border-radius: 0; 
}
.card.osource .card-icon{
	background-color: #263740; 
}
	.intro .avatar{
		margin-left: 0;
		display: inline-block;
		width: 128px;
		height: 128px;
	}
	.intro .text{
		padding-left: 20px;
		display: inline-block;
		vertical-align: top;
		width: 552px;
	}
	.intro .text p{
		margin: 0;
	}
	.pulzee{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		margin-top: 20px;
	}
	.quater{
		width: 50%;
	}
	.card{
		border: solid 1px #eceff2;
		box-sizing: border-box;
		overflow: hidden;
	}
	.card .card-header{
		position: relative;
		width: 100%;
		height: 120px;
		overflow: hidden;	
		text-align: center;	
	}

	.card:hover .card-header .ripper{
		opacity: 1;
		transform: scale(10);
	}
	.card:hover .card-header .card-title{
		color: white;
	}
	.card-header .ripper{
		position: absolute;
		top: 10px;
		left: 10px;
		opacity: 0;
		transition: all 2s;
	}
.card-title .text{
    vertical-align: top;
    line-height: 52px;
    font-size: 24px;

}

.card-icon, .card-title .text{
	display: inline-block !important;
	margin-left: 15px;
}
	.card-icon, .card .card-header .ripper{
		width: 100px;
    	height: 100px;
	    border-radius: 50%;
	}

	.card-body{
		padding: 10px;
		margin-top: 0px !important; 
	}

@media(max-width: 799px){
	.intro .avatar{
		display: block;
		margin-right: auto;
		margin-left: auto;		
	}
	.intro .text{
		width: 100%;
		padding-left: 0;
	}
}

@media(max-width: 600px){
	.quater{
		width: 100%;
	}	
}

</style>
<div class="row pull-right" style="margin-bottom: 20px">
	<div class="pull-right">
		<span class="flag vi" title="switch to Vietnamese"></span>
		<span class="flag en" title="switch to English"></span>
	</div>
</div>
<br>
<blockquote class="intro">
<img class="avatar no-fancy" src="images/avatar.png" title="xin chào, tôi là Minh" />
<div class="text">
	<p>Xin Chào tôi tên là <strong>Lục Văn Minh</strong>, tôi là một người trầm tính it nói và lười nhác . Cuộc đời đối với tôi khá đơn có <strong>gia đình</strong>, có <strong>bạn bè</strong> là có tất cả, à còn cần có <strong>mạng</strong> nữa chứ nhỉ. Đam mê lớn nhất của tôi là <strong>lập trình</strong>, và tôi quết định giành cả tuổi thanh xuân để theo đuổi đam mê của mình, từ những dòng code của mình tôi hy vọng sẽ góp phần cho thế giới tốt đẹp hơn.</p>
</div>
</blockquote>
<div class="row pulzee">
	<div class="quater card life">
		<div class="card-header">
		<div class="ripper">
		</div>
		<div class="card-title">
		<img src="images/flat-faces-icons-circle-3.png" alt="my life" class="card-icon no-fancy">
		<h4 class="text">Về Cuộc Sống</h4>
		</div>
		</div>
		<p class="card-body">
			Cuộc sống của tôi khá đơn giản, ngoài lập trình thì và thời gian rảnh tồi thường <strong>lưót ưeb</strong> tìm hiểu sự tình giang hồ, các <strong>công ngệ mới</strong> cũng như <trong>hackernews</trong>. vói các hoạt offline, tôi thích <strong>ăn</strong> và thích nấu ăn, <trong>đọc sách</trong>. môn thể tao yêu thích của tôi là <strong>chạy bộ</strong> và <strong>bơi lội</strong>, có lẽ tại không giỏi môn nào khác :).
		</p>
	</div>
	<div class="quater card dream">
		<div class="card-header">
		<div class="ripper">
		</div>
		<div class="card-title">
		<img src="images/Creative-Tail-rocket.svg.png" alt="dream" class="card-icon no-fancy">
		<h4 class="text">Về Động Lực</h4>
		</div>
		</div>
		<div class="card-body">
			Tôi luôn muốn học hỏi những <strong>điều mới mể</strong>, đi lên những <strong>vùng đất mới</strong>, trả nghiệp những nền <strong>văn hóa mới</strong> và nếm thử những <strong>mốn ăn mới</strong>. với công việc tôi luôn muốn hoàn thiện <strong>kỹ năng</strong> cũng như <strong>tu duy</strong> của mình để mỗi sản phẩm của mình đều <strong>chạm đến trái tim của người dùng</strong>. 
		</div>
	</div>
	<div class="quater card code">
		<div class="card-header">
		<div class="ripper">
		</div>
		<div class="card-title">
		<img src="images/monitor_code__editor-512.png" alt="coding" class="card-icon no-fancy">
		<h4 class="text">Về Lập Trình</h4>
		</div>
		</div>
		<div class="card-body">
			Tôi có một niềm đam mê với <strong>lập trình</strong> nói chung và <strong>lập trình web</strong> nói riêng. Tôi thích sự tiện lợi của <strong>PHP</strong>, yêu  sự ôn định của <strong>java</strong>,  yêu sự mềm dẻo của <strong>javascript</strong>, sự mạnh mẽ của <strong>python</strong>, sự đơn giản của <strong>ruby</strong>. ngoài ra tôi cũng thích những front-end frameworks như <strong>React</strong>, <strong>Angular 2</strong>, <strong>Polymer</strong>. môi trường lập trình yêu thích của tôi là <strong>Linux</strong> và các IDE của <strong>JetBrain</strong>.
		</div>
	</div>
	<div class="quater card osource">
		<div class="card-header"> 
		<div class="ripper">
		</div>
		<div class="card-title">
		<img src="images/github-icon.png" alt="open-source" class="card-icon no-fancy">
		<h4 class="text">Về Mã Nguồn Mở</h4>
		</div>
		</div>
		<div class="card-body">
			Tất nhiên rồi, tôi yêu mã nguồn mở và gành cả ngày trên <strong>github</strong>. Thật hạnh phúc khi đưọc đóng góp cho những dự án tuyệt vời như <strong>LearnPress</strong> ..., tôi sẵn sàng tham gia vào các dự án mã nguồn mở ý nghĩa, cho đi cũng là nhận lại, vì một cộng đồng mã ngồn mở lớn mạnh.
		</div>
	</div>
</div>
{% endraw %}

## Chỉ Mục
dưới đâu là những trang ưeb tôi thường xuyên lui tới, đây à những nguôn thông tin khổng lồ giúp tôi giải trí cũng như hoàn thiên bản thân mình hơn.

- [medium](http://medium.com) 👉 tất cả trên một trang duy nhất
- [wait but why](http://waitbutwhy.com/) 👉 nhìn cưọc sống qua một góc nhìn mới
- [Freecodecamp](https://medium.freecodecamp.com/)  👉 một cộng đòng năng động và tụ vị
- [hackernews](https://news.ycombinator.com/) 👉 tổng hợp tin tức công nghệ
- [TED](https://www.ted.com/) 👉 nơi chia sẻ những câu chuyện ý nghĩa, những ý tưởng kiệt suất
- [Javascript sence](https://medium.com/javascript-scene) 👉 mọi khía cạnh của javascript
- [techtalk](http://techtalk.vn/) 👉  tin tức công nghệ tiwngs việt
- [toidicodedao](toidicodedao.com) 👉 những câu chuyện chận thực về cuộc sống của lập trình viên
- [daynhauhoc](https://daynhauhoc.com)  👉  diên đần trao đổi về công nghệ

## Sách
tôi đã học được rất nhiều từ những cuốn sách này: 

{% raw %}
<style>
.books{
	display: flex;
	flex-direction: row;
	flex-wrap: wrap;
	justify-content: space-between;
}
.book{
	box-sizing: border-box;
	width: 23%;
	margin-bottom: 18px; 
	-webkit-box-shadow: 3px 3px 2px 0px rgba(0,0,0,0.75);
	-moz-box-shadow: 3px 3px 2px 0px rgba(0,0,0,0.75);
	box-shadow: 3px 3px 2px 0px rgba(0,0,0,0.75);
	transition: all .5s;
}
.book .cover{
	width: 100%;
	height: 100%;
}
.book:hover{
	transform: scale(1.1);
	-webkit-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
	-moz-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
	box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
}

.grayscale{
	-webkit-filter: grayscale(60%); /* Safari 6.0 - 9.0 */
    filter: grayscale(60%);
}

@media(max-width: 959px){
	.book{
		width: 46%;
	}
}
</style>
<div class="books">
	<div class="book">
		<img src="images/thoi-that-rong-lon.jpg" class="cover no-fancy" title="thế giới quả thật rộng lớn và có rất nhièu việc phải làm">
	</div>
	<div class="book">
		<img src="images/cafe-cung-tony.jpg" class="cover no-fancy" title="cà  phê cùng Tony">
	</div>
	<div class="book">
		<img src="images/nha-gia-kim.u84.d20161102.t102644.515752.jpg" class="cover no-fancy" title="nhà gia kim">
	</div>
	<div class="book">
		<img src="images/download.jpg" class="cover no-fancy" title="mật mã dvanci">
	</div>
	<div class="book">
		<img src="images/big-data.jpg" class="cover no-fancy" title="Dữ liệu lớn : cuộc cách mạng sẽ làm thay đổi cách chúng ta sống, làm việc và tư duy">
	</div>
	<div class="book">
	<img src="images/code-cmplete.jpg" class="cover no-fancy" title="code complete 2">
	</div>
	<div class="book">
		<img src="images/quoc-gia-khoi-nghiep.jpg" class="cover no-fancy" title="quốc gia khởi nghiệp">
	</div>
	<div class="book">
		<img src="images/EINSTEIN-mua-sach-re-420x606.jpg" class="cover no-fancy" title="EINSTEIN cuộc đời và vũ trụ">
	</div>
</div>
{% endraw %}

## Liên Hệ
hiện tai tôi đang sinh sống và làm việc tại <strong>Hà Nội</strong>.
Bạn có thể liên hệ với tôi bất cứ lúc nào qua:

- email: [luk.mink@gmail.com](mailto:luk.mink@gmail.com) 
- facebook: [minhlucvan3](https://fb.com/minhlucvan3)
- twiter: [@Minhlucvan](https://twitter.com/Minhlucvan)
- skype: live:minhmeo004

Rất vui khi được làm quen với bạn.

{% raw %}
<script type="text/javascript">
	(function(){
		var books = document.querySelectorAll('.books .book');
		function fadeAll(){
			for(let b of books){
				if(this !== b){
					b.classList.toggle('grayscale');
				}	
			}
		}

		books.forEach(function(book){
			book.onmouseenter = fadeAll.bind(book)
			book.onmouseleave = fadeAll.bind(book);
		});
	}());
</script>
{% endraw %}