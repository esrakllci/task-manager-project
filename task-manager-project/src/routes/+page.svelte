<script lang="ts">
	import Card from '$lib/components/Card.svelte';
	import MemberDrawer from '$lib/components/MemberDrawer.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
	import TaskDrawer from '$lib/components/TaskDrawer.svelte';
	import ShowAll from '$lib/components/ShowAll.svelte';
	let taskDrawer = false;
	let memberDrawer = true;
	let taskType = 'All Tasks';
	const handleTask = (e: { detail: string }) => {
		taskType = e.detail;
	};
</script>

<main>
	<div class="dashboard">
		<Sidebar
			on:openTaskDrawer={() => (taskDrawer = true)}
			on:openMemberDrawer={() => (memberDrawer = true)}
			on:changeTask={handleTask}
		/>
		<ShowAll {taskType} />
	</div>

	<TaskDrawer {taskDrawer} on:closeTaskDrawer={() => (taskDrawer = false)} />
	<!-- <Card /> -->
	<MemberDrawer {memberDrawer} on:closeMemberDrawer={() => (memberDrawer = false)} />
</main>

<style>
	.dashboard {
		display: flex;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
