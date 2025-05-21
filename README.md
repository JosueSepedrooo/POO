import javax.swing.*;

public class IMCApp {
    public static void main(String[] args) {
        // Criando a janela
        JFrame tela = new JFrame("Calculadora de IMC");
        tela.setSize(300, 250);
        tela.setLayout(null);
        tela.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        // Campos e rótulos
        JLabel rotuloPeso = new JLabel("Peso (Kg):");
        rotuloPeso.setBounds(20, 20, 100, 25);
        JTextField campoPeso = new JTextField();
        campoPeso.setBounds(120, 20, 100, 25);

        JLabel rotuloAltura = new JLabel("Altura (cm):");
        rotuloAltura.setBounds(20, 60, 100, 25);
        JTextField campoAltura = new JTextField();
        campoAltura.setBounds(120, 60, 100, 25);

        JButton botaoCalcular = new JButton("Calcular");
        botaoCalcular.setBounds(90, 100, 100, 30);

        JLabel resultado = new JLabel("");
        resultado.setBounds(20, 150, 250, 25);

        // Adicionando os itens na tela
        tela.add(rotuloPeso);
        tela.add(campoPeso);
        tela.add(rotuloAltura);
        tela.add(campoAltura);
        tela.add(botaoCalcular);
        tela.add(resultado);

        // Ação do botão
        botaoCalcular.addActionListener(e -> {
            try {
                double peso = Double.parseDouble(campoPeso.getText());
                double altura = Double.parseDouble(campoAltura.getText()) / 100;

                double imc = peso / (altura * altura);
                String mensagem = "";

                if (imc < 18.5) {
                    mensagem = "Abaixo do peso";
                } else if (imc < 25) {
                    mensagem = "Peso normal";
                } else if (imc < 30) {
                    mensagem = "Sobrepeso";
                } else if (imc < 35) {
                    mensagem = "Obesidade grau I";
                } else if (imc < 40) {
                    mensagem = "Obesidade grau II";
                } else {
                    mensagem = "Obesidade grau III";
                }

                resultado.setText("IMC: " + String.format("%.2f", imc) + " - " + mensagem);

            } catch (Exception erro) {
                resultado.setText("Digite números válidos!");
            }
        });

        // Mostrar a tela
        tela.setVisible(true);
    }
}
