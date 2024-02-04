<script>
	import DropdownButton from './DropdownButton.svelte';
	import PasswordButton from './PasswordButton.svelte';
	import Partner from './Partner.svelte'
	import SearchInput from './SearchInput.svelte'
	import Modal from './Modal.svelte'

	let menuOpen = false;
	let passwordTrue = false;
	var players = ['Sameer', 'Wu', 'Varshan', 'Subas', 'Gurav']
	let inputValue = "";
	let playerName = "";
	let passwordInput = ""
	const password = "test123"
	let response = "";
	let selectedPartner = "";
	let showModal = false;
	
	/**
	 * @type {string | any[]}
	 */
	let filteredPartnerNames = [];
	const handleInput = () => {
		return filteredPartnerNames = players.filter(player => player.toLowerCase().match(inputValue.toLowerCase()))
	}

	function checkPassword(){
		passwordTrue = passwordInput == password;
		if(!passwordTrue){
			response = "Incorrect Password"
		}
	}

	function addPlayer(){
		if(playerName != ""){
			showModal = true;
			if(!(players.indexOf(playerName) !== -1)){
				players = [...players, playerName]
				console.log(players)
			}
		}
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>


<h1>
	Next tournament<br />Tuesday 13th February
</h1>


{#if !passwordTrue}
<section class=signup>
	<h1>
		Enter this week's password to sign up
	</h1>
	<div class="horizontal-div">
		<input type=password id=passwordField  bind:value={passwordInput}>
		<PasswordButton on:click={() => checkPassword()}/>
	</div>
	<h2>{response}</h2>
</section>

{:else}
	<section class=signup>
		<div class="vertical-div">
			<h2>Password Correct</h2>
			<h1>Sign up below!</h1>
			<div class="horizontal-div">
				<input placeholder="Name" bind:value={playerName}>
				<DropdownButton on:click={() => menuOpen = !menuOpen} {menuOpen} />
			</div>

			{#if menuOpen}
				<div class="dropdown-content">		
					<SearchInput bind:inputValue on:input={handleInput} />		
						{#if filteredPartnerNames.length > 0}
							{#each filteredPartnerNames as partnerName}
								<Partner name={partnerName} on:click={() => selectedPartner = partnerName}/>
							{/each}
						{:else}
							{#each players as partnerName}
								<Partner name={partnerName}  on:click={() => selectedPartner = partnerName}/>
							{/each}
						{/if}		
				</div>
			{/if}
			
			{#if selectedPartner != ""}
				<div class="horizontal-div">
					<p>Partner: {selectedPartner || "Not Selected"}</p>
					<button class=remove-button on:click={() => selectedPartner = ""}>Remove</button>
				</div>	
			
			{/if}
			
			{#if playerName != ""}
				<button class=confirm-button on:click={() => {addPlayer()}}>Confirm Entry</button>
			{/if}

		</div>
	</section>
{/if}

<section>
	<Modal bind:showModal>
		<h2 slot="header">Confirm entry</h2>
		<h2>Confirm the following entry for the tournament:</h2>
		<p>Name: {playerName}</p>
		{#if selectedPartner != ""}
			<p>Partner: {selectedPartner}</p>
			<p>Note: selecting a partner will remove them from the list of available partners for everyone else</p>
		{:else}
			<p>No partner selected</p>
			<p>Note: by not selecting a partner, you will be available for other players to select</p>
		{/if}

		<button class=confirm-button>Confirm Entry</button>

	</Modal>
	

</section>




<style>
	/* https://coolors.co/palette/f4f1de-e07a5f-3d405b-81b29a-f2cc8f */
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

	h1 {
		width: 100%;
	}
	
	input {
		border-radius: 1rem;
		padding-left : 1rem;
	}

	button{
		background-color: #81B29A;
		color: white;
		padding: 16px;
		font-size: 16px;
		cursor: pointer;
		border-radius: 15px;
		width: 10rem;
		margin-left: 1rem;
	}

	.confirm-button {
		background-color: #E07A5F;
		margin: 2rem;
		width: 80%;
	}

	.confirm-button:hover{
		background-color: #e68368;
	}

	.remove-button{
		background-color: #F2CC8F;
	}
	
	.dropdown-content {
		position: relative;
		background-color: #f6f6f6;
		border-radius: 10px;
		flex-direction: column;
		margin:1rem;
	}

	.signup {
		position: relative;
		border-radius: 10px;
		display:flex;
		flex-direction: column;
		margin:1rem;
	}

	.vertical-div{
		display: flex;
		flex-direction: column;
		height: 3rem;
		margin: 1rem;
		align-items: center;
	}

	.horizontal-div {
		display: flex;
		flex-direction: row;
	}

</style>
