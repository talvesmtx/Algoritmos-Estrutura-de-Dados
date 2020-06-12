# Algoritmos-Estrutura-de-Dados
import javax.swing.JOptionPane;

public class Exerc {

	public static void main(String[] args) {
		char vetor[] = new char[10];

		digitarChar(vetor);
		mergeSort(vetor);
		char chave = buscarChar();
		int indice = BuscaBináriaRecursiva(vetor, 0, vetor.length-1, chave);
		mostrarChar(vetor);
		Resposta(indice);
	}
	
	public static void digitarChar(char vetor[]) {
		System.out.println("Vetor digitado: ");
		for(int i = 0; i < vetor.length; i++) {
			String x = JOptionPane.showInputDialog("Digite um caracter: ");
			vetor[i] = x.charAt(x.length()-1);
			System.out.print(vetor[i] + " ");
		}
	}
	
	public static void mergeSort(char vetor[]) {  
        if(vetor.length > 1) {
        	
        	int t1 = vetor.length/2;  
            int t2 = vetor.length-t1;  
            char v1[] = new char[t1];  
            char v2[] = new char[t2];  
              
            for(int i = 0; i < t1; i++) {
                v1[i] = vetor[i];
            }
            
            for(int i = t1; i < (t1+t2); i++) {
                v2[i-t1] = vetor[i];  
            }
            
            mergeSort(v1);
            mergeSort(v2);
            merge(vetor, v1, v2);
        }
    }
    
    public static void merge(char w[], char w1[], char w2[]) {
    	int	i = 0, j = 0, k = 0;  
    	
    	while(w1.length != j && w2.length != k) {
        	if(w1[j] <= w2[k]) {
        		w[i] = w1[j];
                i++;  
                j++;  
            }
        	
            else {
            	w[i] = w2[k];
                i++;  
                k++;  
            }  
        }
    	
        while(w1.length != j) {
        	w[i] = w1[j];  
            i++;  
            j++;  
        }
        
        while(w2.length != k) {  
        	w[i] = w2[k];  
            i++;  
            k++;  
        }  
    }
	
	public static char buscarChar() {
		String busca = JOptionPane.showInputDialog("Digite o caracter que queira buscar no índice: ");
		return busca.charAt(busca.length()-1);
	}

	public static int BuscaBináriaRecursiva(char vetor[], int baixo, int alto, char chave) {

		if(baixo <= alto)	{
			int meio = (baixo + alto)/2;
			if(chave < vetor[meio])
				return	BuscaBináriaRecursiva(vetor, baixo, meio-1, chave);
			else
				if(chave > vetor[meio])
					return	BuscaBináriaRecursiva(vetor, meio+1, alto, chave);
					else
						return meio;
		}
		else
			return  -1;
	}
	
	public static void mostrarChar(char vetor[]) {
		System.out.println("\n\nVetor ordenado: ");
		for( int i = 0; i < vetor.length; i++) {
			System.out.print(vetor[i] + " ");
		}
	}

	public static void Resposta(int i) {
		if(i < 0) {
			System.out.println("\n\nCaracter não encontrado no índice");
		}
		else
			System.out.println("\n\nCaracter está no índice " + i);
	}
}





































