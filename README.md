# Trabalho_2_PC2

```java
import javax.swing.JOptionPane;

public class Main {

    public static void main(String[] args) {
        double inss, irpf, salBruto, salLiquido;
        int numDependentes;
        String s;
        
        do {
            s = JOptionPane.showInputDialog("Digite o valor do salário bruto (digite 0 (zero) para parar):");
            salBruto = Double.parseDouble(s);
            
            if (salBruto > 0) {
                s = JOptionPane.showInputDialog("Digite o número de dependentes:");
                numDependentes = Integer.parseInt(s);
                
                inss = calcularINSS(salBruto);
                irpf = calcularIRPF(salBruto, numDependentes);
                salLiquido = salBruto - inss - irpf;
                
                JOptionPane.showMessageDialog(null, "Salário Bruto: R$" + salBruto
                        + "\nDesconto INSS: R$" + inss
                        + "\nDesconto IRPF: R$" + irpf
                        + "\nSalário Líquido: R$" + salLiquido);
            }
            
        } while (salBruto != 0);
        
    }
    
    public static double calcularINSS(double salBruto) {
        double inss;
        
        if (salBruto <= 1212) {
            inss = salBruto * 0.075;
        } else if (salBruto <= 2427.35) {
            inss = salBruto * 0.09;
        } else if (salBruto <= 3641.03) {
            inss = salBruto * 0.12;
        } else if (salBruto <= 7087.22) {
            inss = salBruto * 0.14;
        } else {
            inss = 992.22;
        }
        
        return inss;
    }
    
    public static double calcularIRPF(double salBruto, int numDependentes) {
        double baseCalculo, valorDeducao, valorDevido;
        
        baseCalculo = salBruto - calcularINSS(salBruto) - numDependentes * 189.59;
        
        if (baseCalculo <= 1903.98) {
            valorDevido = 0;
        } else if (baseCalculo <= 2826.65) {
            valorDeducao = 142.80;
            valorDevido = (baseCalculo * 0.075) - valorDeducao;
        } else if (baseCalculo <= 3751.05) {
            valorDeducao = 354.80;
            valorDevido = (baseCalculo * 0.15) - valorDeducao;
        } else if (baseCalculo <= 4664.68) {
            valorDeducao = 636.13;
            valorDevido = (baseCalculo * 0.225) - valorDeducao;
        } else {
            valorDeducao = 869.36;
            valorDevido = (baseCalculo * 0.275) - valorDeducao;
        }
        
        return valorDevido;
    }

}

```
