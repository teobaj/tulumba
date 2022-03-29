<script lang="ts">
import { name, parsedObject } from "./store/store";


  function displayValue(key: string, value: any){
    
  }

  function isArray(value: object){
    return !!value[0]
  }

  function displayInterface(obj: any, padding = 20){
    let template = '<code>';
    Object.entries(obj).forEach(([key, value]) => {
      if(typeof value === 'object'){
        if(isArray(value)){
          template += `<p style="margin:0; padding:0;padding-left: ${padding}px;"><span style="color:#D39A67;">${key}</span>: Array<{${displayInterface(value[0], padding+20)} <span style="padding-left:${padding}px; color=#60AFEE">}></span> </p>`
        } else{

         template = template + `<p style="margin:0; padding:0; padding-left:${padding}px;"><span style="color:#D39A67;">${key}</span>: {${displayInterface(value, padding+20)} <span style="padding-left:${padding}px; color:#60AFEE">}</span></p>`

        } 
        
      } else {
        template = template + `<p style="margin:0;padding:0; padding-left:${padding}px;"><span style="color:#D39A67;">${key}</span>:<span style="color:#60AFEE">${value}</span></p>`
      }        
    })
    template +="</code>"
    return template
  }

  function renderOpenBracket(iname: string){
    return `<code><span style="color:#60AFEE">export</span> <span style="color: #C778DD">interface</span> <span style="color:#D39A67">${iname}</span> {</code>`

  }
  
  function renderCloseBracket(){
    return `<code>}</code>`
  }

</script>

<div class="result">
  <div class="code">

  {@html renderOpenBracket($name)} 
  {@html displayInterface($parsedObject)}
  {@html renderCloseBracket()}


  </div>
</div>
<style>
  * {
    font-weight: 600;
    color: #fff;
  } 
  .result {
    padding: 1rem;
    background-color: var(--bg-color);
  }
  p{
    margin:0;
    padding:0;
  }

  .code {
    padding: 1rem;
    background-color:var(--code-bg-color) ;
  }
</style>
