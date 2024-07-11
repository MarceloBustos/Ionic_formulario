<template>
    <ion-page>
        <ion-header>
            <ion-toolbar>
                <ion-title>Formulario</ion-title>
            </ion-toolbar>
        </ion-header>
        <ion-content class="ion-padding">
            <ion-grid>
                <ion-row>
                    <ion-col>
                        <h1>Input</h1>
                        <ion-input label="Nombre:" label-placement="floating" placeholder="Escriba su nombre"
                            maxlength="15" :counter="true" :clear-input="true" color="primary"
                            v-model="nombre"></ion-input>

                        <h1>Select</h1>
                        <ion-select label="paises" placeholder="Seleccionar" label-placement="stacked" fill="solid"
                            cancel-text="Cerrar" ok-text="Seleccionar" color="primary" v-model="pais">
                            <ion-select-option value="Chile">Chile</ion-select-option>
                            <ion-select-option value="El Salvador">El Salvador</ion-select-option>
                            <ion-select-option value="Honduras">Honduras</ion-select-option>
                            <ion-select-option value="Guatemala">Guatemala</ion-select-option>
                        </ion-select>

                        <h1>Checkbox</h1>
                        <ion-checkbox label-placement="end" color="primary" value="Playstation" v-model="consolas[0]">
                            Playstation
                        </ion-checkbox><br>
                        <ion-checkbox label-placement="end" color="primary" value="Xbox" v-model="consolas[1]">
                            Xbox
                        </ion-checkbox><br>
                        <ion-checkbox label-placement="end" color="primary" value="Nintendo Switch"
                            v-model="consolas[2]">
                            Nintendo Switch
                        </ion-checkbox>

                        <h1>Radio</h1>
                        <ion-radio-group allow-empty-selection="true" v-model="genero">
                            <ion-radio value="Mujer" label-placement="end" color="primary">Mujer</ion-radio><br>
                            <ion-radio value="Hombre" label-placement="end" color="primary">Hombre</ion-radio>
                        </ion-radio-group>

                        <br><br><br><br>
                        <ion-button color="primary" expand="block" shape="round"
                            @click="imprimirDatos()">Enviar</ion-button>
                    </ion-col>
                </ion-row>

                <ion-row>
                    <ion-col v-show="datos">
                        <h2>Impresión</h2>
                        <div v-html="datos"></div>
                    </ion-col>
                </ion-row>
            </ion-grid>
        </ion-content>
    </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonContent, IonGrid, IonRow, IonCol, IonInput, IonSelect, IonSelectOption, IonCheckbox, IonRadioGroup, IonRadio, IonButton } from '@ionic/vue';

export default {
    name: 'FormsComponents',
    components: { IonPage, IonHeader, IonToolbar, IonContent, IonGrid, IonRow, IonCol, IonInput, IonSelect, IonSelectOption, IonCheckbox, IonRadioGroup, IonRadio, IonButton },
    data() {
        return {
            nombre: '',
            paises: '',
            consolas: [],
            genero: '',
            datos: ''
        }
    },
    methods: {
        imprimirDatos() {
            let consolasSeleccionadas = ''
            consolasSeleccionadas += (this.consolas[0]) ? 'Playstation <br>' : ''
            consolasSeleccionadas += (this.consolas[1]) ? 'Xbox <br>' : ''
            consolasSeleccionadas += (this.consolas[2]) ? 'Nintendo Switch <br>' : ''

            this.datos =
                '<h3>Nombre: </h3>' + this.nombre + '<br>' +
                '<h3>Pais: </h3>' + this.pais + '<br>' +
                '<h3>Consolas: </h3>' + consolasSeleccionadas + '<br>' +
                '<h3>Genero: </h3>' + this.genero + '<br>'

            //imprimir en consola el resultado
            console.log(this.datos);
        }
    }
}
</script>

<style></style>