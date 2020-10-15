[You might not need jQuery](http://youmightnotneedjquery.com/)  
[제이쿼리는 필요 없을 수도 있다?
](https://www.zerocho.com/category/jQuery/post/57b356d4d841141500b31e1e)


#### Selector
```
single: $('.string') => document.querySelector('.string')
multi: $('.string') => document.querySelectorAll('.string') // nodeList 반환 
```

#### Style
```
get: $(el).css('color') => getComputedStyle(el)['color'];
set: $(el).css('color', 'red') => el.style.color = 'red'
$(el).hide() => el.style.display = 'none'
$(el).show() => el.style.display = '/block/flex'
```

#### Attributes
```
get: $(el).attr('string') => el.getAttribute('string')
set: $(el).attr('string', 123) => el.getAttribute('string', 123) 
remove: $(el).removeAttr('string') => el.removeAttribute('string')
```

#### Class
```
$(el).addClass('string') => el.classList.add('string')
$(el).removeClass('string') => el.classList.remove('string')
$(el).toggleClass('string') => el.classList.toggle('string')
$(el).hasClass('string') => el.classList.contains('string')
```

#### Position
```
$(el).position().top => el.offsetTop
```

#### Text
```
get: $(el).text() => el.textContent
set: $(el).text('string') => el.textContent = 'string'
```
