# ejemplo3.1

package Vista;
import Import.*;
import java.awt.*;
import java.util.*;
import javax.swing.*;
import java.awt.event.*;

/**
 *
 * @author x
 */
public class Vision extends JFrame{
    private JTextField Modelo, Tipo, Peso, Marca;
    private JTextArea Reporte;
    private JButton Agregar, Modificar, Eliminar, Listar;
    private JList<String> ListaA;
    private DefaultListModel<String> modeloLista;
    private ArrayList<Automovil> Autos;
    private int indiceS = -1;
    
    public Vision(){
    setTitle("Gestion de estudiante");
    setSize(600,500);
    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    setLayout(new BorderLayout());
    
    Autos = new ArrayList<>();
    
    JPanel Panel1 = new JPanel(new GridLayout(5,2));
    Tipo= new JTextField();
    Modelo = new JTextField();
    Peso = new JTextField();
    Marca = new JTextField();
    
    Panel1.add(new JLabel("Modelo: ")); Panel1.add(Modelo);
    Panel1.add(new JLabel("Tipo: ")); Panel1.add(Tipo);
    Panel1.add(new JLabel("Peso: ")); Panel1.add(Peso);
    Panel1.add(new JLabel("Marca: ")); Panel1.add(Marca);
    
    add(Panel1,BorderLayout.NORTH);
    
    JPanel Panel2 = new JPanel();
    modeloLista = new DefaultListModel<>();
    ListaA = new JList<>(modeloLista);
    Reporte = new JTextArea(5,40);
    Reporte.setEditable(false);
    JScrollPane scrollReporte = new JScrollPane(Reporte);
    Panel2.add(new JLabel("Automoviles"));
    Panel2.add(ListaA);
    Panel2.setLayout(new BorderLayout());
Panel2.add(new JScrollPane(ListaA), BorderLayout.WEST);
Panel2.add(scrollReporte, BorderLayout.CENTER);
    add(Panel2,BorderLayout.CENTER);
    
    JPanel Panel3 = new JPanel();
    Agregar = new JButton("Agregar");
      Modificar = new JButton("Modificar");
      Eliminar = new JButton("Eliminar");
      Listar = new JButton("Listar");
      Panel3.add(Agregar);
          Panel3.add(Modificar);
              Panel3.add(Eliminar);
                  Panel3.add(Listar);
                  
                  add(Panel3,BorderLayout.SOUTH);
                  
                  Agregar.addActionListener(e -> agregar());
                  Modificar.addActionListener(e -> Modificar());
                  Eliminar.addActionListener(e -> Eliminar());
                  Listar.addActionListener(e -> Listar());
                  
                  ListaA.addListSelectionListener(e -> SeleccionarDesdeLista());
    }
    
    private void agregar(){
    Automovil A1 = new Automovil(
    Modelo.getText(),
            Tipo.getText(),
            Peso.getText(),
            Marca.getText()
    );
    
    
    Autos.add(A1);
    actualizarVista();

    Modelo.setText("");
    Tipo.setText("");
    Peso.setText("");
    Marca.setText("");
    }
                  
          
      
    
    private void Modificar(){
    if(indiceS >= 0){
    Automovil A1 = Autos.get(indiceS);
    A1.setModelo(Modelo.getText());
            A1.setTipo(Tipo.getText());
            A1.setPeso(Peso.getText());
            A1.setMarca(Marca.getText());
            
            
            
            actualizarVista();
    
    
    }
