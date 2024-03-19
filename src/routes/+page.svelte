<script>
     import '../style.css';
     let todoItem = '';
     let todoList = [];
     function addToArray(){
          if (todoItem == '') {
               return;
          }
          todoList = [...todoList, {
               text: todoItem,
               done: false
          }]
          
          
          console.log(todoList);
          todoItem= '';
     }
     function removeThis(index){
          todoList.splice(index, 1);
          todoList = todoList;
     }

</script>
<h1>Welcome to Our ToDo APP</h1>
<form on:submit|preventDefault={addToArray}>
     <input type= "text" bind:value={todoItem}>
     <button type = "submit">Submit</button>
</form>
<ul>
{#each todoList as product, index }
 <li> <input type="checkbox" bind:checked= {product.done}>
    <span class:done= {product.done}> {product.text}</span>  
    <span on:click={()=> removeThis(index)} class="remove" role="button" >&times;</span>
</li>
 {/each}
</ul>

<style>
     ul{
          list-style: none;
     }
     .done{
          color: #ccc;
          text-decoration: line-through;
     }
     li{
          font-size: 1.3rem;
     }
     .remove{
          color: brown;
          cursor: pointer;

     }
</style>