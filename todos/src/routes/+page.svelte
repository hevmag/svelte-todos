<script>
    let completeCount = 0;
    let newTodo = "";
    let todos = [];
    
    function addTodo() {
        
        if (newTodo !== "") {
            const newTodoEntry = {
            task: newTodo,
            completed: false
            };
            todos = [...todos, newTodoEntry];
            newTodo = "";
        };
    };
</script>

<main class="container">
<header>
    <h1>Cool Todos</h1>
    <h2>{completeCount} tasks completed so far</h2>
</header>
<section>
    <ul>
        {#each todos as todo, i}
            <li>
                {todo.task}
            </li>
        {/each}
    </ul>
    <form on:submit|preventDefault={addTodo}>
        <label>
            <input type="task" bind:value={newTodo} placeholder="Add a task">
        </label>
        <button class="add-task-button">+</button>
    </form>
</section>
<footer>
    Hev 2022
</footer>
</main>


<style>
    h1 {
        color: darkcyan;
    }
    footer {
        position: absolute;
        bottom: 0;
    }
</style>
