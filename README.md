# Proyectos
Breves proyectos de creación personal
```java

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package reto7pilaa;

/**
 *
 * @author Harol
 */
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class Reto7Pilaa extends JFrame {
    private JProgressBar trainingProgressBar;
    private JButton startButton;

    private int totalTime = 10000; // Tiempo total de entrenamiento en milisegundos
    private Timer trainingTimer;
    private int elapsedTime = 0;

    public Reto7Pilaa() {
        setTitle("|Politecnico Internacional | Dragon Ball  | Entrenamiento en la Sala del Espíritu y el Tiempo");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(300, 150);
        setLocationRelativeTo(null); // Centrar la ventana en la pantalla

        trainingProgressBar = new JProgressBar(0, totalTime);
        trainingProgressBar.setStringPainted(true);

        startButton = new JButton("Iniciar Entrenamiento");
        startButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                startTraining();
            }
        });

        JPanel panel = new JPanel(new BorderLayout());
        panel.add(trainingProgressBar, BorderLayout.CENTER);
        panel.add(startButton, BorderLayout.SOUTH);

        add(panel);
    }

    private void startTraining() {
        startButton.setEnabled(false);
        elapsedTime = 0;
        trainingProgressBar.setValue(0);

        trainingTimer = new Timer(100, new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                elapsedTime += 100;
                trainingProgressBar.setValue(elapsedTime);

                if (elapsedTime >= totalTime) {
                    trainingTimer.stop();
                    JOptionPane.showMessageDialog(Reto7Pilaa.this, "¡Entrenamiento completado!",
                            "Entrenamiento", JOptionPane.INFORMATION_MESSAGE);
                    startButton.setEnabled(true);
                }
            }
        });

        trainingTimer.start();
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            Reto7Pilaa frame = new Reto7Pilaa();
            frame.setVisible(true);
        });
    }
}
```
