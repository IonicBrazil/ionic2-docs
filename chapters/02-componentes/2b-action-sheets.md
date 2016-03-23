Action Sheets (Folhas de Ação)
-----------

Action Sheets, deslizam para cima a partir da borda inferior da tela do dispositivo, e exibe um conjunto de opções com a capacidade de confirmar ou cancelar uma ação. Action Sheets podem por vezes, ser usado como uma alternativa para os menus, no entanto, eles não devem ser utilizados para a navegação.
	   
O Action Sheet aparece sempre acima de quaisquer outros componentes na página, e deve ser descartado se quer interagir com o conteúdo que fica por baixo.
Quando é acionado, o resto da página escurece para dar mais foco nas opções do Action Sheet.


### Uso Básico


    presentActionSheet() {
	
	    let actionSheet = ActionSheet.create({
	    
	    title: 'Modify your album',
	    
	    buttons: [
	      {
	        text: 'Destructive',
	        
	        style: 'destructive',
	        
	        handler: () => {
	        
	          console.log('Destructive clicked');
	          
	        }
	      },{
	        text: 'Archive',
	        
	        handler: () => {
	        
	          console.log('Archive clicked');
	          
	        }
	      },{
	        text: 'Cancel',
	        
	        style: 'cancel',
	        
	        handler: () => {
	        
	          console.log('Cancel clicked');
	          
	        }
	      }
	    ]
	    });
    this.nav.present(actionSheet);
    }