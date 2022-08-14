## Bit Counting


var countBits = function (n) {

  let binario = n.toString(2);
  
  let ContadorBi = 0;
  
  for (let i = 0; i < binario.length; i++) {
  
    if (binario[i] === '1') ContadorBi++;
    
  }
  
  return ContadorBi++;
  
};
