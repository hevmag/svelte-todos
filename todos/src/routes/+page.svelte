<script>
    let completeCount = 0;
    let newTodo = "";
    let todos = [];
    let completedTodos =[]
    
    function addTodo() {
        if (!!newTodo) {
            const newTodoEntry = {
            task: newTodo,
            completed: false
            };
            todos = [...todos, newTodoEntry];
            newTodo = "";
        };
    };

    function removeTodo(i){
        const toDelete = todos[i];
        todos = todos.filter((todo) => todo !== toDelete);
    };

</script>

<main class="container">
    <nav>
        Logbook
    </nav>
<header>
    <h1>What do you want to do today?</h1>
    <h2>{completeCount} tasks completed so far</h2>
</header>

<section>
        {#each todos as todo, i}
            <div class="todo-card">
                <span class={todo.completed === true ? "todo-checked" : "todo"}>{todo.task}</span>
                <button 
                class="check-button" 
                disabled={todo.completed !== true ? false : true} 
                on:click={() => {
                    todo.completed = true
                    completeCount += 1
                    completedTodos = [...completedTodos, todo]
                    }}>
                    ✅
                </button>
                <button class="cross-button" on:click={()=>{removeTodo(i)}}>
                    ❎
                </button>
            </div>
        {/each}
    <form on:submit|preventDefault={addTodo}>
        <label>
            <input type="task" bind:value={newTodo} placeholder="Add a task" >
        </label>
        <button class="add-task-button">+</button>
    </form>
    <button on:click={() => {todos = []}}>Clear</button>
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
    button {
        padding: 0;
        border: none;
    }
    .todo-card {
        border: 1px solid black;
        padding: 20px;
        border-radius: 20px;
        margin-bottom: 15px;
        font-size: 1rem;
        align-items: center;
    }
    .todo-checked {
        text-decoration: line-through;
    }
</style>
