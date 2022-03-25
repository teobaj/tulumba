<script lang="ts">
import { parsedObject } from "./store/store";
import { onMount } from 'svelte'


let response: string;
let hasError: boolean = false;

function transformToType(value: any){
  

  if(typeof value === 'object' && value !== null){
    let objType = {};
    Object.entries(value).forEach(([key,value]) => {
      objType[key] = transformToType(value);
    }) 
    return objType;
  }
  return typeof value
}

function parseStringToJson(text: string){
  try {
    hasError = false;
    const obj = JSON.parse(text);
    let typeObj = {};
  
    Object.entries(obj).forEach(([key,value]) => {
      typeObj[key] = transformToType(value);
    })
    return typeObj;
  } catch (error) {
    hasError = true;    
  }
}

function setStore(){
  let obj = parseStringToJson(response)
  if(obj){
    parsedObject.set(obj)
  }
}

function handlePostMessage(event: any){
  if(event.data.type === 'transform'){
    setStore();
  }
}

onMount(() => {
  window.addEventListener('message', handlePostMessage)
})

</script>

<div class="json">
  {#if hasError}
    <p style="color: red">Invalid Json</p>
  {/if}
  <textarea bind:value={response}></textarea>
</div>

<style>
.json {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: var(--bg-color);
  border: 1px solid var(--tertiary-color);
  padding: 1rem;
}
textarea {
  width: calc(100% - 1rem);
  height: calc(100% - 1rem);
  padding: 0.5rem;
  background-color: var(--code-bg-color);
  color: #fff;
}
</style>
