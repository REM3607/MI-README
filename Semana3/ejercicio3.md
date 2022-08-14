## Your order, please


function order(words) {
  let ordenado = [];
  let palabra = words.split(' ');
  for (let i = 0; i < palabra.length; i++) {
    let wordNumber = numpalabra(palabra[i]);
    ordenado[wordNumber] = palabra[i];
    
  }
  return limpiar(ordenado).join(' ');
}

function numpalabra(word) {
  for (let i = 0; i < word.length; i++) {
    if (!Number.isNaN(Number(word[i]))) return word[i];
  }
}

function limpiar(array) {
  let result = [];
  for (let i = 0; i < array.length; i++) {
    if (array[i] != undefined) result.push(array[i]);
  }
  return result;
}
