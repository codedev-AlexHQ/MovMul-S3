# MovMul-S3
# E1:
class Usuario {
  String nombre;
  String email;
  String password;
  Usuario(this.nombre, this.email, this.password);
}

mixin Autenticacion {
  void iniciarSesion(String email, String password) {
    print("Iniciando sesión con: $email");
  }
}

class UsuarioAutenticado extends Usuario with Autenticacion {
  UsuarioAutenticado(String nombre, String email, String password) 
    :super(nombre, email, password);
}

void main() {
  var usuario = UsuarioAutenticado('Alex', 'alex@gmail.com', 'clave123');
  usuario.iniciarSesion('alex@gmail.com', 'clave123');
}

# E2:
class Votante {
  String nombre;
  int edad;
  bool haVotado;
  Votante(this.nombre, this.edad, this.haVotado);
}

mixin ValidacionVoto {
  void validarVoto(int edad) {
    if (edad >= 18) {
      print('El votante es elegible para votar');
    } else {
      print('El votante NO es elegible para votar (menor de edad)');
    }
  }
}

class VotanteValido extends Votante with ValidacionVoto {
  VotanteValido(String nombre, int edad, bool haVotado) 
    : super(nombre, edad, haVotado);
}

void main() {
  var votante1 = VotanteValido('Carlos', 25, false);
  votante1.validarVoto(votante1.edad);

  var votante2 = VotanteValido('María', 16, false);
  votante2.validarVoto(votante2.edad);
}
