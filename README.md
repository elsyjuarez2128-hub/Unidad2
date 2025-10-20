/**
 *
 * @author Elsy Joselyn Godinez Juarez 
 */

class Nodo {
    String dato;
    Nodo sig; 

    public Nodo(String dato) {
        this.dato = dato;
        this.sig = null;
    }
}


public class ListaSimpleVisual {

    private Nodo inicio; 

    public ListaSimpleVisual() {
        inicio = null;
    }

    public void insertarFinal(String dato) {
        Nodo nuevo = new Nodo(dato);
        if (inicio == null) {
            inicio = nuevo;
        } else {
            Nodo aux = inicio;
            while (aux.sig != null) {
                aux = aux.sig;
            }
            aux.sig = nuevo;
        }
        System.out.println("Insertado: " + dato);
        mostrar();
    }


    public void insertarDespuesDe(String referencia, String nuevoDato) {
        Nodo nuevo = new Nodo(nuevoDato);
        Nodo aux = inicio;

        while (aux != null && !aux.dato.equals(referencia)) {
            aux = aux.sig;
        }

        if (aux != null) {
            nuevo.sig = aux.sig;
            aux.sig = nuevo;
            System.out.println("\nInsertado " + nuevoDato + " después de " + referencia);
            mostrar();
        } else {
            System.out.println("No se encontró el nodo con dato: " + referencia);
        }
    }

   
    public void eliminar(String dato) {
        if (inicio == null) {
            System.out.println("La lista está vacía.");
            return;
        }

        if (inicio.dato.equals(dato)) {
            inicio = inicio.sig;
            System.out.println("\nEliminado: " + dato);
            mostrar();
            return;
        }

      
        Nodo aux = inicio;
        while (aux.sig != null && !aux.sig.dato.equals(dato)) {
            aux = aux.sig;
        }

        if (aux.sig != null) {
            aux.sig = aux.sig.sig;
            System.out.println("\nEliminado: " + dato);
            mostrar();
        } else {
            System.out.println("No se encontró el nodo con dato: " + dato);
        }
    }

    public void mostrar() {
        System.out.println("\nEstado actual de la lista:");
        Nodo aux = inicio;
        while (aux != null) {
            System.out.print("[" + aux.dato + "]");
            if (aux.sig != null) {
                System.out.print(" → ");
            } else {
                System.out.print(" → NULL");
            }
            aux = aux.sig;
        }
        System.out.println("\n");
    }

    
    public static void main(String[] args) {

        ListaSimpleVisual lista = new ListaSimpleVisual();

  
        System.out.println("=== Creación de la lista ===");
        lista.insertarFinal("Ana");
        lista.insertarFinal("Benjamín");
        lista.insertarFinal("Carla");
        lista.insertarFinal("Diego");

        
        lista.insertarDespuesDe("Carla", "Elena");

       
        lista.eliminar("Benjamín");
    }
}
