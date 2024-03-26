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
<h1>Anime To Watch This year</h1>
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
     ul {
    list-style: none;
    padding: 20px;
    margin: 0;
  }

  li {
    font-size: 1.3rem;
    background-color: #82cae0;
    border-radius: 8px;
    padding: 10px;
    margin-bottom: 8px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .done {
    color: #888;
    text-decoration: line-through;
  }

  .remove {
    color: #8b0000;
    cursor: pointer;
    font-weight: bold;
  }

  .remove:hover {
    color: #ff0000;
  }
</style>