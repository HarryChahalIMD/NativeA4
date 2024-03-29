<script>
      import '../style.css';
     import { onMount } from 'svelte';
   
     let todoItem = '';
     let todoList = [];
   
     function addToArray() {
       if (!todoItem.trim()) {
         return;
       }
       todoList = [...todoList, {
         text: todoItem,
         done: false
       }];
       todoItem = '';
     }
   
     function removeThis(index) {
       todoList.splice(index, 1);
       todoList = [...todoList];
     }
   
     onMount(() => {
       const todoContainer = document.getElementById('todo-container');
       todoContainer.scrollTop = todoContainer.scrollHeight;
     });
   </script>

   <div class="navbar">
     <p class="navbar-title">ToDo List</p>
   </div>

   <div class="trending-card">
     <h2 class="trending-card-title">Trending Anime</h2>
     <ul class="trending-anime-list">
       <li>Naruto</li>
       <li>Attack on Titan</li>
       <li>MHA</li>
       <li>DBZ</li>
       <li>IMD</li>
       <li>LUCY</li>
       <li>Shrek</li>
       <li>Ogy</li>
       <li>OnePiece</li>
       
     </ul>
   </div>


   <h1>Anime To Watch This Year</h1>
   
   <form on:submit|preventDefault={addToArray}>
     <input type="text" placeholder="Add an anime to watch" bind:value={todoItem} />
     <button type="submit">Add Anime</button>
   </form>
   
   <div id="todo-container" class="todo-container">
     <div class="todo-card">
       <h2>WatchList:</h2>
       <ul>
         {#each todoList as anime, index }
           <li>
             <input type="checkbox" bind:checked={anime.done} />
             <span class:done={anime.done}>{anime.text}</span>
             <span on:click={() => removeThis(index)} class="remove" role="button">&times;</span>
           </li>
         {/each}
       </ul>
     </div>
   </div>

   


<style>
      .todo-container {
    display: flex;
    justify-content: center;
    align-items: flex-start; 
    height: 30vh;
    flex-direction: column; 
  }

  .todo-card {
     max-height: 70vh; 
    overflow-y: auto; 
    width: 300px;
    padding: 18px;
    background-color: rgb(45, 43, 43);
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    margin-top: 40px; 
  }

             /* scroll bar additional property done by the help of ChatGPT, and then custumize it. */

  /* Styles for the scrollbar */
  .todo-card::-webkit-scrollbar {
    width: 12px; /* Width of the scrollbar */
  }

  /* Track */
  .todo-card::-webkit-scrollbar-track {
    background: rgb(45, 43, 43); /* Color of the track */
  }

  /* Handle */
  .todo-card::-webkit-scrollbar-thumb {
    background: #888; /* Color of the scroll handle */
    border-radius: 10px; /* Rounded corners for the handle */
  }

  /* Handle on hover */
  .todo-card::-webkit-scrollbar-thumb:hover {
    background: #555; /* Color of the scroll handle on hover */
  }

     ul {
    list-style: none;
    padding: 20px;
    margin: 0;
    color: burlywood;
  }

  li {
    font-size: 1.3rem;
    background-color: rgb(21, 19, 19);
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

  .navbar {
    background-color: rgb(14, 81, 92);
    color: #fff;
    padding: 10px 0;
    text-align: center;
    position: fixed; 
    width: 100%; 
    top: 0; 
    z-index: 1000; 
  }

  .navbar-title {
    margin: 0;
    font-size: 1.5rem;
  }
  p{
     color:rgb(141, 191, 235);
     font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  }
</style>