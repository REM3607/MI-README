# Persistent Bugger

function persistence(num) {

var contador = 0

var numeros = []

while (num >= 10) {

  numeros = num.toString().split('');
  
  num = 1
  
for (let i=0; i < numeros.length; i++) {

    num *= numeros[i] 
    
   // console.log(num)
   
}

contador++

}

return(contador)

}
