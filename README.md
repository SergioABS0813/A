# a

## main

        import java.util.ArrayList;
        import java.util.Scanner;
        
        public class Main {
            public static void main(String[] args) {
        
                Scanner scanner = new Scanner(System.in); //el usuario va a interactuar con teclado
                ArrayList<Equipo> listaEquipos = new ArrayList<>(); //creamos la lista dinámica de equipos
                ArrayList<Tecnico> listaTecnicos = new ArrayList<>(); //Creamos un array list de tecnicos
                AppController appController = new AppController(); //creamos el objeto de appController
        
                buclePrincipal:
                while (true){
                    System.out.println("+++++++++++++++++++++++++++++++++++++");
                    System.out.println("|             Menú                  |");
                    System.out.println("|   1 <- Registrar Nuevo Equipo     |");
                    System.out.println("|   2 <- Registrar Nuevo Técnico    |");
                    System.out.println("|   3 <- Listar  Equipos            |");
                    System.out.println("|   4 <- Listar técnicos x salario  |");
                    System.out.println("|   5 <- Buscar técnicos x DNI      |");
                    System.out.println("|   9 <- Salir                      |");
                    System.out.println("+++++++++++++++++++++++++++++++++++++");
        
                    System.out.print("Ingrese una opción: ");
                    String opcionSeleccionada = scanner.nextLine();
        
                    //convertimos la opcionSeleccionada a Integer
                    int opcionInt = Integer.parseInt(opcionSeleccionada);
        
                    switch (opcionInt){
        
                        case 1:
                            System.out.println("Registrar Nuevo Equipo");
                            System.out.println("----------------------------------------");
                            appController.registrarNuevoEquipo(listaEquipos); //le mandamos la lista de Equipos
                            break;
                        case 2:
                            System.out.println("Registrar Nuevo Técnico");
                            System.out.println("----------------------------------------");
                            appController.registrarNuevoTecnico(listaTecnicos);
                            break;
                        case 3:
                            System.out.println("Listar Equipos");
                            System.out.println("----------------------------------------");
                            appController.listarEquipos(listaEquipos);
                            break;
                        case 4:
                            System.out.println("Listar Técnicos x Salario");
                            System.out.println("----------------------------------------");
                            appController.listarTecnicosXSalario(listaTecnicos);
                            break;
                        case 5:
                            System.out.println("Bucar técnico x DNI");
                            System.out.println("----------------------------------------");
                            appController.buscarTecnicoxDni(listaTecnicos);
                            break;
                        case 9:
                            System.out.println("---Cerrando Programa---");
                            break buclePrincipal;
                        default:
                            System.out.println("Error al ingresar la opción, por favor vuelva a ingresar de nuevo una");
                            break;
                    }
        
        
        
        
        
        
        
        
        
                }
        
        
        
            }
        }



## AppController
        import java.util.ArrayList;
        import java.util.Scanner;
        import java.util.HashSet;
        
        public class AppController {
        
        
            HashSet<String> listaNumeroSeries = new HashSet<>(); //Creo el HashSet de numero de series
            HashSet<String> listaDniTecnicos = new HashSet<>(); //Creo el HashSet de listaDNI
        
            public void registrarNuevoEquipo(ArrayList<Equipo> listaEquipos){ //lista de equipos
                Equipo equipo = new Equipo();
                Scanner scanner = new Scanner(System.in); //indica interaccion con el teclado de parte del usuario
        
                System.out.print("Marca: ");
                String marca = scanner.nextLine();
                System.out.print("Tipo: ");
                String tipo = scanner.nextLine();
                System.out.print("Cantidad de puertos");
                String cantidadDePuertosstr = scanner.nextLine();
                int cantidadDePuertos = Integer.parseInt(cantidadDePuertosstr);
                System.out.print("Costo: ");
                String costo = scanner.nextLine();
                Float costoRouter = Float.parseFloat(costo);
                System.out.print("Numero de serie: ");
                String numeroSerie = scanner.nextLine();
        
        
                if (listaNumeroSeries.contains(numeroSerie)){
                    System.out.println("Error, ya existe el número de serie");
                }
                else{
                    listaNumeroSeries.add(numeroSerie); //añadimos al hashset el numero de serie
                    equipo.setMarca(marca);
                    equipo.setTipo(tipo);
                    equipo.setCantidadDePuertos(cantidadDePuertos);
                    equipo.setCosto(costoRouter);
                    equipo.setNumeroDeSerie(numeroSerie);
                    listaEquipos.add(equipo); //Se añade a la lista de equipos que creamos
                }
        
            }
        
            public void registrarNuevoTecnico(ArrayList<Tecnico> listaTecnicos){
        
                Tecnico tecnico = new Tecnico(); //Creamos objeto
        
                Scanner scanner = new Scanner(System.in);
                System.out.print("Nombre: ");
                String nombreTecnico = scanner.nextLine();
                System.out.print("Apellidos: ");
                String ApellidosTecnico = scanner.nextLine();
                System.out.print("DNI: ");
                String dniTecnico = scanner.nextLine();
                System.out.print("Edad: ");
                String edadTecnico = scanner.nextLine();
                System.out.print("Teléfono: ");
                String telefonoTecnicoStr = scanner.nextLine();
                //Convertimos a Integer
                int telefonoTecnico = Integer.parseInt(telefonoTecnicoStr);
                System.out.print("Salario: ");
                String salarioTecnicoStr = scanner.nextLine();
                //Cambiamos a Floar
                float salarioTecnico = Float.parseFloat(salarioTecnicoStr);
                System.out.print("Cargo: ");
                String cargoTecnico = scanner.nextLine();
        
                if (listaDniTecnicos.contains(dniTecnico)){
                    System.out.println("Error, ya existe el dni");
                }
                else{
                    //Tenemos que guardar el DNI del tecnico en la lista de DNIs hashset
                    listaDniTecnicos.add(dniTecnico);
                    tecnico.setNombre(nombreTecnico);
                    tecnico.setApellido(ApellidosTecnico);
                    tecnico.setDni(dniTecnico);
                    tecnico.setEdad(edadTecnico);
                    tecnico.setTelefono(telefonoTecnico);
                    tecnico.setSalario(salarioTecnico);
                    tecnico.setCargo(cargoTecnico);
                    //Guardamos el tecnico en la listaTecnicos
                    listaTecnicos.add(tecnico);
        
                }
        
            }
        
            public void listarEquipos(ArrayList<Equipo> listaEquipos){
                for (Equipo equipo: listaEquipos){ //Usamos For Each Loop
                    System.out.println("nombre: " + equipo.getMarca());
                    System.out.println("tipo: " + equipo.getTipo());
                    System.out.println("cantidad de puertos: " + equipo.getCantidadDePuertos());
                    System.out.println("numero de serie: " + equipo.getNumeroDeSerie());
                    System.out.println("costo: " + equipo.getCosto());
                }
        
            }
        
            public void listarTecnicosXSalario(ArrayList<Tecnico> listaTecnicos){
                Scanner scanner = new Scanner(System.in);
                System.out.print("Ingresa el salario: ");
                String salarioStr = scanner.nextLine();
        
                //Convertir a Float
                Float salarioF = Float.parseFloat(salarioStr);
        
                for (Tecnico tecnico: listaTecnicos){
        
                    if (tecnico.getSalario() > salarioF){
                        System.out.println("nombre: " + tecnico.getNombre());
                        System.out.println("apellidos: " + tecnico.getApellido());
                        System.out.println("dni: " + tecnico.getDni());
                        System.out.println("edad: " + tecnico.getEdad());
                        System.out.println("teléfono: " + tecnico.getTelefono());
                        System.out.println("salario: " + tecnico.getSalario());
                        System.out.println("cargo: " + tecnico.getCargo());
                    }
        
                }
        
            }
        
            public void buscarTecnicoxDni(ArrayList<Tecnico> listaTecnicos){
        
                Scanner scanner = new Scanner(System.in);
                System.out.print("Ingrese el DNI que quiere ingresar: ");
                String dniEscogido = scanner.nextLine();
        
                for (Tecnico tecnico: listaTecnicos){
        
                    if (tecnico.getDni().equals(dniEscogido)){
                        System.out.println("nombre: " + tecnico.getNombre());
                        System.out.println("apellidos: " + tecnico.getApellido());
                        System.out.println("dni: " + tecnico.getDni());
                        System.out.println("edad: " + tecnico.getEdad());
                        System.out.println("teléfono: " + tecnico.getTelefono());
                        System.out.println("salario: " + tecnico.getSalario());
                        System.out.println("cargo: " + tecnico.getCargo());
                    }
        
                }
        
            }
        
        
        }


## EQUIPO
        public class Equipo {
        
            private String marca;
            private String tipo;
            private int cantidadDePuertos;
            private String numeroDeSerie;
            private Float costo;
        
            public String getMarca() {
                return marca;
            }
        
            public void setMarca(String marca) {
                this.marca = marca;
            }
        
            public String getTipo() {
                return tipo;
            }
        
            public void setTipo(String tipo) {
                this.tipo = tipo;
            }
        
            public int getCantidadDePuertos() {
                return cantidadDePuertos;
            }
        
            public void setCantidadDePuertos(int cantidadDePuertos) {
                this.cantidadDePuertos = cantidadDePuertos;
            }
        
            public String getNumeroDeSerie() {
                return numeroDeSerie;
            }
        
            public void setNumeroDeSerie(String numeroDeSerie) {
                this.numeroDeSerie = numeroDeSerie;
            }
        
            public Float getCosto() {
                return costo;
            }
        
            public void setCosto(Float costo) {
                this.costo = costo;
            }
        }


## Tecnico

        public class Tecnico {
        
            private String nombre;
            private String apellido;
            private String dni;
            private String edad;
            private int telefono;
            private Float salario;
            private String cargo;
        
            public String getNombre() {
                return nombre;
            }
        
            public void setNombre(String nombre) {
                this.nombre = nombre;
            }
        
            public String getApellido() {
                return apellido;
            }
        
            public void setApellido(String apellido) {
                this.apellido = apellido;
            }
        
            public String getDni() {
                return dni;
            }
        
            public void setDni(String dni) {
                this.dni = dni;
            }
        
            public String getEdad() {
                return edad;
            }
        
            public void setEdad(String edad) {
                this.edad = edad;
            }
        
            public int getTelefono() {
                return telefono;
            }
        
            public void setTelefono(int telefono) {
                this.telefono = telefono;
            }
        
            public Float getSalario() {
                return salario;
            }
        
            public void setSalario(Float salario) {
                this.salario = salario;
            }
        
            public String getCargo() {
                return cargo;
            }
        
            public void setCargo(String cargo) {
                this.cargo = cargo;
            }
        }



