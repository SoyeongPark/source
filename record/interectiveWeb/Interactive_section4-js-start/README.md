### <u>js selector</u>

```html
<script>
    const ilbuni = document.querySelector('.ilbuni');
    ilbuni.classList.add('newclassname');
    ilbuni.classList.remove('newclassname');
    ilbuni.classList.toggle('newclassname');
</script>
```


### <u>js event</u>
```html
<script>
    window.addEventListener('DOMContentLoaded',function(){
        const ilbuni = document.querySelector('.ilbuni.c');

        ...
    });
</script>
```


### <u>js event 위임</u>
```html
<script>
    const menu = document.querySelector('.menu');

    function clickHandler(event){
        event.target.dataset.value;
    }

    menu.addEventListner('click', clickHandler);
</script>
```