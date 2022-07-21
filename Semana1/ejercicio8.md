# CODIGO INCORRECTO
var cond = false;

if ((cond = true)) {
  console.log('The cond variable is true');
} else {
  console.log('The cond variable is false');
}

# EXLICACION
El codigo es incorrecto porque en if cond = true esta asignango el valor true a cond y no haciendo una comparación

# CODIGO CORRECTO
var cond = false;

if (cond == true) {
  console.log('The cond variable is true');
} else {
  console.log('The cond variable is false');
}
