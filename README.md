/**
 *
 * @author Elsy Joselyn Godinez Juarez 
 */
public class ListaCircular {
    
class Nodo {
    String dato;
    Nodo sig; 

    public Nodo(String dato) {
        this.dato = dato;
        this.sig = null;
    }
}

    private Nodo cabeza; 

   
    public ListaCircular() {
        cabeza = null;
    }
    public void crearListaInicial() {
        Nodo rojo = new Nodo("Rojo");
        Nodo verde = new Nodo("Verde");
        Nodo azul = new Nodo("Azul");
        Nodo amarillo = new Nodo("Amarillo");

        rojo.sig = verde;
        verde.sig = azul;
        azul.sig = amarillo;
        amarillo.sig = rojo; 

        cabeza = rojo;
        System.out.println("Lista circular creada correctamente.");
    }
    public void recorrerUnaVuelta() {
        if (cabeza == null) return;

        Nodo aux = cabeza;
        System.out.println("\nRecorrido circular (1 vuelta):");
        do {
            System.out.print("[" + aux.dato + "] → ");
            aux = aux.sig;
        } while (aux != cabeza);
        System.out.println("(vuelve al inicio)");
    }

 
    public void insertarMorado() {
        if (cabeza == null) return;

        Nodo aux = cabeza;
        while (!aux.dato.equals("Azul")) {
            aux = aux.sig;
        }

        Nodo nuevo = new Nodo("Morado");
        nuevo.sig = aux.sig; 
        aux.sig = nuevo;     

        System.out.println("\nInsertado 'Morado' entre Azul y Amarillo.");
    }
    public void eliminar(String dato) {
        if (cabeza == null) return;

        Nodo aux = cabeza;
        Nodo anterior = null;

        do {
            if (aux.dato.equals(dato)) {
                if (anterior != null) {
                    anterior.sig = aux.sig;
                } else { // si es el primero
                    Nodo temp = cabeza;
                    while (temp.sig != cabeza) {
                        temp = temp.sig;
                    }
                    cabeza = aux.sig;
                    temp.sig = cabeza;
                }
                System.out.println("\nEliminado nodo: " + dato);
                return;
            }
            anterior = aux;
            aux = aux.sig;
        } while (aux != cabeza);

        System.out.println("\nNo se encontró el nodo: " + dato);
    }

    
    public static void main(String[] args) {

        ListaCircular lista = new ListaCircular();

      
        lista.crearListaInicial();
        lista.recorrerUnaVuelta();
        lista.insertarMorado();
        lista.recorrerUnaVuelta();
        
        lista.eliminar("Verde");
        lista.recorrerUnaVuelta();
    }
}


