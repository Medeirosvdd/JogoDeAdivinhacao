## Trabalho Final. 
 <img align="center" alt="Java" src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white"/>
 
### Resumo do Trabalho Final.

O projeto consiste no desenvolvimento de um jogo simples em Java, onde o objetivo é adivinhar um número aleatório gerado pelo programa.  
 O número é escolhido aleatoriamente dentro do intervalo de 1 a 10. O jogador deve tentar adivinhar o número, e o jogo fornecerá dicas baseadas nas tentativas feitas.Se o jogador chutar um número menor que o correto, o jogo dirá "maior". Se o jogador chutar um número maior, o jogo dirá "menor".  
 O jogo continuará até que o jogador adivinhe corretamente o número ou decida encerrar o jogo.

### Funcionalidades principais:

Geração de um número aleatório entre 1 e 10.  
Interface de entrada para o jogador fazer suas tentativas.
Fornecimento de dicas após cada tentativa (indicando se o número correto é maior ou menor que a tentativa).  
Loop que mantém o jogo ativo até o jogador adivinhar o número ou encerrar o jogo.

### Tecnologias utilizadas:

Linguagem de programação Java.<br>  
Bibliotecas padrão do Java para entrada e saída de dados.  
Esse projeto demonstra o uso de conceitos básicos de programação em Java, como controle de fluxo, loops, e manipulação de entrada e saída, além de lógica de comparação.

##
## Explicação do Codigo usado no progama.

### Primeiro Jframe (Tela de Menu)
![alt text](image.png)

```java
 private void jButton2ActionPerformed(java.awt.event.ActionEvent evt) {                                         

        new Jogo().setVisible(true);


    }                                      
```


° "jButton2ActionPerformed" = Botão jogar.  
° new Jogo(): Cria uma nova instância da classe Jogo.  
° .setVisible(true): Torna a nova janela (instância de Jogo) visível.
  
  Neste caso a janela é a tela do jogo.

### Segundo Jframe (Inserção de Nome)

![alt text](image-2.png)
```java
 public Jogo() {
        initComponents();
        setLocationRelativeTo(null);

        str = JOptionPane.showInputDialog(null, "Qual seu nome? ");
        Integer name = Integer.getInteger(str);
        if (str.getBytes().equals("Cancelar")) {
         
        } else {
     }
}
```

° O construtor Jogo() é responsável por iniciar uma nova instância da classe Jogo, que é uma janela de interface gráfica em Java. Aqui está o que ele realiza: 
° "initComponents();": Este método inicializa os componentes visuais da interface gráfica do jogo.  
° "setLocationRelativeTo(null);": Define a posição da janela do jogo como centralizada na tela do dispositivo.  
° Solicitação de Nome: Utiliza JOptionPane.showInputDialog(null, "Qual seu nome? ") para exibir um diálogo de entrada onde o usuário pode digitar seu nome. O nome inserido pelo usuário é armazenado na variável str. 


##


### Segundo Jframe (Tela do Jogo)

![alt text](image-3.png)

```java
public class Jogo extends javax.swing.JFrame {

    Random random = new Random();
    int numeroSecreto = random.nextInt(10) + 1;
    int tentativas = 0;
    int tent = 0;
    int acertos = 0;

    String str;
    ...
```

° Instância de Random: Uma instância da classe Random é criada para gerar números aleatórios.  

° Número Secreto: Um número aleatório entre 1 e 10 é gerado e armazenado na variável numeroSecreto. Este número será o alvo que o jogador tentará adivinhar.  

° Contadores: Três variáveis inteiras (tentativas, tent, acertos) são inicializadas para manter o controle do número de tentativas atuais, tentativas totais e acertos do jogador, respectivamente.  

° Nome do Jogador: Uma variável de string (str) é declarada para armazenar o nome do jogador, que será solicitado quando o jogo começar.  

#

### Segundo Jframe (Verificação dos Números)


```java
  private void botaoEnviarActionPerformed(java.awt.event.ActionEvent evt) {                                            
        // TODO add your handling code here:

        String input = NumberUsuario.getText();
        int numero = Integer.parseInt(input);
        tentativas++;
        tent++;

        TxtTent.setText("" + acertos);
        TxtJoga.setText("" + tentativas);

        if (numero == numeroSecreto) {

            Random random = new Random();
            numeroSecreto = random.nextInt(10) + 1;
            acertos++;

            JOptionPane.showMessageDialog(this, "Parabéns " + str + "!!!" + "\n" + " Você adivinhou o número em " + tentativas + " tentativas."
                    + "\n" + "\n" + "Tentativas Totais: " + tent + "\n" + "Acertos Totais: " + acertos);
            tentativas = 0;
            

        } else if (numero >= numeroSecreto) {
            JOptionPane.showMessageDialog(this, "O numero secreto é menor que: " + "``" + numero+ "´´");
        } else if (numero <= numeroSecreto) {
            JOptionPane.showMessageDialog(this, "O numero secreto é maior que " + "``" + numero+ "´´");
        }

    }

```
O método botaoEnviarActionPerformed é responsável por lidar com a ação de enviar um número digitado pelo usuário durante o jogo.  

° Obtenção do Número Digitado: O método obtém o texto digitado pelo usuário no campo NumberUsuario e converte esse texto em um número inteiro utilizando Integer.parseInt(input).  

° Contadores Incrementados: As variáveis tentativas e tent são incrementadas para contar o número de tentativas atuais e totais, respectivamente.  

° Atualização da Interface Gráfica: Os valores de acertos (que deveria ser tentativas) e tentativas são exibidos nos campos de texto TxtTent e TxtJoga, respectivamente.  

° Mensagens de Feedback: Se o número digitado for maior ou menor que o numeroSecreto, uma mensagem informando isso é exibida ao usuário, utilizando JOptionPane.showMessageDialog.

° Lógica de Verificação do Número: Se o número digitado pelo usuário for igual ao numeroSecreto:  
- Um novo número secreto é gerado aleatoriamente.  
- O contador de acertos (acertos) é incrementado.  
- Uma caixa de mensagem é exibida parabenizando o jogador, mostrando o nome (str) e   quantas tentativas foram necessárias para acertar, além de mostrar o total de tentativas e acertos. 

   ![alt text](image-1.png)

- O contador de tentativas (tentativas) é resetado para zero.  



##

### Segundo Jframe (Opções de Volta para o Primeiro Jframe)

![alt text](image-4.png)

```java
private void botaoVoltarActionPerformed(java.awt.event.ActionEvent evt) {                                            
        // TODO add your handling code here:

        Object[] opcoes = {"Sim", "Não",};
        int escolha = JOptionPane.showOptionDialog(null, "Você Teve " + acertos + " acertos e " + tent + " Erros " + "\n" + "Deseja mesmo voltar?",
                "Deseja mesmo voltar?", JOptionPane.DEFAULT_OPTION,
                JOptionPane.INFORMATION_MESSAGE, null, opcoes, opcoes[0]);
        if (escolha == 0) {
            dispose();

        } else {

        }
   }

```
O método botaoVoltarActionPerformed trata a ação de voltar na interface do jogo:

° Diálogo de Confirmação: Exibe um diálogo usando JOptionPane.showOptionDialog para confirmar se o jogador deseja realmente voltar.

- O diálogo mostra a quantidade de acertos (acertos) e erros (tent) que o jogador teve.

- Oferece duas opções: "Sim" e "Não".

° Ação com Base na Escolha: Dependendo da escolha do jogador:  

- Se escolher "Sim" (índice 0), fecha a janela atual usando dispose(), encerrando o jogo ou voltando à tela anterior, dependendo da implementação.

- Se escolher "Não" (índice 1), a ação é ignorada e a janela permanece aberta.
