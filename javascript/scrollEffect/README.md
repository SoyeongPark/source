# Scroll Effect

페이지 스크롤 시 설정된 위치에서 정의된 효과가 적용됩니다. 
간단한 효과를 적용을 할 때 사용합니다. 
조금 더 정교하고 화려한 효과를 주고싶다면 SCROLL MAGIC의 고유 기능이나 GSAP 등을 사용하세요.

## 기본 사용 방법
### HTML
```html
<div data-scroll="fadein_up">효과가 적용된 요소</div>
```
 효과를 적용하고자 하는 요소에 data-scroll을 삽입하고 " "안에는 적용하고자 하는 효과의 명칭을 자유롭게 작성합니다. (효과는 style로 정의됩니다.)  

### Javascript
```Javascript
<script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.7/ScrollMagic.min.js"></script>
// 스크롤 시 태그 위치 확인을 위해 scrollMagic 플러그인을 사용합니다. 

<script>
	$(function(){
		// run sroll effect 
		if( $('[data-scroll]').length) 
			scrollEffect();
	});
	// 페이지 내 data-scroll이 존재하는 경우 scrollEffect()를 실행합니다.

	/* scroll effect */
	function scrollEffect(){
		var controller = new ScrollMagic.Controller();
		
		var revealElements = document.querySelectorAll('[data-scroll]');
		for (var i=0; i<revealElements.length; i++) {
			var tar = {
				el : revealElements[i],
				hook : revealElements[i].getAttribute('data-hook')? revealElements[i].getAttribute('data-hook') : 0.9,
			};

			var scene = new ScrollMagic.Scene({
				triggerElement: tar.el,
				triggerHook: tar.hook
			})
			.setClassToggle(tar.el, "on") // add class toggle
			.addTo(controller);
		};

		if( $('[data-scroll="steps"]').length ){
			$('[data-scroll="steps"] [data-scroll]').each(function(i){
				$(this).css('transition-delay',(i*.1)+'s');
			});
		}
	}
</script>
```
> 스크롤이 요소를 지나가면 .on이 추가됩니다.  
> 세부 옵션은 코멘트 없이 아래 별도 항목으로 기입합니다.

### css
```css
[data-scroll="fadein_up"]:not([data-steps]),
[data-scroll="fadein_up"][data-steps] [data-step]{opacity:0; transform:translateY(-30px); transition:.3s;}
[data-scroll="fadein_up"]:not([data-steps]).on,
[data-scroll="fadein_up"][data-steps].on [data-step]{opacity:1; transform:translateY(0);}
```
> html에 삽입한 효과 명칭에 적용하고자 하는 스타일 효과를 작성합니다.   
  
  
  
## OPTIONS
### [효과 적용 위치 변경]
기본적으로 효과가 적용되는 트리거의 위치는 화면의 Y축 90%입니다.
트리거의 위치를 변경하려면 효과가 적용될 요소에 data-hook=""에 0~1 사이의 값을 삽입합니다. 0은 화면의 제일 상단, 1은 화면의 제일 하단을 뜻합니다.

```html
<div data-scroll="fadein_up" data-hook=".5">화면의 50%에서 .on</div>
```

### [순차 적용]
data-steps 하위 요소에 시간차로 효과를 적용합니다. 하위 data-step에 순서대로 transition-delay가 적용됩니다. 1번째 항목부터 0.1s씩 delay가 증가합니다. 

```html
<ul data-scroll="fadein_up" data-steps>
	<li data-step="fadein_up">Do</li>
	<li data-step="fadein_up">Re</li>
	<li data-step="fadein_up">Mi</li>
	<li data-step="fadein_up">Fa</li>
	<li data-step="fadein_up">Sol</li>
	<li data-step="fadein_up">La</li>
	<li data-step="fadein_up">Si</li>
</ul>
```
```css
[data-scroll="fadein_up"][data-steps] [data-step]{opacity:0; transform:translateY(-30px); transition:.3s;}
[data-scroll="fadein_up"][data-steps].on [data-step]{opacity:1; transform:translateY(0);}
```