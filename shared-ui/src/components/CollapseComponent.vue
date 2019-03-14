<template>
    <div :class="[$style.collapsableComponent]">
        <div :class="[$style.collapsableHeader]" @click="onHeaderClick" :title="title">
            <span>{{ title }}</span> 
        </div>
        <div :class="[$style.collapsableBody]" v-if="expanded">
            <slot name="body-content"></slot>
        </div>
    </div>
</template>

<script lang="ts">
    import { Vue, Component, Prop } from 'vue-property-decorator'

    @Component({})
    export default class CollapsableComponent extends Vue {
        @Prop({ default: "" })
        title!: string;

        @Prop({default: false})
        startExpanded!: boolean;

        private expanded: boolean = false;

        constructor() {
            super();
            this.expanded = this.startExpanded;
        }

        get isVisible(): boolean {
            return this.expanded;
        }

        onHeaderClick(): void {
            this.toggle();
        }

        public toggle(expand?: boolean): void {
            if(expand === undefined) {
                this.expanded = !this.expanded;
            }
            else {
                this.expanded = expand;
            }
            this.$emit(this.expanded? 'epxand' : 'collapse');
        }

        public expand() {
            this.expanded = true;

        }

        public collapse() {
            this.expanded = false;
        }
    }
</script>

<style module>
    :host {
        display: block;
    }

    .collapsableComponent {
        background-color: white;
    }

    .collapsableHeader {
        border: 1px solid grey;
        background: grey;
        height: 35px;
        color: black;
        border-radius: 15px 15px 0 0;
        text-align: left;
        font-weight: bold;
        line-height: 35px;
        font-size: 0.9rem;
        padding-left: 1em;
    }

    .collapsableBody {
        border: 1px solid black;
        border-top: 0;
        border-radius: 0 0 10px 10px;
        padding: 1em;
    }
</style>
