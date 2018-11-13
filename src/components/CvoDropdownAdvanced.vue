<template>
    <div class="dropdown">
        <div class="handle" @click="isOpen = !isOpen">
            <div class="handle-tekst">
                {{ actieveKeuze ? actieveKeuze : "Kies een item" }}
            </div>
            <div class="handle-pijl">
                <svg v-show="!isOpen" enable-background="new 0 0 32 32" version="1.1" viewBox="0 0 32 32">
                    <g>
                        <rect fill="none" height="32" width="32" />
                    </g>
                    <g>
                        <polygon points="2.002,10 16.001,24 30.002,10  " />
                    </g>
                </svg>
                <svg v-show="isOpen" enable-background="new 0 0 32 32" version="1.1" viewBox="0 0 32 32">
                    <g>
                        <rect fill="none" height="32" width="32" />
                    </g>
                    <g>
                        <polygon points="30,22 16.001,8 2.001,22  " />
                    </g>
                </svg>
            </div>
        </div>
        <ul class="list" v-show="isOpen">
            <li v-for="keuze of keuzes" :key="keuze" @click="kiesItem(keuze)">{{ keuze }}</li>
        </ul>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                isOpen: false
            }
        },
        props: {
            keuzes: Array,
            value: String
        },
        computed: {
            actieveKeuze() {
                return this.value; 
            }
        },
        methods: {
            kiesItem(keuze) {
                this.$emit("input", keuze);
                this.isOpen = false;
            }
        },
    }
</script>

<style>
    .dropdown {
        width: 200px;
    }

    .dropdown .handle {
        height: 50px;
        margin: 0;
        padding: 0.5em;
        background: darkorchid;
        color: white;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .handle-pijl {
        fill: white;
        width: 20px;
        height: 20px;
    }

    .list {
        list-style: none;
        margin: 0;
        padding: 0;
        background: orchid;
    }

    .list li {
        /* text-align: center; */
        height: 40px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-top: 1px solid black;
        color: white;
    }

    .list li:hover {
        background: darkorchid;
    }
    
</style>