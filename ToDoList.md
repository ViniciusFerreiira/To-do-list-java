# To-do-list-java
import java.util.ArrayList;
import java.util.Scanner;

public class ToDoList {

    private static ArrayList<String> tarefas = new ArrayList<>();
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        boolean running = true;
        
        while (running) {
            System.out.println("\n--- ToDo List ---");
            System.out.println("1. Adicionar tarefa");
            System.out.println("2. Ver tarefas");
            System.out.println("3. Remover tarefa");
            System.out.println("4. Sair");
            System.out.print("Escolha uma opção: ");
            
            int escolha = scanner.nextInt();
            scanner.nextLine();
            
            switch (escolha) {
                case 1:
                    adicionarTarefa();
                    break;
                case 2:
                    verTarefas();
                    break;
                case 3:
                    removerTarefa();
                    break;
                case 4:
                    running = false;
                    System.out.println("Saindo...");
                    break;
                default:
                    System.out.println("Opção inválida.");
            }
        }
    }

    public static void adicionarTarefa() {
        System.out.print("Digite a nova tarefa: ");
        String tarefa = scanner.nextLine();
        tarefas.add(tarefa);
        System.out.println("Tarefa adicionada!");
    }

    public static void verTarefas() {
        if (tarefas.isEmpty()) {
            System.out.println("Nenhuma tarefa na lista.");
        } else {
            System.out.println("\nTarefas:");
            for (int i = 0; i < tarefas.size(); i++) {
                System.out.println((i + 1) + ". " + tarefas.get(i));
            }
        }
    }

    public static void removerTarefa() {
        verTarefas();
        if (!tarefas.isEmpty()) {
            System.out.print("\nDigite o número da tarefa que deseja remover: ");
            int numero = scanner.nextInt();
            scanner.nextLine(); // Limpa o buffer do scanner

            if (numero > 0 && numero <= tarefas.size()) {
                tarefas.remove(numero - 1);
                System.out.println("Tarefa removida!");
            } else {
                System.out.println("Número inválido.");
            }
        }
    }
}
