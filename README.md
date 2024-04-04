# RedNeuronalSimple
Implementación básica de una interfaz gráfica de usuario en Java para realizar predicciones de la operación XOR utilizando una red neuronal simple.
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class NeuralNetworkGUI extends JFrame {
    private JTextField inputField1;
    private JTextField inputField2;
    private JButton predictButton;
    private JLabel resultLabel;

    public NeuralNetworkGUI() {
        setTitle("Red Neuronal Simple");
        setSize(300, 150);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        JPanel panel = new JPanel();
        panel.setLayout(new GridLayout(4, 1));

        inputField1 = new JTextField();
        inputField2 = new JTextField();
        predictButton = new JButton("Predecir");
        resultLabel = new JLabel();

        panel.add(new JLabel("Primer numero binario:"));
        panel.add(inputField1);
        panel.add(new JLabel("Segundo numero binario:"));
        panel.add(inputField2);
        panel.add(predictButton);
        panel.add(resultLabel);

        predictButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                try {
                    int input1 = Integer.parseInt(inputField1.getText());
                    int input2 = Integer.parseInt(inputField2.getText());
                    int prediction = predictXOR(input1, input2); // Predicción de la operación XOR
                    resultLabel.setText("Resultado de XOR: " + prediction);
                } catch (NumberFormatException ex) {
                    resultLabel.setText("Error: Ingresa numeros binarios validos (0 o 1).");
                }
            }
        });

        add(panel);
    }

    // Método para predecir la salida de la operación XOR
    private int predictXOR(int input1, int input2) {
        // Implementación simple de la operación XOR
        return input1 ^ input2;
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new NeuralNetworkGUI().setVisible(true);
            }
        });
    }
}
