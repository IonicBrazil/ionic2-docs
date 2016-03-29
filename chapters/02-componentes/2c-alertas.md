# Alertas

Alertas são uma ótima forma de oferecer ao usuário a habilidade de escolher uma ação específica ou uma lista de ações. Eles também podem prover ao usuário importantes informações ou requerer dele que tome uma decisão (ou várias decisões).

De uma perspectiva de interface de usuário, você pode imaginar os alertas como um tipo de modal flutuante, que cobre apenas uma parte da tela. Isso significa que alertas apenas podem ser usados para rápidas ações como verificaçao se senhas, pequenas notificações ou ações rápidas. O fluxo mais complexo do usuário deve ser reservado para a tela cheia.

Alertas são bastante flexíveis, e podem ser customizados facilmente. Dê uma olhada em [API docs](http://github.com) para mais informações.

* [Contents](http://github.com)
* [Basic Alerts](http://github.com)
* [Prompt Alerts](http://github.com)
* [Confirmation Alerts](http://github.com)
* [Radio Alerts](http://github.com)
* [Checkbox Alerts](http://github.com)

## Utilização básica:

Alertas básicos são geralmente usados para notificar o usuário sobre novas informações (uma modificação no app, uma nova funcionalidade), uma situação urgente que requer reconhecimento, ou como uma confirmação para o usuário que uma ação foi teve sucesso ou não.

```
  doAlert() {
    let alert = Alert.create({
      title: 'New Friend!',
      subTitle: 'Your friend, Obi wan Kenobi, just accepted your friend request!',
      buttons: ['Ok']
    });
    this.nav.present(alert);
  }
```

## Prompt Alerts

Prompts offer the user a way to input data or information. For example, often times Prompt Alerts will be used to ask the user for password confirmation as a means of security before moving forward in an app’s ux flow.
```
    let prompt = Alert.create({
      title: 'Login',
      message: "Enter a name for this new album you're so keen on adding",
      inputs: [
        {
          name: 'title',
          placeholder: 'Title'
        },
      ],
      buttons: [
        {
          text: 'Cancel',
          handler: data => {
            console.log('Cancel clicked');
          }
        },
        {
          text: 'Save',
          handler: data => {
            console.log('Saved clicked');
          }
        }
      ]
    });
```

## Confirmation Alerts

Confirmation Alerts are used when it is required that the user explicitly confirms a particular choice before progressing forward in the app. A common example of the Confirmation Alert is checking to make sure a user wants to delete or remove a contact from their address book.

```
    let confirm = Alert.create({
      title: 'Use this lightsaber?',
      message: 'Do you agree to use this lightsaber to do good across the intergalactic galaxy?',
      buttons: [
        {
          text: 'Disagree',
          handler: () => {
            console.log('Disagree clicked');
          }
        },
        {
          text: 'Agree',
          handler: () => {
            console.log('Agree clicked');
          }
        }
      ]
    });
```

## Radio

Radio Alerts are simply another type of Confirmation Alert, but use the Radio component to offer several choices. They offer the user a set of options to choose from, but are allowed to only make one final selection before continuing forward.

```
  doRadio() {
    let alert = Alert.create();
    alert.setTitle('Lightsaber color');

    alert.addInput({
      type: 'radio',
      label: 'Blue',
      value: 'blue',
      checked: true
    });

    alert.addButton('Cancel');
    alert.addButton({
      text: 'Ok',
      handler: data => {
        this.testRadioOpen = false;
        this.testRadioResult = data;
      }
    });
```

## Checkbox

Checkbox Alerts are simply another type of Confirmation Alert, but use the Checkbox component to offer several choices. They offer the user a set of options to choose from.

```
  doCheckbox() {
    let alert = Alert.create();
    alert.setTitle('Which planets have you visited?');

    alert.addInput({
      type: 'checkbox',
      label: 'Alderaan',
      value: 'value1',
      checked: true
    });

    alert.addInput({
      type: 'checkbox',
      label: 'Bespin',
      value: 'value2'
    });

    alert.addButton('Cancel');
    alert.addButton({
      text: 'Okay',
      handler: data => {
        console.log('Checkbox data:', data);
        this.testCheckboxOpen = false;
        this.testCheckboxResult = data;
      }
    });
  }
```
