<svelte:head>
	<title>About</title>
	<meta name="description" content="About this app" />
</svelte:head>

<section>
<div class="text-column">
	<h1>About Wu Tournaments</h1>

	<p>Wu tournaments are organised weekly tournaments held at Wimbledon Racquets & Fitness Club</p>
	<p>Participation is invite-only via the offial Wu Badminton Whatsapp group</p>
	<p>Each week, invited players may sign up using the weekly password</p>

	<h1>About this app</h1>

	<p>
		This webapp was created to simplify organising and running of Wu tournaments.<br>
		It's built using Svelte, with a nodejs backend<br>
		Details on <a href="">GitHub</a>
	</p>
</div>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
		width: 100%;
		flex-direction: column;
		margin:1rem;
	}

	p {
		text-align: center;
	}
</style>