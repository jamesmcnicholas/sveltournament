<script>
	/**
	 * @type {string}
	 */
	 export let name;
</script>

<style>
button {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
  border-radius: 10px;
  border-color: black;
  width: 100%;
}	
	
button:hover {background-color: #ddd}
</style>


<button on:click>{name}</button>