# vue-web-component-issue
Example repo of issue with vue cli 3 and web components


## shared-ui
Project that is compiled to web component (`--target wc --name shared-ui ./src/components/*.vue`)

## shared-ui-consumer
Project that imports shared-ui and attempts to render an element inside of Collapsible Component. 


## Update (workaround found)
I found a workaround for this that doesn't require any modifications to Vue or plug-ins and it appears to be working across all major browsers. 

Basically just wire up the `$nexttick` event to clear out the innerHTML of the parent of the slot element and insert a new slot. I answered my own question on StackOverflow so you can see the working example here: https://stackoverflow.com/questions/55169976/how-to-properly-use-slot-inside-of-vue-js-web-component-and-apply-styles/55712612#55712612
