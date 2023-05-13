import java.util.Scanner;
import java.io.IOException;

class Console {

    public static void clear(String... arg) throws IOException, InterruptedException {
        new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
    }
}

class ContaBancaria {
	
  static double saldo;  
  
  public static boolean validarSangria(double valor){    
    
    if(valor > saldo){
      return false;
    }
  
    return true;
  
  }
  
  public static void reforcoSaldo(double valor){
    saldo = saldo + valor;
  }
    
  public static void depositar() {
    
      Scanner teclado = new Scanner(System.in);   
      
      double valor;
      
      System.out.print("Qual o valor que voce deseja depositar?\n\n");
      
      valor = teclado.nextDouble();
      
      reforcoSaldo(valor);  

      menu(); 	  
      
  }
  
    public static void sangriaSaldo(double valor){
    saldo = saldo - valor;
    }

	public static double sacar() {
		 
	Scanner teclado = new Scanner(System.in);  
	  
    double valor;
	
	System.out.print("Qual o valor que voce deseja sacar?\n\n");
	
    valor = teclado.nextDouble();
	  
	  
      if(validarSangria(valor) == false){
        System.out.print("Saldo insuficiente\n\n");
        menu();
		
	reforcoSaldo(valor);  
		
		
      }
      
      saldo = saldo - valor;
        
    return saldo;
  } 
  
  public static double exibirSaldo() {
      
    System.out.print(saldo);
        
    return saldo;
  }
  
	public static void topo() throws IOException, InterruptedException{ 
	Scanner teclado = new Scanner(System.in);
	Console console = new Console();
	console.clear();
	
	System.out.println("_________________________________BANCO____________________________________\n\n");
	System.out.println("___________________________________DO_____________________________________\n\n");
	System.out.println("________________________________FENOMENO_________________________________\n\n");
	
	}
	
	public static void pressioneParaMenu() throws IOException,InterruptedException{
		System.out.print ("precione enter para voltar ao menu principal");
	System.in.read();
	
	}
	public static void menu() {
    Scanner teclado = new Scanner(System.in);
	
    int opcao;
	
   
    System.out.print("\n\n ola senhor. BEM VNDO ao banco do ronaldo fenomeno \n\n");
    System.out.print("------------------------\n\n");
    System.out.print("Por favor selecione uma opcao:\n");
    System.out.print("------------------------\n\n");
    System.out.print("[1] - Depositar\n");
	System.out.print("________________________\n\n");
    System.out.print("[2] - Sacar\n");
	System.out.print("________________________\n\n");
    System.out.print("[3] - Exibir saldo\n");
	System.out.print("________________________\n\n");
    System.out.print("[4] - Sair do sistema\n");
    System.out.print("________________________\n\n");
	
    opcao = teclado.nextInt();   

     System.out.print("agradecemos pela a preferencia o banco ronaldo fenomeno agradece! \n\n");    
    
    switch (opcao) {
      case 1:
      depositar();
      break;

      case 2:
      sacar();
      menu();
      break;

      case 3:
      exibirSaldo();
      menu();
      break;

      case 4:
      System.exit(0);
      break;

    default:
      System.out.printf("Insira uma opção válida");
      main(null);
    }
    
  }
  

	public static void main(String args[]){  

    saldo = 0;

    menu();    
       
    System.exit(0);
		
	}

}
