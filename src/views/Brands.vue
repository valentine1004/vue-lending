<template>
	
		<div id="taskApp">
			<h1>Todo Task List App</h1>
             <!-- Add new task form -->
             <div class="panel panel-default">
             	<h2>Add New Task</h2>

             	<form v-on:submit="addTask">
             		<div class="container-fluid">
             			<div class="col-sm-8">
             				<input type="text" class="form-control" v-model="tasks.name">
             			</div>

             			<div class="col-sm-4">
             				<input type="submit" value="Add" class="btn btn-primary btn-block">
             			</div>
             		</div>
             	</form>
             </div>

            <table class="table">
            	<thead>
            		<th>Checkmark Done</th>
            		<th>Task Name</th>
            		<th>Delete</th>
            	</thead>

            	<tbody>
            		<tr v-for="task in tasks">
            			<td><input type="checkbox" v-model="task.done"></td>
            			<td><span :class="{taskDone: task.done}">{{task.name}}</span></td>
            			<td><button class="btn btn-danger btn-block" v-on:click="deleteTask(task)">Delete</button></td>
            		</tr>
            	</tbody>
            </table>


		</div>
	
</template>

<script>
module.exports = {
	data:function(){
		return{
			tasks:[
			{name: 'gotta do this task first',done:false},
			{name: 'buy some pet food',done:false},
			{name: 'install fishtank in living room',done:false}
			]

		}
	},
	methods:{
		addTask: function(e){
			e.preventDefault();
			this.tasks.push({
				name: this.tasks.name,
				done: false
			})
		},
		deleteTask: function(task){
           this.tasks.splice(this.tasks.indexOf(task),1)
		}
	}
};
</script>

<style>
	#taskApp{
		padding-top: 80px;
		margin:0 auto;
		width:980px;
	}
	#taskApp h1{
		padding-bottom: 60px; 
	}
	.panel{
		padding: 20px;
	}
	.taskDone{
		text-decoration: line-through;
	}
</style>