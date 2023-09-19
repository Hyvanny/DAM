package tema1;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.util.logging.Level;
import java.util.logging.Logger;
import javax.xml.parsers.DocumentBuilderFactory;
import javax.xml.parsers.ParserConfigurationException;
import javax.xml.transform.Transformer;
import javax.xml.transform.TransformerConfigurationException;
import javax.xml.transform.TransformerException;
import javax.xml.transform.TransformerFactory;
import javax.xml.transform.dom.DOMSource;
import javax.xml.transform.stream.StreamResult;
import org.w3c.dom.Document;
import org.w3c.dom.Element;
/**
 *
 * @author joange
 */
public class A4_CP_GenerarXML_DONE {
    
public static void main(String[] args) {
         String[] modulos = {"Acceso a Datos", "Programación de servicios y procesos",
                "Desarrollo de interfaces", "Programación multimedia y dispositivos móviles",
                "Sistemas de gestión empresarial", "Empresa e iniciativa emprendedora"};
            boolean[] permiteFCT = {false, true, false, false, true, true};
            int[] horas = {6, 3, 6, 5, 5, 3};
            double[] notas = {8.45, 9.0, 8.0, 7.34, 8.2, 7.4};
        
        try {
           
            
            Document document = DocumentBuilderFactory.newInstance()
                                       .newDocumentBuilder().newDocument();
            document.setXmlVersion("1.0");
            
            Element raiz = document.createElement("modulos");

            document.appendChild(raiz);
            
            for (int i = 0; i < notas.length; i++) {
                //creamos un elemento módulo y lo añadimos a la raíz
                Element modulo = document.createElement("modulo");
                raiz.appendChild(modulo);
		// añadimos los atributos, previa conversión a String
                modulo.setAttribute("horas", String.valueOf(horas[i]));
                modulo.setAttribute("permiteFct", String.valueOf(permiteFCT[i]));
                
                //añadimos el nombre del módulo
                Element nombre = document.createElement("nombre"); 
                nombre.appendChild(document.createTextNode(modulos[i]));
                modulo.appendChild(nombre);
                
                 //añadimos la nota del módulo
                Element nota = document.createElement("nota"); 
                nota.appendChild(document.createTextNode(String.valueOf(notas[i])));
                modulo.appendChild(nota);
            }

            // Preparamos el transformer para la conversión
            Transformer trans = TransformerFactory.newInstance().newTransformer();
            
            // Origen: el DOM del documento creado
            DOMSource source = new DOMSource(document);	
            
            //Destino: un fichero XML
            StreamResult result = new StreamResult(
                                 new FileOutputStream("misModulos.xml"));
           //Conversión !!
            trans.transform(source, result);

        } catch (ParserConfigurationException ex) {
            System.out.println(ex.getMessage());
        } catch (FileNotFoundException ex) {
            System.out.println(ex.getMessage());
        } catch (TransformerConfigurationException ex) {
            System.out.println(ex.getMessage());
        } catch (TransformerException ex) {
            System.out.println(ex.getMessage());
        }
}
}
