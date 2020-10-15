[You might not need jQuery](http://youmightnotneedjquery.com/)  
[제이쿼리는 필요 없을 수도 있다?
](https://www.zerocho.com/category/jQuery/post/57b356d4d841141500b31e1e)


#### Selector
```
single: $('.test') => document.querySelector('.test')
multi: $('.tests') => document.querySelectorAll('.tests') 
```

#### Class
```
$(el).addClass('test') => el.classList.add('test')
$(el).removeClass('test') => el.classList.remove('test')
$(el).toggleClass('test') => el.classList.toggle('test')
$(el).hasClass('test') => el.classList.contains('test')
```
