## ASCII Total




```JavaScript
function uniTotal (string) {

  var acumulador = 0
  
for (let i = 0; i < string.length; i++){

  acumulador = acumulador + string.charCodeAt(i)
  
  }
  
  return acumulador
  
}

console.log(uniTotal("aaa"))
```
