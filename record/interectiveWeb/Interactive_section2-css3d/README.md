### <u>회전하는 카드 만들기</u>

```html
<style>
    .word{
        perspective: 500px;
    }
    .card{
        transform-style: preserve-3d;
    }
    .card-side{
        -webkit-backface-visibility: hidden;
        backface-visibility: hidden;
    }
</style>

<div class="word">
    <div class="card">
        <div class="card-side card-front">Front</div>
        <div class="card-side card-back">Back</div>
    </div>
</div>
```