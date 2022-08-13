
function remove(string) { 
var long = string.length

for(let i = 0; i < long; i++) {
  var long2 = string.length
  if (string.slice(long2-1, long) == "!"){
  string = string.slice(0,-1)
  }
}
  return(string)  
}
