---

title: Sandbox 1 - awsome submit button
date: 2016-11-20 06:24:29
categories:
    - "lập trình"
tags:
    - "sandbox"
    - "front-end"
    - "ui/ux"
keywords:
	- html
	- html5
	- css
	- css3
	- animation
	- button
  - nút bấm
thumbnailImage: awsome-submit.png
thumbnailImagePosition: left 
coverImage: awsome-submit.gif
description: hôm nay của chúng ta là là xây xựng một nút submit có thể dùng cho form, upload file, xóa file... như hình cover ở trên thay vì tốn diện tích cho tất cả các progress bar, har alert tất cả sẽ được buit-in trong một nút duy nhất thôi. vô tình thấy được ý tưởng này trên  mạng thấy khá hay nên quên định trển luôn vào cuối tuần.

---

Xin chào, hôm nau mình xin được giới thiệu một chuên mục nóng hổi vừa thổi vừa ăn, đó cính là [#sandbox](/tags/sandbox), đúng như cái tên của nó sandbox sẽ là nơi mình show những sản phẩm siêu nhỏ mà mình làm trõng những lúc rảnh rỗi, như những lâu đài cayys thôi tất cả chỉ làm trong vòng vài tiếng và chủ yếu mang tính chất giải trí là chính. Để khởi đâu cho loạt bài này hôm nay mình sẽ quết định làm cái gì thực tế một chút, một nút submit của tương lai, ít nhất thì mình tinh là thế :D.
<!--more-->

{% pullquote "full goal" %}
**Mục tiêu** hôm nay của chúng ta là là xây xựng một nút submit có thể dùng cho form, upload file, xóa file... như hình cover ở trên thay vì tốn diện tích cho tất cả các progress bar, har alert tất cả sẽ được buit-in trong một nút duy nhất thôi. vô tình thấy được ý tưởng này trên  mạng thấy khá hay nên quên định trển luôn vào cuối tuần.
{% endpullquote %}

### Yêu Cầu
sản phẩm của ta phải đạt dủ các yêu cầu sau:
- thân thiện mobile
- hoạt đọng tốt trên các trình duyệt thông dụng
- animation mượt mà như trong thiết kế
- đảm bảo accessibility
- tận dụng tối da css
- không dùng thư viện js (kể cả jQuery)
- combo html5/css3/ES5

## Ok, Let's Play

đầu tiên ta phải có một karkup HTML

```html

	<div class="sandbox">
		<form onsubmit="return false;" role="form">
			<button class="awesome-submit">
			<div class="inner">
				<div class="back">
					<div class="content">
						
						<div class="progress-bar" data-=""></div>
					</div><i class="icon-arrow"></i>
				</div>
				<div class="front">
					<div class="content">
						Submit
					</div>
          <i class="icon-arrow">
            <span></span>
            <span></span>
            <span></span>
          </i>
				</div>
			</div></button>
		</form>
	</div>

```

cũng không có gì đặc biệt, nút của chúng ta bao gông hai phần phần là ``front`` phần ddawcf trước và ``back`` phần dằng sau mỗi phần có mooyj content chứa nột dung và icon. 

Tiếp là icon, các bạn có thể dùng [font aswesome](http://fontawesome.io/) nhưng vấn đề là ta chỉ dùng một vài icon thôi nên mình sẽ chỉ lấy vài icon cần thiết [fontello](http://fontello.com/) sẽ giúp ta tạo được một icon font của riêng mình.

đây là ion font mà mình đã tạo.

![cusom icon font](custom-image-font.png)

các bạn có thể tải về tại [dây](fontello-586e5351.zip).


### Làm màu nào.

Việc dầu tiên ta phải cho nó một cái giao diện tĩnh, khi không có gì tác động.

```CSS

.sandbox{
  width: 100%;
  height: 100px;
  padding: 20px;
  background-color: #edeaed;
}

form{
  width: 500px;
  margin-left: auto;
  margin-right: auto;
}

.awesome-submit{
  padding: 0;
    border-radius: 50px;
    text-align: center;
    line-height: 70px;
    font-size: 22px;
    color: #fff;
    cursor: pointer;
    box-shadow: none;
    border: none;
    z-index: 40;
    -webkit-transition: ease-in 4s;
    transition: ease-in 4s;
}


.awesome-submit .inner{
  position: relative;
  height: 70px;
}

.awesome-submit:active,
.awesome-submit:focus,
.awesome-submit:active .inner,
.awesome-submit:focus .inner{
  outline: none;
  box-shadow: 0 0 0 rgba(0, 0, 0, 0.5);
}
.awesome-submit .front,
.awesome-submit .back,{
  overflow: hidden;
  border-radius: 50px;
}

.awesome-submit .inner,
.awesome-submit .front,
.awesome-submit .back,
.awesome-submit .content{
  transition: all 1s;
}

.awesome-submit .front{
  position: absolute;
    ;
  top: 0;
  left: 0;
  white-space: nowrap;
} 

.awesome-submit .back{
 background-color: #fff;
  height: 100px;
}

.awesome-submit .back .content{
  display: inline-block;
}
.awesome-submit .back i:last-child{
  margin-left: 6px;
}

.awesome-submit .front{
  padding: 0 40px;
  background-color: #52475b;
  box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.5);
  white-space: nowrap;
}

.awesome-submit .front.circle{
  padding: 0;
  width: 70px;
}

@keyframes float-right{
  from{ transform: translateX(-105px); }
  to{ transform: translateX(0);}
}
.awesome-submit .primary .front .icon-arrow {
    display: inline-block;
    animation: float-right .6s ease-out 0s 1 normal;
}

.awesome-submit .front.circle .content{
  display: none;
}

.awesome-submit .front .content{
  display: inline;
}

.awesome-submit .back{
  //width: 100%;
  height: 100%;
  background-color: #fff;
  color: #494151;
  padding: 0 40px 0 90px;
  white-space: nowrap;
}

.awesome-submit .process{
  
}
// process icon 

@keyframes bounching1 {
  0% {
    transform: translateY(0px);  
  }

  25% {
    transform: translateY(-10px);
  }
  
  50%{
     transform: translateY(0px);
  }
}

@keyframes bounching2 {
  0% {
    transform: translateY(0px);  
  }

  25% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
  75% {
    transform: translateY(0px);
  }
  100%{
    transform: translateY(0px);
  }
}

@keyframes bounching3 {
  0% {
    transform: translateY(0px);  
  }

  50% {
    transform: translateY(0px);
  }
  75% {
    transform: translateY(-10px);
  }
  100%{
     transform: translateY(0px);
  }
}

i:not(.icon-bounce) span{
  display: none;
}

.icon-bounce{
    font-family: "fontello";
    font-style: normal;
    font-weight: normal;
    speak: none;
    display: inline-block;
    text-decoration: inherit;
    text-align: center;
    /* opacity: .8; */
    font-variant: normal;
    text-transform: none;
    line-height: 1em;
}

.icon-bounce span:first-child{
  
animation: bounching1 2s linear 0s infinite normal;
}

.icon-bounce span:nth-child(2){

animation: bounching2 2s linear 0s infinite normal;
}

.icon-bounce span:last-child{

animation: bounching3 2s linear 0s infinite normal;
}

.icon-bounce span{
    width: auto;
    display: inline-block;
    padding: 0 2px;
    margin: 0;
    font-weight: bold;
}
//progress bar
.awesome-submit .process .back{
  padding-left: 72px;
  padding-right: 15px;
}
  
.awesome-submit .process .content{
  background-color: #fff; 
}
.awesome-submit .process .content .progress-bar{
  position: relative;
  width: 270px;
  height: 8px;
  background-color: #e8e8e9;
  line-height: 70px;
  display: inline-block;
  vertical-align: middle;
  border-radius: 4px;
}

.awesome-submit .process .content .progress-bar .value{
  content: " ";
  position: absolute;
  background-color: #b7e88e;
  width: 0%;
  height: 100%;   
   border-radius: 4px;
  transition: width .1s;
}

.awesome-submit .process .back i[class^=icon-]{
  line-height: 1;
   overflow: hidden;
   vertical-align: middle;
  font-size: 22px;
  color: #dedbdb;
  padding: 0 4px;
  transition: color .1s;
}

.awesome-submit .process .back i[class^=icon-]:hover{
color: #71647b;
}

// error 

.awesome-submit .error .front{
  background-color: #e0444c;
}

.awesome-submit .error .front span{
  display: none;
}

.awesome-submit .error .back{
  color: #e0444c; 
}

.awesome-submit .error .back i:last-child{
display: none;
}

//success

.awesome-submit .success .front,{
display: none;
}

.awesome-submit .success .back {
  padding-right: 70px;
  color: #69c719;
}

```

he, hơi dài nhỉ mình cũng chả biết mình viết cái gì dây nữa, kỳ sau mình sẽ dùng sass cho anh em dễ nhìn nhé, chứ thế này hiếp dâm thị giác người đọc quá :D.

{% pullquote "full tip"%}
có một lưu ý nhỏ ở dây là bạn phải style sao cho khi trình duyệt không chạy javascript họn vẫn submit được bình thường và không bị vỡ design, code ra phải dảm bảo ai cũng dừng được chứ :).
{% endpullquote %}

## tạo scandal nào!

Tất nhiên chỉ làm màu thôi là chưa đủ, để có thể thành công ta không thể thiếu scandal, javascript sẽ qui định các trạng thái của nút.


```javascript

var AsweomeSubmit = function(selector) {
    if (!selector) return;
    if (typeof selector === 'string') {
        var el = document.querySelector(selector)
    } else {
        var el = selector;
    }
    var defaultState = {
        className: '',
        frontClass: '',
        frontText: '',
        frontIcon: '',
        backText: '',
        backIcon: '',
        live: 0
    };

    var states = {
        primary: {
            text: 'Submit',
            frontIcon: 'icon-arrow'
        },
        confrim: {
            className: 'confrim',
            frontClass: 'circle',  
            backText: 'Try again?',
            icon: 'icon-repeat'
        },
        process: {
            className: 'process',
            frontClass: 'circle',
            frontIcon: 'icon-bounce',
            backIcon: 'icon-cancel'
        },
        error: {
            className: 'error',
            frontClass: 'circle',
            backText: 'Oops! Something went wrong.',
            icon: 'icon-cancel'
        },
        success: {
            className: 'success',
            backText: 'Success',
            backIcon: 'icon-ok',
            live: 3000
        }
    };


    var staticClass = el.getAttribute('class');
    var inner = el.querySelector('.inner');
    var front = inner.querySelector('.front');
    var frontContent = front.querySelector('.content');
    var frontIcon = front.querySelector('[class^=icon-]');
    var back = inner.querySelector('.back');
    var backContent = back.querySelector('.content');
    var backIcon = back.querySelector('[class^=icon-]');

    var instance = function(el) {
        var state = 'primary';
        var value = 0;
        var error = false;

        var pushState = function(nextState) {
            if (!states[nextState]) return;
            var data = Object.assign({}, defaultState, states[nextState]);
            state = nextState;
            inner.className = 'inner ' + nextState;
            front.className = 'front ' + data.frontClass;
            frontContent.innerHTML = data.text || data.frontText;
            frontIcon.className = data.icon || data.frontIcon;
            backContent.innerHTML = data.backText;
            backIcon.className = data.backIcon;
        }

        inner.addEventListener('click', function(){
            switch(state){
              case 'error': { 
                el.AWE.confrim(); 
              } break;
              case 'confrim': {
                el.AWE.reset(); 
              } break;
              case 'success': {
                el.AWE.reset(); 
              } break;
            }
         })
      
      this.state = function(){
        return state;
      }
      
        this.reset = function() {
            pushState('primary');
        }

        this.process = function(value) {
            var prBar = backContent.querySelector('.progress-bar');
            if(!prBar) return;
            prBar.setAttribute('data-value', value);
            prBar.querySelector('.value').style.width = '' + value + '%';
        }

        this.success = function() {
            pushState('success');
            var that = this;
          
            setTimeout(function() {
              that.reset();
            }, 30000);
        }

        this.submit = function() {
            if (state !== 'primary') return;
            pushState('process');
            backContent.innerHTML = '<div class="progress-bar" data-value="0"><div class="value"></div></div>';


            var that = this;
            var value = 0;

            backIcon.onclick = function(e) {
                e.stopPropagation();
                e.preventDefault();
                that.cancel();
            }
        }

        this.cancel = function() {
            if (state !== 'process') return;
            this.reset();
        }

        this.error = function() {
            pushState('error');
        }
        
        this.confrim = function(){
          pushState('confrim');
          //backContent.style.width = '500px'; 
        }
    }


    el.AWE = new instance(el);

    return el;
}

var button = AsweomeSubmit('.awesome-submit');
var value = 0;

function grow() {
  if(button.AWE.state() == 'error') return;
  
    button.AWE.process(value += 2);
    if (value <= 100) {
        setTimeout(grow, 200);
    } else {
     button.AWE.success();
    }
}

button.addEventListener('click', function(){
  if(this.AWE.state() != 'primary') return;
  value = 0;
  var willFail = (Math.random() > .6) ? false : true;
  this.AWE.submit();
  var _this = this;
  
  setTimeout(grow, 1000);
  if(!willFail) return;
  setTimeout(function(){
    _this.AWE.error();
  }, 8000)
})

```

{% pullquote "full tip"%}
đây là một UI component nên mình sẽ không tập trung vào logic, cũng như không có thiều thời gian nên code chưa tối ưu anh em thông cảm nhé.
{% endpullquote %}

## kết quả 
và dây là kết quả của chúng ta. bạn có thể fork lại tai [codepen](http://codepen.io/minhlucvan/pen/yVMjNx)

{% iframe './demo/index.html' 100% 180px %}


Ôi trời ơi, sandbox đầu tiên mệt ngoài sức tưởng tượng. ban đầu mình định dung tất cả basic để chơi nhưng thực sự là không vui một chút nào cả. chắc lần sau mình sẽ dùng libs, jQuery, React gì đó để đỡ khổ hơn. Hy vọng đã dem lại được điều gì đó cho anh em, Hẹn gặp lại ở sandbox kỳ sau.

**writen @Minhlv wuth <3** 
