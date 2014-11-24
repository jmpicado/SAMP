
DOC
 Clase Principal Demo1 
 	* 1 Vista (Demo1View(JComponent))
 	* 2.1 JSplitPane con una Paleta (SAMMSPaletteActionsList wrapeado en un JScrollPane. A) y 2.2 Tree (SAMMSPalette que no vamos a usar de momento) 
 	* Listeners:
 		-- Cuando se cierra la ventana
 	* Acciones 
 		-- InsertSimpleNodeAction	

1. Vista (Demo1View extends SAMMSView)
	 * Documento (SAMMSDocument)
	 	* Layers (SAMMSLayer)
	 * Canvas (SAMMSViewCanvas)
	 	El principal metodo es el paint() q repinta cada vez
	 	El principal Listener es el onMouseDragged() q recalcucla la posicion
	 *init() -- Se le da el aspecto a la vista	

2. Palette

 Añadir acciones a la Palette
  Se crea una JList..
     myList = new SAMMSPaletteActionsList();
     AppAction[] insertitems =
          {
            InsertSimpleNodeAction
          };
    myList.setListData(insertitems);
  Se crea una JScrollPane con esa lista
    myListScrollPane = new JScrollPane(myList);

3. Simple Node
   	
 * A SimpleNode has an icon, a label, and up to two ports. 
 	* The label is a SimpleNodeLabel, positioned at the bottom center * of the icon.
	 * The two ports are SimpleNodePort's, one for "input" and one for * "output", assuming a left-to-right "flow".
		DragOnDrop
			-Exporting data from a component..
			The first set of methods we will examine are used for exporting data from a component.
			-Importing data into a component..
			Now we will look at the methods used for importing data into a component. 
	 * El Metodo doUncapturedMouseMove(int paramInt, Point paramPoint1, Point paramPoint2, SAMMSView paramJGoView) cambia el tipo de Cursor del Ratons    

4. SAMMSArea
 Es la clase q pinta a traves del metodo paint()


Funcionalidades...................
1. Movimiento de Arrastre    
	Iniciar la accion de arrastre desde la Paleta (Evento DragGestureEvent)
	Finalizar la accion desde la Vista (Evento DropTargetDropEvent)
	     CANVAS --> public void drop(DropTargetDropEvent e)   
	 	VIEW --> public void onDrop(DropTargetDropEvent paramDropTargetDropEvent)    
	 	
  Funcionamiento de la Vista SAMMSView
     public void onDrop(DropTargetDropEvent paramDropTargetDropEvent)
     	Final del arrastre y creacion del objeto SimpleNode

     public boolean doMouseUp(int modifiers, Point dc, Point vc)
     
  