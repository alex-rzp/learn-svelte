<script>
	let name = '';
	let email = '';
	let gender = '';
	let programmingLang = [];
</script>

<main class="grid md:grid-cols-2 gap-4">
	<section class="space-y-4">
		<h1 class="text-3xl">User Form</h1>
		<form class="space-y-2">
			<div class="flex flex-col">
				<label for="name" class="text-xl">Name</label>
				<input type="text" id="name" name="name" class="border p-2 rounded-md" bind:value={name} />
			</div>
			<div class="flex flex-col">
				<label for="email" class="text-xl">Email</label>
				<input
					type="email"
					id="email"
					name="email"
					class="border p-2 rounded-md"
					bind:value={email}
				/>
			</div>
			<div class="flex flex-col">
				<label for="gender" class="text-xl">Gender</label>
				<select id="gender" name="gender" class="border p-2 rounded-md" bind:value={gender}>
					<option value="male">Male</option>
					<option value="female">Female</option>
					<option value="other">Other</option>
				</select>
			</div>
			<!-- multi select programming lang of interest -->
			<div class="flex flex-col">
				<label for="programming-lang" class="text-xl">Programming Languages</label>
				<select
					id="programming-lang"
					name="programming-lang"
					class="border p-2 rounded-md"
					multiple
					bind:value={programmingLang}
				>
					<option value="javascript">JavaScript</option>
					<option value="typescript">TypeScript</option>
					<option value="python">Python</option>
					<option value="java">Java</option>
					<option value="c">C</option>
					<option value="cpp">C++</option>
					<option value="go">Go</option>
				</select>
			</div>
		</form>
	</section>
	<section class="space-y-4">
		<h1 class="text-3xl">View Form Data</h1>
		<div class="space-y-2">
			<p class="text-xl">Name: {name}</p>
			<p class="text-xl">Email: {email}</p>
			<p class="text-xl">Gender: {gender}</p>
			<p class="text-xl">Programming Languages: {programmingLang.join(', ')}</p>
		</div>
	</section>
</main>
