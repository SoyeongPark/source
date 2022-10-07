### <u>생성자함수</u>

```html
<script>
    function Card(num, color){
        this.num = num;
        this.color = color;
        this.init();
    }

    Card.prototype = {
        constructor: Card,
        init: function(){
            const mainElem = document.createElement('div');
            mainElem.style.color = this.color;
            mainElem.innerHTML = this.num;
            mainElem.classList.add('card');
            document.body.appendChild(mainElem);
        }
    };

    const card1 = new Card(1,'green');
    const card2 = new Card(7,'blue');
</script>
```