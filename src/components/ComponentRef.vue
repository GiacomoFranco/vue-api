<template>
    <!-- <h1>Este es el componente ComponentRef</h1> -->
    <div><h1>erda</h1></div>
    <!-- Bindear múltiples attrs -->
    <h1 v-bind="attrs" >acá deben de verse reflejados los attrs</h1>
    <H1 v-bind:[argVariable]="'bindeo'" >Bindeo argumentos</H1>
    <H1 :[argVariable]="'depende'">ShortHand del bindeo de argumentos</H1>
    <button @[argHandler]="funcArgHandler">HOVER me, and look at the console</button>
    <!-- SI ESTE FEATURE SE ESCRIBE EN HTML Y NO DENTRO DE UN SFC TIENE QUE USARSE LAS MINÚSCULAS, DE OTRA FORMA NO VA A AGARRAR LA VARIABLE, POR QUE EN LOS ELEMENTOS DEL DOM LOS TRADUCE A MINÚSCULAS  -->
    <p>{{ globalVar }}</p>
    <p>{{ textToInject }}</p>
    <p>{{defaultInjected}}</p>
    <div >
        <p ref="itemsRef" v-for="(item, index) in array" :key="index" :class="`text-${index + 1}`">{{ item }}</p>
    </div>
    <p :id="`text-${id}`">bindeando a una clase con variable en el v-bind:</p>

</template>

<script>

export default {
    name: 'componentRef',
    expose: ['id'], // NORMALMENTE AL NO TENER EXPOSE SE PUEDEN VER TODOS LOS METODOS / VARIABLES / COMPUTADAS DE ESTE COMPONENTE EN EL PADRE SI SE ACCEDE POR MEDIO DE $REFS
    data() {
        return {
            attrs: {
                id: 'idPorMedioDeBinding',
                class: 'classPorMedioDeBinding'
            },
            id: 'bindeando con : en un v-bind y no con {{}}',
            argVariable: 'class',
            argHandler: 'mouseover',
            globalVar: this.$root.globalData,
            id: '1',
            array: ['texto1', 'texto2', 'texto3', 'texto4', 'texto5'],
        }
    },
    // inject: ['textToProvide'],
    inject: {
        textToInject: {
            from: 'textToProvide',
        },
        defaultInjected: {
            from: 'noExiste',
            default: 'Lol, si no hay un componente que tenga el provide al que se hace referencia se le puede asignar un valor predeterminado :)'
        }
    },
    // de esta forma, dentro del componente le podemos asignar un nombre distinto al que se le da en provide :)
    methods: {
        funcArgHandler(){
            console.log('hey, es dinámico');
        },
    },
    mounted() {
        console.log(this.$el);
        console.log(this.$root);
        console.log(this.$refs.itemsRef);
    }
}

</script>
