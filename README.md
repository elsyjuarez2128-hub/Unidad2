/**
 *
 * @author Elsy Joselyn Godinez Juarez
 */
public class ListaDoble {
class Nodo {
    String dato;
    Nodo siguiente;
    Nodo anterior;

    public Nodo(String dato) {
        this.dato = dato;
        this.siguiente = null;
        this.anterior = null;
    }
}


    private Nodo cabeza; 

   
    public ListaDoble() {
        cabeza = null;
    }

    public void crearNodo(String dato) {
        Nodo nuevo = new Nodo(dato);

        if (cabeza == null) {
            cabeza = nuevo;
        } else {
            Nodo temp = cabeza;
            while (temp.siguiente != null) {
                temp = temp.siguiente;
            }
            temp.siguiente = nuevo;
            nuevo.anterior = temp;
        }

        System.out.println("Nodo creado: " + dato);
    }

    
    public void insertarDespuesDe(String referencia, String nuevoDato) {
        Nodo temp = cabeza;

        while (temp != null && !temp.dato.equals(referencia)) {
            temp = temp.siguiente;
        }

        if (temp != null) {
            Nodo nuevo = new Nodo(nuevoDato);
            nuevo.siguiente = temp.siguiente;
            nuevo.anterior = temp;

            if (temp.siguiente != null) {
                temp.siguiente.anterior = nuevo;
            }

            temp.siguiente = nuevo;

            System.out.println("Insertado " + nuevoDato + " después de " + referencia);
        } else {
            System.out.println("No se encontró el nodo con dato: " + referencia);
        }
    }
    public void recorrerAdelante() {
        Nodo temp = cabeza;
        System.out.println("\nRecorrido hacia adelante:");
        while (temp != null) {
            System.out.print("[" + temp.dato + "]");
            if (temp.siguiente != null) {
                System.out.print(" ↔ ");
            }
            temp = temp.siguiente;
        }
        System.out.println(" → NULL");
    }

    public void recorrerAtras() {
        if (cabeza == null) return;

        Nodo temp = cabeza;
        while (temp.siguiente != null) {
            temp = temp.siguiente;
        }

        System.out.println("\nRecorrido hacia atrás:");
        while (temp != null) {
            System.out.print("[" + temp.dato + "]");
            if (temp.anterior != null) {
                System.out.print(" ↔ ");
            }
            temp = temp.anterior;
        }
        System.out.println(" → NULL");
    }


    public static void main(String[] args) {

     ListaDoble lista = new ListaDoble();

        
        lista.crearNodo("Programación");
        lista.crearNodo("Mate");
        lista.crearNodo("Inglés");

        lista.recorrerAdelante();
        lista.insertarDespuesDe("Programación", "Base de Datos");
        lista.recorrerAdelante();
        lista.recorrerAtras();
    }
}
