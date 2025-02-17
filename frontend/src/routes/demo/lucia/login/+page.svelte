<script lang="ts">
	import { enhance } from '$app/forms';
	import type { ActionData } from './$types';

	let { form }: { form: ActionData } = $props();
</script>

<div class="flex h-screen items-center justify-center bg-black text-white">
	<div class="w-full max-w-md rounded-lg bg-gray-900 p-8 shadow-lg">
		<h1 class="mb-6 text-center text-2xl font-bold">Login/Register</h1>
		<form method="post" action="?/login" use:enhance class="flex flex-col gap-4">
			<label class="flex flex-col">
				<span class="mb-1 text-gray-300">Username</span>
				<input
					type="text"
					name="username"
					class="rounded-md border border-gray-700 bg-gray-800 p-2 focus:ring focus:ring-blue-500"
				/>
			</label>
			<label class="flex flex-col">
				<span class="mb-1 text-gray-300">Password</span>
				<input
					type="password"
					name="password"
					class="rounded-md border border-gray-700 bg-gray-800 p-2 focus:ring focus:ring-blue-500"
				/>
			</label>
			<div class="flex justify-between">
				<button class="rounded-md bg-blue-600 px-4 py-2 hover:bg-blue-700">Login</button>
				<button
					formaction="?/register"
					class="rounded-md bg-green-600 px-4 py-2 hover:bg-green-700"
				>
					Register
				</button>
			</div>
		</form>
		<p class="mt-4 text-red-500">{form?.message ?? ''}</p>
	</div>
</div>
